---
title: "Cloning a Windows Hard Drive with DD"
date: 2013-11-27
forum: General Help
---

### Post by SirLouen on 2013-11-27
I have a windows 8 installation in an HD, /dev/sdb

I would like to clone it into an disk image lets say win8.bin

After that I would like to put win8.bin in a new hard drive (lets say I swap the HD with the new one so It could be also /dev/sdb

I believe I could do this with DD by running this commands:

# dd if=/dev/sdb of=/home/user/images/win8.bin bs=1M
# dd if=/home/user/images/win8.bin of=/dev/sdb bs=1M

Thing is: Should I format the new disk with the same filesystem as the origin? (in this case as is Windows 8, NTFS)

---

### Post by oldfred on 2013-11-27
Never used dd for cloning but it is for exact size to exact size imaging. It is a bit for bit copy so no formatting of new drive required, it will end up being identical down to same UUIDs. In fact you cannot have both drives plugged in when you reboot as then you have duplicate UUIDs.

dd also copies all unused space so if drive is half empty it will still copy all of that also. That can make it a lot slower than other cloning tools.

       Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[URL="http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/"]http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/

      [/URL]
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)

 
    [URL="http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/"]
[/URL]

---

### Post by VMC on 2013-11-27
> **oldfred said:**
> ...dd also copies all unused space so if drive is half empty it will still copy all of that also. That can make it a lot slower than other cloning tools...I've seen this topic come up in other forums. I don't know if its because of "old school" or what. I don't know the reasoning behind using *dd* in this this way, when other programs can do a better job. As in verification, and much smaller by not copying unused space. 

*dd* has its place, but I never use it this way. I can't think of any benefits. Maybe someone else can.

---

### Post by SirLouen on 2013-11-27
Maybe the simplicity of a built in command that doesnt require much knowledge in order to run a very soft clone of hdd. I know there are plenty of solutions that do the trick but the thing is this:
- I have my old HDD 60Gb
I would like to clone it into a new (not formated) 120Gb HDD

I believe that if i clone the 60gb into the 120gb then the other 60gb may be appear in a non-filesystem state or something? Thats why i was thinking the idea of preformatting the 120Gb before doing the cloning :)

---

### Post by oldfred on 2013-11-27
Even if you attempt to format it before hand the dd will write your old partition table info over anything you have on new drive.
I did see one user who was not able to use any partition tools after a dd clone. He ended up downloading some software from hard drive vendor that seemed to unlock whatever locked it up. Most cases you have to resize afterwards with gparted or your favorite partitioning tools.

---

### Post by efflandt on 2013-11-27
Note that if you have any bad sectors, dd would also attempt to copy those, even if you already repaired the partition. And if you already mark out badblocks those would also be locked out when cloned. But I could not get clonezilla to work for a repaired Windows partition with bad sectors, because it choked when it could not get past the bad sectors. So I had to image the drive with Acronis (WD free version) which had an option to do file by file image instead of sector by sector. That worked and could even expand a partition while writing it to a different drive.

More recently the Linux partition at the far end of my 1 TB drive started going bad. I used Acronis to image the Win7 partitions (after shrinking main partition to increase room for Linux) to a new drive (and mbr since I have grub on a different drive), reinstalled Linux, and copied my home directory over to the new drive. As far as I know only a few Steam game files were corrupted from the failing drive and I was able to fix those by verifying game cache. With Steam for Linux I needed more room for Ubuntu anyway, so that gave me a chance to enlarge my Linux partition.

---

### Post by SirLouen on 2013-11-27
Ok, I will try dd straight away and resizing with gparted afterwards.
Lets see how it looks in the end :)
In case i find problems I will format and try cloning specific tools.

---

### Post by aysiu on 2013-11-28
I would highly recommend using CloneZilla instead of *dd*. It will clone much more quickly!

If you are going to go a *dd*-like route, use *ddrescue* instead.

---

### Post by sudodus on 2013-11-28
> **aysiu said:**
> I would highly recommend using CloneZilla instead of *dd*. It will clone much more quickly!

If you are going to go a *dd*-like route, use *ddrescue* instead.

+1

---

