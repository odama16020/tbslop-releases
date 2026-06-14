> 📖 **日本語版マニュアルはこちら → [README_ja.md](README_ja.md)**

---

# tbslop Manual

> 📥 **To download the game, use the "Releases" section on the right side of this page.** It provides the latest Linux / Windows builds.

tbslop is a minimal turn-based tactics game with a text-based interface.
Deploy your units, then combine movement, attacks, skills, and extra actions to clear each map objective within the turn limit.

## Controls

### Keyboard

| Input | Action |
| --- | --- |
| WASD / Arrow keys | Move the cursor. Hold Shift while moving the map cursor to move faster |
| Z / Space | Confirm |
| E / Enter | Confirm, advance menus |
| X / Esc | Cancel |
| R | Toggle danger range |
| L | Show the log |
| H | Unit info / help |
| U | Undo menu |
| Ctrl+U | Quick Undo |
| Ctrl+S / Ctrl+L | Save / Load |
| O | Options |
| Ctrl+C | Quit confirmation |
| Ctrl+Q | Return to stage selection during a game |
| 0-9 | Jump to the corresponding player unit |

On stage selection, press `L` to open the load screen. During a game, confirming a tile without a unit opens the menu.

### XInput

| Input | Action |
| --- | --- |
| D-pad / Left stick | Move the cursor |
| A | Confirm |
| B | Cancel |
| X | Undo menu |
| Y | Unit info / help |
| LB / RB | Move the cursor to the previous/next living player unit. In save/load screens, switch tabs |
| LT | Show the log |
| RT | Toggle danger range |
| START | Load on stage selection. Start during deployment. Open the phase menu during player phase |
| SELECT / Back | Options |
| L3 | Jump to the boss |

When enemy phase is set to manual progression, A or B advances to the next enemy action, and START opens skip confirmation.

### Basics

- During deployment on regular maps, choose units and place them on candidate deployment tiles marked by `$`. Once you have deployed up to the maximum number, you can start the map. Tutorial maps use fixed unit placement.
- During player phase, select a player unit, choose its destination, then choose a command such as attack, skill, extra, or wait.
- During enemy phase, enemy AI acts. With manual enemy phase progression, you can inspect enemy actions one at a time.

## Game Rules

### Basics

You win by completing the map objective within the turn limit. Most maps require defeating all enemies or defeating the boss.
You lose if all player units are defeated, or if you have not won by the end of the enemy phase on the final turn.

Phases proceed as `Deployment -> Player Phase -> Enemy Phase -> Player Phase...`. By default, the turn does not end automatically even after every player unit has acted, so choose end turn from the phase menu when needed. This can be changed in settings.

### Movement And Terrain

Movement is four-directional. Each unit can move up to its `Mv` value.

| Terrain | Symbol | Basic Rule |
| --- | --- | --- |
| Floor | `.` | Passable |
| Wall | `#` | Impassable |

| Display | Meaning |
| --- | --- |
| HP | The unit is defeated when this reaches 0 |
| Pw | Power. If `x2` or similar is shown, the attack hits that many times |
| Ht | Hit. An attack lands when the attacker's Ht is at least the defender's Ev |
| Ev | Evasion. If this is higher than the attacker's Ht, the attack misses |
| Sp | Speed. The side with higher Sp makes a follow-up attack |
| Df | Physical defense. Reduces physical damage |
| Rs | Magical resistance. Reduces magical damage |
| Mv | Movement |

### Commands

| Command | Description |
| --- | --- |
| Attack | Make a normal attack. Range differs by unit |
| Skill | Spend AP to use a command skill. Some skills are area attacks or support effects |
| Extra | Spend AP to let the unit act again |
| Wait | Finalize the unit's action |
| Canter | Post-action movement enabled by some effects. After acting, move within the remaining movement range |

Passive skills trigger automatically when their conditions are met. Command skills are used from each unit's skill command.

### AP

AP is a shared resource for all player units. It is spent on skills and extra actions.
You start maps with a fixed amount, and gain 1 AP when you defeat an enemy.

### Boost

When a player unit defeats an enemy during player phase, that unit's Boost effect is automatically applied to the whole party.
Boost effects differ by unit. Only a limited number of Boosts can be active at once; when the limit is exceeded, the oldest Boost expires first.

### Extra

Extra spends AP to make a unit able to act again. It can be used as long as you have AP, even if the unit is already waiting.
It can be used multiple times in the same turn, but the AP cost increases the more often it is used on the same unit. The usage count resets when the turn changes.

### Save, Load, And Undo

You can manually save and load during maps. If autosave is enabled, the game saves automatically at player phase start or after each unit action.
Undo is available during player phase. The Undo menu lets you choose a previous point, while Quick Undo returns to the previous step. Save data also includes Undo history.
