---
title: "stupid me - can't start ubuntu now"
date: 2007-02-28
forum: General Help
---

### Post by khyer123 on 2007-02-28
Well, I made a really stupid move. It all started out with me trying to expand my ubuntu partition. What I did was re-sized my windows partition so it was smaller, copied my ubuntu partition onto this new one, erased the original ubuntu partition and then extended it to span both (making one large ubuntu partition, and of course my windows one). 

The old one was on partition /dev/sda2, and this new one is /dev/sda4 

well, I was a moron and thought that it would be just fine. Needless to say, it didn't work. I was able to reconfigure grub by editing it to point to the new sda4 partition, and that works just fine.... but now when I boot into Ubuntu recovery, it stops at

"Begin: Waiting for root file system....."

and then it waits a while, and then I get...

"ALERT! /dev/sda2 does not exist. Dropping to a shell!"

and then I'm in shell

Is there anything that I can do that doesn't involve a COMPLETE reformatting and reinstallaion of linux? I have a lot of cool software that I've gotten on there and I'd really like it so that I don't have to do that all over again. I can access shell, and I can access any files on there by using the boot disk and mounting the drive. 

Some of the things I've heard that MIGHT solve this are

-Reinstalling the kernel (I do not know how to do this without actually being in ubuntu)
-Editing /etc/fstab (I found nothing in that file that was of any use to edit)
-Editing the name of the sda4 back to sda2 (I haven't found a way to do this)

Any other ideas?

---

### Post by erkki70 on 2007-02-28
Hi,
Maybe you should try to edit your /boot/grub/menus.lst file and replace sda2 with sda4...
From shell try:
```
sudo nano /boot/grub/menu.lst
``` and edit the entries to match your new partition.
Hope it helps...

---

### Post by Johan! on 2007-02-28
I think you have to make some changes in /etc/fstab

Can you post the file?

---

### Post by kidders on 2007-02-28
**Edit:** Oops! Lots of other help has arrived while I've been posting this. Please ignore!

[COLOR="Silver"]Hi there and welcome,

> **khyer123 said:**
> It all started out with me trying to expand my ubuntu partition.I know it's a bit late to be pointing this out, but extending Linux partitions is normally unnecessary. Ubuntu will operate perfectly happily when spread over multiple filesystems. In fact, I just came from a thread where the poster was trying to find reasons *not* to install his Ubuntu into just one partition! Hehe.

In general terms, moving (but especially resizing) partitions should be avoided wherever there is any other option. It's _not_ a safe thing to be doing on a routine basis.

> **khyer123 said:**
> "ALERT! /dev/sda2 does not exist. Dropping to a shell!"Unfortunately, there are far too many things that could have gone wrong. :-( All anyone is likely to be able to post would be guesswork. You see, assuming this error can be solved, there may well be further problems, that will only come to light once more of your boot process succeeds.

For the sake of long-term stability, I would recommend reinstalling your Ubuntu (which is not something I would normally say to a person!) Having said that, if you would really hate to do that, I am happy to start firing suggestions at you, to see if we can't find the cause of your problems.

If I were you I would:
[LIST]
[*]Try to find a way to hold onto as much data as possible, shove it to one side of your hard disk (or onto a DVD) & reinstall Ubuntu.
[*]Recover the .debs for your nice software off the old install, transfer all your personal data, /etc settings, and anything else you would like to keep. This would naturally be a tight squeeze.
[*]Format Ubuntu's original location & un-squeeze your new Ubuntu install, by letting it start to use the rest of your disk space ... *without* resizing any partitions!
[/LIST]

Other options:

> **khyer123 said:**
> -Reinstalling the kernel (I do not know how to do this without actually being in ubuntu)
-Editing /etc/fstab (I found nothing in that file that was of any use to edit)
-Editing the name of the sda4 back to sda2 (I haven't found a way to do this)
One of these *may* work, depending on exactly what it is the problem turns out to be. Unfortunately, they are non-trivial (with the exception of the /etc/fstab tweak, which you've rejected), unless you are fairly familiar with Linux. Again, I'd be happy to describe how to make the other two changes, if you can't bear reinstalling.[/COLOR]

---

### Post by Herman on 2007-02-28
Hello khyer123, 
It has been a long time since I have done this, but in earlier releases the thing to do was to edit /etc/fstab and [re-install grub]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD"), if the partition was copied and pasted so that partition the number had been changed. With the old sytle /etc/fstab it would have been necessary to edit /etc.fstab and change where it said 'dev/hda2' to 'dev/hda4', and save and close the file.

Another strategy was to resize the partition, paste it somewhere out of the way, and then delete the original partition. This frees up the original partition number so when you copy and paste the new copy, it will be allocated the original partition number, so you don't have to do anything. Your system will boot right up as normal. You can even save the spare copy of the partition as a backup copy of your operating system and all your added software. That's what I still do especially when testing unstable releases. It only takes ten minutes to restore if the system gets 'hosed'.  

Nowadays if you use [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"), you don't need to bother copying and pasting the partitions at all (unless you want to), because GParted LiveCD has for quite a long time now, been able to 'move' linux partitions around or resize from the start of the partition. The version in Ubuntu is a very old version of GParted I guess.  

[COLOR=Silver] Finally, without further ado, the new style /etc/fstab files, since Edgy Eft was released, use what is called filesystem UUID numbers to identify our filesystems (partitions). 
I think you will probably need to check and see if you need to edit your filesystem UUID numbers in /etc/fstab. See if this link will help you,                      [About Edgy Eft's new /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")
```
sudo dumpe2fs -h /dev/hda4
```And look for the UUID number n the superblock data```
sudo gedit /etc/fstab
```But I am not sure about that because I am not certain if the UUID number will be changed or not when we copy and paste the partition. EDIT (because I haven't needed to do it this way anymore, I use the latest [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") ). Any feedback will be appreciated.
[COLOR=Black]EDIT: I ran an experiment and copied and pasted my new Fiesty Fawn partition and I found out that GParted LiveCD gives the original UUID to the new copy of the partition, so [/COLOR][/COLOR]khyer123 won't need to edit /etc/fstab after all. 
In a second experiment, I pretended my Fiesty Fawn installation was trashed, and I deleted it. Then I copied and pasted the new copy to the deleted orginal installation's place on the hard disk. I discovered that it was given the original UUID number. The copy of it had its UUID number changed to a new one now. All I did was re-install grub and reboot. It did a filesystem check and rebooted me again, then it booted right up as good as gold. :)
It seems as if the GParted LiveCD team have already though of us and planned ahead. Thanks Patrick Verner and plors and Larry T ! You guys rock! :)

Regards, Herman :)

---

