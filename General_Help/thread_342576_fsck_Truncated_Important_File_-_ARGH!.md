---
title: "fsck Truncated Important File - ARGH!"
date: 2007-01-20
forum: General Help
---

### Post by bleearg on 2007-01-20
Today I decided to upgrade my Dapper machine to Edgy.  I did the smart thing and made backups of all my important directories and files.  I basically tar'd up my home directory, /etc, and some other important dirs and moved them onto a separate disk, as I was going to reformat my Ubuntu partition and do a clean install.

All went well until I rebooted.  During the reboot, fsck felt it necessary to check all my FAT32 partitions and found the most important file, home.tar.gz (uh, my home directory), and truncate it to 0 bytes:

```
/backup/home.tar.gz
  File size is 4294967295 bytes, cluster chain length is 90 bytes.
  Truncating file to 0 bytes.
Performing changes.
```

I need to know if it's possible to get this file back! I've tried using 'dosfsck', but the '-u' option elicits the following error:

```
sudo dosfsck -u /dev/sdc1/backup/home.tar.gz
Duplicate dots in name.
```

I'm so mad, because I made the backup and spent minutes making sure I formatted the right partition during install, double and triple checking everything.  I wasn't aware that I needed a backup of my backup and a backup of that backup on three different forms of media using off-site storage in an underground bunker protected by Cerebus and his legions of Hellhounds, just to ensure that stupid FSCK doesn't mess up something it shouldn't be touching in the first place.

As you can probably see, I'm a bit frustrated...I normally don't beg for help and would spend two days working the problem myself before posting, but I feel this warrants some more eyes earlier in the game.  Please help!

Thanks in advance.

---

### Post by rai4shu2 on 2007-01-20
FAT32 has a file size limit of 4GB - 1 (4294967295) bytes.

---

### Post by bleearg on 2007-01-20
So, basically, I'm screwed...even if I did recover the file, it probably wouldn't untar?

---

### Post by rai4shu2 on 2007-01-20
It might not have even written a file, actually. The archiver might have thrown an unseen error during your backup. This is why I always verify my archives after I make them.

If it did create a file, I'm not sure whether it's possible to recover.

---

### Post by bleearg on 2007-01-20
I did perform a 'tar -tvf' after the file was made and it did list the contents.  I assumed that was enough to verify the file.  I forgot about the 4GB limit on FAT32 partitions, though.  I *knew* I should have moved all the backups to my NAS device, but I had an itchy trigger finger and wanted to get the upgrade going as soon as possible.

Would using an app such as 'ddrescue' be worth it?

---

### Post by rai4shu2 on 2007-01-20
Might be worth a shot. I guess it couldn't hurt to try.

---

### Post by bleearg on 2007-01-20
=D>  I got my file back!  =D> 

It seems that Windows and DOS are actually good for *something*.  I booted back into my Windows installation and ran 'chkdsk /f'.  It recognized the file had the wrong size of 0 and fixed it.  I haven't yet tried to unpack the archive, but a list of the contents shows all my files!

I caution anyone who has this same problem to not make any changes to your FAT partitions.  Set the fsck option in /etc/fstab to '0' (the last column) and either unmount the drive or mount it read-only until you can boot into a Windows install to run 'chkdsk'.

I wish I could say I thought of this all on my own, but I found it here:

[https://bugs.launchpad.net/ubuntu/+source/dosfstools/+bug/62831](https://bugs.launchpad.net/ubuntu/+source/dosfstools/+bug/62831)

---

### Post by dcstar on 2007-01-21
> **bleearg said:**
> 
........
I wish I could say I thought of this all on my own, but I found it here:

[https://bugs.launchpad.net/ubuntu/+source/dosfstools/+bug/62831](https://bugs.launchpad.net/ubuntu/+source/dosfstools/+bug/62831)

Since (it seems) the fixed version has been uploaded into the Feisty repository, it would seem a backport of this would be in order to prevent any further corruption of people's data.

It may be a very good idea to put in a Backport request (in the relevant forum).

---

