---
title: "Mount NTFS partitions on boot"
date: 2008-04-29
forum: General Help
---

### Post by guitarmaniac on 2008-04-29
I'm running Ubuntu 8.04.
I haven't been using Linux for about 4 months now so I'm a little rusty.
How do I set Ubuntu to mount my widows ntfs partitions on boot (I know it involves editing my /etc/fstb file)?

It's easy enough to mount them myself, but if I open up Rhythmbox to play some music before I mount my ntfs partition for instance, it has to rescan my entire collection again.

Cheers :popcorn: (should be a beer but popcorn was the closest I could find :wink:)

---

### Post by adityakavoor on 2008-04-29
go to add-remove

select all available applications

search ntfs-3g

install it

applications > system tools > ntfs config tool

---

### Post by guitarmaniac on 2008-04-29
ntfs-3g comes on 8.04 standard.
I already installed ntfs-config.
Heres all it is.
There's no option to mount NTFS at boot.

---

### Post by adityakavoor on 2008-04-30
If you are dual booting windows and ubuntu, then reboot to windows and shut it down correctly.

It worked many times for me

---

### Post by Ziggy72 on 2008-04-30
Look at my post here: [http://ubuntuforums.org/showthread.php?t=775262](http://ubuntuforums.org/showthread.php?t=775262)

---

### Post by sujoy on 2008-04-30
in fstab add the line,

/dev/(the partition name) /path/where/you/want/to/mount ntfs defaults 0 0

add one such line for all your ntfs partitions

---

### Post by guitarmaniac on 2008-04-30
OK thanks guys.

---

