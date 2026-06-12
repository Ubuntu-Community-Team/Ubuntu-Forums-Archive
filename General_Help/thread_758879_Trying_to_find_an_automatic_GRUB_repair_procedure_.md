---
title: "Trying to find an automatic GRUB repair procedure for semi-newbies."
date: 2008-04-18
forum: General Help
---

### Post by jingo811 on 2008-04-18
I've been experimenting with GRUB trying out different scenarios where you have Win XP, Debian, Fedora and SuSE overriding the Ubuntu "menu.lst".
So far I've used Debian Etch 4.01 install CD to manually repair GRUB but that's not what I'm after.  I'm looking for access to the part where you install a Distro from scratch and the GRUB install automatically detects all operating systems and puts them into the menu.lst.

I've tried to Ctrl+Alt+F2 during the install process in order to jump right to the "install GRUB" line with the Debian CD but when I do it also wants to completely do a full Base-Install.  I don't want that I just want to access the "install GRUB" part when my relevant partition's /boot/grub/ folder is corrupted or renamed.

It sounds messy when I try to explain hope you understand what I'm after :)

---

### Post by dstew on 2008-04-18
> I'm looking for access to the part where you install a Distro from scratch and the GRUB install automatically detects all operating systems and puts them into the menu.lstFrom my reading, it is the installer program that detects the other operating systems, not grub. From the [grub manual]("http://www.gnu.org/software/grub/manual/grub.html"), I can't see that grub has any ability to look for other operating systems. It might be possible to look carefully at the Debian installer documentation to see if the code that detects other OS's can be broken out and used somehow as an updater of menu.lst. Currently, update-grub, which runs in a functioning OS, just looks in the current root file system for kernel images and adds them to menu.lst.

---

### Post by Slim Odds on 2008-04-18
> **jingo811 said:**
> I've been experimenting with GRUB trying out different scenarios where you have Win XP, Debian, Fedora and SuSE overriding the Ubuntu "menu.lst".

Dude... XP doesn't know anything about menu.lst.......

and no one outside ubuntu should be messin' with ubuntu's data....

---

### Post by ajgreeny on 2008-04-18
I have looked at many other linux distros and the only one that seems guaranteed to find all the other linux installs on a machine so far is ubuntu, which finds everything and adds it automatically to the list.  It even seems clever enough to find distro installations that you are about to format and overwrite with the new current install procedure, which can be a bit confusing, but of course you can always edit the list when you have everything installed so it's not a big problem.

---

### Post by forrestcupp on 2008-04-18
> **Slim Odds said:**
> Dude... XP doesn't know anything about menu.lst.......

and no one outside ubuntu should be messin' with ubuntu's data....
I don't know the OP's circumstances, but I think the problem is that when you install XP or something else over your Linux install, it overwrites GRUB on the MBR.  It doesn't change menu.lst; it just overwrites the MBR.

It would be nice if there were some kind of script that you could run from the Live CD to restore GRUB for you.

---

### Post by Wally_dog on 2008-04-18
At the end of this tutorial: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

There is a section on repairing the GRUB MBR after XP overwrites it.

---

### Post by jingo811 on 2008-04-18
[SIZE="4"]**Earlier at school:** [/SIZE]
This is weird I did this procedure earlier today where I manually "updated/organized/repaired" the Debian menu.lst which SuSE overrided with it's own GRUB that didn't pick up all my previous OS'.  And this procedure did the trick using the Etch 4.01 CD.

So I basically did this in a pseudo code kind of way.  Since SuSE was my latest distro install.
```
merge and cp [COLOR="Sienna"]"SuSE/dev/sda9"[/COLOR]/boot/grub/menu.lst [COLOR="Sienna"]"Debian/dev/sda8"[/COLOR]/boot/grub/menu.lst
```

> 
[LIST]
[*]press Ctrl+Alt+F2 when asked about hostname.
[*]fdisk -l      ; Locate the chosen distro partition "/boot/grub/menu.lst" I want to install to MBR.
[*]mkdir /mydisk
[*]mount /dev/sda8 /mydisk
[*]chroot /mydisk
[*]grub-install /dev/sda
[*]shutdown -r now
[/LIST]


[SIZE="4"]**Later at home:** [/SIZE]
I would think that I follow procedures to the point as above when pasting and reparing all old GRUB info from other distros into Ubuntu Feisty's GRUB menu.lst.
But this time around everything stopped at this stage using the Debian CD.
> 
[LIST]
[*]grub-install /dev/hda
[/LIST]

So I basically did this in a pseudo code kind of way.  Since Dapper was my latest distro install.
> merge and cp [COLOR="Sienna"]"Feisty+Dapper"[/COLOR]/boot/grub/menu.lst [COLOR="Sienna"]"Debian/dev/hda8"[/COLOR]/boot/grub/menu.lst > [COLOR="DarkOrange"]Feisty's menu.lst[/COLOR]

Also when before and after having fixed the GRUB replacing problem, I got and still have this error.  When running in Ubuntu or using the Feisty Live CD so it seems Ubuntu Live CD isn't so friendly when it comes to merging distros together for GRUB. :( maybe I'm missing some piece of knowlegde for Ubuntu.
```

grub> find /boot/grub/stage1
[COLOR="Red"]Error 15: File not found[/COLOR]
```

I tried to fix this by going into GPARTED and select my Feisty partition and set the flag into "boot" but no difference.
Anyhow GRUB got fixed at the end but then weirdness number 2 kicked in.  My user account couldn't log in anymore and to make things more irritating GDM doesn't allow root login.
Well guess that I shouldn't bring this scenario up on my website's Beginner's tutorial section.  I had to use several different hacks to get back in.  I guess multi-Linux-distro-GRUB isn't intended for newbie reading :)

---

### Post by jingo811 on 2008-04-18
Correction it works now I don't get any error anymore. I forgot to "sudo grub" I just did "grub" when running Feisty.  But this didn't work on the LiveCD for repair so.....

```
grub> find /boot/grub/stage1
 (hd0,5)
 (hd0,6)
 (hd0,7)
```

---

### Post by Az_135r on 2008-04-18
annoying isnt it!

im lazy and just backed up the MBR when i first installed ubuntu... then

1 .install new OS
2. restore the MBR post new installation 
3. customise grub via ubuntu


was necessary today as i couldnt load windows 2008 in a VM, there are alternatives, but i find this quickest

---

### Post by jingo811 on 2008-04-19
This is bad for the lazy side of me.  Every time I want to login with my user account GDM doesn't relate to the /etc/passwd and shadow file.  B'coz when I Ctrl+F2 I can login like normal with user account but not through GDM.

So now I'm forced to change user password everytime I want to log into X-Gnome through GDM.
Guess it's a good thing for the paranoid side of me.  Since I never changes passwords now I'm forced to change it every day :)

---

### Post by forrestcupp on 2008-04-19
> **Wally_dog said:**
> At the end of this tutorial: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

There is a section on repairing the GRUB MBR after XP overwrites it.

Well, there's a lot of information out there about how to manually restore GRUB.  But someone needs to come up with a script that can automatically detect your drives and restore GRUB for you.

---

### Post by ramjet_1953 on 2008-04-19
You may find this utility useful:

[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)

Regards,
Roger :cool:

---

