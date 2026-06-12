---
title: "Delete and reinstall grub"
date: 2006-11-09
forum: General Help
---

### Post by podunk on 2006-11-09
Well, the title says it all. :-) 

My grub has an error of some sort in it. I want to delete and reinstall it.

I do *not* want to take Linux off. All the how to's I've read are related to completely removing Linux - to which I say Nebber! :-)

Can you remove and reinstall grub without doing a complete reinstall?

---

### Post by Sef on 2006-11-09
> Can you remove and reinstall grub without doing a complete reinstall?

Yes. Read [Restoring GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by confused57 on 2006-11-09
You can also use the desktop live cd:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by podunk on 2006-11-09
I went ahead and did a new install, still have the same problem. On boot up it gets to Checking file system, then drops out of the usplash (is that what they call it Dapper?) and goes to black and white readout with the following error:
"There are differences between the boot sector and it's back up"

I messed this Kubuntu install up trying to tweak some speed out of it. Why I did that I don't know - well, stupidity comes to mind, it was fast as heck before I messed with it.

The first time I installed it it went like a dream, but now I can't it back. It's buggy as heck. This is the only consistent error I can find.

I was hoping wiping grub would make a new back up of the boot sector or something like that and would resolve everything.

---

### Post by Herman on 2006-11-10
Hello podunk,
Probably, if you press 'ctrl'+'d' keys, Ubuntu will carry on to complete the boot-up as nomal, but your Windows partition will not be automatically mounted. The icon called 'hda1' will be missing from your desktop.

>  "There are differences between the boot sector and it's back up" I don't think either Grub nor Ubuntu are buggy, it's my guess  *they are trying to warn you that you have a problem in your Windows partition.*

Are you dual booting with Windows? If so, is it FAT32 or NTFS?

You can fix your FAT32 bootsector by running dosfsck on an unmounted Windows filesystem with a Linux LiveCD like Ubuntu Dapper or Edgy Desktop Live/Install CD, or GParted LiveCD. Try this code,  ```
sudo dosfsck -ar /dev/hda1
``` or this one, ```
sudo fsck -V -r /dev/hda1
``` When it finishes , it will give you a report, and offer you three chioces
1) Copy original to backup
2) Copy backup to original
3) No action
?
Type a '2' after the ? prompt if you want to restore your backup copy of your Windows bootsector, which should be still good, and fix your corrupted present one. 
After a few seconds, it will ask you to confirm with, 'Perform changes? (y/n) to which I answered 'Y' for yes. That's all you need to do, it will be fixed! 

Neither Ubuntu or Grub would corrupt your Windows bootsector, as they write Grub to MBR, and do not touch the Windows bootsector in any way at all.
However, something apparently has, and Ubuntu is detecting it for you. You should be happy! :-D Maybe Ubuntu is saving your Windows from a bootsector virus that has a timer in it and is waiting to deliver its payload! I would re-install Windows, actually.
I am not 100% sure that this is your problem, podunk, it's just a guess, you didn't even say you have a Windows dual boot, so I might be embarassed here, but that's my bet about what your problem is and I'll stick to it until otherwise notified. :D

You could also do it with a Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), by applying the 'fixboot' command. This might be better, especailly if you have NTFS.

Why do people always think Ubuntu is the one that has something wrong or is 'buggy'?
It is Windows that is the bug! :-D

 :D He-he, do you want to know how I found out about this error and how to cure it? After the last time I was reading about it, I *deliberately* did a 'sudo grub-install /dev/hda1' just to see what would happen, (do not try this at home, folks), and  corrupted my Windows bootsector on purpose, just to find out how to get that error message and learn how to fix it. 

Regards, Herman ;)

---

### Post by podunk on 2006-11-10
Yeha! :-0

Thank you Herman!

---

### Post by Herman on 2006-11-10
It's my pleasure! Thanks for the feedback and I'm glad you got it fixed. :D

---

### Post by jingo811 on 2006-11-29
Saved post for future reference for myself.

---

### Post by rusyear04 on 2007-03-20
:lolflag:

had the same problem...
> There are differences between the boot sector and it's back up
after reinstall of *edgy eft*

i first tried to repair my [_[COLOR="DeepSkyBlue"]grub[/COLOR]_]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub") -which didn't seem to help.
so i went over my fstab

```
sudo cp /etc/fstab /etc/fstab.backup
sudo gedit /etc/fstab
```

i deleted the automatical entry of the win-partition and changed all entries for additional (NTFS as well as FAT32!) partitions to a format found in the [_[COLOR="DeepSkyBlue"]edgy-wiki[/COLOR]_]("http://ubuntuguide.org/wiki/Ubuntu:Edgy") under
**1.15 Windows**.

restarted the system and *voila* :mrgreen:

---

### Post by Herman on 2007-03-21
Hello rusyear04,
> [1.15.5 How to mount Windows partitions (NTFS) on boot-up, and allow users read and write access]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access") You installed 3-g did you? (for your NTFS data partitions). That's good. I would agree with that. :)

I'm not so sure whether I would recommend all users just delete their /etc/fstab entry for the Windows partition with the problem though.
Well, whatever makes you happy, you can 'sweep the problem under the carpet', or 'bury your head in the sand', but the problem still exists.
I mean. like if you oil light comes on when you are driving your car, do you remove the light bulb or pull out the wire so the light won't bother you anymore?
Well it's up to you, do what ever you like, as long as you're happy! It's only your Windows, and now that you have Ubuntu you won't need that anymore anyway.:) 
:lolflag::guitar::popcorn:
LOL, lol ,LOL, he-he... 
Want to know an ever better way to fix that?
Just delete Windows! He-he. :)

Regards, Herman :lolflag:

---

### Post by lw5 on 2007-04-25
* super kick *

I used the solution Herman describes (on Feisty) and it works fine, except that now, during boot, Usplash goes into standard textmode when it starts checking the disks. The disks seem to be fine, no warnings or whatever, but Usplash doesn't make it through the entire boot sequence.

As a note; I probably shouldn't have done this, but instead over writing the backup to the original, I wrote the original to the backup...

Is there a way to fix this?

Edit:
And it's already fixed.
Apparently FAT disks get checked each time at boot which causes Usplash to go into cli. Simply changing the 1 or 2 at the end of the fat partition line in the /etc/fstab file solves the problem.

---

