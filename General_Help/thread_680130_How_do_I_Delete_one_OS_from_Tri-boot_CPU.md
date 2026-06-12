---
title: "How do I Delete one OS from Tri-boot CPU?"
date: 2008-01-27
forum: General Help
---

### Post by lizadove on 2008-01-27
So, currently I've got Grub automatically starting up Kubuntu on my SATA hard drive.  The other two options are a different Kubuntu on my IDE hard drive and XP on the same IDE.  How do I format the SATA to get rid of the second Kubuntu (I needed it to fix the other kubuntu, which is now running smoothly)?  When I'm booted from the IDE I can't even detect the SATA drive.  

Does anyone have any ideas here? I guess what I need in the first place, is to know how to detect the SATA when booted from a different location.  

Thank you for any help.

---

### Post by seventhc on 2008-01-27
```
sudo gparted
```should show you your partitions and you can use it to delete partitions. Make sure you delete the right one.
if you don't have gparted installed then
```
sudo apt-get install gparted
``` should do it.
I am not positive if this works for two separate hard drives or not, I only have 1 :(
If the one you want to get rid of is on the same drive as xp, you can boot to xp and use Disk management to delete the kubuntu from there. That way you won't accidentally lose your xp.

---

### Post by lizadove on 2008-01-27
=====================
libparted : 1.7.1
======================
Unable to open /dev/hdb read-write (Read-only file system).  /dev/hdb has been opened read-only.
Unable to open /dev/hdb - unrecognised disk label.
                                                             
Hmmm....  This is what I got, but then it did open

I see:
/dev/hda1 ntfs  /media/hda1  74.90 GiB  13.65 used
/dev/hda2 ext3 /media/hda2 71.09 GiB 13.40 used
/dev/hda3 extended [blank] 3.06 GiB [blank]
/dev/hda5 linux-swap  [blank] 3.06 GiB [blank]

What do you think?  The SATA I'm trying to get rid of I believe I only formatted 40GiB of 320 GiB  I don't see it in the list...

---

### Post by seventhc on 2008-01-27
well first let me get this straight. You have 2 drives, 1 drive contains winxp and kubuntu, and the other drive has kubuntu only?

If this is the output from the drive with both

/dev/hda1 ntfs  /media/hda1  74.90 GiB  13.65 used
/dev/hda2 ext3 /media/hda2 71.09 GiB 13.40 used
/dev/hda3 extended [blank] 3.06 GiB [blank]
/dev/hda5 linux-swap  [blank] 3.06 GiB [blank]

then as long  leave the ntfs partition alone and xp will be ok. The ext3 & swap should be the kubuntu. 
Honestly I would probably power off, unplug the hdd that i want to keep, then either do it from xp or with the live cd.
if from the live cd and you get the same reading delete the ext3 and the linux swap. I dont know what you have on the other 'blank'(hda3) so I would leave that until you're certain. If no data is on it, then you can delete that too.
don't delete the ntfs, that is windows. By unplugging your other hdd, you have no risk of making a mistake and deleting the wrong kubuntu.

---

### Post by lizadove on 2008-01-27
That's a very bright idea to unplug the IDE and delete it from the Live CD.  I will try it out and report back.  Thanks - even if it doesn't work, it's a good idea.

---

### Post by seventhc on 2008-01-27
Good Luck I think you will be fine. :)

---

### Post by lizadove on 2008-01-27
Uh oh... It appears I have a different problem.  When I unhooked the primary IDE and powered up I get this screen first, and then a lovely single blinking cursor in the upper left.

Any more good ideas?  The second screenshot is of my desired boot - the first on the list is the one I want to be rid of.  If I can't entirely delete it, do you know how to make the selected item the one that boots automatically?

Thanks

---

### Post by seventhc on 2008-01-27
go here
[http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391](http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391)
This is a program that might make it easier for you to choose the boot order, I read about this from another post today, can't remember who posted it though. once the page opens the download links are down a bit. 
I don't see why you couldn't boot from the live cd though. Is your BIOS set to boot from a CD???

---

### Post by lizadove on 2008-01-28
Ahh... at last.  Now everything starts up normally.  I'm not going to worry about deleting it - since I can't figure out how.

And strangely, BIOS wouldn't let me choose CD as a boot option when I only had the SATA plugged in- only USB and the hard drive.  Weird.

---

