---
title: "Mounting Windows partition help D:"
date: 2007-08-26
forum: General Help
---

### Post by SrEstroncio on 2007-08-26
Hello everyone :D

I tried to mount my windows partition to access it through ubuntu using this tutorial: [http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481)
I did everything it said but after I reboooted I got this screen when trying to acces the drive.

Unable to mount the selected volume.
mount: only root can mount /dev/hda1 on /media/windows

Any help would be appreciated. I'm quite the ubuntu illiterate D: thanks in advance

---

### Post by aJayRoo on 2007-08-26
EDIT: Sorry gave some advice that wasn't relevant.

---

### Post by SrEstroncio on 2007-08-26
oh thanks I was trying to access it by clickin on it, now thought the terminal
What would be the code to mount it from there?
sudo mount ...? my drive is called "44.0 GB Volume" and the folder I'm supposed to to mount it to is called /media/windows 
thanks again

---

### Post by SrEstroncio on 2007-08-26
Help, please? T_T

---

### Post by merlinus on 2007-08-26
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

-merlin

---

### Post by khughitt on 2007-08-26
Can you paste the contents of your [FONT="Courier New"]/etc/fstab[/FONT] file?

There is a "user" switch that is supposed to allow the drive to be mounted by all users which may do the trick.

---

### Post by SrEstroncio on 2007-08-27
here it its:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1    /media/windows    ntfs-fuse    auto,gid=1001,umask=0002    0    0

Uh, yersterday after my last post I looked around for a bit and after a while I terminaled this:

sudo -s -H
Password: ******* and I got into root, I think

Then I did this:

sudo mount /dev/hda1 
And BAM, I could access the windows partition through Filesystem > Media > Windows

Problem is, today when I turned on my comp i could not acces the partition
then I tried the same thing as yesterday

sudo -s -H
sudo mount /dev/hda1 
and error:
root@Raidne:/home/srestroncio# sudo mount /dev/hda1
mount: unknown filesystem type 'ntfs-fuse'
 
then I tried this:
root@Raidne:/home/srestroncio# sudo mount /dev/hda1 /media/windows

then the 44GB drive was treated as if mounted, but when I tried to access it through
Media > Windows I got this error:

The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "windows".

Any help would be rgreatly appreciated, thanks in advance.

---

### Post by SrEstroncio on 2007-08-27
snif, help please T_T

---

### Post by HellDragon on 2007-08-27
Looks like some chmod problem, but not sure

---

### Post by strabes on 2007-08-28
A line like this in your fstab should be enough:```
/dev/hda1 /media/windows  ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
```

Assuming you have ntfs-3g installed.

---

