---
title: "Creating A GRUB Boot Floppy"
date: 2007-04-04
forum: General Help
---

### Post by Virgo53 on 2007-04-04
I'm trying to create a GRUB boot floppy as per the instructions listed at the community 

documentation:

[[url]https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28boot%29%7C%28floppy%29]("[https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28boot%29%7C%28floppy%29[/url")(https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28boot%29%7C%28floppy%29[/url"][url]https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28boot%29%7C%28floppy%29[/url)]

I get as far as step 3- "mount /dev/fd0 /media/floppy" and get this message:

You must specify the filesystem type

Wasn't that already done in step 2?  "mke2fs /dev/fdo"    :confused:

---

### Post by zvacet on 2007-04-04
Here is another way to do it 
[http://ubuntuforums.org/showthread.php?t=224345&highlight=floppy]("http://ubuntuforums.org/showthread.php?t=224345&highlight=floppy")

---

### Post by Herman on 2007-04-04
And here's another way to do it too, [How to make your own personalized Grub Floppy Disk]("http://users.bigpond.net.au/hermanzone/p15.htm#grub_floppy_howto_make")

Regards, Herman :)

---

### Post by al7kz on 2007-04-04
deleted

---

### Post by Virgo53 on 2007-04-04
I followed zvacet's link but it didn't work for me-
when I got to mount I got this message:
mount: can't find /media/floppy0 in /etc/fstab or /etc/mtab  :confused: 

I also tried Herman's link but I still am getting the 
You must specify the filesystem type when I get to mount  :confused:

---

### Post by Herman on 2007-04-05
Okay Virgo53,
That's odd, well try modifying the command a little then, and see if it'll work. You implied earlier that you have the ext2 filesystem in your floppy disk, so we'll try specifying that in the mount command to see if it helps, ```
sudo mount -t ext2 /dev/fd0 /media/floppy0
```That should work if it's ext2. I works for me, and the simpler command works too, I just re-tested them both.

If it was a FAT32 floppy you might try ```
sudo mount -t vfat /dev/fd0 /media/floppy0
```Regards, Herman :)

---

### Post by Virgo53 on 2007-04-05
When I type mount  /dev/fd0 I'm getting the message:

mount: can't find /dev/fd0 in /etc/fstab or /etc/mtab

I was able to select the filesystem type (Linux native ext2)

and format the floppy by running GFloppy.

Then from terminal I put in:

mkdir /media/floppy/boot

mkdir /media/floppy/boot/grub

cd /boot/grub

cp stage1 stage2  /media/floppy/boot/grub

I haven't checked yet to see if it'll work or not- hoping to get more replies on this

first to see if anything has been overlooked.  :confused:

---

### Post by Herman on 2007-04-05
Quoted from the Official Ubuntu Wiki how-to:
> If you want to boot the operating system already installed on the machine you are making the floppy from, also copy /boot/grub/menu.lst and /boot/grub/device.map to the corresponding directories on the floppy.

---

### Post by Virgo53 on 2007-04-05
Yes, I saw that but aren't exactly sure of all  the commands to get /boot/grub/menu.1st

and /boot/grub/device.map placed properly on the boot floppy.  :confused:

---

### Post by Herman on 2007-04-05
```
sudo cp -r /boot/grub /media/floppy0/boot
``` Why not just copy the whole grub directory and everything in it at once?

---

### Post by Virgo53 on 2007-04-05
I tried sudo cp -r /boot/grub media/floppy0/boot and got:

cp: cannot create directory  ` /media/floppy0/boot` : No such file or directory

BTW, what exactly does the 0 after floppy signify?  :confused:

---

### Post by Herman on 2007-04-06
Well, if you do 'ls -l /media' you'll get a list of directories in /media which are 'mount points'. ```
ls -l /media
``` Mine includes both floppy and floppy0, cdrom and cdrom0. 
I'm not sure why anymore now, but I have always used floppy0 to copy to whenever I'm copying things to a floppy disk. That's a good question, I'll give it some thought and see if I can remember the reason why, or re-discover the reason. It may not make any difference, since floppy and cdrom are symlinks to floppy0 and cdrom0 anyhow.

I just found a box with some new looking floppy disks in it, I'll run through my how-to again and re-check that it works okay just to make sure. You should be able to copy the commands off the website and paste them in your own terminal and they should work. It might prevent any typing or syntax errors. That's how I do it. Sometimes there are a few things you have to be aware of that might need changing to suit your particular set-up though. The Wiki how-to should work the same, pretty much copy and paste. I'm running Edgy Eft at the moment, and you're Dapper LTS I see. I don't think that should make any difference. 

Do you get an icon on your Desktop that looks like a miniature floppy disk when the floppy is mounted? 

Regards, Herman :)

---

### Post by Herman on 2007-04-06
Yup, well I can definitely confirm that my own grub floppy disk how-to does work for me at least. It should work for anybody running Ubuntu in the whole world. Anyone should be able to just copy each of those commands off the website and paste them one at a time into a terminal. pressing 'enter' for each one and make a grub boot floppy in a few minutes. 
Unless there's a hardware problem or the floppy disks are defective. That happens to me a lot. It's hard to buy good quality floppy disks these days.

I hope you will be able to do it, grub floppy disks can be a lot of fun once they are made. You can add more menu.lst files to them and configure them run extra commands and do all sorts of tricks. Add a bunch of different splashimages to try out, try out some different color combinations for your grub menus and run all kinds of experiments.
It's really worth persevering with if you can have a grub floppy disk to play with when you are done. Don't give up.

Regards, Herman :)

---

### Post by Virgo53 on 2007-04-06
The main reason I wanted to create a GRUB boot floppy is so just in case my XP install ever

 goes sour and requires a reinstall, it would rewrite the mbr leaving Ubuntu inaccessible, right?

Anyway, my persistence along with Herman's help paid off- I successfully created the disk!

Summary of what worked for me:

1. Insert  blank floppy and open GFloppy > choose (Linux native) ext2 filesystem > format floppy

2. On Desktop click Places > Computer > Right click Floppy Drive and select Mount Volume
. 
3. Login to a terminal as root and type: (press enter after each command)

mkdir /media/floppy/boot

mkdir /media/floppy/boot/grub

cd /boot/grub

cp -r /boot/grub /media/floppy/boot

4. Right click the floppy icon on the desktop and select unmount volume

5. In the terminal window type: (press enter after each command)

grub

device (fd0) /dev/fd0

root (fd0)

setup (fd0)

quit

Thank you very much Herman from down-under!!     :guitar:

---

