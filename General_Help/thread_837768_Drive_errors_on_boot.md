---
title: "Drive errors on boot"
date: 2008-06-22
forum: General Help
---

### Post by ad_267 on 2008-06-22
I've got Ubuntu 8.04 running well on my computer and just installed it on my family computer which wasn't running well on windows XP, probably due to accumulation of junk. It installed fine and everything seems to work except for one problem. When I boot into Ubuntu it closes from the splash screen and shows a whole lot of errors about the drive then eventually continues booting into Ubuntu. I tried to copy them down and they look something like this:

```
ata1.00: status { DRDYERR }
ata1.00: error {UNC }
ata1.00: exception check 0x0 SAct -x- SErr 0x0 alter 0x0
ata1.00: BBDA

```

Then a whole lot of lines beginning with:
```
Buffer I/O error on device SDA1 
```

I'm not sure what to make of this. Also some of that may be wrong as I was copying in a hurry and my handwriting is pretty bad. Hope someone can help me out.

Cheers,
Adam

---

### Post by spiderbatdad on 2008-06-22
If I understand, the system eventually boots to a desktop?

Can you post the contents of dmesg from that computer?
Run this in terminal:```
dmesg > ~/Desktop/dmesg.txt
```this will write a file on you desktop. Right click that file and "create an archive." Upload that archive here with the manage attachment tool below.

---

### Post by ad_267 on 2008-06-22
Thanks, yeah it eventually loads fine. After another boot I saw something about "There are differences" and then it went away too fast with a whole lot of numbers and something about "Not automatically fixing this"

I've attached the output of dmesg.

---

### Post by PmDematagoda on 2008-06-22
It looks like your hard drive is going to fail, or it has a hell of a lot of bad sectors. In my case when that happened, the PC still did work but it decreased the responsiveness of the system rather drastically and in one case it seemed that the hard drive came very close to a complete failure.

In my opinion, you are better off getting a new hard drive.

---

### Post by ad_267 on 2008-06-23
Hmm ok thanks for that. It does seem a lot less responsive than it should. I thought it was just junk in Windows slowing it down before and Ubuntu would be lightning fast in comparison but it isn't really.

Can I run fsck or something to confirm this?

---

### Post by PmDematagoda on 2008-06-23
> **ad_267 said:**
> Hmm ok thanks for that. It does seem a lot less responsive than it should. I thought it was just junk in Windows slowing it down before and Ubuntu would be lightning fast in comparison but it isn't really.

Can I run fsck or something to confirm this?

I ran fsck myself, in particular you have to check for bad sectors, but this really did not make much of an improvement. In anycase the fsck you would want is:-
```
sudo e2fsck -c /dev/location-of-drive
```
but be warned, if it is the root partition/drive, then you would need to check the root through a Live CD and not while the normal Ubuntu install is running.

---

### Post by ad_267 on 2008-06-23
This is the output from e2fsck. I'm not quite sure what to make of it.

```

ubuntu@ubuntu:~$ sudo e2fsck -c /dev/sda2
e2fsck 1.40.8 (13-Mar-2008)
Checking for bad blocks (read-only test): done                                
/dev/sda2: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda2: 135029/463296 files (0.6% non-contiguous), 813155/1851483 blocks

```

Edit: Still getting the same errors on boot. I noticed the "Buffer I/O" error is on sda1, a Windows Fat32 partition. I ran chkdsk on this today after getting that error but I wasn't there when that finished so didn't see the output.

---

