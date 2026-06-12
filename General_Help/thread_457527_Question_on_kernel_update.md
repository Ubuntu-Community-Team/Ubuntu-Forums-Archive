---
title: "Question on kernel update"
date: 2007-05-28
forum: General Help
---

### Post by floke on 2007-05-28
I'm currently triple-booting between distros and have a question about the 7.04 kernel update.
To boot ubuntu I have copied over the relevant stanzas to my SUSE grub entry (not my main distro, but it now runs grub since it was installed after Feisty). The old kernel boots fine, but the new one chucks errors at me in grub. I've coped over the entry and it looks exactly like the old kernel entry except for the 20.16 rather than 20.15. The error I'm currently on is about it not being an appropriate file path or something - even though its the same one as the old kernel!

That gurgling is the sound of Ubuntu's reputation going down the drain.

---

### Post by Gannin on 2007-05-28
Just because you're having problems doesn't mean that everyone is, and just because Ubuntu's reputation may be going down the drain with you doesn't mean that it is with everyone.  In fact, I've never heard of this problem before, so you must just be special.

Having said all that, in response to your actual problem instead of your editorial, it would be interesting to set Ubuntu's GRUB as the main GRUB to see how it handles the situation.  There are instrunctions on how to do this without reinstalling Ubuntu on the net.

---

### Post by floke on 2007-05-29
You've never heard of the problem with the new kernel??
I suggest you take a 10-second look around this forum; it's created a whole heap of crap for a load of people.

I suggest you take a look here:

[http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)

or here...

[http://ubuntuforums.org/showthread.php?t=457394](http://ubuntuforums.org/showthread.php?t=457394)

or here

[http://ubuntuforums.org/showthread.php?t=457594](http://ubuntuforums.org/showthread.php?t=457594)

or here...

[http://ubuntuforums.org/showthread.php?t=456702](http://ubuntuforums.org/showthread.php?t=456702)

you want me to go on, or do you get the point?

---

### Post by mikewhatever on 2007-05-29
Ubuntu is not perfect, every one knows it. If you want help, post your menu.lst here and the exact text of the error message.

---

### Post by floke on 2007-05-29
Of course it's not perfect, and I don't expect it to be.

I do expect, however, that I won't be sent a new kernel that doesn't work!

From what I've read about other people's cases, I got off lightly - just select old kernel from grub. Other people have had their entire systems hosed. So I, along with them, have every right to be angry. Frankly, if we care about spreading ubuntu then we should all be up in arms about things like this. Its terrible. I've just set up a couple of friends with ubuntu after a long campaign of persuasion, and now this happens. Fortunately I managed to warn them first, but it makes me look like an ****. How do I explain this? "Oh it doesn't happen that often" (only once every few months)? This will absolutely put a load of people off Ubuntu, and I can't say I blame them, Its amateurish at best.

Anyway, glad I got that off my chest.

My question, really, is about whether its the 20.16 kernel itself that's shot, or whether its the way in which I've copied it over to the menu.lst

The file is this:

title           UBUNTU, kernel 2.6.20-16-generic
kernel        (hd0,0)/boot/vmlinuz-2.6.20-16-generic root=UUID=20b99c9b-dffc-$
initrd          (hd0,0)/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title UBUNTU, kernel 2.6.20-15-generic (/dev/sda1)
    kernel (hd0,0)/boot/vmlinuz-2.6.20-15-generic root=UUID=20b99c9b-dffc-40a6-$
    initrd (hd0,0)/boot/initrd.img-2.6.20-15-generic


20-15 works, 20-16 doesn't. All the files are in the right places. Entries are exactly the same, except for the change in the kernel name.

---

### Post by merlinus on 2007-05-29
My first bit looks like this:

```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=74ea0d79-f0a5-4381-a98d-08258758e696 ro quiet splash vga=795
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

Looks like the root line is missing in yours, and the kernel line is different as well.

BTW, you will want to change your root to (hd0,0).

I had to edit grub upon bootup (pressing the e key) to change the root, which had changed after the upgrade.

hth...

-merlin

---

### Post by floke on 2007-05-29
I'll give this a go. But the old kernel stanza had no root line present and worked fine prior to update.
I took the root line out of the new one to try and get it to work since it was already chucking errors.
Anyway, will edit and try...

---

### Post by floke on 2007-05-29
Ok, putting the root line back in gets me through to the 'savedefault' line - i.e. it appears on the screen rather than errors about the previous two lines - but now I get an error 15 file not found error - even though the kernel image is definitely in the /boot/grub dir. 

Any thoughts?

---

### Post by merlinus on 2007-05-29
Where is grub located?  That may be the problem.

If you can boot to a terrminal:

```

sudo grub
find boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

```

Your grub root will probably be different from mine, so substitute the result of the find line.

-merlin

---

### Post by merlinus on 2007-05-29
One more thought:

As you may have read in the various threads about the kernel upgrade, it changed sd's to hd's, so you may need to edit /etc/fstab.  I had to do this, but after ubuntu booted.

Also, for some reason your UUIDs may have changed, and that is why grub is not finding the kernel.

Look at the difference in UUIDs in your kernel stanzas:

> 
title UBUNTU, kernel 2.6.20-16-generic
kernel (hd0,0)/boot/vmlinuz-2.6.20-16-generic root=UUID=20b99c9b-dffc-$
initrd (hd0,0)/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title UBUNTU, kernel 2.6.20-15-generic (/dev/sda1)
kernel (hd0,0)/boot/vmlinuz-2.6.20-15-generic root=UUID=20b99c9b-dffc-40a6-$
initrd (hd0,0)/boot/initrd.img-2.6.20-15-generic


-merlin

---

### Post by cblanquer on 2007-05-29
Mine did not boot at all, I tried 3 times this morning, then had to hurry to my job.
Might it be due to the change from sd to hd ? 
I shall try accessing through the safe mode in order to modify the fstab.

= Some additional thoughts for the community ====
I am feeling kernel upgrades should come with a kind of warning on expected effects and how fixing them, totally unexperienced users should not be forced to go to forums and type commands to fix such kernel stuff.

At least my recent family  enrolled ubunteros do not like to become techies, I think this is the attitude of the average user that Ubutnu and other Linux distributions are trying to catch form Windows.

Such issues and other as WiFi problems (ref. RaLink chips case) we are missing the target into people conversion to GNU/Linux.
=================================

---

### Post by merlinus on 2007-05-29
You might check the UUIDs in your kernel stanzas, as they may have changed.  And they also may have changed for your partitions.

Good luck!

-merlin

---

### Post by floke on 2007-05-29
Thanks for the help and advice merlinus. Have tried your suggestions but still no joy.
At present I have three distros:

sda1=Feisty
sda3=SUSE
sda4=PCLOS

The mbr was overwritten by my SUSE install, so I have the SUSE grub. PCLOS was third on, and its grub was installed to sda4. The boot entries for ubuntu and PCLOS were then copied to the grub on sda3 - which is this:

# Modified by YaST2. Last modification on Sat May 26 23:23:53 BST 2007
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,2)/boot/message
##YaST - activate

title openSUSE 10.2 - 2.6.18.8-0.3
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.18.8-0.3-default root=/dev/sda3 vga=0x314 resume=/dev/sda5 splash=silent showopts
    initrd /boot/initrd-2.6.18.8-0.3-default

title Failsafe -- openSUSE 10.2 - 2.6.18.8-0.3
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.18.8-0.3-default root=/dev/sda3 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off
    initrd /boot/initrd-2.6.18.8-0.3-default

###Don't change this comment - YaST2 identifier: Original name: Ubuntu, kernel 2.6.20-15-generic (/dev/sda1)###

title UBUNTU, kernel 2.6.20-15-generic (/dev/sda1)
    kernel (hd0,0)/boot/vmlinuz-2.6.20-15-generic root=UUID=20b99c9b-dffc-40a6-ad67-3bfc81cf68e9 ro quiet splash
    initrd (hd0,0)/boot/initrd.img-2.6.20-15-generic

title           UBUNTU, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=20b99c9b-dffc-40a6-ad67-3bfc81cf68e9 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title PCLOS
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sda4  acpi=on resume=/dev
/sda5 splash=silent vga=788
initrd (hd0,3)/boot/initrd.img

--

The .15 kernel boots fine. The images for .16 are also in /boot/grub - but chuck error 15 still.
My fstab for ubuntu shows that the UUID's are still the same. There's also no 'sda' to change to 'hda', so it can't be this either.

steve@steve-laptop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=20b99c9b-dffc-40a6-ad67-3bfc81cf68e9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=75e36344-b7a3-4d91-94c4-b4848dbf91be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

I tried the 'sudo grub' commands - and got as far as find boot/grub/stage1 - which also chucked an error 15 - file not found! Didn't go past this since don't know what the commands do, and don't want to overwrite my mbr or something!

Any thoughts?

---

### Post by floke on 2007-05-29
All sorted.

It must have been the way I copied the stanza over, or the way in which the SUSE grub works. 
I installed a vanilla Feisty onto a spare partition I have set aside for experimenting with Gutsy and overwrote the mbr with a new grub, which picks up all my kernels fine. 

20.16 works perfectly here as far as I can tell.

Many thanks for the help.

---

