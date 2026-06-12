---
title: "Cloned HD - Now how to use GParted - HELP!"
date: 2007-11-15
forum: General Help
---

### Post by mikey12345 on 2007-11-15
I had Ubuntu 7.10 installed with a 40 gig drive. I did a standard install and put some programs on top etc.

I recently bought a 400 gig HD to replace it so i could store more on it.

I used Ghost For Linux (G4L) to clone from the 40gig HD to my new 400gig HD.

It has sucessfully cloned and i'm using that HD now.

However my system shows it as being a 40gig drive still. What do i need to do? I assume i just need to use Gparted and extend it?


Here is the output from df -h:
mikey@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  2.8G   32G   9% /
varrun                379M   96K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
udev                  379M   52K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
tmpfs                 379M   34M  345M   9% /lib/modules/2.6.22-14-generic/volatile


So /dev/sda1 should be saying something like 400gig i guess? 

What do i need to do now to make it so it is 400 gig?

Also what are all the other partitions? Do i need to worry about them?

Look forward to the replies. Thanks.

---

### Post by mikey12345 on 2007-11-15
This is also the output from fdisk:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x664924c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4773    38339091   83  Linux
/dev/sda2            4774        4866      747022+   5  Extended
/dev/sda5            4774        4866      746991   82  Linux swap / Solaris

---

### Post by oneadvent on 2007-11-15
Yes, it is pretty intuitive on how to increase size of partions. 

Do it on the LiveCD.and resize from the end to the begining. It makes it easier to see what you are doing. Be prepared for a wait though, it takes a long time to move that many GBs.

---

### Post by kaiju on 2007-11-15
have you tried looking in gparted whether it shows all the available space or not?
i mean theoretically you should have the partitions shown by fdisk and a big fat empty space.
and if that's so, you'd only need to partition that space and add its entries into fstab.

---

### Post by mikey12345 on 2007-11-15
I've got Gparted open now.

It shows:
/dev/hda1 as 36.5 gig (used 2.6gig). - ext3
/dev/hda2 - 729.51meg - extended
/dev/hda5 - 729.48 - linux-swap
unallocated - 225.33gig - unallocated.


So what do i need to do here, what do i need to increase and how?

Thanks.

---

### Post by maybeway36 on 2007-11-15
move the extended partiton all the way to the right, and resize the ext3 partition to fill the gap. hopefully it will work.

---

### Post by mikey12345 on 2007-11-15
Not sure what you mean?

I've attached a picture of the screen to show what it displays. I'm unsure what to do.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=50286&stc=1&d=1195149094[/IMG]

Thanks.

(If someone could also explain the reasons why i need to do it etc that would be great so i can understand it also).

---

### Post by mikey12345 on 2007-11-15
Sorry to Bump back up. Just don't want to rush ahead and mess it up.
Thanks.

---

### Post by ViRMiN on 2007-11-15
You'll need to move your extended partition over to the right and then you'll be able to expand your first partition.

---

### Post by kaiju on 2007-11-15
you might also want to take a look at your /etc/fstab and /boot/grub/menu.lst files.
in case they contain enties like UUID=0a1c0c75-c9ad-435e-bae9-abfb8defd471, you might not be able to boot you system after changing partition sizes.

in this case you need to remove the uuid=whateverandwhatnot parts so that they will contain the corresponding /dev/... entry.
that means that in /etc/fstab for ex:
```

# /dev/sda1
UUID=0a1c0c75-c9ad-435e-bae9-abfb8defd471   /   ext3   defaults,errors=remount-ro   0    1

```
becomes
```

/dev/sda1   /   ext3   defaults,errors=remount-ro   0   1

```
and in /boot/grub/menu.lst,
```

kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=12e6200b-7b04-4a0b-9c80-da775c5b9f31 ro quiet splash

```
becomes
```

kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro quiet splash

```
(assuming, that /dev/sda1 is the partition of your linux install)

just wanted to let you know about these as i had this problem not long ago, so you don't need to freak out in case you can't boot later. you should only make these changes if you can't boot.
and please let us know how things work out.

peace :)

---

### Post by mikey12345 on 2007-11-15
> **ViRMiN said:**
> You'll need to move your extended partition over to the right and then you'll be able to expand your first partition.

Hi,

I did this, right to the end of the unallocated space. Applied and rebooted etc and no different.
Loaded up Gparted again and it didn't show any different other than showing the extended part was bigger but was wrapped around an unallocatd grey part.

I then decided to undo all that and start again.

So i clicked on the unallocated grey area and did new partition. Rebooted etc and then tried to grow the /hd1 into it but i just can't grow the hd1 part.

Therefore my system still shows the filesystem as being 40gig.

I'm lost:( ?

---

### Post by kaiju on 2007-11-15
did you try to grow sda1 while the grey, unallocated area was next to it?

---

### Post by kaiju on 2007-11-15
if your extended partition that contains the swap partition is at the right end, and the unallocated space is next to the ext3 partition, you should be able to right click on it and expand it to comprise all of the free space.

---

### Post by mikey12345 on 2007-11-15
> **kaiju said:**
> if your extended partition that contains the swap partition is at the right end, and the unallocated space is next to the ext3 partition, you should be able to right click on it and expand it to comprise all of the free space.

I think that's the bit i want but don't understand how to get it.

My /dev/dha1 is on the left showing 40gig.
Next to that is my /dev/hda2 which is extended and contains swap.
Next to that is the unallocated section (400 gig ish).

I don't know how to get the unallocated section next to the /hda1 so i can grow the hda1 in to the unallocated section.

Does that make sense?

---

### Post by kaiju on 2007-11-15
if you select /dev/hda2 in gparted and tell it to move it, then just try to pull it to the right, does that work?

---

### Post by mikey12345 on 2007-11-15
> **kaiju said:**
> if you select /dev/hda2 in gparted and tell it to move it, then just try to pull it to the right, does that work?

I can select it.  I can resize. I can't 'move' it though?

It says 'move or resize' as the option but no idea how to move it?

---

### Post by kaiju on 2007-11-15
you should be able to just drag the red tile to the right
you select hda2, press resize/move, get a smaller window with a red tile in it and you drag that to the right side of the grey portion it's in. then you should get "free space following (MiB): =0"

---

### Post by kaiju on 2007-11-15
no wait. it will be blue, because you're selecting the whole extended partition :P

---

### Post by mikey12345 on 2007-11-15
> **kaiju said:**
> you should be able to just drag the red tile to the right
you select hda2, press resize/move, get a smaller window with a red tile in it and you drag that to the right side of the grey portion it's in. then you should get "free space following (MiB): =0"

Right.
My /dev/dha1 is on the left showing 40gig.
Next to that is my /dev/hda2 which is extended and contains swap shows about 2 gig.
Next to that is the unallocated section (400 gig ish).


If my last section is unallocated, i can move the extended partition right in to it. However it still remains unallocated and i still can't resize my dev/hda1.

If my last section is allocated as ext3 (is this correct) i can't move my extended partition in to it at all.

I just don't get it.
?

---

### Post by kaiju on 2007-11-15
1.
you select the etxtended partition and move it to the right.

then you have, from the left to the right: linux partition, unallocated space, swap partition.

2.
you select the linux partition and make it grow until there is no more unallocated space left next to it.

this should leave you with a big linux partition on the left and the swap partition to the right

3.
apply changes :)

pls. let me know what doesn't work

---

### Post by kaiju on 2007-11-15
p.s.

you can only resize partitions or move them around if there is unallocated space next to them.

---

### Post by mikey12345 on 2007-11-15
> **kaiju said:**
> 1.
you select the etxtended partition and move it to the right.

then you have, from the left to the right: linux partition, unallocated space, swap partition.

2.
you select the linux partition and make it grow until there is no more unallocated space left next to it.

this should leave you with a big linux partition on the left and the swap partition to the right

3.
apply changes :)

pls. let me know what doesn't work

Think you've just cracked it!? Got to apply the changes and see how it goes but looks promising.

It was my error. I'd done step 1 by moving the extended partition all the way to the right. What i didn't then do was move the swap partition with it! Seems obvious now.

But when i did that, i was able to do your step 2 and 3, which let me grow /dev/sda1 for the first time.

So looks like it will work!


What should i set my extended partion as afterwards and what should my swap be? What do they both do.

My drive is 400 gig so i can afford to dedicate some to them if needs be.
I've got 2gig for both at the moment.


THANKS!

---

### Post by kaiju on 2007-11-15
wait a second...

i thought your swap partition was inside of the extended one.

extended partitions exist because you can normally only have four partitions on a disk. that means that if you need to use five partitions, two of them them will have to be placed inside an extended one.

looking at your partitions, you will notice that swap is on hda5. that's because whatever is placed inside an extended partition, gets a number starting from 5 (1-4 for primary and extended partitions and up from 5 for partitions inside an extended one)
that said, you don't need to fave an extended partition if you have less than four partitions. if you want to, you can just convert it to a primary one.

swap woks sort of like ram on your harddisk. if you want to prepare a swap partition, you have to format it as swap. regarding the size, you should google around to see how much of it should fit your system.

---

### Post by kaiju on 2007-11-15
oh, and do not forget to edit /boot/grub/menu.lst and /etc/fstab to point to your new partitions.
if you're using the gparted livecd, you have to first mount your linux partition, like
```

mkdir /mnt/disk
mount /dev/sda1 /mnt/disk

```
(that sda1 might be called hda1)

and then you edit /mnt/disk/boot/grub/menu.lst and /mnt/disk/etc/fstab with whatever editor you have at hand.

---

### Post by mikey12345 on 2007-11-15
Just to clarify my swap was inside my extended partition.

Thanks for the explanation  -it makes sense. 

I've set my swap as 2gig and the extended which wraps around it to be 2gig.


My sda1 is now something like the remaining 370gig.

Just restarted and booted up and all is working fine:) I've not needed to edit anything else or mount anything.


Thanks for you help - it has been greatly appreciated.

---

### Post by kaiju on 2007-11-15
hm... interesting :)
and you're welcome.

peace

---

