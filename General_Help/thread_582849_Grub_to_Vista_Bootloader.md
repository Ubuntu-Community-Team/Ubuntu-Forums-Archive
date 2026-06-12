---
title: "Grub to Vista Bootloader"
date: 2007-10-20
forum: General Help
---

### Post by Zacha on 2007-10-20
Please do not post things like "Why do you want to do that?" or "Vista Sucks!" in this thread please.

Well. To make it short.
Yesterday I installed Ubuntu.
I thought I told it NOT to install GRUB to MBR.
But when I restarted my computer I was met by GRUB to my surprise.
At first I thought "What the heck" but yesterday I noticed that I can't hibernate in Vista anymore (maybe because of the wrong MBR). So I though I'd would go back to Vista Bootloader as Vista is my main OS. Even though the hibernate problem in Vista may not be because of this I still want to go back to Vista Bootloader (So I just can throw ubuntu out if I ever need/want to).

So I wonder how do I put GRUB on the ubuntu partition instead and still be able to restart and boot into Vista to fix the bootloader there afterwards? (As I have no Vista DVD, only recovery CD's...)

Or should I fix the bootloader first in Vista and then use a LiveCD to install grub to the ubuntu partition (and how do I do so it doesn't write to MBR again if so?)

---

### Post by r-mo on 2007-10-20
With gutsy on the normal installer you can select not to install grub,  you couldn't do that with feisty.  It's under advanced on the last screen :)

I've never tried to put grub in a partition rather than mbr, always done this with lilo which works just as well :)

so in a terminal

```

sudo su -
apt-get install lilo lilo-doc
apt-get remove grub
nano /etc/lilo.conf

```

You should have lilo.conf open in nano editor, just make it look like the following, substituting sda3 with whatever partition you installed linux on.

```

boot=/dev/sda3
default=Ubuntu

map=/boot/map
delay=1
image=/vmlinuz initrd=/initrd.img
append="quiet splash"
root=/dev/sda3
label=ubuntu
read-only

```

ctrl+o to save ctrl+x to go back to terminal

```

/sbin/lilo -v

```

You should now have a bootloader in the lnux partition rather than mbr.

Do what you like with vista ;)

---

### Post by Zacha on 2007-10-20
> **r-mo said:**
> With gutsy on the normal installer you can select not to install grub,  you couldn't do that with feisty.  It's under advanced on the last screen :)

I've never tried to put grub in a partition rather than mbr, always done this with lilo which works just as well :)

Do what you like with vista ;)
But I did not use the usual installer. I used the text based one =P

Anyhow. So would this allow me to boot Vista before repairing the MBR (as I don't know how to repair it outside Vista)? It doesn't remove the grub in MBR or something (leaving me stranded?)

(And as a side question, is there any difference between LILO and GRUB?

---

### Post by r-mo on 2007-10-20
To be honest I have no idea about the bootloader in vista.  I'd have to recommend getting that working before doing this, just in case ;)  Can you even add an option to boot from your linux partition.  The only place I've used this method is triple booting a mac with rEFIt.

As for the difference between lilo and grub they aren't that great.  grub can boot from a network whereas lilo can't and grub has a command line interface whereas lilo doesn't.  Lilo's a lot easier to set up though ;)

---

### Post by r-mo on 2007-10-20
oops, if you fix your vista bootloader first, you won't be able to boot into ubuntu to install lilo the way I described.  However if you boot from a live cd you can do it by chrooting into your ubuntu install.  To do this:

From the live cd, open a terminal
```

sudo su -
mkdir /mnt/ubuntu
mount /dev/sda3 /mnt/ubuntu
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu /bin/bash

```

---

### Post by logos34 on 2007-10-20
Zacha,

The easiest way to do this is to boot into vista first and download EasyBCD.  Use it to restore the vista boot manager on the MBR.  Add linux entry.

Then reboot into the ubuntu live cd and reinstall Grub to the ubuntu **root partition** using the howto below.  But make sure to do 'setup (hd0,**x**)', where x=root partition #.

[http://neosmart.net/wiki/display/EBCD/linux](http://neosmart.net/wiki/display/EBCD/linux)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Zacha on 2007-10-20
> **logos34 said:**
> Zacha,

The easiest way to do this is to boot into vista first and download EasyBCD.  Use it to restore the vista boot manager on the MBR.  Add linux entry.

Then reboot into the ubuntu live cd and reinstall Grub to the ubuntu **root partition** using the howto below.  But make sure to do 'setup (hd0,**x**)', where x=root partition #.

[http://neosmart.net/wiki/display/EBCD/linux](http://neosmart.net/wiki/display/EBCD/linux)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Yeah, that's what I thought...
Will try it later when I get the time.
Thank you for your short and concise answer =)

EDIT: Later: Well. EasyBCD can't fix my mbr... hmm, I wonder if I should let Windows fix it...

(Do I need to change the Vista partition back to active partition in gParted or does EasyBCD do it too?)

Oh, and thanks r-mo, but I think I'll stick to grub ;)

---

### Post by Zacha on 2007-10-21
Problem solved.
It hadn't installed GRUB to MBR, ubuntu had just made the ubuntu partition the active one (activated the boot flag on it) so the windows MBR which just boots the active partition booted the ubuntu partition where I had installed GRUB.
A quick google search came up with some ppl who said that the hibernation file must be on the active partition. And as windows couldn't access the ext3 partition it couldn't hibernate.

---

