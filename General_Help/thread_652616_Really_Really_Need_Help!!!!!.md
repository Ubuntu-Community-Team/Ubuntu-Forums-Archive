---
title: "Really Really Need Help!!!!!"
date: 2007-12-28
forum: General Help
---

### Post by yamabushi334 on 2007-12-28
I am currently running off the live cd. I am getting a grub 22 error not that common of a error from what i have read. I was playing one of my games on windows cause Ubuntu was messed up. It was giving me /init 172 panic not found error. After I was done playing my game I restarted my computer cause it was getting a little laggy. When grub booted up it gave my the error 22 message. I heard that this message was one of the worst ones. If anyone could please help me I would be very grateful. I really dont want to be on the live cd forever.

---

### Post by ntowakbh on 2007-12-28
> **yamabushi334 said:**
> I am currently running off the live cd. I am getting a grub 22 error not that common of a error from what i have read. I was playing one of my games on windows cause Ubuntu was messed up. It was giving me /init 172 panic not found error. After I was done playing my game I restarted my computer cause it was getting a little laggy. When grub booted up it gave my the error 22 message. I heard that this message was one of the worst ones. If anyone could please help me I would be very grateful. I really dont want to be on the live cd forever.

I just did a bit of googling, and all of the results I found mentioned putting in the Windows XP disk, going to recovery console, and typing "fixmbr."  I don't know if this would work.  Here is one of the pages that someone suggested this:

[http://www.linuxforums.org/forum/installation/55749-grub-error-22-a.html](http://www.linuxforums.org/forum/installation/55749-grub-error-22-a.html) (second post)

---

### Post by ASquared21 on 2007-12-28
Hi,
Can't you just install Ubuntu with a new CD directly to your hard drive? I use the Edubuntu CD rather than the Ubuntu or Edubuntu desktop or live CDs for my installs. You can find this at
[http://www.edubuntu.org/](http://www.edubuntu.org/)
You just go to the right hand side, near the top, where it says "download", make the CD, and use the "install a work station"

Send me a message for more help, or reply to thist forum.
Good Luck

---

### Post by bodhi.zazen on 2007-12-28
We need more information regarding the geometry of your hard drives and configuration of grub.

My guess is your ubuntu partition is corrupt, I would check the integrity. You can do this from the live CD.

First, make sure the ubuntu partition is NOT MOUNTED. If it is, unmount it first.

Then :

```
fsck -y /dev/hdxy
```

Where /dev/hdxy = your ubuntu partition.

See this thread for ideas : [http://ubuntuforums.org/showthread.php?t=375501](http://ubuntuforums.org/showthread.php?t=375501)

Otherwise to help we need :

output of : sudo fdisk -l

Post your /boot/gurb/menu.lst (from your ubuntu partition)

---

### Post by yamabushi334 on 2007-12-28
```
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb72018d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         582       24321   190691550    7  HPFS/NTFS
/dev/hda2               1         581     4666851    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x9800481f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17753   134212648+   7  HPFS/NTFS

```



here are the results of fdisk -l



Also when i pull up menu.lst it comes up blank i dont know if im doing it right or not

---

### Post by meierfra on 2007-12-29
Ubuntu does not show up in your partition table. If you are lucky only your partition table is messed up  and "testdisk" can fix it. You can run testdisk on the LiveCD as follows:

1)  Enable the   Universe Repository

Go to Systems-> Adminstration->Software Sources"
Click on the Box next to "Community-maintained Open Source Software (universe)

2)  Install testdisk

```
sudo apt-get update
sudo apt-get install testdisk
```

3)  Start testdisk:

```
sudo testdisk
```


For more info on testdisk click on testdisk in my signature.

---

### Post by yamabushi334 on 2007-12-29
thanks meierfra that did make it work but i still cant login to windows your linux. I get a error when i try to login to windows but when i try to login to ubuntu it just freezes at the startup screen the one with the orange bar. Is it possible for me to run my computers recovery disk without ruining anything on the linux part?

---

### Post by pyronaut on 2007-12-29
you might have to reinstall grub.. however one thing that should be really done before you play around anymore is BACKUP your data both on windows and linux

---

### Post by yamabushi334 on 2007-12-29
I have used my windows recovery cd so i can try to log on to windows but that didnt work all it does it goes to the windows loading screen and then reboots. I have reinstalled linux like 5 times now. Still no go on that. I have also tried reinstalling GRUB with a walkthrough from another post but both of those didnt work. So i am not quite sure on what i need to do to fix it. Also before I did my system recovery disc it came up with this error. \system32\hal.dll was not found please copy the file from the windows installation CD.

---

### Post by yamabushi334 on 2007-12-30
Ok i have got linux working on a another hard drive that i have but i am having difficulties on getting windows on it does anyone have any suggestions

---

