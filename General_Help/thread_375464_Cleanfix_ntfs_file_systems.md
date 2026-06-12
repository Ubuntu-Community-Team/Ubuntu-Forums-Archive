---
title: "Clean/fix ntfs file systems???"
date: 2007-03-03
forum: General Help
---

### Post by PaulFXH on 2007-03-03
I have three ntfs partitions on an external usb HD that appear to have been corrupted which has made it more difficult to mount the systems (although by no means impossible).
I have tried "fsck" to no avail (error = no fsck.ntfs found ) and attempts to check the partitions in Windows always lead to bluescreening.
Is there any other way to clean/check/fix these ntfs file systems within Ubuntu?

---

### Post by Azakus on 2007-03-03
Install ntfsprogs, ntfs-3g, and gparted.
Then use Gparted and run the check from there.
```
sudo aptitude install ntfsprogs ntfs-3g gparted
```

---

### Post by PaulFXH on 2007-03-04
Thanks for the reply, Azakus
I tried what you suggested. However, the fs check from the Gparted live CD didn't seem to do much checking. The check on each  of the 50-60 GB systems took about 1 second each and no reading of the external drive was evident.
I also checked the other partition on the same drive which is ext3 (also 55 GB) and this took about 20 seconds with a lot of "noise" from the external drive.
Also, it made no difference to the problem I'm still trying to eliminate. (And, yes, I DID install the ntfsprogs and ntfs-3g).
Anyway, worth a try.
Paul

Edit:
Just after posting this, I realised that running from the Gparted live CD was crazy as there is no access to ntfsprog or ntfs-3g.
OK, so I ran Gparted from Terminal. However, now there was no "check" option in the Partitions tab so even though the ntfs tools were now available I still couldn't do the check.
Googling on this seemed ti indicate that the version of Gparted (0.2.5) in Ubuntu's repos is problematic.
Paul

---

### Post by Sef on 2007-03-04
Check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by PaulFXH on 2007-03-04
Thanks Sef
However, from what I can see this is more a tool for data recovery rather than "fixing" a corrupted partition. Note that my problem is not lack of access to my data on the usb drive but the fact that I can't get it to automount (hotplug).
However, this may well prove useful in the future.
Paul

---

### Post by Azakus on 2007-03-04
Try using the latest version of GParted. Current version is 0.3.3 I believe (that's the one I'm using). Here's a script to make it.
```
sudo aptitude install libgtkmm-2.4-dev libgtkmm-2.4-1c2a libparted1.7-1 libparted1.7-dev
wget http://downloads.sourceforge.net/gparted/gparted-0.3.3.tar.bz2?modtime=1165424936&big_mirror=0
tar xjvf gparted*
cd gparted*
./configure
make
make install
```

---

### Post by PaulFXH on 2007-03-04
Thanks, Azakus
I'm going to download that newer version of Gparted as it's a very useful tool to have in the armoury.
However I got the problem solved. Turns out it wasn't a corrupted partition issue (external drive mounted perfectly to another computer) but a broken diskmounter (or something) in Ubuntu.
I used this [guide]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") (script method) to get things back to where they were.
Best wishes
Paul

---

