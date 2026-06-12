---
title: "Complete rebuild of &quot;/var&quot; directory"
date: 2007-10-29
forum: General Help
---

### Post by cybrid on 2007-10-29
Hi there fellow ubunters ;) . I need your help please. I run a home server with a normal (meaning it's not the server edition) ubuntu v7.10 (recently upgraded from v7.04). I used one HD for "/" and another for "/var", now the problem is that the one in witch "/var" was mounted, has crashed and seems unrecoverable (at least till where my knowledge reaches). What I would like to do is to maintain the machine working, since the systems still boots (with a lot of errors, produced by programs that need data that was in the "/var" directory) and the "/" HD still works OK . My question is; is there a way to rebuild the "/var" directory in the "/" HD, to a point where the system is fully usable again?

---

### Post by chrisccoulson on 2007-10-29
Someone posted recently after deleting the contents of /var accidentally. The post can be found here [http://ubuntuforums.org/showthread.php?p=3644570]("http://ubuntuforums.org/showthread.php?p=3644570")

It seems that they got a working system by copying the contents of /var from the live CD across. However, note that all the information related to installed packages on your system is stored in /var/lib/dpkg, so apt will have no idea what packages are installed on your system anymoe.

You may have success in trying this, but please be aware that your mileage may vary and you may end up just doing a reinstall anyway.

---

### Post by az on 2007-10-29
> **cybrid said:**
> Hi there fellow ubunters ;) . I need your help please. I run a home server with a normal (meaning it's not the server edition) ubuntu v7.10 (recently upgraded from v7.04). I used one HD for "/" and another for "/var", now the problem is that the one in witch "/var" was mounted, has crashed and seems unrecoverable (at least till where my knowledge reaches). What I would like to do is to maintain the machine working, since the systems still boots (with a lot of errors, produced by programs that need data that was in the "/var" directory) and the "/" HD still works OK . My question is; is there a way to rebuild the "/var" directory in the "/" HD, to a point where the system is fully usable again?

Well, you can edit your fstab and remove the /var entry.  Then, create the /var directory in your / directory.   When you get another hard drive, you can copy var back there and then mount it again.

Try data recovery using ubuntu-rescue-remix.  I don't know what you were running, but you can't just transplant a /var directory from one system to another.  As for re-installing, you would need to re-install just about every package on your system.  And even then, they package user data will be lost.

It would be far simpler to reinstall.

Better yet, try to recover the lost drive.  
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

Ask for data recovery help here:
[http://ubuntu-rescue-remix.org/forum/1](http://ubuntu-rescue-remix.org/forum/1)

Basically, image the faulty drive with gnu-ddrescue and then mount the image and fsck it.

---

### Post by cybrid on 2007-10-30
Thanks for the help :D . I think I'll try to use ddrescue to see if I can recover some data and if not, copy the /var directory from the live cd. 

Currently I'm at work, so I cannot try till I get home. I'll let you know the results ;) .

---

### Post by cybrid on 2007-10-30
Hey. I'm trying to use ddrescue, but my fear I don't have another 200Gb disk arround here to dump the image file, besides less than 5Gb were occupied in the crashed drive. Do you think I can mount a network HD from another machine I have, into the crashed server; witch has enough room for those 160Gb?. Also, is there any commandline tool to get info about witch /dev directory is being used for witch drive?.

Thanks in advance ^_^

---

### Post by az on 2007-10-31
> **cybrid said:**
> Hey. I'm trying to use ddrescue, but my fear I don't have another 200Gb disk arround here to dump the image file, besides less than 5Gb were occupied in the crashed drive. Do you think I can mount a network HD from another machine I have, into the crashed server; witch has enough room for those 160Gb?. 


[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

> **cybrid said:**
> 
Also, is there any commandline tool to get info about witch /dev directory is being used for witch drive?.

Thanks in advance ^_^
Well, if they are mounted, use mount or look in /etc/fstab

To see an individual partition's filesystem info , use vol_id

To see what drives are attached to your computer, run
cat /proc/partitions

---

### Post by cybrid on 2007-11-01
Finnaly I've stoped trying to recover the data, It's impossible. I think ddrescue is a great tool, but it seems to be a hardware malfunction. Therefore I've deciced to remove the damaged drive and install a fresh 7.10 server edition into the working one.

After installing one problem has arised. If I put the <vga=795> option into the grub menu entry to get the framebuffer properly set up to 1280x1024 and 16M. I only get a black screen, though there's no problem if I just don't use that option. I have an ATI 9600 card, am I doing something wrong? or should I file a bug to launchpad?

---

