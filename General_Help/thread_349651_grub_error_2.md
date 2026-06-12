---
title: "grub error 2"
date: 2007-01-30
forum: General Help
---

### Post by bradcarr on 2007-01-30
Been running Edgy for quiet some time now with no problems. I reboot today and I got error after grub started  "error 2". I searched the forums and google with no luck. I booted from an older drive with Dapper and put Edgy as my secondary and went in the disk manager and for my Edgy drive it said " file system unknown and  status inaccessable". Is there anyway to fix this or am I reinstalling. 


THANKS

---

### Post by dannyboy79 on 2007-01-30
run fsck on the drive. sudo fsck /dev/hd?, where ? equals the drive letter that fdisk -l tells you is the drive you want to check. if that doesn't work, you may have to check each partition seperately. that would be sudo fsck /dev/hd??, where the first ? is the drive letter and the second ? is the partition number. Example: sudo fsck /dev/hda2. good luck. oh, make sure you don't have any filesystem mounted that you run fsck on!!!

---

### Post by bradcarr on 2007-01-31
Big thanks Dannyboy-

I will try that as soon as I get home.

---

### Post by bradcarr on 2007-01-31
Ok I did a fdisk -l and it came up with this:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/hda2            6375       19266   103554990   83  Linux
/dev/hda3           19267       19444     1429785   83  Linux
/dev/hda4           19445       19457      104422+   5  Extended
/dev/hda5           19445       19457      104391   82  Linux swap / Solaris

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       24133   193848291   83  Linux
/dev/hdc2           24134       24321     1510110    5  Extended
/dev/hdc5           24134       24321     1510078+  82  Linux swap / Solaris

then I tried  sudo fsck /dev/hdc1  and I got :

fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
fsck.ext3: Filesystem revision too high while trying to open /dev/hdc1
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

then I tried  sudo  e2fsck -b 8193  /dev/hdc1  and got  the same thing.

So I guess it looks like I'm screwed ?

---

### Post by dannyboy79 on 2007-01-31
you made sure you didn't have this device mounted at the time you tried to run fsck correct?

here is a suggestion i found to work for someone with Debian Sarge Installed:

e2fsck -b 32769 /dev/hd??

Many inodes corrupted, but after the fix I could mount my filesystem :-)

---

### Post by bradcarr on 2007-01-31
yea I'm sure

When I go to  Places - Computer  and click on that drive it says:

Unable to mount the selected volume

Show more details

error: device /dev/hdc1 is not removable

error: could not execute pmount

I'm not sure if I have Debian Sarge (looked in the package manager and couldn't find it)

anyway I tried  e2fsck -b 32769 /dev/hdc1 and came up with the same thing as before.

---

### Post by dannyboy79 on 2007-01-31
ha, i think you misunderstood what I wrote. I was merely saying that a person that has Debian Sarge (a very similar os to Ubuntu, Ubuntu is based on Debian) had the same problem   and they solved it by typing in e2fsck -b 32769 /dev/hdc1. so if that doesn't work, not sure what to tell you. I have never seen that error about the filesystem revision being to high before??? sorry and good luck

---

### Post by bradcarr on 2007-02-01
Thanks for the help

---

### Post by dannyboy79 on 2007-02-01
why, you you fix your hard drive? it's able to boot now? are you able to mount it now?

---

### Post by bradcarr on 2007-02-01
still not able to boot or mount

---

### Post by dannyboy79 on 2007-02-01
OK good,
Looks like the tool used to create the ext3 partitions was newer then the one you are trying to fsck with. First step I'd say is to run fsck on the same system (distro) that it was created on. What did you use to make the partitions, was it with Knoppix or something else? You might have to find a newer copy of Knoppix

or

The filesystem is corrupt (ext3 has done that to me more then once) and you'll need to unmount the partition and run fsck.ext3 on it (fsck.ext3 is just a frontend to e2fsck but i prefer it)

Some options you might want to focus on when running that

Code:
 -c     This  option  causes  e2fsck  to run the badblocks(8) program to
              find any blocks which are bad on the filesystem, and then  marks
              them  as  bad  by  adding  them to the bad block inode.  If this
              option is specified twice, then the bad block scan will be  done
              using a non-destructive read-write test.

-f     Force checking even if the file system seems clean.

-p     Automatically repair ("preen") the file system without any questions.

-y     Assume an answer of `yes' to all questions; allows e2fsck to  be
              used non-interactively.Be careful with the -p and -y options, I have had to use these when the entire journal has gotten screwed up and there is an error on almost every file. I recommend running it manually at first but if there are too many errors (and you're feeling lucky) run the -p and -y options crossing your fingers. 

Worse case I've had with this is that the journal got hosed and every file ended up in lost+found, but was all files were still recoverable from there. Absolute worse case we need to start digging in with forensic tools 

or I wonder if you could install the latest version of fsck, it is 1.39.

---

### Post by bradcarr on 2007-02-02
OK 

When I installed I did the "auto install" where it sets up the partitions for me and 

I'm not quiet sure by what you mean to run fsck on the same system (distro) that it was 

created on. Are you saying to run fsck on one of the other partitions on that drive with the 

bad partition. 

Also, I never got the partition to mount 

So the first thing I guess is to run 

fsck.ext3 /dev/hdc1

question, the -c option 

when you say when is option is specified twice then it would look somthing like:

 fsck.ext3 -c -c  /dev/hdc1 ?

Thanks for all the help

---

### Post by dannyboy79 on 2007-02-02
> **bradcarr said:**
>  OK 

When I installed I did the "auto install" where it sets up the partitions for me and 

I'm not quiet sure by what you mean to run fsck on the same system (distro) that it was 

created on. Are you saying to run fsck on one of the other partitions on that drive with the 

bad partition.  
No, that's not at all what I am saying. That statement is saying that if you used a live cd like Knoppix to partition your hard disk ahead of time, than you should use Knoppix to run the fsck program. You state that you used Ubuntu to perform the partitioning scheme and the formatting so therefore you should be using ubuntu to check the parititons using fsck, GET IT? So that's obviously not your problem because you ARE using ubuntu to check your partitions with FSCK that were parititoned using Ubuntu originally.  The reason  for this is because 1 distro might be using mkfs verison x.x and fsck version 1.38 whereas another distro could be using mkfs version x.v and fsck version 1.39. (mkfs is the command that is used in the background when you you the installer to **m**a**k**e your **f**ile**s**ystems. ie: partitioning and formatting)

> **bradcarr said:**
> 

Also, I never got the partition to mount 

So the first thing I guess is to run 

fsck.ext3 /dev/hdc1

question, the -c option 

when you say when is option is specified twice then it would look somthing like:

 fsck.ext3 -c -c  /dev/hdc1 ?

Thanks for all the help 
this last statement doesn't make sense, you had to have it mounted if you stated that you have been using ubuntu for awhile now. can you explain this comment??? and yes, I just tried the double -c option and it works, what it does is "the bad block scan will be  done
              using a non-destructive read-write test." you can simply run a sudo fsck /dev/hdc1 and you'll be fine. I have ran it before and not lost any data. the -c option by itself would potentially be destructive but when you don't use any option it's not a destructive test. good luck

---

### Post by bradcarr on 2007-02-02
Ya, what I meant to say it has not mounted since I got the "error 2" error 

Anyway, I tried 

fsck.ext3 /dev/hdc1  

       and 

fsck.ext3 -c -c /dev/hdc1

 with not luck. I get the same thing that I got when I try to run the  e2fsck command.

---

### Post by dannyboy79 on 2007-02-05
i am out of options but I have found another possible solution within gogle, it's here: [http://unix.derkeiler.com/Mailing-Lists/SunManagers/2005-03/0353.html](http://unix.derkeiler.com/Mailing-Lists/SunManagers/2005-03/0353.html)

you really need to be searching gogle if you're not getting help in here. it's contains all the answers you could ever want!!!! all I did was look up  fix bad super block and found the above and after reading it briefly, it appeared like a valid solution. good luck!

if you're ready to give up, you could always try to use dd_rescue which makes an image of the filesystem, then you basically reimprt the image onto a newly created parititon. (i think!! you obviously need to research this before using dd_rescue but I have read before that it can obtain info from corrupts drives)

---

### Post by bradcarr on 2007-02-05
sounds awesome,

I am away from my computer right now but I will try it when I get home

Big thanks again DB

---

### Post by bradcarr on 2007-02-06
Looked at the link. Didn't understand the "newfs -N"  and the "fsck -F File_System -o b=32 

<Raw_Device>" commands. But I did try this command

fsck -y /dev/hdc 

didn't help 

going to look into dd rescue

thanks

---

