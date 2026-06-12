---
title: "Grub customizing help"
date: 2012-10-27
forum: General Help
---

### Post by daniel.cotter on 2012-10-27
Hello,

I have looked around the forum, but don't see the answer.

I have 12.04 and 12.10 installed, as I need 12.10 for its ease of use on DoD sites, but it crashes frequently, so I use 12.04 most of the time.

Rather than choose 12.04 from the grub menu every time, I would like to change it to the default OS, and only choose 12.10 when I need it.

I'm reading [https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2), but I'm lazy.  Is there a text file that shows the same order that the grub menu shows, so I can look at it before editing /etc/default/grub.  Otherwise,  I will have to reboot to find the order before editing it.

Thanks

---

### Post by Bucky Ball on 2012-10-27
You need Grub Customizer:

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

You can change the order, splash and a heap of other things very easily.

---

### Post by daniel.cotter on 2012-10-27
Okay,

I downloaded grub-customizer and ran it, but it is more confusing than editing a text file.  I have 6 entries on my list, with 2 submenus (Grub2), but grub-customizer shows 20 entries, none of which have obvious meanings.  I made a change to the default boot OS, but not only does my PC still boot into 12.10, but the order of the list changed.

So, I counted the items on the grub menu, then edited /etc/default/grub, replacing the 0 with a 4 (according to 12.04's new menu position), and ran update-grub, but it still boots by default into 12.10.

O.o

---

### Post by daniel.cotter on 2012-10-28
bump, if you don't mind

---

### Post by bogan on 2012-10-28
Hi!, **daniel.cotter,**

I used Grub Customizer with 10.04 to 1204.1 with multiple Ubuntu installations. It worked well but in the later, started giving duplicate entries that it was impossible to tell apart, or to completely delete, similar to your report,

In 12.10, it is hopeless, for the same reason, and also because It does not understand the new 'Additional Features' sub- menus, so there are no recovery options.

I have to highlight entries, press 'e' and check the 'hdo:msdosx', in order to identify the partition I am booting into.

To see what the grub menu will look like, without rebooting, use this:```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```

Chao!, **bogan.**

---

