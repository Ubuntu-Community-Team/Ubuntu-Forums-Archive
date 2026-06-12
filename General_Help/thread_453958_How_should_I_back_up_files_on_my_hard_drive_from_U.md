---
title: "How should I back up files on my hard drive from Ubuntu live CD"
date: 2007-05-24
forum: General Help
---

### Post by Nate7679 on 2007-05-24
My computer only has windows installed on it but won't boot windows. The computer works fine, I just can't load the OS. I would restore it with a clean install of windows, but the problem is that my files aren't backed up. 

The only option seems to be to boot up the Ubuntu live CD, get into the hard drive and copy the contents to an external drive. The live CD doesn't recognize my NTFS formatted hard drive or external drives, so how should I go about doing this?

---

### Post by aysiu on 2007-05-24
Well, it should recognize the external drive, but even if it does, you'll have to enable NTFS *write* support first, if you're going to use that external drive for backup (plug in the drive first):
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Once you've done that, paste (do not retype) these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo fdisk -l
df -h
cat /etc/fstab
``` and then paste the output back into this thread.

---

### Post by Nate7679 on 2007-05-25
I copied that into the terminal and I got this:

fdisk: invalid option -- h

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

What was that command for and what does all of this mean?

---

### Post by aysiu on 2007-05-25
The command is ```
sudo fdisk -l
``` There is no *h* in the command at all. That last letter is a lowercase L. Just copy and paste the commands *one line at a time*. Copy and paste the first command and then press *Enter*. Then copy and paste the second command, etc.

---

### Post by troseph on 2007-05-25
Make sure you have  "df -h"  as a different command, those are not options for fdisk.

---

### Post by Nate7679 on 2007-05-25
Sorry, my mistake.

sudo fdisk -l returns:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785       12161    91385752+   7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666    7  HPFS/NTFS

---

### Post by aysiu on 2007-05-25
That's great. Can you also post the output of those other two commands? Thanks.

---

### Post by Nate7679 on 2007-05-25
df -h returns

Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
varrun                506M  112K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  124K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
tmpfs                 506M   12K  506M   1% /tmp
/dev/sdb1             280G  223G   57G  80% /media/Maxtor 279GB 1 Touch


and cat /etc/fstab returns:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by aysiu on 2007-05-25
```
/dev/sdb1 280G 223G 57G 80% /media/Maxtor 279GB 1 Touch
``` Well, it looks as if your external drive *is* recognized. Its contents should be viewable in the /media/Maxtor directory.

Paste this command into the terminal: ```
sudo apt-get update && sudo apt-get install ntfs-config
``` Then go Applications > System Tools > NTFS Configuration Tool

The rest *should* be self-explanatory, but you can find a step by step guide (with screenshots) for NTFS write support here:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by Nate7679 on 2007-05-25
I had to add the universe and multiverse software sources but I have installed ntfs-config. 

I am able to mount /dev/sda1 but that is a partition that dosen't contain files I'm interested in backing up.

When I tried mounting /dev/sda2 I got this error:

Mounting /media/windows failed.

Failed to mount '/dev/sda2': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.

But as you know, I can't boot windows. Now when I start up the NTFS configuration tool I am unable to mount any other drives or partitions. What should I do now?

---

### Post by aysiu on 2007-05-25
That input/output error could actually be related to your inability to boot into Windows.

You might have to do something a little more complicated, like use *ddrescue*. More details at the bottom of this page:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by Nate7679 on 2007-05-25
Well I'm willing to do what it takes to back up this drive. As I understand it, ddrescue would allow me to copy the partition containing my important files to my external drive without mounting it? That sounds like it could be my best option for getting the files off of this drive. One question though, would the error message that I get cause any problems backing it up? Or is that error related to mounting the drive, which I don't need to do to copy the partition?

---

### Post by aysiu on 2007-05-25
Yes, it will allow you to copy the info without mounting it, but you could also probably have a better chance of mounting the .img later (after ddrescue) in order to retrieve the backed up files. In fact, right after copying with *ddrescue*, I'd mount the .img file and make sure you can see the files before you do a reinstall of Windows (you don't want to lose your data!).

I'm not a *ddrescue* expert, but I have used it once before. I wouldn't proceed further without reading up more on *ddrescue*:
[http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)
[http://www.cyberciti.biz/tips/how-do-i-save-recover-data-from-crashed-disks-with-dd-and-ddrescue-command.html](http://www.cyberciti.biz/tips/how-do-i-save-recover-data-from-crashed-disks-with-dd-and-ddrescue-command.html)
[http://www.garloff.de/kurt/linux/ddrescue/](http://www.garloff.de/kurt/linux/ddrescue/)
[http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html](http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html)

---

### Post by Nate7679 on 2007-05-25
Why do you recommend copying it into a .img file? Wouldn't that just make it more difficult to manage?

And another question, does my external drive need to be empty?

---

### Post by aysiu on 2007-05-25
> **Nate7679 said:**
> Why do you recommend copying it into a .img file? Wouldn't that just make it more difficult to manage?

And another question, does my external drive need to be empty?
The answer to all those questions is: an .img file allows you to copy it over without erasing everything that's already on the external drive. If you do something like ```
dd_rescue /dev/sda2 /dev/sdb1
``` that copies all of /dev/sda2 to all of /dev/sdb1. If, however, you do ```
dd_rescue /dev/sda2 /media/Maxtor/sda2.img
``` then the image of /dev/sda2 will appear as a file called .img on /dev/sdb1 and won't erase the other contents on the Maxtor drive.

---

### Post by Nate7679 on 2007-05-25
Alright, so thats what I have to do if my drive isn't empty, which its not.

And then once I have the image on my external drive, I can mount it on my other computer from windows, then copy the data from the virtual drive over to wherever I want? This dosen't sound too difficult. 

In my case, would running fsck on the disc image be helpful, or is it just good to do regardless? Will it fix any errors that it finds?

---

### Post by aysiu on 2007-05-25
I don't really know how to mount .img files in Windows, but it probably can be done.

My understanding is that dd_rescue will copy all the bits and bytes of a drive but skip anything bad (those input/output errors?) so that you can retrieve what's... retrievable.

After copying to the .img file, I'd check in Ubuntu first (mount the .img file) to make sure you can see some of the files **before** you reinstall Windows (if that's what you're planning to do).

---

### Post by Nate7679 on 2007-05-25
Honestly, I don't know why it wouldn't be able to recover everything. The problem seems to be within windows, I don't think theres a problem with the drive itself.

---

### Post by Nate7679 on 2007-07-28
Sorry for the long delay. I made this thread a while ago.

Anyway, I typed in the command

dd_rescue /dev/sda2 media/Maxtor 114GB.img

And it returned

dd_rescue: (fatal): open "/dev/sda2" failed: Permission denied

What do I need to do to make Ubuntu recognize this partition? I have tried to mount it with NTFS-3G but I always get this error:

Mounting /media/internaldrive failed.

Failed to mount '/dev/sda2': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.

But I can't do that... is there anything else I can try?

---

### Post by nisarg on 2008-03-12
Hi,

I am wondering if anyone can give me a hand with ddrescue.
Heres, the thread I started. 
[http://ubuntuforums.org/showthread.php?t=722350](http://ubuntuforums.org/showthread.php?t=722350)

I need to resume the backup that was running for over a week, and crashed due to may be a reset or something on the network.
Now when I am using the same command I used previously, pointing to the same backup.img and backup.log it starts and then terminates in a couple of mins with error: Invalid argument.
Would you be able to help?
Thanks, N

---

