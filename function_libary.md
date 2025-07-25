## Stat Getters/Setters:
- getHealth(), setHealth(val), addHealth(val)
- getMaxHealth(), setMaxHealth(val), addMaxHealth(val)
- getXP(), addXP(val)
- getAttack(), setAttack(val), addAttack(val)
- getDefence(), setDefence(val), addDefence(val)

## Flags
- controlsEnabled — flag for enabling/disabling input (used by menu).
- actionButtonAPressed, actionButtonBPressed — flags for A/B button presses (used for interactions).

## Character System
- Character(x, y, spriteSrc, type, customData) — Base class for NPCs and enemies, supports custom data and unique IDs.
- NPC(...), Enemy(...) — Friendly and hostile character constructors.

## Spawning Helpers
- spawnNPC(npcId, x, y) — Spawns an NPC from NPC_DEFINITIONS at a location.
- spawnEnemy(typeId, x, y) — Spawns an enemy from ENEMY_TYPES at a location.
- spawnCharactersForMap(mapIndex) — Spawns all NPCs and enemies for a given map based on their definitions.

## Data Definitions
- NPC_DEFINITIONS — Object mapping NPC IDs to their data (name, sprite, wander area, dialogue, quests, etc).
- ENEMY_TYPES — Object mapping enemy type IDs to their data (name, sprite, stats, wander area, etc).
- ITEM_DEFINITIONS — Object mapping item IDs to their data (name, description, image, stackable, useable, etc).

## Warping/Teleportation
- warpToMap(mapIndex, spawnType) — Warp player to a map and spawn NPCs/enemies.
- tryWarpToMap(targetMapIndex, spawnType, requiredXP) — Warp if player has enough XP.
- checkTeleport() — Handles teleport tile logic and notifications.
- checkBackTeleport() — Handles back-teleport tile logic and notifications.

## Notification & Dialogue System
- notify(text, time) — Show a notification at the top of the screen for a set time.
- dialogue(...lines) — Show a dialogue block at the bottom of the screen, disables player movement, advances on click.
- showDialogueLine(idx) — Internal: advances dialogue lines.

## NPC Interaction
- checkNpcInteraction() — Checks if player is in range of an interactive NPC, shows notification, starts dialogue, and handles NPC facing/stop movement during interaction.
- getDirectionToFace(npc, player) — Helper: returns direction key for NPC to face the player.

## Inventory System
- addItem(itemId, amount) — Add an item to the inventory (stacks if possible).
- removeItem(itemId, amount) — Remove an item from the inventory, shifts items to fill empty slots.
- hasItem(itemId, amount) — Returns true if player has at least `amount` of the item.
- updateInventoryUI() — Renders the inventory grid.
- showItemDropdown(index, slot, def) — Shows dropdown menu for inventory item actions.
- showRemoveAmountPrompt(slot, def) — Shows prompt to remove a specific amount of an item.

## Player Menu Navigation
- openMenu(), closeMenu() — Show/hide the player menu, disables/enables controls, starts/stops stat refresh.
- showInventoryMenu() — Shows the inventory page in the player menu.
- showPlayerMenuMain() — Returns to the main player menu page.
- updatePlayerMenuSprite() — Draws the player sprite in the menu preview.
- updatePlayerMenuStats() — Displays player stats (health, XP, attack, defence) in the menu, updates regularly.

## Drawing & Updating
- updateCharacters() — Updates all NPCs and enemies (AI, movement).
- drawCharacters() — Draws all NPCs and enemies.
- wanderAI(char) — Handles wandering AI for NPCs/enemies (respects isInteracting flag).

## Utility
- Log(type, text) — Log data to screen (e.g. FPS, coords).
- LoadURL(url, callback) — AJAX call for loading map and other data.

