---
title: "fsck bug drawing system unbootable"
date: 2005-10-24
forum: General Help
---

### Post by teevee on 2005-10-24
Well, not really a fsck bug but a bug in Ubuntu's implementation.

This morning I booted my PC, it greeted me with the message...
> Checking root file system...
/dev/sda1 contains a file system with errors, check forced.
/dev/sda1:
Inodes that were part of a corrupted orphan linked list found

...blah blah... unexpected inconsistency: **run fsck manually**

...blah blah... Control-D will reboot

Give [color=red]**root**[/color] password for maintenance: (in order to be able to run fsck manually!)

But there is no root password in Ubuntu! My user password which I use for sudo'ing did not work either. Luckily I had a Knoppix CD and could run fsck /dev/sda1 from there, but this looks like a pretty buggy bug. You can also run a shell from within the Ubuntu install CD, iirc, but this should be noted in this error message. Or one should be prompted for login and password (preferable, since not everyone will keep the install CD).

Should this be filed in Bugzilla?

(My FS was repaired successfully btw. ;-))

---

### Post by teevee on 2005-10-24
Oh btw, what could be the cause of the corruption? Yesterday I had to reset my system, something (Beagle, I guess, since I was testing it at that time) was eating all resources and didn't even let me move my mouse or Ctrl+Alt+Backspace anymore. But earlier resets did not cause any harm yet.

Edit: Yep, guess this was the cause. ;-) Someone had the same problem with Beagle: [http://www.ubuntuforums.org/showpost.php?p=438205&postcount=16](http://www.ubuntuforums.org/showpost.php?p=438205&postcount=16)

(I have 512MB too)

---

