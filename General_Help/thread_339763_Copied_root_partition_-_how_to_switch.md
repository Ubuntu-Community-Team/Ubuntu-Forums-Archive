---
title: "Copied root partition - how to switch?"
date: 2007-01-16
forum: General Help
---

### Post by IamAcoconut on 2007-01-16
I've copied my "/" fs to another partition. What do I need to do to be able to boot from there? I'm gonna reinstall GRUB from a LiveCD, but that isn't enough, is it?

I need that done, because I want to have my new root encrypted, so, I want to switch to my copied system, encrypt the partition on which it was originally residing, and then move '/' contents back to that partiotion. Yeah, It could be done easier, but I'd have to lose everything on my 'data' partition, so... Is what I describe doable?

Thanks in advance! :)

---

### Post by IamAcoconut on 2007-01-16
Any1?

---

### Post by chrisccoulson on 2007-01-16
If /boot is on its own partition which hasn't moved, then it would just be a case of modifying your /etc/fstab to point to the new root filesystem, and modifying the the 'root=/dev/.....' kernel boot option in /boot/grub/menu.lst to also point to the new filesystem.

However, if /boot is not on its own partition, or it has moved as well, then you need to re-run the setup for grub so that it can find the data it needs to boot the system. To do this, type (from a command window):

```
sudo grub
```

You'll now be at the Grub prompt. Assuming you haven't moved the filesystem to a different physical disk, type:

```
root (hd0,x)
```

where x is the new partiton number of the filesystem containing /boot. Eg, if /boot is on /dev/hda3, then it should read.

```
root (hd0,2)
```

Then type

```
setup (hd0)
quit
```

You will also need to modify the 'root (hd0,x)' option in your /boot/grub/menu.lst to match what you put above.

Then you should be ready to go.

---

### Post by bodhi.zazen on 2007-01-16
First how did you copy the partition ?

Second you will need to edit both grub and fstab (from the live CD)

See here and let me know if you still have problems :

[http://www.ubuntuforums.org/showthread.php?&t=316237](http://www.ubuntuforums.org/showthread.php?&t=316237)

---

### Post by IamAcoconut on 2007-01-16
@**bodhi.zazen**,  I  used the copy option in Gparted. 
BTW, I''ll have to make a boot partition anyway, so... 
[LIST][*]Can't I just create new GRUB like they advise here [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub) ? If so, than I should delete (backup) actual boot contents (those on '/')?
[/LIST]

@**chrisccoulson**, [LIST]
[*]on which filesystem should I perform the operations you described?
[/LIST][LIST][*]Is that correct?> Eg, if /boot is on /dev/hda**3** root, it should read (hd0,**2**)
[/LIST]
[LIST]
[*]> You will also need to modify the 'root (hd0,x)' option in your /boot/grub/menu.lst to match what you put above.Like changing every (hd0,1) to (hd0,6) when moving from hda1 to hda6?
[/LIST]

And BTW, I'm running Dapper.

---

### Post by ~LoKe on 2007-01-16
It's hd(0,2) because the 0 countes.
1.2.3
0.1.2
hd(0,2)

---

### Post by bodhi.zazen on 2007-01-16
[QUOTE=IamAcoconut;2021582]@**bodhi.zazen**,  I  used the copy option in Gparted. 
BTW, I''ll have to make a boot partition anyway, so... 
[LIST][*]Can't I just create new GRUB like they advise here [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub) ? If so, than I should delete (backup) actual boot contents (those on '/')?
[/LIST]

OK, now we are getting complicated.

Can you list your partition scheme ?

If you move your root partition you will need to update /boot/grub/menu.lst and /etc/fstab.

You can update grub by re-installing it or manually.

What ~LoKe is saying is Linux and grub count partitions different.

Disk 1
Partition 1 = /dev/hda1 = root (hd0,0)
Partition 2 = /dev/hda2 = root (hd0,1)
...

Disk 2
Partition 1 = /dev/hda1 = root (hd1,0)
Partition 2 = /dev/hda2 = root (hd1,1)

See here fro information : [http://www.ubuntuforums.org/showthread.php?&t=282018](http://www.ubuntuforums.org/showthread.php?&t=282018)

If you add a /boot partition you should also update /etc/fstab

root = (hd0,x) where x = boot partition
kernel = /vmlinux-xyz root=/dev/hdy where y = ubuntu partition

In Ubuntu fstab:

/dev/hdz /boot  ..... where z = boot partition



As I said, it is becoming somewhat confusing.

Can you post your partition scheme ```
sudo fdisk -l
```

Identify the partitions and what you want to do.

This may help:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by IamAcoconut on 2007-01-16
```
sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            3522        4733     9735390   83  Linux
/dev/hda2               1        1670    13414243+   c  W95 FAT32 (LBA)
/dev/hda3            4734        4864     1052257+  82  Linux swap / Solaris
/dev/hda4            1671        3521    14868157+   5  Extended
/dev/hda5            1671        2266     4787338+  83  Linux
/dev/hda6            2267        3479     9743391   83  Linux
/dev/hda7            3509        3521      104391   83  Linux

Partition table entries are not in disk order
```[LIST][*]hda1 is my current system.
[*]hda2 is for data storage.
[*]hda5 - empty
[*]hda6 - copy of hda1
[*]hda7 holds a place for the new /boot
[/LIST]
I planned to:
[LIST=1]
[*]Copy hda1 to hda6
[*]Install GRUB on new /boot partition, pointing to system on hda6
[*]Format and encypt hda1 using cryptsetup-LUKS based on the system on hda6
[*]Copy hda6 to hda1
[*]Point GRUB to hda1
[*]Backup data from hda2 and delete it.
[*]Delete hda5 and hda6 creating one partition for data storage instead, using the space freed by hda2.
[*]Encrypt the new partition. (...)
[/LIST]

---

### Post by bodhi.zazen on 2007-01-16
OK boot to Ubuntu, HD or CD

Now lets install Grub in a few partitions:

```
sudo grub
```

At teh Grub prompt:

```
# /dev/hda1
root (hd0,0)
setup (hd0,0)

# /dev/hda6
root (hd0,5)
setup (hd0,5)

# /dev/hda7 AKA boot partition ....
root (hd0,6)
setup (hd0,6)
setup (hd0)
```


OK, now in /dev/hda7 (boot partition) edit /booot/grub/menu.lst:

> title Ubuntu 1 hda1
root (hd0,1)
chainloader +1
boot

title Ubuntu 2 hda6
root(hd0,5)
chainloader +1
boot


Now on /dev/hda1, edit /etc/fstab
/dev/hda1 / .....

And on /dev/hda6
/dev/hda6 / ......

**No need to mount the boot partition on either /dev/hda1 or /dev/hda6**

Each ubuntu partition, hda1 and hda6 will have a /boot which is referred to by the chainloader +1 in hda7

Each hda1 and hda6 will update grub as needed as you update the OS

On both hda1 and hda7 you can set the default to Ubuntu and the timeout to 0 (after you confirm it boots of course :p )

HTH

---

### Post by IamAcoconut on 2007-01-17
I'm currently runnng Dapper from a LiveCD...
```
grub> setup (hd0,6)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

There's no /boot/grub on my hda7, just ```

abi-2.6.15-23-386         lost+found                vmlinuz-2.6.15-23-386
config-2.6.15-23-386      memtest86+.bin
initrd.img-2.6.15-23-386  System.map-2.6.15-23-386
```I assume I skipped something obvious, that you didn't mention. How to install GRUB there?

---

### Post by floke on 2007-01-17
Not entirely sure if this will help, but I've just done a similar thing.
I followed the instructions listed here...

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Although, you seem to be in the middle of a different process so this might not be relevant.

i had a thread on this, where I got some useful advice (the above listed process didn;t work exactly according to plan) and noted my experience, here...

[http://ubuntuforums.org/showthread.php?t=338553](http://ubuntuforums.org/showthread.php?t=338553)

Good luck

---

### Post by bodhi.zazen on 2007-01-17
> **IamAcoconut said:**
> I'm currently runnng Dapper from a LiveCD...
```
grub> setup (hd0,6)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

There's no /boot/grub on my hda7, just ```

abi-2.6.15-23-386         lost+found                vmlinuz-2.6.15-23-386
config-2.6.15-23-386      memtest86+.bin
initrd.img-2.6.15-23-386  System.map-2.6.15-23-386
```I assume I skipped something obvious, that you didn't mention. How to install GRUB there?

Use another partition for root, either hda1 [ root (hd0,0) ] or hda6 [ root (hd0,5) ]

Then setup (hd0,6)

Then edit hda7/boot/grub/menu.lst (may be just hda7/grub/menu.lst) with chainloader ....

---

### Post by IamAcoconut on 2007-01-17
> Then edit hda7/boot/grub/menu.lst (may be just hda7/grub/menu.lst) with chainloader ....But how do I do that, when there are still only the files I listed on my hda7? Or should I follow this guide at [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub) in the very first order?

---

### Post by bodhi.zazen on 2007-01-17
```
sudo gurb

root (hd0,0)
setup (hd0,6)
quit
```

should install grub to /dev/hda7, same effect as your link, 6 of one, half-dozen of the other.

Either way you need to install grub to your boot partition ...

Then use your boot partition to set up your MBR ...

---

### Post by IamAcoconut on 2007-01-18
Copied /boot from my hda1 to hda7, and tried changing entries in menu.lst, but no avail. 
Bootloader displays countdown on, and on - 3,2,1 booting, 3,2,1 booting, 3,2,1 ... If I try to choose between the two entries from menu.lst I get this endless countdown again, no matter which system I choose to boot.

```
sudo grub

root (hd0,0)
setup (hd0,6)
quit
```This doesn't work. It changes  n o t h i n g  ](*,)  So, am I missing something  b a s i c ?
Instructions from the guide I linked don't work either. I don't get 'installation failed' message, but some error instead. And  n o t h i n g  changes ](*,) 

Please tell me what information I should provide to clarify the issue, so you could help me a bit more. :neutral:

---

### Post by bodhi.zazen on 2007-01-18
Well, I would say it has gotten more complex then it has to be.

Next steps:

1. Now what is in /dev/hda7 ? You should have /boot/grub/menu.lst

Find menu.lst on hda7 and edit the stanzas with chainloader ....

title Ubuntu hda1
root (hd0,0)
chainloader +1
boot

title Ubuntu hda6
root (hd0,5)
chainloader +1
boot

OK, now ....

Step two ...

sudo grub
root (hd0,6)
setup (hd0)
quit

Almost done ..

Step 3 

Check /etc/fstab on partitions hda1 and hda6

Make sure you have the correct root partition in fstab

/dev/hda1 / .... for hda1

/dev/hda6 / .... for hda6

Step 4 Reboot

---

### Post by IamAcoconut on 2007-01-18
1. hda7 contains exactly the following:
```
abi-2.6.15-23-386         lost+found                vmlinuz-2.6.15-23-386
config-2.6.15-23-386      memtest86+.bin
initrd.img-2.6.15-23-386  System.map-2.6.15-23-386
```
Now I copy /boot from hda1. So there's /grub and everything that should be there.
I edit menu.lst to contain exactly```
title Ubuntu hda1
root (hd0,0)
chainloader +1
boot

title Ubuntu hda6
root (hd0,5)
chainloader +1
boot
```

2. Now I type```
sudo grub
root (hd0,6)
setup (hd0)
quit
```

3. Fstab entries are:```

proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /boot           ext3    defaults        0       2
/dev/hda2       /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```And```
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /boot           ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

4. Rebooting right now to make sure. To be continued.

---

### Post by bodhi.zazen on 2007-01-18
Don't mount /hda7 in fstab as boot ...

Keep a /boot directory on hda1 and hda6 or chainloader will fail ....

---

### Post by IamAcoconut on 2007-01-18
Right. It failed. Should I delete the entry for /hda7 or just set mountpoint to 'none'?
I deleted it. Grub's the same on all 3 partitions. Rebooting, TBC...

---

### Post by bodhi.zazen on 2007-01-18
Comment it out :p

Just add a # at the front of the lines, like this:

> # /dev/hda7       /boot           ext3    defaults        0       2

---

### Post by IamAcoconut on 2007-01-18
It's the same as If I deleted it, right?

Here I am again. The result is following:```
Booting 'Ubuntu1 hda1'
root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
chainloader +1
boot
GRUB loading stage2...
Press 'ESC' to enter the menu... 2,1,0
(Press 'ESC' to enter the menu... 2,1,0)

```

---

### Post by bodhi.zazen on 2007-01-18
> **IamAcoconut said:**
> It's the same as If I deleted it, right?

No problem here :p

> Here I am again. The result is following:```
Booting 'Ubuntu1 hda1'
root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
chainloader +1
boot
GRUB loading stage2...
Press 'ESC' to enter the menu... 2,1,0
(Press 'ESC' to enter the menu... 2,1,0)

```

Ouch ...

It looks like grub is not setup on hda1 ...

Boot to the live Cd (I assume you are there :) )

Let's re-install grub to hda1:

sudo grub

root (hda1)
setup (hd0,0)
quit

Take a look at /dev/hda1:

sudo mount /dev/hda1 /mnt

Look at /mnt/boot/grub/menu.lst ... 

If it looks good, reboot

You may need to set up hda6 as well ;)

---

### Post by IamAcoconut on 2007-01-18
```
grub> root (hda1)

Error 23: Error while parsing number
```It should be (hd0,0), shouldn't it?
**Edit**: Whatever - I still get '23'

---

### Post by bodhi.zazen on 2007-01-18
OOO, sorry

root (hd0,0)

---

### Post by IamAcoconut on 2007-01-18
I already wrote, I still get
```
Error 23: Error while parsing number
```

---

### Post by bodhi.zazen on 2007-01-18
> **IamAcoconut said:**
> I already wrote, I still get
```
Error 23: Error while parsing number
```

What a flail, so sorry :)

quit grub

Restart:

sudo grub

what do you get when you enter:

find /boot/grub/stage1

---

### Post by IamAcoconut on 2007-01-18
```
grub> find /boot/grub/stage1
 (hd0,0)
 (hd0,5)
```

---

### Post by bodhi.zazen on 2007-01-18
Let me re-group for a post :p

What we need to do is:

Install grub into 3 partitions, hda1, hda6, and hda7

Once we are done we will set up your MBR using hda7 as your boot partition ....

but we will chainload to hda1 and hda6 ...

OK

It does not look like grub is in fact installed into hda7

So, from you grub prompt try again 

root (hd0,0)

Or 

root (hd0,5)

Then setup (hd0,6)

then

find /boot/grub/stage1

And

find /grub/stage1

---

### Post by IamAcoconut on 2007-01-18
```
grub> setup (hd0,6)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes[U]
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,6)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)[/U]
 Running "install /boot/grub/stage1 (hd0,6) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub> find /boot/grub/stage1
 (hd0,0)
 (hd0,5)

grub> find /grub/stage1
 (hd0,6)
```

---

### Post by bodhi.zazen on 2007-01-18
OK, now let us re-check hda7 ....

exit grub

mount hda7

check what is in /grub/menu.lst

(see chainloader as above) ...

Then set up your MBR again:

sudo grub

root (hd0,6)
setup (hd0)

Reboot and see if you can boot hda1 or hda6 ...

---

### Post by IamAcoconut on 2007-01-18
hda7/grub/menu.lst remained unchanged:
```
title Ubuntu hda1
root (hd0,0)
chainloader +1
boot

title Ubuntu hda6
root (hd0,5)
chainloader +1
boot
```
Should I reboot anyway?

---

### Post by bodhi.zazen on 2007-01-18
Lets look at a few more things ..

In the grub prompt,

What happens with:

root (hd0,0)

root (hd0,5)

root (hd0,6)

And on hda1 and hda6

what does /boot/grub/menu.lst look like ?

it should be

title Ubuntu
root (hd0,0)
kernel /boot/vmlinuz-x,y,z root=/dev/hda1 ro
initrd /boot/initrd.img-xyz
boot

etc ...

---

### Post by IamAcoconut on 2007-01-18
```
grub> root (0,0)
Error 11: Unrecognized device string

grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
```
Exactly the same with other numbers.

---

### Post by bodhi.zazen on 2007-01-18
If /boot/grub/menu.lst is OK on hda1 and hda6 ...

Reboot ...

Try to boot both hda1 and hda6

---

### Post by IamAcoconut on 2007-01-18
As in post #31.
Same on hda7
Rebooting!

---

### Post by bodhi.zazen on 2007-01-18
If on hda1 and hda6 your menu.lst has those chainloader lines, that is the problem :)

Awaiting re-boot

---

### Post by IamAcoconut on 2007-01-18
No luck, result very same as before.> **bodhi.zazen said:**
> If on hda1 and hda6 your menu.lst has those chainloader lines, that is the problem :)So what should menu.lst  look like? I mean, what should be the difference between hda7 and hda1 and 6?

---

### Post by bodhi.zazen on 2007-01-18
Oi

Now we are getting somewhere :)

It so happens I wrote them for you already :

On **hda1**, edit /boot/grub/menu.lst

> title Ubuntu hda1
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
boot


And on **hda6**, edit /boot/grub/menu.lst

> title Ubuntu hda6
root (hd0,5)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
boot

I trust you are quite proficient at mounting and editing from the Live Cd :p

Oh, almost forgot, reboot after edit ;)

---

### Post by IamAcoconut on 2007-01-18
Oh, yeah :D 
I'm now booted from hda6! No joke!
> I trust you are quite proficient at mounting and editing from the Live Cd No doubt I improved tonight :) 

What exactly does chainloader +1 do? Should it remain on hda7?
And where do we go now, to gain independence from '/boot' on hda1 and hda6?

BTW, I had the countdown displayed again after choosing the OS, is that normal? There was some information, had no time to read it though.

---

### Post by bodhi.zazen on 2007-01-18
That was a tough nut to crack :p

sorry for the flail there.

Short answer ...

Leave chainloader on hda7, your boot partition

What is chainloader does (short over view)

MBR -> Boots hda7 -> Chainloader then turns booting to hda1 (or hda6) -> boot directory on hda6 then boots ....

Why you ask ?

Well, at some point you will update your kernel. If you do not chainload, then you will have to edit /boot/grub/menu.lst on your boot partition.

This way, when say hda1 updates, it takes care of itself by maintaining it's own /boot

It gets messy if you do not chain load because you will accumulate multiple kernels on hda7 and you would need to manually keep track ...

If that makes sense ?

What you have done is set up a more complex partitioning/boot scheme that will be low maintenance.

I hope you can follow what I have done :p


In summary, when you move a partition you need to (manually) update grub (menu.lst) and fstab.

But you added a boot partition as well ...

hda7 should chainload hda1 adn hda6

hda1 and hda6 should keep track of kernels and booting in thier own /boot

The stanzas in menu.lst on hda1 and hda6 will look like:

ubuntu
root (hdx,y)
kernel /boot/vmlinux-xyz root=/dev/hdax ro quite splash
initd /boot.initd.img-xyz
boot

Keep hdx,y and root=/dev/hdx straight and in sync with fstab :p

xyz will be highest set of #'s (lower numbers = older kernel image)

You can remove old kernels via synaptic once you are sure the new one updates and boots ....



[color=blue]Again, I am sorry for the flail in getting you set up, but I hope you learned a little[/color] :p

If you have questions, look here:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

And feel free to PM me if you like ;)

---

