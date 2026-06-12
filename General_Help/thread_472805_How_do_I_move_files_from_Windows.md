---
title: "How do I move files from Windows?"
date: 2007-06-13
forum: General Help
---

### Post by mickeyu422 on 2007-06-13
I have video and audio files saved to a folder in Windows XP. I have both drives hooked up to my computer with the XP one as my slave drive. Because I don't have a lot of free space left on my Ubuntu drive I was wondering if there was some way that I could make ubuntu recognize my XP hard drive in the slave slot? That way I could just play the files from that hard drive in VLC without having to save them to my filled hard drive. Thanks for the help.

---

### Post by HIFH on 2007-06-13
What type of drive is the XP drive?

Is Ubuntu currently not recognising the XP drive at all or do you just want to be able to write to the XP drive?

---

### Post by mickeyu422 on 2007-06-13
I have the NFTS 200GB IDE drive. It doesn't see it at all. I'm looking at "Computer" under the Places menu and I can see my USB flash drive when I plug it in but not my hard drive

---

### Post by HIFH on 2007-06-13
Post the results of the command

```

sudo fdisk -l

```

and it should be no problem to get it sorted

---

### Post by merlinus on 2007-06-13
Very useful info here:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

-merlin

---

### Post by mickeyu422 on 2007-06-13
Disk /dev/hda: 4327 MB, 4327464960 bytes
255 heads, 63 sectors/track, 526 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         500     4016218+  83  Linux
/dev/hda2             501         526      208845    5  Extended
/dev/hda5             501         526      208813+  82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *         581       24320   190691550    7  HPFS/NTFS
/dev/hdb2               1         580     4658818+   b  W95 FAT32

Partition table entries are not in disk order

---

### Post by mickeyu422 on 2007-06-13
do I have to be using 7.04 because that's what the website says. I have 7.04 but I haven't installed it yet

---

### Post by HIFH on 2007-06-13
No, 6.10 is just fine. Ok, I'm assuming you DO NOT what write permission, only read so you can play the files. Enter the following commands to do so:

```

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab

```

Add this line to the very bottom of the file that's just opened (on a new line)

```

/dev/hddb    /media/windows ntfs  nls=utf8,umask=0222 0    0

```

Save the file and then restart Ubuntu. Log back in, and it should now show you the new drive in Computer (or in /media/windows).

Hope it works :)

[COLOR="Red"]my bad. you actually wanted to paste this line into your fstab, not the one above:[/COLOR]

```

/dev/hdb1    /media/windows ntfs  nls=utf8,umask=0222 0    0

```

eek. sorry, very clumsy typo #-o hope its all alright for you.

---

### Post by mickeyu422 on 2007-06-13
Ya I wondered why it didn't work the 1st time lol but thanks so much for your help. really appreciated and it works beautifully now

---

### Post by HIFH on 2007-06-13
Ace. Glad it worked :) If, for any reason, you fancy having read as well as write access, a brilliant guide is [right here](http://ubuntuforums.org/showthread.php?t=217009)

That's just if you ever need it :)

---

