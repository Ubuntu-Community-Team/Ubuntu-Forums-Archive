---
title: "Option to Factory Reset Ubuntu"
date: 2023-10-20
forum: General Help
---

### Post by crisdeodates2 on 2023-10-20
Hi community, I couldn't find a similar thread in the ubuntu forum asking to include this feature. This could be similar to the full OS reset feature in Windows OS and the Android OS and could be added to the OS settings. It would be really helpful than having to reinstall the whole OS again from scratch. Also an additional option to just reset the settings and packages without affecting any personal files.

---

### Post by ian-weisser on 2023-10-20
This idea pops up occasionally.

Ubuntu users are participants, not customers. The user community is expected to contribute improvements to the code.
One purpose of this site is to help users acquire the skills to offer useful improvements.
Many folks choose to contribute in small-but-vital ways: Bug triage,  testing, translation, documentation, art, support, and many others.
Others lead and contribute to projects: Flavors, desktops, packaging, toolsets, Debian, etc.

If any community member wants to code (and  maintain) any particular feature, they  are welcome to gather a group of like-minded and get started.
If any deep-pocketed companies want to hire a developer to code (and maintain) a feature, they don't need anybody's permission. They can jump right in.

It is unlikely that Canonical will have it's paid engineering staff create this feature based on your external submission here. That's not generally how they work. (And you are not their customer)
But don't be discouraged by that. There are lots of great ways to help improve Ubuntu.

---

### Post by dragonfly41 on 2023-10-20
One  ploy might be to keep a parallel Cubic instance up to date (step by step by scripting as new applications are added to the mainline OS). Then it would be an easier task to get back into the mainline OS with a Cubic custom profile of applications and settings. Also look to scripting Synaptic and Ansible as other thoughts. It is one thing to reinstall or upgrade Ubuntu but getting back to a configured status is another task. Cubic seems to play that process.

---

### Post by Holger_Gehrke on 2023-10-20
The Asus EEE 701 using Xandros Linux (a commercial Debian variant) had something like that. It was done by having the base installation in a read only partition and use some kind of overlay filesystem for the updates. If you wanted to reset you basically cleaned out the overlay and were done. It would probably be possible to do something similar on Ubuntu.

Holger

---

