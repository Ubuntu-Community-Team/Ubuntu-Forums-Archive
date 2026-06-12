---
title: "Root partition size?"
date: 2008-07-04
forum: General Help
---

### Post by Replicon on 2008-07-04
So, I was looking at my partitions today...

Filesystem            Size  Used Avail Use% Mounted on
**/dev/sda1             5.6G  5.1G  189M  97% /**
varrun                2.0G  128K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   52K  2.0G   1% /dev
devshm                2.0G   60K  2.0G   1% /dev/shm
lrm                   2.0G   43M  1.9G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3             171G   46G  117G  28% /home


It looks like my root patition has been growing a lot.

1) Is there something I can run to do a cleanup of stale/unused packages? I'm sure a large part of that has to do with it. Is that a safe operation?

2) If I don't manually resize it soon, and if an ubuntu update finally goes beyond the threshold, will it fail gracefully and offer to resize for me, or is that more of a "oh crap" state?

3) How easy is it to do that, and is it safe enough that I don't have to back up my data partition?

thanks

---

### Post by Elfy on 2008-07-04
```
sudo apt-get clean
```

will remove your downloaded packages - but I wouldn't expect it to be very big - probably <1Gb

run df -h again afterwards to check, it might be worth doing a resize while you can do it without any pressure :)

---

### Post by Replicon on 2008-07-04
Ok, looks like I'm up to 800MB free now hehe. What's the incantation for the resize? Is there anything special I need to do first?

---

### Post by hyper_ch on 2008-07-04
> **Replicon said:**
> Is there anything special I need to do first?

Backup your data first

---

### Post by Elfy on 2008-07-04
> What's the incantation for the resize?4 frogs, 1 weasel, 2 pints of frogspawn, 1 cauldron, a wart and a stick - mix well then drink.

If you are dualbooting with win - boot windows and make sure you have defragged a couple of times before you start.

Or alternatively - get your livecd and boot with it - after you have made sure that you have suitable backups ;)

Once you've booted with the livecd you can use the partition editor to do the resize for you. On Hardy it comes default with the livecd - it is in the System > Admin menu I think. I can't remember if it is there on Gutsy - if it's not available you can install it with

```
sudo apt-get install gparted
```

You will also need to turn swap off as it is likely it will be used by the livecd

```
sudo swapoff -a
```

Run the editor, it will show you your partitions as they are now - if you did the guided install in the first place then I would expect you to have your ext3 and swap inside an extended partition you have to resize this first before you can add space to your / - so if that is the case 

1 - shrink the ntfs partition (if you have vista you will be better of doing this from within from vista)

2 - resize extended partition to include the new unallocated space

3 - add the spce to your ext3 partition.

---

### Post by Replicon on 2008-07-04
Nope, just a good ol' single-boot laptop from System 76. So I guess I need to generate a boot CD of sorts so it doesn't mount any partition from my hd...

---

### Post by Elfy on 2008-07-04
IF you haven't got the buntu livecd get partedmagic and use that, you have to burn it as iso so that you can boot with it.

But you should be able to use the buntu livecd if you have it, just will need to turn off the swap.

---

