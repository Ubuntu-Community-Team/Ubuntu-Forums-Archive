---
title: "busybox can't access tty... can i retrieve my files?"
date: 2006-10-24
forum: General Help
---

### Post by dezany1 on 2006-10-24
hi all, linux newbie here. been pretty satisfied with ubuntu for the past few months that i've tried it. then a couple of days ago, out of the blue, my system hanged on me. restarted and got this error: 

/bin/sh: can't access tty; job control turned off
([click here]("http://img322.imageshack.us/img322/6071/img003dc6.jpg") for full screenshot)

i searched the forums and found threads where others encountered the same error. but the few i browsed did not really mention how to solve the problems except for a fresh install. i tried k.mandla's suggestions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=279884") but to no avail. i was unable to get any login prompt using ctrl + alt + the f keys. next i tried using the live cd to mount the partition sda1 and it had an error, saying something was wrong with it, am not very sure, i forgot to take a screenshot.

now that i know edgy eft's gonna be released, i was thinking of installing that. is there anyway i can do it without deleting the current files i have kept on my hdd? i have most of my important files in a partition, and a couple of files on my desktop.

for now my linux computer is useless and my dad's a little miffed that we can't even boot it. that, and me constantly using his computer right now. i miss my ubuntu... ;_;

thanks for your time!

---

### Post by RichJacot on 2006-11-12
Same here.

I'm am now getting the same thing:

[FONT="System"][SIZE="2"]Busybox v1.1.3(Devian 1:1.3-2ubuntu3) Built-in Shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't tty; job control turned off
(initramfs)

#[/SIZE][/FONT]

I have been trying to do a fresh install of edgy and encrypt root, swap and home.  I have done at least 8 or 10 different full installs with the single cd I downloaded.  IT WAS WORKING, at least for a few installs.  At this point I have even downloaded the alt cd and I get the same result after installing from that.

I think it has something to do with the partitioning.  The reason I think so is because...  If I let the installer erase the whole disk and let it do the partitioning piece, after the install it boots-up fine.](*,)   Needless to say the default partitioning setup is not what I need. 

I'm open to suggestions, anyone?

---

