---
title: "Ubuntu 18.04 boots into emergency mode"
date: 2019-05-29
forum: General Help
---

### Post by epjm on 2019-05-29
Hello,
my computer boots into emergency mode. I am not sure what caused this as I have not changed anything. The only thing I've done to the boot drive that I think could've done this is when I tried unmounting the drive using the disks app.
I don't know if this is anything but I switched from gnome to unity because I was also having a hard time booting into ubuntu using gnome, and the only way I could get into ubuntu was by changing the gui to unity.
I only have images of my issue, so apologies in advance.
[IMG]https://imgur.com/sxj3sqE[/IMG][IMG]https://i.imgur.com/sxj3sqE.png[/IMG]

and here's the first thing that it boots into
[IMG]https://i.imgur.com/YIUCJxw.png[/IMG]

The second thing it shows me after it boots into ubuntu
[IMG]https://i.imgur.com/c4uQOwe.png[/IMG]

and the full message it shows me
[IMG]https://i.imgur.com/lUPcNYG.png[/IMG]

I am stuck and unsure what to do next. Any help is appreciated!

---

### Post by CatKiller on 2019-05-29
Your fstab doesn't have an entry for /. I don't see how that's going to work.

---

