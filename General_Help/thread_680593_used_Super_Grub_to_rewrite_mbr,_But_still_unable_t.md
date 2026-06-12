---
title: "used Super Grub to rewrite mbr, But still unable to boot windows xp"
date: 2008-01-28
forum: General Help
---

### Post by cantri on 2008-01-28
Having problems loading Win xp after installing ubuntu 7.10. Would hang on first blank text "starting" screen. Tried super grub to re write mbr but didn't work still couldn't get into windows and have to start ubuntu with super grub cd now. I noticed that my old windows part of the hard drive is called "/media/disk-1" all my files are still there. Should this be called C:\, there is no mention of c:\ anywhere in properties. Could this be why the grub doesn't do anything when I Choose win xp. ( I am new and don't know to much about this). Is there any way I can just get windows back without having to format my old files. Here is my menu.lst

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=71c1dfc1-2763-4b27-acf0-2750745b31fe ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=71c1dfc1-2763-4b27-acf0-2750745b31fe ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by LaRoza on 2008-01-28
> **cantri said:**
> Should this be called C:\, there is no mention of c:\ anywhere in properties. Could this be why the grub doesn't do anything when I Choose win xp. ( I am new and don't know to much about this). Is there any way I can just get windows back without having to format my old files. Here is my menu.lst

No, Linux will not call it C:, that is an old and ancient way of addressing drives used by a pre DOS operating system.

Try using the SGD again, using:

Advanced->Windows(Advanced) and the first option. It should make Windows boot, with no hint of Grub.

---

### Post by cantri on 2008-01-28
> 
Advanced->Windows(Advanced) and the first option. It should make Windows boot, with no hint of Grub.

I did this, and in the last section when it asks you to choose your previous operating system before having grub, Win xp is not an option. So I chose linux as there was nothing else to choose. Grub is erased but, with out SG disk I can't boot now, computer instantly gets an error message. I think I'm going to track down a Win Xp disk and try to run chkdsk and fix the mbr through that, will this work?:confused:

---

### Post by Herman on 2008-01-28
FIXMBR should work, but only if the fault is in your MBR. Then you'll always need Super Grub Disk every time to boot Ubuntu.

FIXBOOT  will fix the Windows boot sector, if you have a problem there, but if you do it has nothing to do with either GRUB or Ubuntu. because nothing writes to the Windows boot sector except Windows and some viruses.

Here is a link to a great website for helping you boot Windows XP, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm").
You can download a CD from that site with the three vital Windows bootloader files, NTLDR, NTDetect and boot.ini, and the boot.ini in that is preconfigured with generic entires so you can boot almost any Windows XP with that.
That bypasses about any boot problem you can have with Windows XP. :)
Read that web site and follow the instructions.
 There's also a more basic but similar how-to from the makers of the other software too, [How to make your own Windows Xp boot floppy]("http://support.microsoft.com/kb/305595/EN-US/")
Either of those two links contains instructions that should help you boot your Windows Operating system so you can fix it.

I'm presuming you'll prefer to get your Windows XP booting for sure first, then you'll have time to fiddle around with GRUB later. We can help you with that then. Actually, I don't think it's a GRUB problem, I suspect it's a Windows problem that you're having. We might even be able to help with that too, but we'll see. I hope that will get you going for the time being.

Regards, Herman:)

---

### Post by Herman on 2008-01-28
Another lesson I learned with trying to boot Windows is if it goes into a blue screen, try booting it in safe mode and see if that will work at all.
Sometimes it will boot in safe mode okay, and then you can look for problems from there.

---

### Post by cantri on 2008-01-28
Yes!!!:) I'm almost there. I can boot into windows with the NTLDTR disk, but with out it I get a disk error message that says to hit cntrl alt Del on boot up, same as beforel, (but "Del" is misspelled as "el".) So I'm assuming I can still boot in ubuntu with super grub disk. Should I run the super grub disk and try to write a new mbr. Or is there more I should do so that windows for sure will be able to boot. Thanks for the help, but i'm worried about the next step, should I run chkdsk from windows? fixmbr? fixboot? Thanks again windows seems to be completely intact and I technically should still be able to get into ubuntu

---

### Post by Herman on 2008-01-29
You should be okay to reinstall GRUB to MBR with Super Grub Disk so at least Ubuntu will boot normally.

Then, we need to see what's wrong with Windows XP.
You couild try 'FIXBOOT' to refresh your Windows boot sector to see if that helps.
If that's not it then we'll need to take a look at boot.ini and NTLDR. 

Because of the fact that the NTLDR disk will boot Windows, it seems like it's probably one of those three files that's causing your problem if not the boot sector.

The boot sector is the first thing to suspect, and also the easiest to fix, (with the FIXBOOT command).

Regards, Herman :)

---

### Post by Herman on 2008-01-29
It's always a good idea to run a file system check. A file system check never does any harm and can often solve booting problems, You can't run too many file system checks, so your idea to run CHKDISK is a good idea.

Regards, Herman

---

### Post by adrian15 on 2008-01-30
> **cantri said:**
> I did this, and in the last section when it asks you to choose your previous operating system before having grub, Win xp is not an option. So I chose linux as there was nothing else to choose. Grub is erased but, with out SG disk I can't boot now, computer instantly gets an error message. I think I'm going to track down a Win Xp disk and try to run chkdsk and fix the mbr through that, will this work?:confused:
[b]
Can you please confirm me that the instat error message is:
```

Error: No active partition error found.

```?
[/b]

You can get rid of this error with: Boot & Tools -> Activate Partition.

The new version of Super Grub Disk which I am developing (I'm quite busy at the moment trying to automatise the Super Grub Disk uploads) will not ask about which it is your Windows disk (in Windows basic menu I mean) and will automatically activate the windows partition when fixing boot of windows.

adrian15

---

