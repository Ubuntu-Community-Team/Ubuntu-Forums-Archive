---
title: "Problems getting RocketRaid 622 PCIe Sata III controller to work"
date: 2012-12-02
forum: General Help
---

### Post by cwn42 on 2012-12-02
I am having issues installing the drivers as well and am not sure how to proceed.  It looks like the directions from: "https://help.ubuntu.com/community/RocketRaid#Shortcut_-_DEB_Packages_for_DKMS" may be the most accurate but as a newbie I am having difficulties following these directions.  I am installing on 12.04 LTS and it looks like pals007 had the same problem I have now.  CharlesA if you're out there can you help?  Thanks in advance!

---

### Post by CharlesA on 2012-12-02
Move to it's own thread. The other thread can be found [here]("http://ubuntuforums.org/showthread.php?t=1918036").

So you are running Ubuntu 12.04 with the RocketRaid 622? I have not had much success with the debs, so I compile from source.

When you try to install the debs, does it give you an error?

---

### Post by cwn42 on 2012-12-02
Thank you Charles.  Last time i made all the changes and then the build did not complete.  So I reinstalled the OS to start over from a clean slate.  I just attempted to follow the guide again making all of the changes and when I got to "* Remove the config.h include statement from osm_linux.h"
I would use

joker@GothamCity:~/rr62x-linux-src-v1.1$ vi osm_linux.h

and i also tried

joker@GothamCity:~/rr62x-linux-src-v1.1$ vi inc/linux/osm_linux.h

and the editor would open a blank slate so I exited out.  

How do I edit the osm_linux.h file?

Or should i just start all over again and follow a different set of instructions?

---

### Post by cwn42 on 2012-12-02
Also I should ask I intend to use the drives in RAID array so do I need version 1.1 of the RocketRaid Drivers?  Or should I just use 1.0 and configure the RAID in the BIOS at bootup?  I guess if I want to modify the arraid later or add drives it would be better to use 1.1?

---

### Post by cwn42 on 2012-12-02
I have also to locate the file using

joker@GothamCity:~/rr62x-linux-src-v1.1$ find /path -name osm_linux.h

but the file cannot be found

---

### Post by CharlesA on 2012-12-02
Did you try installing the deb files first? If they would, it would be way easier than trying to edit the source yourself.

---

### Post by cwn42 on 2012-12-02
I was able to locate the file location using file manager and webmin.  I am editing the file through the command line using VI editor.  I was able to complete the following step:

* Remove the config.h include statement from osm_linux.h

-#ifndef AUTOCONF_INCLUDED
-#include <linux/config.h>
-#endif

The next step says to:

* Fix :: I'm guessing this used to work, but not on 11.10, replace with the following (osm_linux.h)

+#include <generated/autoconf.h>

Does this mean to add the line or to change the current line within the code from "#include <linux/version.h>" to 
"#include <generated/autoconf.h>"?

---

### Post by CharlesA on 2012-12-02
Anything starting with a - is taken out and anything with a + is added.

I will mess with the source and see what happens.

---

### Post by cwn42 on 2012-12-02
I had tried the deb file yesterday but it wouldn't complete the build.  I thought that maybe it would be better to follow the instructions to do the editing instead since you had mentioned that you haven't had good luck deb packages.  If you think it would be better to start over and use the deb package I can start over again. But I was not sure what I was doing wrong before.

---

### Post by cwn42 on 2012-12-02
ok.  I will add that line but should the other line remain?  It wasn't clear since he called it fix.  Also is there a specific place in the code that the new line should be placed?

---

### Post by cwn42 on 2012-12-02
for the instruction 

* Modify the method call to blkdev_get to include a third parameter, NULL, in os_linux.c:

-blkdev_get(bdev, FMODE_READ)
+blkdev_get(bdev, FMODE_READ, NULL)

I found this change on line 263 of the code and did not see it anywhere else

---

### Post by CharlesA on 2012-12-02
> **cwn42 said:**
> ok.  I will add that line but should the other line remain?  It wasn't clear since he called it fix.  Also is there a specific place in the code that the new line should be placed?

I think you needed to remove the AUTCONF lines and add the /generated/whatever line.

> **cwn42 said:**
> for the instruction 

* Modify the method call to blkdev_get to include a third parameter, NULL, in os_linux.c:

-blkdev_get(bdev, FMODE_READ)
+blkdev_get(bdev, FMODE_READ, NULL)

I found this change on line 263 of the code and did not see it anywhere else

I think that is only in there once.

EDIT: I just tried the deb and it worked fine on the VM I tested it on. You need to have DKMS installed first:

```
sudo apt-get install dkms
```

Then install the deb named rr62x-dkms_1.1_all.deb:

```
 sudo dpkg -i rr62x-dkms_1.1_all.deb
```

Try it again and see if it works.

---

### Post by cwn42 on 2012-12-02
ok.  Thanks.   I will try this.  My question for the deb packages is how to i properly download the package?  I tried to download this before but I could not figure out how to download it to the server.

---

### Post by cwn42 on 2012-12-02
I tried this:

joker@GothamCity:~$ sudo wget [https://help.ubuntu.com/community/RocketRaid?action=AttachFile&do=get&target=rr6xx-drivers-precise.tar.gz](https://help.ubuntu.com/community/RocketRaid?action=AttachFile&do=get&target=rr6xx-drivers-precise.tar.gz)
[1] 5547
[2] 5548
joker@GothamCity:~$ --2012-12-02 12:45:10--  [https://help.ubuntu.com/community/RocketRaid?action=AttachFile](https://help.ubuntu.com/community/RocketRaid?action=AttachFile)
Resolving help.ubuntu.com (help.ubuntu.com)... 91.189.90.19
Connecting to help.ubuntu.com (help.ubuntu.com)|91.189.90.19|:443... connected.
HTTP request sent, awaiting response... 403 Forbidden
2012-12-02 12:45:11 ERROR 403: Forbidden.

---

### Post by cwn42 on 2012-12-02
I can download the deb file to my laptop computer.  Should I do this and just transfer the file from my laptop to the server via file manager or filezilla?  If so where would I put the file?

---

### Post by cwn42 on 2012-12-02
I uploaded the file to the Home/Joker directory and ran:

sudo dpkg -i rr62x-dkms_1.1_all.deb

Here is what happens:

joker@GothamCity:~$ sudo dpkg -i rr62x-dkms_1.1_all.deb
Selecting previously unselected package rr62x-dkms.
(Reading database ... 76480 files and directories currently installed.)
Unpacking rr62x-dkms (from rr62x-dkms_1.1_all.deb) ...
Setting up rr62x-dkms (1.1) ...

Loading tarball for rr62x-1.O
Creating /var/lib/dkms/rr62x/1.O/source
Copying dkms.conf to /var/lib/dkms/rr62x/1.O/source...
Loading /var/lib/dkms/rr62x/1.O/2.6.38-11-generic-pae/i686...

DKMS: ldtarball completed.


Unable to load DKMS tarball /usr/share/rr62x-dkms/rr62x-1.1.dkms.tar.gz.
Common causes include: 
 - You must be using DKMS 2.1.0.0 or later to support binaries only
   distribution specific archives.
 - Corrupt distribution specific archive


dpkg: error processing rr62x-dkms (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 rr62x-dkms

---

### Post by cwn42 on 2012-12-02
I checked the file path

/usr/share/rr62x-dkms/rr62x-1.1.dkms.tar.gz

and the file is there.  Not sure what to do now.

I noticed in another forum that you instructed someone to use

sudo apt-get install dkms linux-headers-3.2.0-24-generic

do i need this as well?

---

### Post by CharlesA on 2012-12-02
If you already installed DKMS via apt-get, it should pull all those in with it.

Try downloading the archive again, extracting it and trying again.

Make sure dkms is installed:

```
 sudo apt-get install dkms
```

You could also check the make.log. Not totally sure where it would be but it should be in /var/lib/dkms

---

### Post by cwn42 on 2012-12-02
Here is what happens when i run the DPKG command:

joker@GothamCity:~$ sudo dpkg -i rr62x-dkms_1.1_all.deb
Selecting previously unselected package rr62x-dkms.
(Reading database ... 76480 files and directories currently installed.)
Unpacking rr62x-dkms (from rr62x-dkms_1.1_all.deb) ...
Setting up rr62x-dkms (1.1) ...

Loading tarball for rr62x-1.O
Creating /var/lib/dkms/rr62x/1.O/source
Copying dkms.conf to /var/lib/dkms/rr62x/1.O/source...
Loading /var/lib/dkms/rr62x/1.O/2.6.38-11-generic-pae/i686...

DKMS: ldtarball completed.


Unable to load DKMS tarball /usr/share/rr62x-dkms/rr62x-1.1.dkms.tar.gz.
Common causes include: 
 - You must be using DKMS 2.1.0.0 or later to support binaries only
   distribution specific archives.
 - Corrupt distribution specific archive


dpkg: error processing rr62x-dkms (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 rr62x-dkms

are you able to see what I am doing wrong?

---

### Post by cwn42 on 2012-12-02
CharlesA, thanks again for your help with this.  I saw in some other threads that others have had the same issue as me with the install but the steps presented to help them were not exactly clear so I apologize if you are having to revisit the same problem over and over again by helping me.

---

### Post by CharlesA on 2012-12-02
Run these and post the output please:

```
dpkg -l | grep dkms
```
```
dkms --version
```

---

### Post by cwn42 on 2012-12-02
joker@GothamCity:~$ dpkg -l | grep dkms
ii  dkms                             2.2.0.3-1ubuntu3                    Dynamic Kernel Module Support Framework
iF  rr62x-dkms                       1.1                                 rr62x driver in DKMS format.

joker@GothamCity:~$ dkms --version
dkms: 2.2.0.3
joker@GothamCity:~$

---

### Post by CharlesA on 2012-12-02
Same version I tested then.

Try redownloading the tar.gz and reinstalling the driver and see what happens.

---

### Post by cwn42 on 2012-12-03
Ok.  Maybe if i go step by step it would help.  I am downloading the tar.gz file from here:

[https://help.ubuntu.com/community/RocketRaid?action=AttachFile&do=view&target=rr6xx-drivers-precise.tar.gz](https://help.ubuntu.com/community/RocketRaid?action=AttachFile&do=view&target=rr6xx-drivers-precise.tar.gz)

Is that correct?  I am not sure how to download this using a wget command so i am downloading to my laptop and using filemanager on webmin to upload the file to /home/joker

If i am okay so far what command do I use next?

---

### Post by CharlesA on 2012-12-03
That should be fine.

Purge the failed package:

```
test@ubuntu:~$ sudo apt-get purge rr62x-dkms
```

Then reinstall it with dpkg -i:

```
sudo dpkg -i rr62x-dkms_1.1_all.deb
```

Here is the SHA1SUM of the deb if you want to make sure it isn't corrupted.

```
test@ubuntu:~$ sha1sum rr62x-dkms_1.1_all.deb
73f715d81825ca6a9da688999ad9ef6fefa52271  rr62x-dkms_1.1_all.deb

```

The install should look like this:

```
test@ubuntu:~$ sudo dpkg -i rr62x-dkms_1.1_all.deb
Selecting previously unselected package rr62x-dkms.
(Reading database ... 52263 files and directories currently installed.)
Unpacking rr62x-dkms (from rr62x-dkms_1.1_all.deb) ...
Setting up rr62x-dkms (1.1) ...
Loading new rr62x-1.1 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-23-generic
Building for architecture x86_64
Building initial module for 3.2.0-23-generic
Done.

rr62x:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-23-generic/updates/dkms/

depmod....

Backing up initrd.img-3.2.0-23-generic to /boot/initrd.img-3.2.0-23-generic.old-dkms
Making new initrd.img-3.2.0-23-generic
(If next boot fails, revert to initrd.img-3.2.0-23-generic.old-dkms image)
update-initramfs....

DKMS: install completed.
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic

```

---

### Post by cwn42 on 2012-12-03
I purged the old file and then ran the sha1sum command and it looks similar to yours but the numbers and letters are different:

joker@GothamCity:~$ sha1sum rr62x-dkms_1.1_all.deb
d4f5569e6afbc69c8cea69c595d3a50d3d93b9ef  rr62x-dkms_1.1_all.deb

I am not sure what this means but I am not sure if it means its corrupted or not.  Am okay to continue with the install?

---

### Post by cwn42 on 2012-12-03
It did not install again.  Here is what i get when i run dpkg:

joker@GothamCity:~$ sudo dpkg -i rr62x-dkms_1.1_all.deb
Selecting previously unselected package rr62x-dkms.
(Reading database ... 76544 files and directories currently installed.)
Preparing to replace rr62x-dkms 1.1 (using rr62x-dkms_1.1_all.deb) ...
Error! There are no instances of module: rr62x
1.1 located in the DKMS tree.
dpkg: warning: subprocess old pre-removal script returned error exit status 3
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
Unpacking replacement rr62x-dkms ...
Setting up rr62x-dkms (1.1) ...
Error! rr62x-1.O is already added!
Aborting.


Unable to load DKMS tarball /usr/share/rr62x-dkms/rr62x-1.1.dkms.tar.gz.
Common causes include: 
 - You must be using DKMS 2.1.0.0 or later to support binaries only
   distribution specific archives.
 - Corrupt distribution specific archive


dpkg: error processing rr62x-dkms (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 rr62x-dkms
joker@GothamCity:~$

---

### Post by CharlesA on 2012-12-03
Well a mismatched SHA1SUM means it's corrupted.

I uploaded the deb to my site. You can download it via wget:

```
wget http://charlesa.net/files/rr62x-dkms_1.1_all.deb
```

Purge the failed one before you install that one.

[s]EDIT: Looks like wget isn't working, but you can download it from a browser.

Stupid cheap host.[/s]

I think I fixed it... The problem was I forgot I have my site hosted locally. X_x

---

### Post by cwn42 on 2012-12-03
Just to be sure, I purged the previous install with sudo apt-get purge rr62x-dkms.  When I go the the file tree in File Manager via Webmin it still shows the old deb file and tar.gz file.  Should I remove these from the system before I download the deb from your site?

---

### Post by CharlesA on 2012-12-03
Yeah, either remove them or move them to a different folder.

Also, verify the sha1sum of the file you downloaded to make sure it isn't corrupt as well, even though I verified it after uploading (ssh access to a web host = awesome ;))

---

### Post by cwn42 on 2012-12-03
On a quick side note while i install this, can you explain how wget works?  I understand that it downloads files from other servers but how do you use it?  I tried to use it to download files attached to links on websites but always got error 403.  Is there something to do to get wget to process the download or is it only usable if provided a specific https address?

---

### Post by cwn42 on 2012-12-03
looks like it matches when i run sha1sum.  my fingers are crossed

---

### Post by CharlesA on 2012-12-03
403 is permission denied. If you were trying to download the file from the ubuntu site, you had to enclose it in quotes because the wiki code uses the and sign and the shell thinks that is telling it to run another command.

I ended up being able to download it like this:

```
wget "https://help.ubuntu.com/community/RocketRaid?action=AttachFile&do=get&target=rr6xx-drivers-precise.tar.gz"

```

Renamed the archive after it was saved.

---

### Post by cwn42 on 2012-12-03
here is what i get (looks like it worked!! :-)

joker@GothamCity:~$ sudo wget [http://charlesa.net/files/rr62x-dkms_1.1_all.deb](http://charlesa.net/files/rr62x-dkms_1.1_all.deb)
--2012-12-02 21:49:21--  [http://charlesa.net/files/rr62x-dkms_1.1_all.deb](http://charlesa.net/files/rr62x-dkms_1.1_all.deb)
Resolving charlesa.net (charlesa.net)... 173.254.28.144
Connecting to charlesa.net (charlesa.net)|173.254.28.144|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 460790 (450K) [text/plain]
Saving to: `rr62x-dkms_1.1_all.deb'

100%[======================================>] 460,790      139K/s   in 3.2s    

2012-12-02 21:49:25 (139 KB/s) - `rr62x-dkms_1.1_all.deb' saved [460790/460790]

joker@GothamCity:~$ sha1sum rr62x-dkms_1.1_all.deb
73f715d81825ca6a9da688999ad9ef6fefa52271  rr62x-dkms_1.1_all.deb
joker@GothamCity:~$ sudo dpkg -i rr62x-dkms_1.1_all.deb
Selecting previously unselected package rr62x-dkms.
(Reading database ... 76544 files and directories currently installed.)
Preparing to replace rr62x-dkms 1.1 (using rr62x-dkms_1.1_all.deb) ...
Error! There are no instances of module: rr62x
1.1 located in the DKMS tree.
dpkg: warning: subprocess old pre-removal script returned error exit status 3
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
Unpacking replacement rr62x-dkms ...
Setting up rr62x-dkms (1.1) ...
Loading new rr62x-1.1 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-29-generic
Building for architecture x86_64
Building initial module for 3.2.0-29-generic
Done.

rr62x:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-29-generic/updates/dkms/

depmod.......

Backing up initrd.img-3.2.0-29-generic to /boot/initrd.img-3.2.0-29-generic.old-dkms
Making new initrd.img-3.2.0-29-generic
(If next boot fails, revert to initrd.img-3.2.0-29-generic.old-dkms image)
update-initramfs....

DKMS: install completed.
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
joker@GothamCity:~$

---

### Post by CharlesA on 2012-12-03
Looks good. If you do:

```
sudo fdisk -l
```

You should be able to see the drive array (if one is created).

If you want it to mount on boot, just add an entry to fstab and you should be good to go.

---

### Post by cwn42 on 2012-12-03
Thank you so much for the help.  I have everything plugged in an I had formatted the drives in the enclosure using the BIOS to one 2T JBOD and 6T RAID 5 array.  I ran fdisk and get this:

joker@GothamCity:~$ sudo fdisk -l
[sudo] password for joker: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   625142447   312571223+  ee  GPT

Disk /dev/mapper/GothamCity-root: 302.7 GB, 302744862720 bytes
255 heads, 63 sectors/track, 36806 cylinders, total 591298560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/GothamCity-root doesn't contain a valid partition table

Disk /dev/mapper/GothamCity-swap_1: 16.9 GB, 16852713472 bytes
255 heads, 63 sectors/track, 2048 cylinders, total 32915456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/GothamCity-swap_1 doesn't contain a valid partition table

I am not sure if I see it reading the NAS.  Is there something else I need to do?  I did a reboot already.

---

### Post by cwn42 on 2012-12-03
Also, I do not know what it means to add an entry to fstab? Thank you for the explanation of wget.

---

### Post by CharlesA on 2012-12-03
It should have loaded the module during install, but go ahead a reboot now and see if it sees it.

For more info on fstab see here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Here's what the entry I use in fstab looks like:

```
#RAID Array
UUID=05c730b5-680d-4d33-8e2e-76947d7a93fa       /array  ext4    noexec,nobootwait       0       0

```

I use nobootwait to prevent the machine from hanging in case the array isn't detected. That usually happens after a kernel update where DKMS fails to create the module correctly - something I have no been able to figure out.. removing then reinstalling the module back into dkms solves the problem. *shrugs*

---

### Post by cwn42 on 2012-12-03
Ok.  This is great.  I was pulling my teeth out trying to get the plug in installed.  This being my first time using linux doesn't help either.  

If you are able to help me a little more that would be great.  This also maybe for another thread, but I'll continue this one in case someone else has the same string of events as myself.

As I mentioned earlier I have already configured the disk drives in the enclosure using the RocketRaid BIOS at boot up creating a 6T RAID5 array and one 2T JBOD.  Ubuntu was installed on a 320G harddrive that was already in the computer and I just used the whole drive with LVM at install.  Would it be better to remove this configuration in the RocketRaid BIOS and create the array from the command line in Ubuntu (and if so I have no idea how to do that so some more education would be in order) or can I mount the current configuration that was created in the BIOS?  If I can use the current config here is the FDISK and BLKID:

joker@GothamCity:~$ sudo fdisk -l
[sudo] password for joker: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   625142447   312571223+  ee  GPT

Disk /dev/mapper/GothamCity-root: 302.7 GB, 302744862720 bytes
255 heads, 63 sectors/track, 36806 cylinders, total 591298560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/GothamCity-root doesn't contain a valid partition table

Disk /dev/mapper/GothamCity-swap_1: 16.9 GB, 16852713472 bytes
255 heads, 63 sectors/track, 2048 cylinders, total 32915456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

joker@GothamCity:~$ sudo blkid
/dev/sda1: UUID="C755-408C" TYPE="vfat" 
/dev/sda2: UUID="f32a9cb0-a817-4ccc-94fb-5350f1adf4f6" TYPE="ext2" 
/dev/sda3: UUID="ZUhcLQ-cHMX-tqz2-Plrk-xtD4-nAVO-5shj8j" TYPE="LVM2_member" 
/dev/mapper/GothamCity-root: UUID="fbff683a-857d-4dbb-a3c8-137ce193f892" TYPE="ext4" 
/dev/mapper/GothamCity-swap_1: UUID="7822ed5b-0cc7-4603-89b0-4e3446adafb8" TYPE="swap" 
joker@GothamCity:~$

I am not really sure what all this means exactly.  I know that it is showing me the different partitions I know have and I believe that the volumes sda1, sda2, sda3 are the volumes created at the install on the local harddrive.  Would the ext4 and swap volumes be the NAS arrays?  

I am hesitant to move forward until I know what i have to work with less I do something to screw up the volumes and partitions and risk having to reinstall the drivers again.

---

### Post by CharlesA on 2012-12-03
I created the array I have using the BIOS of the raid card, but I think you need to format those partitions - they should show up. What happens if you run this?

```
sudo modprobe rr62x
```

As Rubylaser pointed out in the other thread, you might need to do this:
```
echo "rr62x" | sudo tee -a /etc/initramfs-tools/modules
```

[http://ubuntuforums.org/showpost.php?p=11653794&postcount=2](http://ubuntuforums.org/showpost.php?p=11653794&postcount=2)

Then reboot again.

---

### Post by cwn42 on 2012-12-04
HI Charles.  i was at work yesterday.  I ran the command modprobe and rebooted and did not see changes when using fdisk or blkid.  I ran the echo command and rebooted.  After rebooting I did not see any changes with fdisk and blkid.  I then ran the modprobe  command and it looks like they show up.  I am going to post the fdisk results and blkid results in different boxes to keep them clear for anyone else who may read this and be confused too.

---

### Post by cwn42 on 2012-12-04
FDISK command:

joker@GothamCity:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   625142447   312571223+  ee  GPT

Disk /dev/mapper/GothamCity-root: 302.7 GB, 302744862720 bytes
255 heads, 63 sectors/track, 36806 cylinders, total 591298560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/GothamCity-root doesn't contain a valid partition table

Disk /dev/mapper/GothamCity-swap_1: 16.9 GB, 16852713472 bytes
255 heads, 63 sectors/track, 2048 cylinders, total 32915456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/GothamCity-swap_1 doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.3 GB, 2000313909248 bytes
255 heads, 63 sectors/track, 243190 cylinders, total 3906863104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 6001.0 GB, 6001008836608 bytes
255 heads, 63 sectors/track, 729581 cylinders, total 11720720384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

---

### Post by cwn42 on 2012-12-04
BLKID command:

joker@GothamCity:~$ sudo blkid
/dev/sda1: UUID="C755-408C" TYPE="vfat" 
/dev/sda2: UUID="f32a9cb0-a817-4ccc-94fb-5350f1adf4f6" TYPE="ext2" 
/dev/sda3: UUID="ZUhcLQ-cHMX-tqz2-Plrk-xtD4-nAVO-5shj8j" TYPE="LVM2_member" 
/dev/mapper/GothamCity-root: UUID="fbff683a-857d-4dbb-a3c8-137ce193f892" TYPE="ext4" 
/dev/mapper/GothamCity-swap_1: UUID="7822ed5b-0cc7-4603-89b0-4e3446adafb8" TYPE="swap"

---

### Post by cwn42 on 2012-12-04
Ok.  So I can see them with fdisk but I don't think they show up in blkid.  Is this because they are not mounted or because they are not formatted?  Can you tell me what "echo "rr62x" | sudo tee -a /etc/initramfs-tools/modules" command was for and what the modprobe command was for?  I think that it worked when I ran the echo command first and rebooted.  Then after the reboot ran the modprobe command.  Will I need to run the modprobe command after every reboot?  Thanks again.

---

### Post by cwn42 on 2012-12-04
Fix one problem and another pops up.  Now after I run the modprobe command the system crashes.  The command line shows rcu_sced detected stall on CPU 0 (t=168481 jiffies).  Then the computer does something called Call Trace:  and Stack:  I have no idea what any of this means.  Is there a problem with the hardware?  Do i need to reinstall the whole system again?

---

### Post by CharlesA on 2012-12-04
> **cwn42 said:**
> Ok.  So I can see them with fdisk but I don't think they show up in blkid.  Is this because they are not mounted or because they are not formatted?  Can you tell me what "echo "rr62x" | sudo tee -a /etc/initramfs-tools/modules" command was for and what the modprobe command was for?  I think that it worked when I ran the echo command first and rebooted.  Then after the reboot ran the modprobe command.  Will I need to run the modprobe command after every reboot?  Thanks again.

They probably don't show up because they do not have a valid file system yet.

modprobe is used to load modules, and I think adding that line to initramfa-tools tells it to load that modules on startup, but I am not sure.

Try a reboot but don't run modprobe and see what happens.

> **cwn42 said:**
> Fix one problem and another pops up.  Now after I run the modprobe command the system crashes.  The command line shows rcu_sced detected stall on CPU 0 (t=168481 jiffies).  Then the computer does something called Call Trace:  and Stack:  I have no idea what any of this means.  Is there a problem with the hardware?  Do i need to reinstall the whole system again?

Not sure, a trace usually means a kernel panic occurred, which shouldn't happen if you are just loading a module. Try rebooting and not using modprobe and see if you can see the array in fdisk.

---

### Post by cwn42 on 2012-12-04
For anyone else who happens to follow this thread here is an explanation on what rcu_sched detected stall means:
[http://www.kernel.org/doc/Documentation/RCU/stallwarn.txt](http://www.kernel.org/doc/Documentation/RCU/stallwarn.txt)

I am still not clear, however, on how the correct this problem.  In my case it seems related to the RAID Controller card again.  Would it be easier to simply get a different card?

---

### Post by cwn42 on 2012-12-04
I rebooted and ran fdisk but the drives do not show up.  They did show up after modprobe command if the system does not crash.  Any ideas?

---

### Post by CharlesA on 2012-12-04
> **cwn42 said:**
> I rebooted and ran fdisk but the drives do not show up.  They did show up after modprobe command if the system does not crash.  Any ideas?
Yeah, the system isn't loading the modules. What you could try is just running the install without any modifications. I tried it earlier and it compiled fine.

---

### Post by cwn42 on 2012-12-04
The last line on the screen after a crash was something about a panic

---

### Post by cwn42 on 2012-12-04
You mean re-installing the OS and then reinstalling the drivers?

---

### Post by CharlesA on 2012-12-04
> **cwn42 said:**
> The last line on the screen after a crash was something about a panic
Yep, likely a kernel panic then.

I will look at the source and see if it will compile via dkms.

> **cwn42 said:**
> You mean re-installing the OS and then reinstalling the drivers?

Nah, just reboot and see if it sees the array. It probably won't. :|

---

### Post by cwn42 on 2012-12-04
> **CharlesA said:**
> Yeah, the system isn't loading the modules. What you could try is just running the install without any modifications. I tried it earlier and it compiled fine.
and what do you mean without modifications?  Thanks.

---

### Post by cwn42 on 2012-12-04
> **CharlesA said:**
> Yep, likely a kernel panic then.

I will look at the source and see if it will compile via dkms.



Nah, just reboot and see if it sees the array. It probably won't. :|
Yeah I tried the reboot and it did not see the array.

---

### Post by CharlesA on 2012-12-04
> **cwn42 said:**
> and what do you mean without modifications?  Thanks.
I was able to just download the source from the highpoint tech site, unpack it and and run:

```
sudo make install
```

And it installed without errors. It does have a check in there for a 3.0 kernel, so maybe that allows it to compile on a 3.2 kernel.

I will have to check when I get home.

---

### Post by cwn42 on 2012-12-04
> **cwn42 said:**
> Yeah I tried the reboot and it did not see the array.
I haven't installed or done anything on the system yet that would be lost if a clean install would easier.  I am waiting to get this driver working before doing anything else so just let me know if you think it would be easier to start over again.

---

### Post by cwn42 on 2012-12-04
> **CharlesA said:**
> I was able to just download the source from the highpoint tech site, unpack it and and run:

```
sudo make install
```

And it installed without errors. It does have a check in there for a 3.0 kernel, so maybe that allows it to compile on a 3.2 kernel.

I will have to check when I get home.
Ok.  Thank you for your help and time.  I will stick with Linux as long as there are people out there like you to help.  Hopefully one day I'll be educated enough to pay it forward.  I will check back tonight when i get home from work.

---

### Post by CharlesA on 2012-12-04
> **cwn42 said:**
> I haven't installed or done anything on the system yet that would be lost if a clean install would easier.  I am waiting to get this driver working before doing anything else so just let me know if you think it would be easier to start over again.

I am not sure to be honest. I think the driver is working, but something is causing the kernel panic after it loads. I am not sure if this is because we used the deb to install it or what.

> **cwn42 said:**
> Ok.  Thank you for your help and time.  I will stick with Linux as long as there are people out there like you to help.  Hopefully one day I'll be educated enough to pay it forward.  I will check back tonight when i get home from work.

I will see if the open source driver compiles ok with dkms on the VM I was testing it on. Hopefully that will get the issue resolved. I am puzzled why the module isn't loading but it can't hurt to try it the hard way. :)

EDIT: This was suggested by Rubylaser. Try running:

```
modprobe --list | grep rr62x
```

After a reboot and see what it says.

---

### Post by cwn42 on 2012-12-04
> **CharlesA said:**
> I am not sure to be honest. I think the driver is working, but something is causing the kernel panic after it loads. I am not sure if this is because we used the deb to install it or what.



I will see if the open source driver compiles ok with dkms on the VM I was testing it on. Hopefully that will get the issue resolved. I am puzzled why the module isn't loading but it can't hurt to try it the hard way. :)

EDIT: This was suggested by Rubylaser. Try running:

```
modprobe --list | grep rr62x
```

After a reboot and see what it says.
okay.  i will try this tonight and post.

---

### Post by cwn42 on 2012-12-04
Here is what I got:

joker@GothamCity:~$ modprobe --list | grep rr62x
updates/dkms/rr62x.ko
joker@GothamCity:~$ 

I tried fdisk again to confirm it was not recognized and its not there.  

When you refer to the open source driver are you referring the instructions on [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid) which talk about editing the files in inc/linux and others?

---

### Post by cwn42 on 2012-12-04
also, i do not know if it means anything the rr62x in the command line "updates/dkms/rr62x.ko" is in red.

---

### Post by CharlesA on 2012-12-04
> **cwn42 said:**
> also, i do not know if it means anything the rr62x in the command line "updates/dkms/rr62x.ko" is in red.
That's fine. grep automatically highlights matches in red.

The file shows the same location for me.

I just reinstalled the file via dkms and it compiled with no problems.

You can try it yourself by downloading the tar.gz from [here]("http://charlesa.net/files/rr62x-v1.2.tar.gz").

After you download it, run these commands in whatever directory you downloaded it to.:

```
tar -xf rr62x-v1.2.tar.gz
cd rr62x-linux-src-v1.2
sudo cp -R . /usr/src/rr62x-1.2
sudo dkms add -m rr62x -v 1.2
sudo dkms build -m rr62x -v 1.2
sudo dkms install -m rr62x -v 1.2

```

That should do exactly the same thing the deb does and if that doesn't work, I would advise you to contact highpoint tech's support and see what they say.

---

### Post by cwn42 on 2012-12-04
ok.  I will try that.  Thank you.  Should I purge the old version first or will this install overwrite the old one?

---

### Post by cwn42 on 2012-12-05
I installed the tar.gz without purging the old version.  Not sure if that matters, but it seemed to work at first but then the system started acting weird.  I rebooted and it wouldn't recognize my password and the system looked like it kept running a disk check on the NAS in a continuous loop without stopping.  Then after I ran the fdisk command again it showed the drives but then had another kernel panic shortly after.  The kernel panic just happens now.  I am going to try and reinstall the OS and start from scratch with tar.gz file and see if maybe that will work.  I read in another thread by a user who had the same problem as me that the Highpoint tech was not much help but I will give that a try if this does not work.

---

### Post by cwn42 on 2012-12-05
One other thought.  Could this have anything to do with the server version I am installing and its compatibility with the processor?  The version I installed was from the main website and it was the 64bit "recommended" version.  I clicked on a link I found for other versions and I found that there is an AMD version and a intel i386 version.  The "recommended" version from Ubuntu's main page for downloads is the 64bit AMD version which is what I had running, but my processor is an Intel processor. Not an AMD processor.  Could this be the cause for the kernel panic and my headache?

---

### Post by CharlesA on 2012-12-05
> **cwn42 said:**
> I installed the tar.gz without purging the old version.  Not sure if that matters, but it seemed to work at first but then the system started acting weird.  I rebooted and it wouldn't recognize my password and the system looked like it kept running a disk check on the NAS in a continuous loop without stopping.  Then after I ran the fdisk command again it showed the drives but then had another kernel panic shortly after.  The kernel panic just happens now.  I am going to try and reinstall the OS and start from scratch with tar.gz file and see if maybe that will work.  I read in another thread by a user who had the same problem as me that the Highpoint tech was not much help but I will give that a try if this does not work.

Can you check dmesg, syslog, or get a picture of the kernel panic? I have a feeling that module is the cause of it, not the hardware itself.

> **cwn42 said:**
> One other thought.  Could this have anything to do with the server version I am installing and its compatibility with the processor?  The version I installed was from the main website and it was the 64bit "recommended" version.  I clicked on a link I found for other versions and I found that there is an AMD version and a intel i386 version.  The "recommended" version from Ubuntu's main page for downloads is the 64bit AMD version which is what I had running, but my processor is an Intel processor. Not an AMD processor.  Could this be the cause for the kernel panic and my headache?

AMD64 is just the name for 64-bit. Just like i386 is the intel name for 32-bit. 

It will run on either processor. I tested it 12.04 server x64, but in a VM because I do not have the card you have. I've been running a RR26xx.

---

### Post by cwn42 on 2012-12-06
I was away at work for a bit.  I  turned off the server for a day while I was away and turned the system back on last night.  Everything turned on and the drives showed up when I used fdisk.  I did not do anything different.  I left the server running until now with out doing anything to see if another panic would happen but it seems to be running ok.  The only concern i have now is the NAS enclosure shows that the single JBOD drive not being used (the light is not blinking) but the three drives in the RAID5 array are in constant use (nonstop blinking).  I've never set up a RAID array so I do not know if this is normal behavior.  I haven't mounted anything yet in the system which I will try next.  Should the RAID5 array be in constant use?

---

### Post by CharlesA on 2012-12-06
You might want to recreate the array and see how it goes, especially if there is one disk showing as a JBOD, which doesn't sound right.

---

### Post by cwn42 on 2012-12-06
I created it that way because I had four disks.  Three 3T disks and one 2T disk.  The 2T disk was salvaged from a My Book Live. Anyone reading this, don't buy the My Book Live.  The firmware sucks and it is fraught with problems. I wanted to salvage something but becuase the disk was 2T instead of 3T I kept it out the RAID array.  If there is a better way to set up the disks I open to suggestions as I am new to this.  Also what is the best file system to use if will be accessing the disks from both a Mac and WIndows?  I think ext3 from what I have read.  Is the samba share then created after the file system is made?

---

### Post by CharlesA on 2012-12-06
Considering all the problems you've had getting this thing up and running, it is kinda pointing to some sort of hardware problem, as the activity lights are definitely not normal.

I would just run the array with 3 x 3TB drives and take out that 2 TB drive and see if the activity lights are still going crazy. If they are normal, format the array and run with it, but be sure to keep good backups. :)

---

### Post by cwn42 on 2012-12-06
its weird.  the activity lights are still going nuts.  I took out the 2T drive and recreated the RAID5 array in the bios and rebooted,  Maybe if I am able to mount the array they will stop.

---

### Post by cwn42 on 2012-12-06
Okay.  I used sudo fdisk to create the partition on /dev/sdb where the array is located and I partitioned the whole drive (I think - I just used the default values) and I used mkfs.ext3 to format the array to ext3.  It looks like it worked so far.  The whole time the activity lights are still constantly on.

---

### Post by cwn42 on 2012-12-06
I edited the fstab file to auto mount the drive by adding the following line to the end:

/dev/sdb1         "mounted location"         ext3             defaults            0                0

I rebooted and ran fdisk and blkid and everything shows up.  I hope this worked, but it looks good so far.  CharlesA, thank you for your help!!   

The activity lights are still constantly going.  I'm still not sure this is normal but maybe it is a result of the RAID5 array and the disks working as one.  I will update if all of this is working and visible on the network.

---

### Post by cwn42 on 2012-12-06
> **cwn42 said:**
> I edited the fstab file to auto mount the drive by adding the following line to the end:

/dev/sdb1         "mounted location"         ext3             defaults            0                0

I rebooted and ran fdisk and blkid and everything shows up.  I hope this worked, but it looks good so far.  CharlesA, thank you for your help!!   

The activity lights are still constantly going.  I'm still not sure this is normal but maybe it is a result of the RAID5 array and the disks working as one.  I will update if all of this is working and visible on the network.
for anyone else reading the "mounted location" is not the type that should be entered into fstab.  I used the quotations because I did not want to show the name of the of folders.  The actual entry I used would be similar to /directoryfolder/folder.  Hopefully that makes sense.

---

### Post by CharlesA on 2012-12-07
I would really contact the tech support guys for that enclosure. That doesn't sound right at all. If anything the lights should be blinking in unison but only if there is activity on the drives.

When you used fdisk, were you able to make the file system on the entire array?

A better way to do it would be to use parted to create the partition as MBR partitions can only support up to 2TB partitions. Use GPT in order to create the 6TB partition.

Sidenote: Why not use ext4 instead of ext3 ? ext4 has some major advantages over ext3 including fscking being super quick compared to ext3.

---

### Post by cwn42 on 2012-12-07
The drives seem to be recognized okay but the constant disk activity makes me nervous.  I think it is a problem with fake raid controller that came with the Sans Digital enclosure.  I've been reading a lot of complaints and i think that it may be a POS.  Some say that RAID0, RAID1, and JBOD work okay with this card but RAID5 is hit or miss.  It seems that it is a miss most of the time.  Do you have any experience with RAID controllers?  Do I need one?  Is there any decent alternative to a RocketRaid card for $100 or less?

---

### Post by cwn42 on 2012-12-07
I got a samba file share working between my macbook and the RAID.  When I do a quick check on the shared volume it says that the size is only 2T instead of 6T.  Is that because of the ext3 file system type?  Also my transfer speeds between my computer and the drives is between 50MB/s and 60MB/s.  Shouldn't be quicker?  I have a wired CAT6 connection.

---

### Post by CharlesA on 2012-12-07
> **cwn42 said:**
> The drives seem to be recognized okay but the constant disk activity makes me nervous.  I think it is a problem with fake raid controller that came with the Sans Digital enclosure.  I've been reading a lot of complaints and i think that it may be a POS.  Some say that RAID0, RAID1, and JBOD work okay with this card but RAID5 is hit or miss.  It seems that it is a miss most of the time.  Do you have any experience with RAID controllers?  Do I need one?  Is there any decent alternative to a RocketRaid card for $100 or less?

If you can turn off the controller in the enclosure and just use the rocketraid one, you should be fine - but I do not know if that will work with the enclosure - if it acts as a port multiplier or what.

If you want to do an external array, you might be better off getting a different enclosure.


> **cwn42 said:**
> I got a samba file share working between my macbook and the RAID.  When I do a quick check on the shared volume it says that the size is only 2T instead of 6T.  Is that because of the ext3 file system type?  Also my transfer speeds between my computer and the drives is between 50MB/s and 60MB/s.  Shouldn't be quicker?  I have a wired CAT6 connection.

The 2TB thing is because you created a MBR partition and not a GPT partition. The Limit for MBR is 2TB.

Transfer speed depends on the size of the files and how they are being transferred. I've hit 100MB/sec + on my 3 disk RAID 5 array when transferring large files and a pathetic speed when transferring small files.

The way I have mine set up is I mounted the array inside the case with the OS drive, so I am not using an enclosure. The card I am using is [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816115053") but it is only a PCIex1 and a 3Gb/sec interface. I've had this one for a while now (27617 hours on one of the drives in the array as of Sunday, which is around 1150 days = 3.1 years) and I haven't had any problems with it. It steams video fine too.

---

### Post by cwn42 on 2012-12-07
Ok.  I don't remember electing to create an MBR partition.  Is this created by default or did I miss a step?  I can reformat the HDD if needed since nothing has been saved on them.  I believe that the enclosure acts as a port multiplier so I am assuming it needs to stay on.  The case with the OS in it is an old one without the space for the additional drives.  I really would like to be able to use the enclosure I got and I will give it another go.  I am going to try different arrays and see if i get the same problems as RAID5.  Its frustrating because newegg specifically says that this setup is built for RAID5 and should see 200MB/s with the controller card.

---

### Post by CharlesA on 2012-12-07
If you created the partition with fdisk, it creates a mbr partition as fdisk doesn't do GPT partitions - you need to use parted for that.

Best thing to do now is to either contact support for the enclosure or contact the vendor for the raid card and say you aren't getting the speeds you think you should be getting.

---

### Post by cwn42 on 2012-12-07
So what it comes down to is that this controller card is actually a piece of trash.  It does not handle anything other than JBOD.  It claims RAID 0, 1, 5, 10 and other than the configuration in the BIOS this thing is useless with Linux unless you want to run your disks as JBOD.

---

### Post by cwn42 on 2012-12-07
I am going to to contact Highpoint and see what they are willing to do and I will post what they say for anyone else who is having the same issue.

---

### Post by CharlesA on 2012-12-07
Good luck. Hopefully after replacing either the controller or enclosure, your setup will be running smoothly.

---

### Post by cwn42 on 2012-12-07
Thanks for all your help with this.  I guess at lease I got a good education on Linux and Ubuntu.  I think the solution will be to get another controller card and never buy or use anything RocketRaid again.  The enclosure should be fine.  I just need to find a decent controller and from what I have seen they are few and far between.

---

### Post by CharlesA on 2012-12-07
Adaptec are good, but they are pricy.

If you do decide to go with a different controller card, hopefully the activity lights behave.

---

### Post by cwn42 on 2012-12-07
I am just using a JBOD configuration for the time being and everything is working fine.  I will look into the adaptec controllers.  I appreciate the suggestion.

---

### Post by JunoKrahn on 2013-04-17
I admit that it is a cheap card, but I am using RocketRaid 622 configured for RAID 10, and it seems to be working well with good performance. The web-interface to configure the card is also working. However, I am not booting off of thr RAID drive, and I also had to patch the source for the latest kernel version.

Also, I had problems booting at first because the card sometimes conflicts with onboard raid controllers. I configured the BIOS to initialize external cards before onboard cards, and that issue was solved.

---

