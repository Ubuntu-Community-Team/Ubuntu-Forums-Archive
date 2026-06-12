---
title: "Kernel Panic :("
date: 2007-03-10
forum: General Help
---

### Post by euph on 2007-03-10
Hi all,

First time post. My laptop recently ran out of battery and shut itself off while ubuntu was loading up. I didn't think much of it until I got home, plugged it in and tried to boot it up.

Straight away I got a grub error. Error 24 to be exact. This stands for corrupt filesystem or something along those lines. So I popped in my live cd and ran 
[INDENT][SIZE="2"][FONT="Fixedsys"]fsck -y -t ext3 /dev/hda4[/FONT][/SIZE][/INDENT]
to sort this out. 

But now when I try and load ubuntu from grub It starts loading and then fails.
When I run it in Recovery Mode I get
[INDENT][SIZE="2"][FONT="Fixedsys"]run-init: /sbin/init: Not a directory
[17179573.764000] Kernel panic - not syncing: Attempted to kill init!
[17179573.764000]  [/FONT][/SIZE][/INDENT]

I'm pretty stumped.
Any ideas?

Cheers,

euph

---

