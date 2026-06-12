---
title: "Booting and partition troubles"
date: 2008-04-04
forum: General Help
---

### Post by Calida on 2008-04-04
Hi folks, I hope someone out there is able to help me with my problem ;)
Since yesterday i am not really able to boot into my Kubuntu any more.During the booting, at mounting the HD i think he quits with the errormsg "Unable to resolve UUID="...." exit status 8
The UUID he can't resolve is the partition that is mounted as home so i changed the fstab to prevent him from mouting it, now i come to the logonscreen but after logging on i get the errormsg "could not start kstartupconfig, check your installation"
On the home partition (the one with the UUID he can't resolve) I tryed to do a fsck which was quited with an errormessage telling me that he can't read the superblock...
Any hints?

Thnx in advance.

---

### Post by forestpixie on 2008-04-04
You could change fstab so that the UUID matches not to prevent mounting. You can use ```
sudo blkid
``` to get UUID information.

You can do it all from recovery if you use nano to edit the file, Ctrl+O then enter to save, Ctrl+X to exit.

---

### Post by Calida on 2008-04-04
Thank you for that, but it seems i have 2 different problems.

The UUID Linux can t resolve belongs to the device i am mounting as home actually it is /dev/sda5
now there seems to be something rly wrong with it. It is not listet is not listed as device whrn i want to autocomplete with tab, when i do a fsck for /dev/sda5 it tells me that he cant read the superblock. When i tryed to access it through windows i found that windows isnt recognicing it as partition but as free space on the HD.

The second problem is that there seems to be something wrong with my kde. When i try to log on it quits with an error saying "could not start kstartupconfig, check your installation"
is this kstartupconfig somewere in the home folder? i mean might the reason for the error be that i am not mounting /dev/sda5 at /home any more?

is there anything i can do to restor the partition with my home folders?

thx

---

### Post by forestpixie on 2008-04-04
Yes I would guess that the two are related - I don't run kubuntu but would assume that the file that can't start is probably on the /home drive.

But I'm afraid I don't know a whole lot about superblock errors - loathe to do anything other than get you to search - would hate to give you bum info and you end up losing you're home.

I would though boot the livecd - find the partition - it should be in /media and see if it will mount so you can try to get data off it.

Did you check the UUID for the drive against the fstab?

---

### Post by ghw on 2008-04-04
I sounds like the /home partition is corrupted, and I would certainly expect all sorts of problems with kde if you do not have a home directory!

Normally if I have disk problems I would boot with a live-cd (although I think all install disks are live-cds nowadays) and use tools like grub, fdisk and fsck to try to fix things. 

However, your problem seems to be limited to the /home partition so you may be able to boot from the hard disk but log in as "root" since "root" does not keep its home directory in the /home partition. Unfortunately though, the "root" account is not enabled by default so if you have never enabled it (eg. "sudo passwd root") then you may have no choice but to boot in single-user mode or boot from a live-cd.

Graeme

---

### Post by Calida on 2008-04-06
Well thx for the help.
What i have figured out to far is that it seems that the partition which used to be my home is gone.
I can find 4 devices on sda which is the HD in my notebook. There is the swap (sda1) partition, the partition for / (sda2) my windows partition (sda3) and last an sda4. There should be an sda5 which is supposed to be mounted as my home, at least that is what is written in the fstab.
Any fsck on sda5 fails ofc because he does not recognice it.
an fsck on sda4 (which i dont know what it should be) results in an error "fsck.ext attempt to read block from file system in short read while trying to open /dev/sda4. Could this be a 0 length partition?"

considering all this, and also that in windows the part of the hd which is supposed to hold my home partition is inicated as free memory and not as unknown file system i think the partition is gone.
Out of interest i want to ask if there is any hint on how this could have happened...

For solving this problem. Can i just go and recreate the partion with fdisk? Will my data be there again after that? is fdisk enough or do i have to make mkfs as well? if so what can i do to restore the data afterward?

---

### Post by forestpixie on 2008-04-06
I'm not able to help with why it happened - could be that the hdd is on the way out.

You should be abel to make a new partition as home - but you'll probabl need to amend fstab to reflect it's UUID if it's changed. I think that the mount point should still exist - but can't be sure.

---

