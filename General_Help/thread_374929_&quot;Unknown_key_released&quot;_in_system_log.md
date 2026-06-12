---
title: "&quot;Unknown key released&quot; in system log?"
date: 2007-03-03
forum: General Help
---

### Post by Hallvor on 2007-03-03
I looked at the system log, and it came up with some messages I can`t understand. What does this mean? Could it cause problems? And if so - what should I do to solve it? 

> Mar  3 11:27:21 localhost kernel: [17239631.456000] atkbd.c: Unknown key released (translated set 2, code 0x7f on isa0060/serio0).
Mar  3 11:27:21 localhost kernel: [17239631.456000] atkbd.c: Use 'setkeycodes 7f <keycode>' to make it known.

Sorry, but this makes no sense to me.

---

### Post by Abiezer on 2007-03-27
Do you own a cat? I do. I got up this morning to find this box unexpectedly shut down. Looking at the logs, I had a lot of these entries too. A search revealed that you get that message when a key in consistently pressed. I've seen my cat bring up the shutdown menu by dancing on the keyboard when I'm working on the laptop instead, so I think that's what happened.
Any chance same or similar happened to you?

---

### Post by dcstar on 2007-03-27
> **Hallvor said:**
> I looked at the system log, and it came up with some messages I can`t understand. What does this mean? Could it cause problems? And if so - what should I do to solve it? 



Sorry, but this makes no sense to me.

You can ignore them, there is a solution which involves a minor change to a configuration file (do a forum search).

It was fixed in 6.10.

---

