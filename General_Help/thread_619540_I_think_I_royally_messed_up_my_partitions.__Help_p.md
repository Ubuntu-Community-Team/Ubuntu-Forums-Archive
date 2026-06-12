---
title: "I think I royally messed up my partitions.  Help please?"
date: 2007-11-21
forum: General Help
---

### Post by curiousnoob on 2007-11-21
So last night I was using Gutsy and Bittorrent to download several very large (1.2 Gig) files.  I had my system set up to dual boot between Windows and Gutsy.  
I knew I did not have enough space on the Gutsy side so I chose to save it to the Windows partition, which I have done many times.  
I believe, however, that I was incorrect in the size available on the Windows side and filled the entire partition up.  When I attempted to start Windows it would not let me log in because it could not load a file.  
I put in the Gutsy start disc with the idea of simply adding some space to the Windows partition.  
I subtracted some space from the Gutsy side but it would not let me put the new stuff back onto the Windows partition.  
Now in Ubuntu I don't even have the Windows partition listed!  
Any ideas would be appreciated.  I have no idea what happened.

---

### Post by Nunu on 2007-11-21
I am not an expert in this but it sounds to me like you might have wiped the windows partition completely

---

### Post by tech9 on 2007-11-21
I would use winpe 2.0 boot CD to boot into a windows 32-bit environment, then delete the file you downloaded to free up space. It sounds like you have no room for file swapping.

---

### Post by tech9 on 2007-11-21
> **Nunu said:**
> I am not an expert in this but it sounds to me like you might have wiped the windows partition completely


I would agree; if you do not see the windows partition under LiveCD

---

### Post by Nunu on 2007-11-21
> **tech9 said:**
> I would agree; if you do not see the windows partition under LiveCD

Thats my thinking, maybe try running from the live CD and post the results before jumping the gun and saying that you lost that partition, it could very well just be Swap space.

---

### Post by curiousnoob on 2007-11-21
I actually DID see it under the live CD.  Now that I am in Ubuntu, though, it has disappeared.  It use be right there.  Is there any way to remount it if it still exists?

---

### Post by Nunu on 2007-11-21
As far as i know you can, but like i said i am no expert in this. It might be wise to see if someone post the the next step that you need to do. Rather be patient and get the right info on this then lose data

---

### Post by tech9 on 2007-11-21
> **curiousnoob said:**
> I actually DID see it under the live CD.  Now that I am in Ubuntu, though, it has disappeared.  It use be right there.  Is there any way to remount it if it still exists?

yes...

post output of

sudo fdisk -l

---

### Post by Nunu on 2007-11-21
hang on if memory serves me right which it usually don't, the reason the partition is lost under Ubuntu is because the partition tables have changed thus causing the OS not to except it because of the drive partition table. From what i can remember about something like this is you need to force a mount but this could be risky for that partition. but don't take my word on it let someone with more knowledge regarding the matter help you out.

Good luck and I really hope you succeed.

---

### Post by bingoUV on 2007-11-21
can you post the output of 
```

sudo /sbin/fdisk -l

```

Also try to tell us which partition in the above output is which(it helps in case there are more than one partitions of a given filesystem type).

---

### Post by curiousnoob on 2007-11-21
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8f6105d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         583       18819   146488702+   7  HPFS/NTFS
/dev/sda2           24180       24321     1140615   82  Linux swap / Solaris
/dev/sda3           21020       23671    21302190   83  Linux
/dev/sda4           18820       21019    17671500   83  Linux

Partition table entries are not in disk order

SDA1 is the Windows partition.  Currently in Ubuntu all I see is SDA3.

---

### Post by tech9 on 2007-11-21
> **curiousnoob said:**
> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8f6105d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         583       18819   146488702+   7  HPFS/NTFS
/dev/sda2           24180       24321     1140615   82  Linux swap / Solaris
/dev/sda3           21020       23671    21302190   83  Linux
/dev/sda4           18820       21019    17671500   83  Linux

Partition table entries are not in disk order

SDA1 is the Windows partition.  Currently in Ubuntu all I see is SDA3.

try...

sudo mount  /dev/sda1

it may ask for your password - but that should do it.

---

### Post by curiousnoob on 2007-11-21
When I use that command I get this message:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0

---

### Post by tech9 on 2007-11-21
> **curiousnoob said:**
> When I use that command I get this message:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0

you could try...

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

but before you do - (this is a long-shot - but may work)

shutdown your box...

physically unplug the windows HD,

then, boot up ubuntu...
next, shut-down properly
next, plug your windows HD back up
lastly, boot up ubuntu - it may even find the HD via PNP

otherwise force the option with inputting your device in your fstab file

---

### Post by curiousnoob on 2007-11-21
I get this message now:
mount: only root can do that

---

### Post by tech9 on 2007-11-21
> **curiousnoob said:**
> I get this message now:
mount: only root can do that

make sure you use...

**sudo **mount /dev/sda1

or type

sudo -i

then

mount /dev/sda1

or

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

---

### Post by curiousnoob on 2007-11-21
> **tech9 said:**
> make sure you use...

**sudo **mount /dev/sda1

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

I'm an idiot.  That solved that problem.  

Now that I have access to the Windows partition and assuming the original problem was filling up this partion, how do I delete files off of it?  
When I right click and choose "move to Trash" it just creates a .trash folder on partition and no memory is actually freed up.

---

### Post by wigglydiggly on 2007-11-21
You can enable Delete under Natulus by EDIT>Prefferences>Behaviors put a check next to Include a Delete command that bypasses trash

Good luck

---

### Post by tech9 on 2007-11-27
> **curiousnoob said:**
> I'm an idiot.  That solved that problem.  

Now that I have access to the Windows partition and assuming the original problem was filling up this partion, how do I delete files off of it?  
When I right click and choose "move to Trash" it just creates a .trash folder on partition and no memory is actually freed up.

Geez curiousnoob! I never implied that you were an idiot. I was only trying to help you out.... WOW! - I guess that's the kind of thanks I get?

---

### Post by curiousnoob on 2007-12-06
> **tech9 said:**
> Geez curiousnoob! I never implied that you were an idiot. I was only trying to help you out.... WOW! - I guess that's the kind of thanks I get?
I didn't mean to imply you were calling me an idiot.  I only meant that I ACTUALLY WAS an idiot for fogetting something as simple as putting "sudo" before a command.  
I always appreciate any help you guys give me, especially when it is simple stuff like that.

---

### Post by tech9 on 2007-12-18
> **curiousnoob said:**
> I didn't mean to imply you were calling me an idiot.  I only meant that I ACTUALLY WAS an idiot for fogetting something as simple as putting "sudo" before a command.  
I always appreciate any help you guys give me, especially when it is simple stuff like that.


I see... simple mistake; so go easy on yourself.
cool - I am glad you got it working :)

---

