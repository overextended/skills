---
name: resource-best-practices
description: "FiveM resource defaults beyond security: entity spawning and network control, cleanup, loops, network traffic, state bags and SQL. Use when writing or reviewing a resource's client or server scripts, or when a resource doubles up after a restart, hitches, or floods the network."
paths:
  - "**/*.lua"
  - "**/*.ts"
  - "**/*.js"
---

# Resource best practices

The defaults every FiveM resource follows, on any framework. The examples use ox_lib. Where a rule needs a framework hook, such as a logout event or a vehicle spawner, use the framework's own. This skill doesn't cover security or NUI. Keep every server-side check as it is.

## Reference

Read each file whose condition the code meets.

| Read | When the code |
| --- | --- |
| [ENTITIES.md](./ENTITIES.md) | Creates, deletes or takes control of an entity, passes entity or network ids, attaches props, plays sounds, ragdolls a ped, or calls a native on an entity it may not own |
| [LIFECYCLE.md](./LIFECYCLE.md) | Creates something that needs cleanup (entities, blips, cameras, timers, per-player state), or registers handlers, commands or zones |
| [EVENTS.md](./EVENTS.md) | Loops, triggers or handles events or callbacks, yields inside a server handler, or uses state bags |
| [DATA.md](./DATA.md) | Queries the database, adds config or convars, or logs |

## Writing

1. Before writing, read every file whose condition your change meets.
2. Follow those rules. In existing code, fix violations in the lines you touch, and list the others you saw at the end.

Done when every line you wrote follows every rule in the files you read.

## Reviewing

1. For each changed hunk, read every file whose condition it meets.
2. Report each violation with its `file:line`, the rule, when it fails, and the fix. A failure names a moment, such as "after a restart", "with 100 players" or "when the player drops mid-purchase". Report only violations whose failure you can name.

Done when every hunk has been checked against every matching file.
