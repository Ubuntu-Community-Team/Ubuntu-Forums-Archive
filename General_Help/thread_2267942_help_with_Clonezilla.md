---
title: "help with Clonezilla"
date: 2015-03-05
forum: General Help
---

### Post by ken18 on 2015-03-05
For some reason, Clonezilla will not list the USB attached device I want to use as a destination for an image.  It will list all the partitions of the drive I want to image (/dev/sda1...sda9) but not the destination drive.  I  know the device is detected because when I exit Clonezilla to a command prompt I can see the device using lsscsi or cat /proc/partitions listed as /dev/sdd2.  I cannot see it using df command.

What could cause this and what should I do?  I wonder if Clonezilla is excluding the drive for some reason as a busy device...

P.S. I actually got it to list the device once (out of about a dozen attempts) by trying different USB ports on my laptop.  I can't seem to get consistent behavior though.  Goofy......

---

### Post by ken18 on 2015-03-10
Found a clue [here]("http://www.geekyprojects.com/ubuntu/how-to-format-a-usb-external-hard-drive-for-linux/") that pretty much explains the issue, but I now have a bigger problem.  For some reason, when I use Clonezilla to make a disk-disk clone, the LInux swap partition is completely ignored and the resulting clone has an unknown partition where the source had a swap partition.   I've tried it multiple times (including preparing the destination drive with a full format, which took hours) with the same result.  During the cloning process, I see messages like "/dev/sda5 is an unknown or unsupported partition....skip /dev/sda5 (no file system...)".  Attached pdf shows a GParted snapshot of the original and of the clone. The clone will boot Linux but complains about a UUID not being found (my guess, the swap partition).  I've tried with and without source checking, always the same result.  The source drive boots w/o any errors.

In case anyone is wondering, I don't attach both drives at the same time (except for the cloning process itself).  I physically attach the drive I want to boot to the internal HDD connector of the laptop (to avoid UUID conflicts).

What am I doing wrong?  Is this a known bug or limitation?  Fyi, I have the same problem using an image.

---

### Post by sudodus on 2015-03-10
I think Clonezilla ignores the swap partition's content, because it contains only temporary data. The partition is there in the cloned copy. What you need to do is make it a swap partition, and match its UUID with the swap entry in the file /etc/fstab.

If you use ***gparted*** to make it a swap partition, you must check its UUID with

```
sudo blkid -c /dev/null
```

and then paste that UUID into the swap entry in the file ***/etc/fstab*** (without quote characters).

If you use ***mkswap***, you check UUID of the swap entry in the file ***/etc/fstab*** and make the swap partition have that UUID

Example: In my /etc/fstab it is

```
# /dev/sda5 swap
UUID=03bed9e9-e39b-4107-8cd6-c2612af9a6aa none            swap    sw              0       0
```

so I would use

```
sudo mkswap -U 03bed9e9-e39b-4107-8cd6-c2612af9a6aa /dev/sda5
```

-o-

Beware, that if you have both the source drive and the target drive of the cloning process connected, and boot into one of them, things can get mixed up and damaged, because they have the same UUIDs. This is most critical for the root partition. It is no problem, if you have only one of the the drives connected.

---

### Post by ken18 on 2015-03-10
> [COLOR=#000000]Beware, that if you have both the source drive and the target drive of the cloning process connected, and boot into one of them, things can get mixed up and damaged, because they have the same UUIDs. This is most critical for the root partition. It is no problem, if you have only one of the the drives connected.[/COLOR]

Hmmm, even though I said I was careful to not have both the boot and clone connected at boot time, upon reflection I can't be certain given the 100+ times I've booted in the past few weeks.  Suppose I did have both connected when booting.  Are there specific things I can check and fix?  I'm wondering if that may be the real reason I'm having trouble using Clonezilla (I've read in the Clonezilla forum that swap partitions are suppose to be automatically created by the program).

Maybe the following is helpful (this is from my original):

```
$ sudo blkid -c /dev/null
/dev/sda1: LABEL="System" UUID="EEF809BBF8098357" TYPE="ntfs" 
/dev/sda2: UUID="880A-E13A" TYPE="vfat" 
/dev/sda3: UUID="C2120C64120C6031" TYPE="ntfs" 
/dev/sda4: LABEL="TI10671000C" UUID="D0181F27181F0BDA" TYPE="ntfs" 
/dev/sda5: UUID="7e95f0ed-2b23-454b-9153-aa9a48362688" TYPE="swap" 
/dev/sda6: UUID="fbb38a95-b2e1-4731-bb06-6c53e5fcb71b" TYPE="ext4" 
/dev/sda7: UUID="545C27605C273BDC" TYPE="ntfs" 
/dev/sda8: UUID="92A8A1DDA8A1C059" TYPE="ntfs" 
/dev/sda9: LABEL="Recovery" UUID="00DC254DDC253DF2" TYPE="ntfs" 

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=fbb38a95-b2e1-4731-bb06-6c53e5fcb71b /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=880A-E13A  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda8 during installation
UUID=7e95f0ed-2b23-454b-9153-aa9a48362688 none            swap    sw              0       0
UUID=880A-E13A    /boot/efi    vfat    defaults    0    1

```

And the same info for the clone:

```
$ sudo blkid -c /dev/null
/dev/sda1: LABEL="System" UUID="EEF809BBF8098357" TYPE="ntfs" 
/dev/sda2: UUID="880A-E13A" TYPE="vfat" 
/dev/sda3: UUID="C2120C64120C6031" TYPE="ntfs" 
/dev/sda4: LABEL="TI10671000C" UUID="D0181F27181F0BDA" TYPE="ntfs" 
/dev/sda5: UUID="888922fa-1d7f-4019-824d-15126b61495b" TYPE="swap" 
/dev/sda6: UUID="fbb38a95-b2e1-4731-bb06-6c53e5fcb71b" TYPE="ext4" 
/dev/sda7: UUID="545C27605C273BDC" TYPE="ntfs" 
/dev/sda8: UUID="92A8A1DDA8A1C059" TYPE="ntfs" 
/dev/sda9: LABEL="Recovery" UUID="00DC254DDC253DF2" TYPE="ntfs" 


$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=fbb38a95-b2e1-4731-bb06-6c53e5fcb71b /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=880A-E13A  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda8 during installation
UUID=7e95f0ed-2b23-454b-9153-aa9a48362688 none            swap    sw              0       0
UUID=880A-E13A    /boot/efi    vfat    defaults    0    1

```

---

### Post by sudodus on 2015-03-11
You can see that the UUID of the swap partition in the source matches that of /etc/fstab. But you must change the UUID of the swap partition in the target (the clone).

Use the mkswap method, that I described in post #3 (with ***your*** UUID string).

---

### Post by ken18 on 2015-03-13
Thanks.  Using [COLOR=#000000]mkswap seems to have solved the UUID error when booting the clone.  

Back to my earlier question, if I ever did boot with both attached at the same time, what would likely happen and how could I detect a problem and fix it?  I'm wondering if I now have a 'damaged' system.  If so, I'd like to take care of it now before I start using it on a regular basis.[/COLOR]

---

### Post by sudodus on 2015-03-13
I think the problem is that your don't really know where files are written, and things can get partially updated. I don't know a waterproof method to find everything that might be damaged. Try each of the systems separately and if the systems and important application programs work, things are probably OK.

-o-

A solution is to ***change the UUIDs*** in the clone for the system partitions (including swap), those in **/etc/fstab**, and of course also in that file (fstab), but also in the file **/boot/grub/grub.cfg**

It is a little bit of work, but you will avoid the problems when both drives are connected and you boot from one of them.

---

