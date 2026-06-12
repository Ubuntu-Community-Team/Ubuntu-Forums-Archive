---
title: "Transfering files using an old 7.04 copy on CD of Ubuntu"
date: 2008-06-21
forum: General Help
---

### Post by MaxGhost on 2008-06-21
I did some stupid things a few weeks back with my computer, and I got a blue screen of death on XP... entirely my fault, I know what I did wrong, etc.

I just remembered today I had an old copy of Ubuntu sitting around I could use to boot up my comp and possibly get the precious files on this hard-drive off and on-to my external hard-drive.

My problem is, I get the "You do not have permissions to write to this folder." error. This is, from what I can see, the only option I have right now, so I need to figure out how to enable permissions to be able to write on my external drive from my internal, while using a on-CD version of Ubuntu.

I really really hope you guys can help me out with this!


MaxGhost

---

### Post by scott_g on 2008-06-21
The drive could be mounted as a read-only...  Is your external drive formatted as a NTFS partition?  Could be why its giving you an error; if so, you'll have to install the ntfs drivers.  

Can you view the files on your external drive?

May be useful to post the output of 

```

sudo fdisk -l

```

when you run that in a terminal.

Scott

---

### Post by Tyke91 on 2008-06-21
you need root privileges. since your HD is already fragged and you're not actually using ubuntu as a working OS, type ```
gksudo nautilus
``` into a terminal and use the new administrative file manager window to copy your files. if you need more root windows, just enter gksudo nautilus as many times as you need to.

---

### Post by MaxGhost on 2008-06-21
> **scott_g said:**
> The drive could be mounted as a read-only...  Is your external drive formatted as a NTFS partition?  Could be why its giving you an error; if so, you'll have to install the ntfs drivers.  

Can you view the files on your external drive?

May be useful to post the output of 

```

sudo fdisk -l

```

when you run that in a terminal.

Scott

The output was :

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS



@Tyke91: I'll try that... thanks

Edit: no that didn't work... it doesn't let me access my main hard-drive, only the files on the CD, the desktop, and the root... nothing else! :(

---

### Post by iaculallad on 2008-06-21
Using your Gutsy LiveCD to mount your (I assume that it's an NTFS) windows drive:

Drop to your terminal and issue the following commands below.

-First is to create a mount point for your external drive:

```
sudo mkdir /mnt/ExtDrive
```

-Then force-mount the drive:

```
sudo mount -t ntfs /dev/sda1 /mnt/ExtDrive -o force
```

That should allow you to copy your files.

---

### Post by erwall on 2008-06-21
While I can't help you w/using a livecd, I can suggest trying Trinity Rescue Kit.  Download the iso and burn it on a cd and boot to it.  Choose the "Fileshare all drives as guest w/no security" option.  It'll then tell you what ip it got to connect to and then you should be able to browse your entire hard drive from any machine on your lan.  It's a great tool that I use daily to get stuff off of bad drives, etc.  Good luck!

---

### Post by MaxGhost on 2008-06-21
@iaculallad: This is the output I got...

ubuntu@ubuntu:~$ sudo mkdir /media/ExtDrive
mkdir: cannot create directory `/media/ExtDrive': File exists

ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sdal /mnt/ExtDrive -o force
mount: mount point /mnt/ExtDrive does not exist

---

### Post by iaculallad on 2008-06-21
Do this instead since you are mounting a removable device:

```
sudo mkdir /mnt/ExtDrive
sudo mount -t ntfs /dev/sda1 /mnt/ExtDrive -o force

```

---

### Post by MaxGhost on 2008-06-21
> **iaculallad said:**
> Do this instead since you are mounting a removable device:

```
sudo mkdir /mnt/ExtDrive
sudo mount -t ntfs-3g /dev/sda1 /mnt/ExtDrive -o force

```

Again, I get "mkdir: cannot create directory `/mnt/ExtDrive': File exists"

???

Edit: I think I should mention, I can see the files on the external usb drive, just can't move files from my intenal drive onto it...

---

### Post by iaculallad on 2008-06-21
If the folder exist, What about:
> 
sudo mount -t ntfs /dev/sda1 /mnt/ExtDrive -o force

---

### Post by MaxGhost on 2008-06-21
> **iaculallad said:**
> If the folder exist, What about:

O_o I get this: 
```
mount: /dev/sda1 already mounted or /mnt/ExtDrive busy
mount: according to mtab, /dev/sda1 is mounted on /media/disk
```

---

### Post by iaculallad on 2008-06-21
> **MaxGhost said:**
> O_o I get this: 
```
mount: /dev/sda1 already mounted or /mnt/ExtDrive busy
mount: according to mtab, /dev/sda1 is mounted on /media/disk
```

If that's the error, try to unmount it first:

```
sudo umount /dev/sda1
sudo mount -t ntfs /dev/sda1 /mnt/ExtDrive
```

---

### Post by MaxGhost on 2008-06-21
> **iaculallad said:**
> If that's the error, try to unmount it first:

```
sudo umount /dev/sda1
sudo mount -t ntfs /dev/sda1 /mnt/ExtDrive
```

Ok this is bull... umount: /dev/sdal: not found

---

### Post by logos34 on 2008-06-21
> **MaxGhost said:**
> Ok this is bull... umount: /dev/sdal: not found

typo--should be 

> sudo umount /dev/sda[COLOR="Red"]1[/COLOR] (not letter 'l')

But shouldn't it work fine mounted at '/media/disk'?  You're just reading from it...it's the usb drive that you're trying to write/copy to.  (By the way, you did download the ntfs-3g driver, right?  7.04 Feisty cd can't do it otherwise

---

### Post by MaxGhost on 2008-06-21
> **logos34 said:**
> typo--should be 



But shouldn't it work fine mounted at '/media/disk'?  You're just reading from it...it's the usb drive that you're trying to write/copy to.  (By the way, you did download the ntfs-3g driver, right?  7.04 Feisty cd can't do it otherwise

No I didn't get the driver... how do I get it? :P 

and thanks for the typo find

---

### Post by iaculallad on 2008-06-21
> **MaxGhost said:**
> Ok this is bull... umount: /dev/sdal: not found

That would be "1" not "l":

umount /dev/sda1

---

### Post by MaxGhost on 2008-06-21
> **iaculallad said:**
> That would be "1" not "l":

umount /dev/sda1

lol too late... logos found it first! :P

but really, how do I get the driver?

---

### Post by logos34 on 2008-06-21
try 

sudo apt-get install ntfs-3g ntfs-config

but you may have to add the provider to the feisty repo list first, not sure

edit: yes, just checked, they're in universe repo, so above should work

---

### Post by iaculallad on 2008-06-21
Try to issue the command below first if it mounts your NTFS drive without using NTFS-3G driver.

```
sudo mount -t ntfs /dev/sda1 /mnt/ExtDrive
```

---

### Post by MaxGhost on 2008-06-21
> **iaculallad said:**
> Try to issue the command below first if it mounts your NTFS drive without using NTFS-3G driver.

```
sudo mount -t ntfs /dev/sda1 /mnt/ExtDrive
```

mount: mount point /mnt/ExtDrive does not exist

... ok this is irritating... lol... btw I just rebooted my comp...

---

### Post by MaxGhost on 2008-06-21
> **logos34 said:**
> try 

sudo apt-get install ntfs-3g ntfs-config

but you may have to add the provider to the feisty repo list first, not sure

edit: yes, just checked, they're in universe repo, so above should work

tried that... I got this:

```
ubuntu@ubuntu:~$ sudo apt-get install ntfs-3g ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-3g
```

---

### Post by logos34 on 2008-06-21
> **MaxGhost said:**
> tried that... I got this:
E: Couldn't find package ntfs-3g[/code]

ok, try just

sudo apt-get install ntfs-config

---

### Post by MaxGhost on 2008-06-21
> **logos34 said:**
> ok, try just

sudo apt-get install ntfs-config

ubuntu@ubuntu:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-config

I have a really old copy, like 2 years old, so I don't think it has the configs on it...

---

### Post by logos34 on 2008-06-21
check to see that 'universe' repository is enabled in synaptic 
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28ntfs-3g%29](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28ntfs-3g%29)

---

### Post by MaxGhost on 2008-06-21
> **logos34 said:**
> check to see that 'universe' repository is enabled in synaptic 
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28ntfs-3g%29](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28ntfs-3g%29)

yep! that did it! universe wasn't enabled...

I still can't get to copy my files to my external drive tho... still says "you don't have permissions..."

---

### Post by MaxGhost on 2008-06-21
bump?

---

### Post by MaxGhost on 2008-06-21
bump...

---

### Post by MaxGhost on 2008-06-21
once again, bump?

---

### Post by MaxGhost on 2008-06-21
bump... This is kinda urgent... I want to be able to do this, then be able to wipe this disk clean to re-install XP on it after...

---

### Post by logos34 on 2008-06-21
> **MaxGhost said:**
> yep! that did it! universe wasn't enabled...

I still can't get to copy my files to my external drive tho... still says "you don't have permissions..."

sorry, last thing I saw was you had enabled universe, thought you could take it from there (I had to go to bed)...You have to then run **sudo ntfs-config** and enable write support for external device and set the mountpoint (which hopefully will take care of permissions issue).

---

### Post by MaxGhost on 2008-06-21
Thanks! that helped!

---

