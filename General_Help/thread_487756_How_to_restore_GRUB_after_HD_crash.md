---
title: "How to restore GRUB after HD crash?"
date: 2007-06-29
forum: General Help
---

### Post by ernstblaauw on 2007-06-29
Hi all,

I **had ** an install that looks like this:
[LIST=1]
[*]hdc: GRUB 
[*]sda6: Ubuntu
[*]sdb*: Windows
[*]sdc: Data
[/LIST]
My first HD (/dev/hdc) crashed this morning, and thus I took it out of the computer. Because I had no GRUB anymore, I couldn't load an OS. As my WinXP install is fairly old, I decided to install WinXP again, on /dev/sdc3/ (I'm not sure about the '3')
Now, my computer boots directly into WinXP (as expected). During the install, it has written to /dev/sda (which now is my first HD) to make it possible to boot WinXP. Of course, I want to install GRUB again. How can I do this? To clarify, I don't know how to boot to Ubuntu on /dev/sda6/.
Does someone know how I should reinstall GRUB to boot WinXP and Ubuntu?

---

### Post by DeathOnJuice on 2007-06-29
OK, your description seems slightly strange. Could you give me the output of fdisk -l in a terminal?

---

### Post by confused57 on 2007-06-29
> **ernstblaauw said:**
> Hi all,

I **had ** an install that looks like this:
[LIST=1]
[*]hdc: GRUB 
[*]sda6: Ubuntu
[*]sdb*: Windows
[*]sdc: Data
[/LIST]
My first HD (/dev/hdc) crashed this morning, and thus I took it out of the computer. Because I had no GRUB anymore, I couldn't load an OS. As my WinXP install is fairly old, I decided to install WinXP again, on /dev/sdc3/ (I'm not sure about the '3')
Now, my computer boots directly into WinXP (as expected). During the install, it has written to /dev/sda (which now is my first HD) to make it possible to boot WinXP. Of course, I want to install GRUB again. How can I do this? To clarify, I don't know how to boot to Ubuntu on /dev/sda6/.
Does someone know how I should reinstall GRUB to boot WinXP and Ubuntu?

You can use the live cd to reinstall grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You can try first, but you probably won't be able to boot Ubuntu in from your current grub menu...what you can do, is at the grub menu, highlight your Ubuntu entry, press "e" to edit, then try changing root from (hdx,y) to (hd1,y) or (hd2,y)...y meaning leave this value as it is...then press "b" to boot, this change is temporary, but should let you know which root value will boot Ubuntu.

You'll then need to add an entry to boot Windows, or modify the root of the one you have to "root (hd0,x)", without quotes.

---

### Post by DeathOnJuice on 2007-06-29
Confused, his GRUB hard drive died, so that won't work. First, he has to get the GRUB files. I'll edit my first post to tell you how after I eat.

---

### Post by confused57 on 2007-06-29
> **DeathOnJuice said:**
> Confused, his GRUB hard drive died, so that won't work. First, he has to get the GRUB files. I'll edit my first post to tell you how after I eat.
A grub hard drive is the first drive booted in bios, since the original hard drive is no longer working, he can install grub to the mbr of any of the hard drives, as long as he boots to that drive first.

In fact, if the OP can boot first to his Ubuntu drive, it may be a good idea to install grub to the Ubuntu drive's mbr...then he can edit his menu.lst, by pressing "e", then change root to (hd0,y)...he can then add an entry to grub to boot Windows or he can set bios to boot first to his Window's drive & boot from Window's IPL on the mbr.

Added:  The grub IPL is the only thing installed to the mbr...this actually gets the information to boot Ubuntu from grub on the root partition...I learned a lot about grub from this site:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
still much to learn, but I'm getting the hang of it.

---

### Post by DeathOnJuice on 2007-06-29
Confused, your added section details exactly why the link you gave earlier won't work. Also, that page you mentioned, along with the Ubuntu GRUB wiki page and the GRUGB manual (just a little), are where I learned everything I know about GRUB.

So, here's what you need to do.

1. Check if you have files like stage1, stage2, fat_stage_1_5, and stuff like that in /boot/grub on your Ubuntu  partition. If so, skip to step 4.
2. sudo mkdir -p /boot/grub
3. sudo cp /usr/lib/grub/i386-pc/* /boot/grub
4. sudo grub
5. find /boot/grub/stage1
6. root (hd0,5), but substitute the output of step 5 for (hd0,5) if needed.
7. setup (hd0)
8. sudo update-grub

That should do it. You'll probably need a little help to get Windows on GRUB properly since it's not the first partition and Microsoft loves making dual-booting as frustrating as possible, but I would recommend making a new topic for that.

---

### Post by Irony on 2007-06-29
Juice's way sounds about right, here is an example of me setting grub to the mbr (hd0)  and pointing it at hda3 (hd0,2) - note I have 7 linuxes installed in various places;

[PHP]grub> find /boot/grub/stage1
 (hd0,2)
 (hd0,5)
 (hd0,6)
 (hd0,8)
 (hd0,11)
 (hd1,1)
 (hd1,2)

grub> root (hd0,2)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded

grub> quit[/PHP]

Note if you can't boot into anything in the first place then use a live CD - you might have to install grub via synaptic first with the live CD, I can't remember so just try the grub command first.

---

### Post by confused57 on 2007-06-29
> **DeathOnJuice said:**
> Confused, your added section details exactly why the link you gave earlier won't work. Also, that page you mentioned, along with the Ubuntu GRUB wiki page and the GRUGB manual (just a little), are where I learned everything I know about GRUB.

So, here's what you need to do.

1. Check if you have files like stage1, stage2, fat_stage_1_5, and stuff like that in /boot/grub on your Ubuntu  partition. If so, skip to step 4.
2. sudo mkdir -p /boot/grub
3. sudo cp /usr/lib/grub/i386-pc/* /boot/grub
4. sudo grub
5. find /boot/grub/stage1
6. root (hd0,5), but substitute the output of step 5 for (hd0,5) if needed.
7. setup (hd0)
8. sudo update-grub

That should do it. You'll probably need a little help to get Windows on GRUB properly since it's not the first partition and Microsoft loves making dual-booting as frustrating as possible, but I would recommend making a new topic for that.

As long as the OP gets his system working, whichever method he uses...the first link I provided has your steps 4-7...the root partition "should" already contain a /boot/grub directory, which would be the result from "find /boot/grub/stage1", if it is indeed there, then "setup (hd0)" would install grub's IPL to the mbr of the boot drive.  Somehow, I think we're basically suggesting the same method.

---

### Post by DeathOnJuice on 2007-06-30
Confused, sorry about that, but you're right. I was thinking that since he had a separate GRUB partition, Ubuntu wouldn't install the GRUB files. Ignore me now.

---

### Post by confused57 on 2007-06-30
> **DeathOnJuice said:**
> Confused, sorry about that, but you're right. I was thinking that since he had a separate GRUB partition, Ubuntu wouldn't install the GRUB files. Ignore me now.
No problem...the thought crossed my mind that the OP may have had a separate /boot partition on the defunct hard drive, which would have made restoring grub more difficult...hope he got everything working.

---

