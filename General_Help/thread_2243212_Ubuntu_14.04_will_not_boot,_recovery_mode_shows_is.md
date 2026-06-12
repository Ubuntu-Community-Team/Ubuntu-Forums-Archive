---
title: "Ubuntu 14.04 will not boot, recovery mode shows issues with HDD"
date: 2014-09-07
forum: General Help
---

### Post by PartisanEntity on 2014-09-07
To give you some background:

Hardware: mid 2010 iMac.
OS: Ubuntu 14.04 (no other OS on the HDD, I do have an external HDD with OSX on it).
Booting using refind.

Computer worked fine up until last night. Have never seen any warning of a failing HDD.

Tried to boot the computer today, remained on the grey screen that is displayed before refind usually shows you the available operating systems to choose from.

Only after hitting ENTER on the keyboard, does a black screen with a yellow error message get displayed on the screen for about 0.1 seconds (too short to read. the only word I can make out is "error"). I am then presented with the various kernels to boot from.

I choose the latest one, 3.13.35 and try to boot from that.

Black screen and nothing happens.

Then I tried to boot in recover mode, and the verbose output that is shown can be seen in the photo I took:

[ATTACH=CONFIG]256229[/ATTACH]

Any tips on what I can try?

(I cannot take the HDD out of the machine at the moment as I need to go but the tools, such as suction cups to remove the glass of the screen, as far as I read).

Thanks.

---

### Post by cariboo on 2014-09-08
It looks like /dev/sda has a problem. If you can boot from a live image, once you get to the desktop, open a terminal and run:

```
sudo fsck /dev/sda
```

To see if that clears up the errors.

---

### Post by PartisanEntity on 2014-09-08
Thanks very much for the suggestion cariboo907. I am going to give that a try.

I tried last night to boot from a Live USB, but that did not work and for reason it sent me to a grub terminal prompt.

I then tried a Live DVD and was only able to boot from the legacy mode and not from the EFI modes.

Will report back on my results.

*On a side note, I had a look at the instructions in order to open up a 27" iMac, what a pain... *

---

### Post by PartisanEntity on 2014-09-08
Hi again,

So the command did not work as stated. I kept getting the error that the disk was in use. After some research it turns out you cannot apply fsck to the entire disk, you have to apply it to a partition.

In my case the main partition was sda2, so the following worked:

```
sudo fsck /dev/sda2
```

However I then got this error message:

> /dev/sda2 contains a file system with errors, check forced
Pass 1: Checking inodes, blocks, and sizes
Error reading block 110100512 (Attempt to read block from filesystem results in short read) while getting next inode from scan. Ignore error<y>?

If I type "yes". I then get this message:

> Force rewrite<y>?

If I type "yes" again then the above error reapears with simply a new block number and this keeps on going through many block numbers.

After some more searching the following command will force the "yes" each time, so you don't have to type it:

```
sudo fsck -y /dev/sda2
```

Now those same errors are appearing again, but the yes is being entered automatically and it is checking the next block. Not sure how long this is going to take.

---

### Post by PartisanEntity on 2014-09-08
Process is over now. It seems many blocks were over-written.

At least I am able to access the drive through the Live CD and am now copying my home folder to an external HDD. Looking good so far.

---

### Post by PartisanEntity on 2014-09-09
So final update, thanks for your help cariboo907 in guiding me in the right direction.

Thank God I was able to make a backup of my home folder. I then ran the short SMART status scan and the hard disk failed it, so it is definitely going down.

I will be marking this thread solved as I achieved the following:

- understood the initial error message
- fsck did help make the drive usable enough to make a backup
- data has been backed up
- drive is definitely failing

---

