---
title: "oh, no! i think i messed up bad!"
date: 2007-08-01
forum: General Help
---

### Post by mshale on 2007-08-01
Hey everyone,

I just bought a new macbook, and am giving my old one to my dad, and i tried to reformat the HD because he wanted only windows on it.  So, like a dummy i shoved the original Toshiba restore disk in and proceeded with the reformat.  All of the partitions were deleted, and it got to the point where i was to remove the cd and reboot.  I did that and when it rebooted, it was supposed to go right into windows and setup, but instead it tried to load grub and produced and grub error 22.  

How do i get it back to like it was from the factory??

---

### Post by init1 on 2007-08-01
> **mshale said:**
> Hey everyone,

I just bought a new macbook, and am giving my old one to my dad, and i tried to reformat the HD because he wanted only windows on it.  So, like a dummy i shoved the original Toshiba restore disk in and proceeded with the reformat.  All of the partitions were deleted, and it got to the point where i was to remove the cd and reboot.  I did that and when it rebooted, it was supposed to go right into windows and setup, but instead it tried to load grub and produced and grub error 22.  

How do i get it back to like it was from the factory??
Easy. If you want to erase everything on the disk, first load a Linux distro, like Ubuntu. 
WARNING, THIS ROUTINE WILL ERASE EVERYTHING.
```

dd if=/dev/zero of=/dev/thedevice

```
do a fdisk -l to determine "thedevice". It might be /dev/sda, or /dev/hda, or something else. 
Then load up fdisk or Gparted (gparted is easier) and add back the partitions, and format it NTFS. All that is missing is the OS, which you will load. That should remove grub. There is probably a simpler way to do it, but this works :D. Or at least it should.

---

### Post by mshale on 2007-08-01
thanks for the advice, but what do you mean by "load"?  Do you mean that i can do all of this using the live cd? or will i actually have to install ubuntu on the HD? gparted has a live cd too, can i use that?

---

### Post by Shmifty on 2007-08-01
Live CD should work

---

### Post by nelamvr6 on 2007-08-01
No, all you have to do is put a bootable windows disk with fisk on it into the cd drive, boot, then at the a:> prompt type "fdisk /mbr" and you're back to factory fresh.

You guys have told him to erase everything, he's gonna have to reload windows again!

---

### Post by bodhi.zazen on 2007-08-01
> **nelamvr6 said:**
> No, all you have to do is put a bootable windows disk with fisk on it into the cd drive, boot, then at the a:> prompt type "fdisk /mbr" and you're back to factory fresh.

You guys have told him to erase everything, he's gonna have to reload windows again!

\o/

If the Toshiba Restore disk can not do it, you can use the knoppix CD ...

Boot Knoppix, open a terminal, enter the following command : ```
sudo testdisk
```

At the third screen, select "write MBR" ... Select "yes" (you are sure)

I also found this :

> The Knoppix equivalent of fdisk /mbr:```
knoppix@tty1[knoppix]$ sudo install-mbr /dev/hda
```

*You might be able to do this with the Ubuntu Desktop CD, you might have to install testdisk first, I am not sure ...

OR 

You can try this : [http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

---

### Post by mshale on 2007-08-03
Hey, thanks for all of your help!!  I am a cool person, so i had already made the complete switch to Ubuntu... lol i'm kidding!  I didn't have windows on this lappy, So i had to reformat the whole thing anyway, and have already transferred all of my files over to my new macbook.  

Again, thanks a ton again eveyone!

---

### Post by init1 on 2007-08-03
> **nelamvr6 said:**
> No, all you have to do is put a bootable windows disk with fisk on it into the cd drive, boot, then at the a:> prompt type "fdisk /mbr" and you're back to factory fresh.

You guys have told him to erase everything, he's gonna have to reload windows again!
I thought that was what he wanted. I wasn't sure about other solutions. Good thing they were suggested.

---

### Post by HermanAB on 2007-08-03
The problem is that Windoze doesn't understand Linux partitions.  The solution is to wipe the partition tables completely before you load Windoze.  That however is easier said than done, since you need to have the disk drive unmounted - that is, you cannot run from the disk drive while you are trying to delete it.

The solution is to boot from a live CD, such as Knoppix, then use disk duplicate to write zeros to the first part of the disk.  For good measure you can zero the whole disk to ensure that all your data is wiped reasonably well.  So, first go to knopper.net and get Knoppix (or get the Ubuntu live CD), then:
$ su -
# dd if=/dev/zero of=/dev/hda bs=16k

Long wait...

Now reboot with the Windoze restore CD.

Cheers,

Herman

---

### Post by DMacATTACK on 2007-09-20
I have this similar problem... Except... heres the kicker...I dont have a windows boot up CD. My backup is on my hardrive like Microsoft has been doing for the past few years. When starting up with the Live CD it shows the windows partitions are still there, but grub blocks me. If i could get some help on this that'd be great. 
Thanks

EDIT: I thought I should give a few more details: I had dual boot of Ubuntu and Vista, and I wanted to remove the Ubuntu sector so i followed these directions [http://ubuntuforums.org/showthread.php?t=508927&highlight=mbrfix](http://ubuntuforums.org/showthread.php?t=508927&highlight=mbrfix), and upon rebooting I get a Grub error 22 and I cant boot into windows. ... 
Any questions just ask.

Thanks again.

---

