---
title: "Grub not booting ubuntu"
date: 2015-07-11
forum: General Help
---

### Post by jonnsl on 2015-07-11
I wanted to mess a bit with arch linux, so I got a HD I wasn't using and cloned my main hd into it(so in case things went wrong, I had a backup), removed the clone, installed arch linux on my main hd (which is now formated with GPT), then I was having problems with gnome on archlinux (problems which are not relevant here), so I connected the cloned hd into my computer (which now isn't /dev/sda anymore) booted it successfully, then a system update dialog appeared and I clicked OK thinking nothing of it, after a few moments I noticed that the update had froze and aptd was consuming quite a bit of cpu, so I restarted the computer and now grub wont boot, It shows something like this:
> 
error: can't find command '[',
error: can't find command '[',
error: can't find command 'save_env',
error: can't find command '[',
error: can't find command '[',
error: can't find command '[',
error: can't find command 'search',
error: can't find command 'linux',
error: can't find command 'initrd'.

Press any key to continue...

the grub theme was also messed up, that box around the list of oses is a bunch of interrogations, as if the font was missing;
systemd-boot which was installed in my main HD also won't boot.

summarizing:
-ubuntu was installed in /dev/sda;
> 
Disk /dev/sda 500 GB
Device        Boot    System
/dev/sda1    *        Linux (boot partition)
/dev/sda2              Extended
/dev/sda5              Linux (root partition, LUKS encrypted)


-I cloned /dev/sda into /dev/sdd;
-Formated /dev/sda with GPT and installed arch linux;
So now /dev/sda is something like this:
> 
Disk /dev/sda 500 GB
Device        Boot    System
/dev/sda1    *        Linux (boot partition)
/dev/sda2              Linux (root partition, LUKS encrypted)
/dev/sda3              Linux (swap)

-Booted into ubuntu(/dev/sdd);
-ubuntu asks to update. Updates grub, gets confused where the boot partition is and messes both boot partitions in /dev/sda and /dev/sdd;

So my question is, how do I restore the grub so I can boot ubuntu again? (I don't really mind about the other boot partition)

---

### Post by Bucky Ball on 2015-07-11
Personally, I would try [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). You could go the recommended repair option, which tends to throw grubs all over, or you can install grub directly to sda, which is normal.

If the latter doesn't work, try the former.

When you say you cloned sda to sdd, what software did you clone it with? The BIOS is set to boot from the correct drive? It may be that your fstab file, which mounts the partitions at boot, is well screwed and the UUID numbers for the partitions are wrong. They would be from the old set up.

Which brings to light another option. You could boot from live media and tweak the UUID numbers in the fstab file for the OS you are trying to boot ... :-k

---

### Post by jonnsl on 2015-07-11
Thanks, I will try that.
Just one question first, I was looking through the advanced options and think that these are the options I should use:
OS to boot by default: sdd5 (will boot-repair even find that ubuntu is installed here, since the partition is encrypted?)
separate boot partition: sdd1
place grub in all disks: NO (definitely don't want this, I specially don't want to mess with windows which are on ssds in raid 0)
place grub into: sdd
Purge grub before reinstalling: yes
all other options: default

is this correct?

Thank you very much.

---

### Post by Bucky Ball on 2015-07-11
As I have no experience of encrypted partitions/disks or raid I am not confident in giving any advice you should follow at this point. Proceed at own risk. Hopefully someone that knows can help.

May have something to do with the cause of the issue originally.

---

