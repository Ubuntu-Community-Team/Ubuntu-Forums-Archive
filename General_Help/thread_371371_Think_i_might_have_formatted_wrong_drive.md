---
title: "Think i might have formatted wrong drive"
date: 2007-02-26
forum: General Help
---

### Post by mr32123 on 2007-02-26
I was installing ubuntu 6.10 on my computer which has 2 drives.  I was installing on the primary.  The secondary has all my data on it.  Is it possible that ubuntu reformatted that drive as well and erased all the data?  If it didnt then is there a way to convert from the Ubuntu filesystem to ntfs without losing any data?


please help, i had some cad files on the drive that i need to recover, but when i boot back into windows, it wont detect the drive.

---

### Post by bodhi.zazen on 2007-02-26
It is possible you re-formatted the disk when you installed Ubuntu ...

Lets look

Boot Ubuntu

In a terminal enter the following and post the output ;

```
sudo fdisk -l
```

---

### Post by JohnPhys on 2007-02-26
How sure are you that you formatted the drive?  When you installed, was the box checked to format the partition?  

If you just wrote a different partition table, it's possible to recover everything, but if you formatted, I'm not sure if it can be done.

---

### Post by mr32123 on 2007-02-26
well see, here's another problem. :(  I knew I set it to install on the primary alongside of windows.  I know i set the partition to set up on the primary.  I'm hoping that if you dont select the secondary for anything it doesnt touch it (it really shouldnt if you think about it).  So when it was partitioning for over three hours i had a hunch something was wrong.  

I halted the process and rebooted my computer.  Ubuntu did not install, so i checked my windows (xp) and there was nothing wrong with it. I hadn't noticed that the secondary drive was MIA.

sooooo... now i dug up another older spare hd i had and im installing ubuntu on it to see if it will recognize the drive... and im hoping it does...

in the meantime any suggestions?

---

### Post by bodhi.zazen on 2007-02-26
Hard to know at this point.

As a first step I would like to know what the partition looks like from Linux.

Either gparted or fdisk -l ???

---

### Post by mr32123 on 2007-02-26
ok so now i hooked up the secondary drive and its taking a very long time... how long does it usually take? that is after you type in sudo fdisk -l

---

### Post by mr32123 on 2007-02-26
idk if this helps but when I open up my computer it only shows one filesystem

---

### Post by llamakc on 2007-02-26
Have you physically removed the drive in question from the machine and replaced it with another disk?

---

### Post by mr32123 on 2007-02-26
bodhi.zazen:

Disk /dev/hda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         747     6000246   83  Linux
/dev/hda2             748         784      297202+   5  Extended
/dev/hda5             748         784      297171   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24321   195358401    7  HPFS/NTFS

---

### Post by bodhi.zazen on 2007-02-26
Well, it looks like your drive is intact ...

Lets see if we can access the data from Ubuntu.

Try installing ntfs-config :

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

Then, let's back up and we can work on Windows, although I do not know if I can help much there ...

---

### Post by mr32123 on 2007-02-26
Its no longer there... I looked on google and im trying to find a working download but no luck so far.  is there another program perhaps? or is it possible for someone to email me the program? It looks as though it is a rather small package [email]robk1324@gmail.com[/email]

---

### Post by Maestro23 on 2007-02-26
> **mr32123 said:**
> Its no longer there... I looked on google and im trying to find a working download but no luck so far.  is there another program perhaps? or is it possible for someone to email me the program? It looks as though it is a rather small package [email]robk1324@gmail.com[/email]

[http://www.gnomefiles.org/app.php?soft_id=1872](http://www.gnomefiles.org/app.php?soft_id=1872)

*Edit: Sorry that is busted as well.

---

### Post by mr32123 on 2007-02-26
What other programs could do the same job?

---

### Post by Maestro23 on 2007-02-26
> **mr32123 said:**
> could ntfs-3g work in its place?

I was looking at that.  Never used it myself, but it looks like it could.

---

### Post by mr32123 on 2007-02-26
hmm not quite

---

### Post by bodhi.zazen on 2007-02-26
Well, you should be able to mount the device read only like this :

```
sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/hdb1 /media/windows
```

Now access the partition as root :

```
gksudo nautilus /media/windows
```

---

### Post by mr32123 on 2007-02-27
rob@rob-desktop:~$ sudo mkdir /mnt/windows
mkdir: cannot create directory `/mnt/windows': File exists
rob@rob-desktop:~$ sudo mount -t ntfs /dev/hdb1 /media/windows
mount: mount point /media/windows does not exist


this is what i get.  After creating the directory,  It says that the mount point doesn't exist

---

### Post by bodhi.zazen on 2007-02-27
> **mr32123 said:**
> rob@rob-desktop:~$ sudo mkdir /mnt/windows
mkdir: cannot create directory `/mnt/windows': File exists
rob@rob-desktop:~$ sudo mount -t ntfs /dev/hdb1 /media/windows
mount: mount point /media/windows does not exist


this is what i get.  After creating the directory,  It says that the mount point doesn't exist

Ooops, me bad ....

Sorry for the typo there ....

Try : ```
sudo mount -t ntfs /dev/hdb1 /mnt/windows
gksudo nautilus /mnt/windows
```

---

### Post by mr32123 on 2007-02-27
Well well well.. thank you everyone for ALL the help and advice.  Especially you, bodhi.zazen, because it would have been your advice that would have saved me as i tried it afterwards...

It turns out after trying various things, the reason why it failed was due to a faulty IDE connector cable, that got progressively worse everytime i swapped drives.

I thank you all for your support and I'm sorry I sort of wasted your time however it taught me a lot.

you guys :guitar:

---

### Post by bodhi.zazen on 2007-02-28
You are most welcome.

---

