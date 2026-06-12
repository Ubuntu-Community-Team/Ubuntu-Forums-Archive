---
title: "Delete Partition Problem"
date: 2012-10-29
forum: General Help
---

### Post by NM5TF on 2012-10-29
I am trying to delete a partition that I had Ubuntu 10.04
installed in...the partition is /dev/sda6 on the attached
screenshot....

I did something REALLY stoopid & resized it down to ~ 20GB
to get some extra space on my HDD....now it won't boot at all,
and worse yet ***it will not even boot from a live CD***:mad:

thank GAWD for the boot repair CD I made earlier....but it still
won't boot from the live CD....it goes to a black GRUB2 screen
with a keyboard & the "little man" image...I tried the trick
of any key + F6, but nothing happens....at least I can still
boot into my 12.04 OS....:P

when I try to delete /dev/sda6 it gives  an error message 
stating that I need unmount all logical partitions > 6....

I can't do that as my 12.04 OS is installed on /dev/sda8 & 
it will not let me unmount it....:(

anyway to delete /dev/sda6 so I can reclaim that 20GB???

anyone???

TIA....Tommy

screenshot below

---

### Post by Bashing-om on 2012-10-29
Getting a live cd to boot is the first priority.
Be advised can not manipulate a partition that is mounted, thus the live cd is required.

With the problems you advise, I suggest that you down load the .iso image again and burn another disk.

Then from the live cd, delete the partition you want gone. Expand into the created free space the partition you intend to use for the current system.(must be adjacent)

from the live cd, choose "boot from first hard disk" -> log in -> open a terminal->
terminal code:
```
 sudo grub-install /dev/sda
``` Assuming sda is the drive you want to boot ubuntu.
and to write the config files
```
sudo update-grub
```[INDENT]all should be good now <== BDQ
[/INDENT]

---

### Post by NM5TF on 2012-10-29
> **Bashing-om said:**
> Getting a live cd to boot is the first priority.
Be advised can not manipulate a partition that is mounted, thus the live cd is required.

Yes, I realilze this....that is why I tried using the live Cd, but as
I explained above....***it will NOT boot from a live CD***....:(

> With the problems you advise, I suggest that you down load the .iso image again and burn another disk.

the live CD I tried to use was the same CD I used to install my
working 12.04 OS....why do you think it's bad???:confused:

rest deleted as I know how to do this....

my ***BIGGEST*** problem is that it WILL NOT BOOT from a live CD...:mad:

if I can get that working then the rest is easy...:guitar:

thanx for the reply tho.....:)

Tommy

---

### Post by NM5TF on 2012-10-29
on another note, I did try booting from the .iso image using
UNetbootin with no results...it was supposed to generate an
automatic GRUB2 entry after finishing, but it never showed up...:confused:

I did manage to boot directly from a 12.10 .iso disk image via a
menu entry into /etc/grub.d/40_custom but it STILL will not let 
me delete /dev/sda6.....there seems to be a bug somewhere as the
menu item "Try Ubuntu Without Install" did not work & 12.10 REALLY
screwed up my Nvidia VGA card....:twisted:

I will download a new copy of 10.04 LTS to Cd & try it again in
the morning....[-o<

Tommy

---

### Post by YannBuntu on 2012-10-30
Hello

1) make sure your BIOS boot priority has "CD" / "USB" first in boot order.

2) if still no success with CD, try with an Ubuntu liveUSB

---

### Post by muteXe on 2012-10-30
Surely not being able to boot from a live cd has nothing at all to do with any partitions on the machine?

---

### Post by NM5TF on 2012-10-31
> **muteXe said:**
> Surely not being able to boot from a live cd has nothing at all to do with any partitions on the machine?

correct.....my problem turned out to be a flaky hardware CD drive...

weird problem as the drive would still play music & DVD's, but gave
erratic results when reading data files.....will look into it when
I have some time....I am a hardware guy at heart, not software....

swapped the drive with a spare....ran Live CD successfully...opened
GParted & deleted sda6....resized what now became sda7 to reclaim the
wasted 20GB.....now happy & will mark as solved....

I think that my next adventure will be to move /home to it's own
partition....should be fun...:P

---

### Post by muteXe on 2012-10-31
my cd drive at work is a bit like that. I can play audio files but sometimes it struggles with reading mp3 files or other files. Weird.

---

