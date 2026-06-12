---
title: "How to make a removable drive show on desktop on mount?"
date: 2007-06-27
forum: General Help
---

### Post by vapore0n on 2007-06-27
When I insert a CD/DVD, the drive shows its icon on the desktop.
When I plug in a usb drive it doesnt.

How can I make it so that it does?

Also, is there a way to add more actions for when a drive mounts?

Like, for when /cdrom mounts Id like an eject icon show up in the desktop below the drive icon. Same for any other removable drive.

Thanks.

---

### Post by merlinus on 2007-06-27
Alt-F2
gconf-editor
apps/Nautilus/desktop

Tick the various boxes for what you are wanting.

-merlin

---

### Post by vapore0n on 2007-06-27
The only option related was already ticked. CDRom, other partitions, and ipod create their own icon on desktop.
Still my usb flashdrive doesnt.

---

### Post by merlinus on 2007-06-27
Ssytem/Preferences/Removable Drives and Media

-merlin

---

### Post by vapore0n on 2007-06-27
> **merlinus said:**
> Ssytem/Preferences/Removable Drives and Media

-merlin
nope. That just shows the same things the config editor shows.

Just read that its a reported bug. Happening randomly.

---

