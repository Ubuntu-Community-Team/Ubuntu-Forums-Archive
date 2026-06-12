---
title: "usb 1 tb drive not recognised"
date: 2017-03-08
forum: General Help
---

### Post by terry-brock on 2017-03-08
Hi all my problem is this i have a 1 tb drive that i store various things including movies, i tried to use my panasonic dvd player to watch some movies but it would not recognise the drive, so it asked me to register the drive, i did this still nothing. Now my laptop will not mount the drive or recognise the drive, with gparted i can see the drive, whats my work around to get it working again

---

### Post by Keith_Helms on 2017-03-09
Your DVD player is not going to play movie files off a hard drive.  You will need to play them with a software app such as vlc or mpv.

---

### Post by QIII on 2017-03-09
Hello!

Your post is confusing.  Could you please try to explain your issue again - in proper English with punctuation?

Thanks!

---

### Post by terry-brock on 2017-03-09
try now

I have played movies before off of the hard drive onto the tv.

---

### Post by QIII on 2017-03-09
Are you saying that after attempting to play a movie on your optical drive, you are having a problem with an HDD?

---

### Post by terry-brock on 2017-03-09
my usb hard drive is not recognised by my laptop, this happened after i tried to use it with my dvd player attached to the tv. As you can see by the screen shot with gparted I can see the drive.

---

### Post by QIII on 2017-03-09
How did you try to use this USB drive (something you didn't mention) with your DVD player attached to the TV?  Is this the DVD player in your laptop?  A stand-alone shelf device?

For us to help you, we need information and we need to understand the conditions.  You are creating a very incomplete word-picture.

---

### Post by terry-brock on 2017-03-09
[COLOR=#000000]i tried to use my panasonic dvd player to watch some movies but it would not recognise the usb hard drive, so it asked me to register the drive, i did this but the dvd player still did not recognise the hard drive. When i then tried to use the hard drive with my laptop it was not recognised by the laptop.[/COLOR]

---

### Post by QIII on 2017-03-09
Repeating a confusing explanation is not helpful.

Please explain how you were using the USB drive with the DVD player.  Is this a stand-alone player?

---

### Post by terry-brock on 2017-03-09
the dvd player has a usb port to which i attached my usb hardrive. The dvd player is attached to a tv

---

### Post by QIII on 2017-03-09
Does this DVD player have a method for cleanly unmounting USB-connected devices?

You say that the drive is 1TB, but that does not seem to be what is shown in your first image.  Your image appears to depict a device with an OS installed.

---

### Post by terry-brock on 2017-03-09
There is no o/s on the hard drive it was a new drive that i had put documents, pictures and some movies on. When I attached it to the dvd player via the usb port the dvd player did not recognise the drive so it told me to register the drive via the dvd menu. This i did but it was still not recognised by the dvd player. At this point i went to my laptop and plugged the hard drive into a usb port and it was not mounted or recognised.

---

### Post by QIII on 2017-03-09
OK.  Sorry for taking the long way around, but I think now we have a description of the issue that folks can bite in to.

---

### Post by howefield on 2017-03-09
Plug the USB drive in and then open a terminal and try the command..

```
dmesg | tail -n 20
```

what's the output ?

---

### Post by lisati on 2017-03-09
I just had a look at the instruction book for one of my DVD players. The page I looked at wasn't particularly clear on this, but I think that it expects to be able to use external HDDs for its own purposes, rather than to play whatever content that might already be on it. It can, however accept SD cards and USB sticks which have MP4 files on them.

---

### Post by Keith_Helms on 2017-03-09
My Blu Ray/DVD Player can play media files, such as mkv off of USB  attached hard drives or thumb drives.  It expects the drives to be  formatted with exfat/fat32 and I doubt it would recognize Ext2/3/4.   Hard drives don't always work as the USB port on the player doesn't  supply enough power, although attaching the drive to a powered USB hub  and then attaching that to the player is a workaround.

---

### Post by terry-brock on 2017-03-09
screen shot after      [COLOR=#000000][FONT=&quot]dmesg | tail -n 20[/FONT][/COLOR]

---

### Post by terry-brock on 2017-03-11
Has anyone an answer to my problem

---

### Post by Keith_Helms on 2017-03-11
What file system is this USB hard drive formatted with?  Fat32/exfat, or did you use one of the Linux file systems?  You would probably need a Fat file system for a stand-alone disc player to recognize it.  Even with a properly formatted drive, my player doesn't always mount a USB hard drive due to insufficient power over the USB connection.  I found that attaching it to a powered USB hub and then plugging that into the disc player is a good workaround.

---

### Post by terry-brock on 2017-03-11
thanks for that reply but i am more interested in getting my laptop to recognise the hard drive so i can recover all the files

---

### Post by Keith_Helms on 2017-03-12
What does gparted show after you have plugged the drive into a USB port?  That image you attached to the first post shows the internal hard drive, not the USB drive.

---

### Post by terry-brock on 2017-03-13
this is a screen shot

---

### Post by mus1cfreak on 2017-03-13
> **terry-brock said:**
> When I attached it to the dvd player via the usb port the dvd player did not recognise the drive so it told me to register the drive via the dvd menu. 

I belief that this is the reason why the 1 Tb HD is not recognised.
After registration the DVD player has, from my point of view, the 1 Tb formated to it's own fileformat.

---

### Post by ajgreeny on 2017-03-13
Yes, it looks as if the DVD player has reformatted the disk in an unrecognised filesystem, hence it showing as unallocated.

It may be worth having a look at [testdisk]("https://help.ubuntu.com/community/DataRecovery") or one of the other utilities  shown to see if that can recover the partition which is now missing.
I can not help with any personal experience of using testdisk, but it has certainly helped many other users.

---

### Post by mus1cfreak on 2017-03-14
> **ajgreeny said:**
> Yes, it looks as if the DVD player has reformatted the disk in an unrecognised filesystem, hence it showing as unallocated.

It may be worth having a look at [testdisk]("https://help.ubuntu.com/community/DataRecovery") or one of the other utilities  shown to see if that can recover the partition which is now missing.
I can not help with any personal experience of using testdisk, but it has certainly helped many other users.

His picture clearly  shows that there is NO partition left, and therefore i am afraid that he lost all his data.
But that is my simple conclusion.

---

### Post by howefield on 2017-03-14
> **mus1cfreak said:**
> His picture clearly  shows that there is NO partition left, and therefore i am afraid that he lost all his data.
But that is my simple conclusion.

However the data may be recoverable. 

The OP can decide when it is time for the doom and gloom.

---

