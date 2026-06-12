---
title: "Mount /home partition"
date: 2014-01-06
forum: General Help
---

### Post by gigenieks on 2014-01-06
Hello!

My /home partition was more than 500GB since I needed additional partition for Windows I started Live CD and shrinked some space using gParted. Restart. Install Windows 7. Then restart Live CD >> boot-repair utility. Voila have dual-boot.

But when I start my Xubuntu 13.04 I got this error:
> The disk drive for /home is not ready yet or not present.
Continue to wait, or Press S to skip mounting or M to manual recovery

Can anyone guide me how to fix this? And get full working Xubuntu again?

---

### Post by Bucky Ball on 2014-01-06
*Thread moved to **General Help**.*

Press 's' to skip and boot to Ubuntu. Please open a terminal and copy and post this file:

```
nano /etc/fstab
```

... and give the output of this command:

```
sudo blkid
```

---

### Post by gigenieks on 2014-01-06
If I press S and try login to my Ubuntu. Nothing happens. Never-ending cycle with me entering password and it returning me back.

Should I do some commands by pressing "M" ?

---

### Post by Elfy on 2014-01-06
Alternatively

Boot to recovery mode - then you can check that the drive exists in fstab

or

Boot the live usb/dvd then you can mount your install and do the same job there.

What you're looking to do is check that the /home partition is listed in fstab properly - hence the blkid.

---

### Post by gigenieks on 2014-01-06
Sorry, can u give some step-by-step? What command output u need guys to help me further? :/

---

### Post by Bucky Ball on 2014-01-06
As Elfy suggests, try the recovery kernel, should be second on the list when you boot. That should get you to a list of options, one of which is to drop to a shell. There you can run the commands I gave in my last post and post the output here. 

Let us know how you went. ;)

---

### Post by gigenieks on 2014-01-06
So I choose "M" for manual recovery.

**nano /etc/fstab**:
```

# / was on /dev/sda1 during installation
UUID=4c7173f5-ff2d-4d75-9dde-abdaf2bc5871 / ...
# /home was on /dev/sda6 during installation
UUID=469c94f6-b3d4-4723-9463-99e41fed0733 /home ...

```

then I tried **sudo blkid**:
it contained only sda1, sda3, sda4 and sda5.

sda1 had the same UUID as in /etc/fstab; sda3 & sda4 are ntfs (Windows partitons) sda5 is swap.
[COLOR="#800000"]**There is no sda6!**[/COLOR]

What now?

---

### Post by Elfy on 2014-01-06
Forget about the dev/sda references.

What is important are the UUID references. Does the UUID for the home partition

469c94f6-b3d4-4723-9463-99e41fed0733

match any of those you see in the blkid output?

If they don't - then you need to sort out which partition is the NEW /home following you working with gparted and change the FSTAB line to match with the correct UUID.

If you've managed to boot into Xubuntu run 

```
sudo fdisk -l 
```

Let's see what partitions you actually have.

Also run the blkid command so we can see that output too.

---

### Post by gigenieks on 2014-01-06
> **Elfy said:**
> Forget about the dev/sda references.

What is important are the UUID references. Does the UUID for the home partition

469c94f6-b3d4-4723-9463-99e41fed0733

match any of those you see in the blkid output?

No. 

> 
If they don't - then you need to sort out which partition is the NEW /home following you working with gparted and change the FSTAB line to match with the correct UUID.

Yeah, but how exactly?

> 
If you've managed to boot into Xubuntu run 

```
sudo fdisk -l 
```

Let's see what partitions you actually have.

Also run the blkid command so we can see that output too.
I can't boot in my Xubuntu. When I type my password (100% correct) it doesn't log in. Dunno why.

---

### Post by deadflowr on 2014-01-06
Run the commands using the Live CD.
maybe even snap a screenshot of what gparted looks like.

---

### Post by gigenieks on 2014-01-06
> **deadflowr said:**
> Run the commands using the Live CD.

I can, but which commands? 
[b]nano /etc/fstab 
sudo blkid[/b]
Anything else?

---

### Post by Bucky Ball on 2014-01-06
> **gigenieks said:**
> I can, but which commands? 
[b]nano /etc/fstab 
sudo blkid[/b]
Anything else?

Yes, those commands and no, not yet.

---

### Post by gigenieks on 2014-01-06
[IMG]http://i59.photobucket.com/albums/g295/gigenieks/Partitioning/Screenshotfrom2014-01-06103830_zpsaaff5e57.png~original[/IMG]

This explains why there is no sda6 ... :@#$

So, I have lost all my data which was on that /home partition which now is unallocated space?!

Well, it's strange I'm like 97% sure when I shrinked 90GB /home partiton was with filesystem and all was fine.
But after I did that shrinking I realized I had another 75GB unallocated space (before shrinking; I forgot that when I installed Xubuntu I specifically left some free space in case I later decide to get dual-boot), then I restarted and installed Win7 on that 75GB (not on space I just shrinked) and somehow after I installed Windows all my home partiton became unallocated huh???!! What guys happened?
Doesn't make sense.

---

### Post by coffeecat on 2014-01-06
> **gigenieks said:**
> I forgot that when I installed Xubuntu I specifically left some free space in case I later decide to get dual-boot), then I restarted and installed Win7 on that 75GB (not on space I just shrinked) and somehow after I installed Windows all my home partiton became unallocated huh???!! What guys happened?
Doesn't make sense.

What has probably happened is that the Windows installer deleted your first logical partition, which happened to be your home partition. The Windows installers are notorious for doing this - they get confused by logical partitions that are formatted with Linux filesystems and sometimes delete the first one that they find. I did some experiments with XP and Vista install disks a few years back. The results were - alarming!

All is hopefully not lost though. If the unallocated 594.20 GB is where your home partition used to be, then the ext4 filesystem is (hopefully) not overwritten and you will be able to restore the partition with testdisk. You can run testdisk from a live session of (X)ubuntu or any flavour of Ubuntu that you prefer.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You will need to boot up with a live CD/USB, make sure you are connected to the internet and install testdisk in the live session. Testdisk will be installed to volatile memory, so you will lose it when you shut down, but that will be long enough for you to recover the lost partition if it is recoverable.

**EDIT**: I just re-read your post and I see that you say that the home partition was originally 90GB and that you had left some free space, so perhaps that huge 594GB unallocated are is not your home partition, or perhaps it contains it. Whatever - it is worth running testdisk and seeing what that can find.

---

### Post by gigenieks on 2014-01-06
> **coffeecat said:**
> 
**EDIT**: I just re-read your post and I see that you say that the home partition was originally 90GB and that you had left some free space, so perhaps that huge 594GB unallocated are is not your home partition, or perhaps it contains it. Whatever - it is worth running testdisk and seeing what that can find.
No no, you misunderstood a lil, let me explain:
I had /home partiton which was bigger than 500 or almost 600GB dont remember, I shrinked it so I got 90GB unallocated space, I remember with absolute certainy that my /home partiton wasn't touched (no big unallocated space of 500GB). So it's very clear that something went wrong during Windows installation... (#$%$@ Windows :@) Does that clarify?

About that testdisk:
1) How do I install it? From terminal or what?
2) When I install what I do? Does it have self-explanatory gui interface? Or I need follow specific steps?

---

### Post by coffeecat on 2014-01-06
> **gigenieks said:**
> So it's very clear that something went wrong during Windows installation...

Yes, and I explained what might have gone wrong in my post.

> **gigenieks said:**
> About that testdisk:
1) How do I install it? From terminal or what?

Boot into the live session of any Ubuntu variant, make sure you are connected to the internet, and:

```
sudo apt-get update
sudo apt-get install testdisk
```

> **gigenieks said:**
> 2) When I install what I do? Does it have self-explanatory gui interface? Or I need follow specific steps?

Read the linked instructions in my post. It's not a GUI app. You can launch it from the terminal with:

```
sudo testdisk
```

---

