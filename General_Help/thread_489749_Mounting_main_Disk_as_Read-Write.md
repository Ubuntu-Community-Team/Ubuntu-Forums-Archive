---
title: "Mounting main Disk as Read-Write"
date: 2007-07-01
forum: General Help
---

### Post by zeph7r on 2007-07-01
Hi. This is my first time in ubuntu and it's being a very pleasant experience. However I've been having some issues mainly because I choose the wubi approach (it's a great app don't get me wrong...)
My disk has winxp in it and it is fat32 formatted so I wanted to mount it with read-write access and do it my main storing device. I've noticed that since the begining the drive has been being mounted, however with no read-write access. Once I tried to unmount it and it didn't work out, I remembered to check the fstab only to find that it wasn't there (only the paths to the images with the virtual disks were). So, as my multiple approaches so far have reached nothing I decided to come to the foruns see if someone could help...

By the way, is there any workaround to the hibernate/suspend issue already? I have an Acer Aspire 1691 WLMi and I'm having the same problem: can't get past the shutting down black screen; it shows a bunch of errors though.

Greets,
--zePh7r

---

### Post by ago on 2007-07-02
> **zeph7r said:**
> I've noticed that since the begining the drive has been being mounted, however with no read-write access.
/media/host is always mounted r/w. Maybe you do not have permission to write, did you try to write as root (just to try)?

> By the way, is there any workaround to the hibernate/suspend issue already?
Not yet

---

### Post by zeph7r on 2007-07-22
yeah, in fact I have write access if i'm the root user or through sudo. But I would prefer to have write access with my main user, since most applications can't deal with super-user mode. So, I thought about changing permissions to /media/host through chmod but it didn't work. Since this device is not mounted through the fstab, I can't change its umask.

---

### Post by zeph7r on 2007-08-07
hasn't anyone got a clue on how to enable disk write access? this is the main thing that's keeping me from using ubuntu as my main os right now

---

### Post by tuxcantfly on 2007-08-07
Assuming that your hard drive is /dev/sda1 and is fat32:
```

sudo mkdir /media/vfat
sudo mount -t vfat /dev/sda1 -o rw /media/ntfs
```

if it works read-write after that, when accessed through /media/ntfs, just add it to the /etc/fstab

---

### Post by zeph7r on 2007-08-13
it didn't work, but i thought that the combination you provided was a little odd, don't you think? Because I didn't create the dir /media/ntfs and therefore it doesn't exist. Also, what is device /dev/sda1-o? I don't have it. I suppose you were trying to say /dev/sda1 -o rw which I also tried, without success. I also tried several other combinations of the mount command trying to mount it and it came up that if I tried no mount it only as a read device it would mount it without a problem, but if I tried to mount it as read-write it showed an sintaxe information on how to use mount, suggesting there was an error.
Really, I'm trying to think this issue of mine is odd enough. Didn't anyone tried to write from ubuntu to the rest of their drive yet? How come no one stumpled upon this problem too yet? Right now this is the one thing that's keeping me from using ubuntu full-time.

---

### Post by zeph7r on 2007-08-18
here is my fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults          0   0
/media/host/wubi/disks/system.virtual.disk      /               ext3        loop,sync         0   1
/media/host/wubi/disks/home.virtual.disk      /home           ext3        loop,sync         0   2
/media/host/wubi/disks/swap.virtual.disk      none            swap        sw                0   0

as uou can see there's no reference to to the rest of my hdd

---

### Post by hh93 on 2007-08-21
Hello All,

Happy to finally meet you all. Thanks so much to Ago and Tuxcanfly that have replied to this thread, I know how busy you guys are, I truly appreciate the time and efforts you put in to assist us wubi users.

Truth is, i am having the same problem as zeph7r did, let me elaborate.

For post installation steps I've followed psycocat (aysiu's) guide, including mounting windows to rectify permissions to allow read and write to host,  prior to trying the method suggested in this thread. 

I had wanted to migrate Ubuntu to a real partition and realized that  another alternative is  to boot from a Live CD and reinstall Ubuntu to a real partition. 

It's just that, i like the Ubuntu  i have running at the moment. It is apparent, that during installation it had extracted all the information from windows, that my laptop and all its accessories  work right away; the laptop connect to both to my home wireless network and wired  network at work immediately and seamlessly; no installation and configuration steps required from my side. I guess Ubuntu must have extracted all information including those regarding network, from windows. 

Now that Ubuntu of mine has basically emulate  windows environment and allow me to experience linux, i am discouraged from  installing ubuntu from live CD, as the ubuntu it installs may not emulate my windows environment as well as wubi installed Ubuntu did.

To migrate Wubi installed Ubuntu to a real partition, i followed the guide provided by herman, and use partition manager. I downloaded partitionmanager_20_all.deb from sourceforge, and run it. It failed, though, to install, due to and i quote

	"error setting ownership of './boot/pmbinint': Operation not permitted dpkg-deb: subprocess paste killed by signal (Broken pipe)"

I have researched and tried suggestions from ubuntu support forum including from this thread to change ownership and permission and the method to mount host to different directories as to allow the installation of partition manager.  No luck yet, unfortunately: after each modification, partition manager still fail to install for the same error cited above. 

Do assist us: thanks so much in advance.

hh93

---

### Post by hh93 on 2007-08-22
Hi All,

My migration problem was resolved please see [http://ubuntuforums.org/showthread.php?t=438591&page=8](http://ubuntuforums.org/showthread.php?t=438591&page=8)

seph7r, do have a look, see if it may provide any insight.

hh93

---

### Post by zeph7r on 2007-09-06
thank you for replying hh93 
could you post the link to that aysiu's guide you mentioned?

cheers

---

### Post by hh93 on 2007-09-18
been away for sometime, sorry for not replying sooner zeph7r.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

