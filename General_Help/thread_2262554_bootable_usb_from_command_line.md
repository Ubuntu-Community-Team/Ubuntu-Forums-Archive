---
title: "bootable usb from command line ?"
date: 2015-01-25
forum: General Help
---

### Post by garyed on 2015-01-25
I wanted to make a bootable usb flash drive of another Linux distro from an iso & found it was not an easy task. I tried the Ubuntu startup disk creator but it wouldn't let me choose an iso that wasn't Ubuntu. I know there are third party programs out there to do it but I didn't want to install another program so i tried the command line. That didn't work out very well either. Using the dd command did not make the it bootable either. It copied all the files but still wouldn't boot. Is there a command line way that will work on any distro or is it distro specific? Either way if anyone knows know to do it I'd love to hear how.

---

### Post by yancek on 2015-01-25
The dd command should work but you forgot to post the actual command you used so we can't tell you if it was done properly.

---

### Post by garyed on 2015-01-25
> **yancek said:**
> The dd command should work but you forgot to post the actual command you used so we can't tell you if it was done properly.
```
sudo umount /dev/sdx
sudo dd if=/path-to-iso of=/dev/sdx bs=1M
```

I tried it every which way unmounted, mounted, partitioned with gparted, partitioned with fdisk & nothing worked except the command did copy all the files over to the usb flash drive.  
I ended up burning the iso (Lucid-Puppy) to a live CD , booted into Puppy & used their disk creator to make a bootable live usb flash drive. 
I spent hours trying to figure it out & the only thing i can come up with is either something is added to the boot drive to make it bootable or the place where it is copied onto the sectors makes the difference.

---

### Post by yancek on 2015-01-25
It might be that the puppy iso you had was not hybrid in which case this probably would not work.  A brief explanation at the link below on that and how to make an iso hybrid before using the dd command.  The posts at the link below are almost 2 years old so I'm not sure that is up to date.

[http://murga-linux.com/puppy/viewtopic.php?p=688262&sid=9e94454a39ec95ad0be18bcad22189ef](http://murga-linux.com/puppy/viewtopic.php?p=688262&sid=9e94454a39ec95ad0be18bcad22189ef)

---

### Post by nerdtron on 2015-01-25
Unetbootin can create bootable linux distro other than Ubuntu.. Also, some disro won't just work with the dd command.

---

### Post by sudodus on 2015-01-26
[TABLE]
[TR]
[TD="bgcolor: #FFFF99"] Wary Puppy 5.5 
[/TD]
   [TD]- needs treatment with isohybrid to be bootable with ***dd*** and ***mkusb***.

[/TD]
[/TR]
[/TABLE]

But dd is risky and deserves its nickname 'disk destroyer'. I wrap mkusb around it to make it safer. If you want a command line tool, use ***mkusb-nox*** or (simpler: ***mkusb-bas***)

See this link [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by garyed on 2015-01-26
Thanks for all the ideas,

I was remebering that even back in the old DOS days to make a bootable floppy it wasn't good enough just to copy the files to the disk. They had to be copied to certain sectors of the disk in order for it to be bootable so you needed to use special command parameters to do it. Things were much simpler so all you needed was "format /s" to make a boot floppy & then copy anything else you wanted onto the disk. I guess it's just progress.

---

### Post by sudodus on 2015-01-26
Do you remember diskcopy in DOS? I think dd can work like that, copying/cloning/flashing each byte, also 'certain sectors of the disk' (the special sectors for example where the bootloader is located).

---

### Post by garyed on 2015-01-26
> **sudodus said:**
> Do you remember diskcopy in DOS? I think dd can work like that, copying/cloning/flashing each byte, also 'certain sectors of the disk' (the special sectors for example where the bootloader is located).

I do remember diskcopy. The floppies held like 720kb & the computers were like 640kb memory so you would have to take the source disk out & put in the new disk then take it out & repeat the process again to finish up. I think the difference with dd is that diskcopy would not work unless both disks were the same type where dd will.

---

