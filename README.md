# Invisible Item Frames

A Paper 1.20.6 plugin that turns dropped item frames invisible when they are splashed with an invisibility potion. Pick up the converted frame and place it — the placed frame is invisible while still holding its item.

> **Status:** the repository is in early development. The public branch currently contains the plugin scaffold; the Maven implementation is being prepared for release.

## Planned behavior

- Splash and lingering invisibility potions convert nearby dropped item frames
- Supports normal and glow item frames
- Converting preserves the stack amount
- Configurable splash radius, glow-frame support, lingering support, and player notifications
- Permission `invisibleitemframes.use` (default: true)
- Works by adding the `entity_data` component `{ id: "minecraft:item_frame", Invisible: 1 }` to the dropped item

## Requirements

| Requirement | Version |
|---|---|
| Server | Paper 1.20.6 |
| Java | 17+ to build (Paper 1.20.6 servers run on Java 21) |
| Build | Maven |

> The implementation uses NMS reflection against the Paper 1.20.6 mappings (`v1_20_R4`). It is not expected to work unchanged on other Minecraft versions.

## Build

```bash
mvn package
```

The plugin JAR is written to `target/invisible-item-frames-<version>.jar`.

## Usage

1. Put the JAR into the server's `plugins/` directory.
2. Start the server to generate `plugins/InvisibleItemFrames/config.yml`.
3. Drop one or more item frames on the ground.
4. Throw a splash or lingering potion of Invisibility at them.
5. Pick up the converted frames and place them — they will be invisible.

## Configuration

```yaml
# Search radius around the potion impact point
splash-radius: 3.0

# Allow converting glow item frames
allow-glow-variant: true

# Allow lingering potions to trigger conversion
allow-lingering-potions: true

# Notify the thrower after a successful conversion
notify-player: true
```

## Permissions

| Permission | Default | Description |
|---|---|---|
| `invisibleitemframes.use` | `true` | Use invisibility potions to convert item frames |

## Project layout

```text
pom.xml
src/main/java/com/ohtoai/invisibleitemframes/
├── InvisibleItemFrames.java
└── listener/PotionSplashListener.java
src/main/resources/
├── config.yml
└── plugin.yml
```

## License

No license file is currently included in this repository.
