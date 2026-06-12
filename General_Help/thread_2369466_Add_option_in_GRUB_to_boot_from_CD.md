---
title: "Add option in GRUB to boot from CD"
date: 2017-08-23
forum: General Help
---

### Post by scratch-monkey on 2017-08-23
I want to add an item in my GRUB menu to boot from CD. I've searched for info on how to do this and the most recent thing I found was from 2009 and included broken links and such. So in 8 years time I suspect things might have changed.

A few notes to save some time:
- I am not trying to recover, repair, or restore anything.  I am not looking for a 1 time solution.
- I don't want to do this from the BIOS. Yes, I know how to do that.
- My computer is dual boot Ubuntu/Windows10 with Grub controlling the boot.
- I am aware of the security issues of allowing a boot from CD.

---

### Post by oldfred on 2017-08-23
I have this in my notes, not sure if still valid or not, but see it is a grub2 stanza.

```
 # Boot whatever is in the CD drive
menuentry "CD on (sr0)" {

 insmod udf
set root= (sr0)
chainloader +1 
 }
```

---

### Post by ajgreeny on 2017-08-23
I have just tried your suggestion, oldfred, adding that stanza to my existing working **/etc/grub.d/40_custom** but it errors out with the message
```
Error; variable "root" is not set
``` 
and quickly goes back to the grub menu.

Can I assume that your suggestion did not need the (sr0) editing to something else, eg /dev/sr0; I copied the words exactly as you showed them and as my CD is definitely sr0, I assumed that was correct.

PS:
For some time now, I think since grub2 appeared, I have had a reboot and halt command added to grub, both of which work fine.
```
menuentry "Reboot" {
    reboot
}
menuentry "Halt" {
    halt
}

```

---

### Post by ajgreeny on 2017-08-23
I noticed that there was a space in the line following the = character
**set root= (sr0)**
and wondered if that was the problem so removed it and tried it again but this time with error message:-
```
Error: No server is specified.
```

I am no grub2 expert and I am just trying this out of personal interest.

---

### Post by oldfred on 2017-08-23
Space may be an issue.

In another place I have this:
 set root='(cd0)'

Edit:
I looked to see if I had any bootable CD/DVDs and have long ago tossed them all as old.
Plus now system is UEFI, and I have never made a bootable DVD for UEFI.

Is CD/DVD in same boot mode as you have booted grub. As once you start booting in UEFI or BIOS, grub can only boot other installs in same boot mode.

---

### Post by ajgreeny on 2017-08-23
It is a DVD from a Linux magazine I was using as a test. I have not thought to try booting from it at power on from the device menu but will try tomorrow.

It is not very important to me as I usually boot from a USB; I am just a curious type!

---

### Post by oldfred on 2017-08-23
I do not have DVD or CD.
I put just something in DVD and tried using entry. Same error.

But then using c to get to grub command line & ls to list what grub sees, it showed cd0.
And manually editing boot stanza, it then gave an error that it was not UEFI bootable which it is not.

So if booted in same boot mode this may work?

```
 # Boot whatever is in the CD drive
menuentry "CD on (cd0)" {

 insmod udf
set root=(cd0)
chainloader +1 
 }
```

---

### Post by ajgreeny on 2017-08-28
I have at last got around to testing your last suggestion of changing to **set root=(cd0)** in the boot stanza, and that does get me one step further, but now tells me there is an incorrect EFI pathway, so it still does not boot.

By the way, the DVD I was using does boot fine in UEFI mode as well as in BIOS mode.

As this is just a case of me being curious and of no real long term use to me, I think I am going to give up on the possibility of doing this from grub; thanks for sticking with me on this.
I wonder if scratch-monkey has had a go and if he succeeded or not.

---

### Post by oldfred on 2017-08-28
Burned a DVD to see what issue was.
Forgot that UEFI boots differently.
And now I remember one of the reasons I stopped using CD/DVD as it is so slow, compared to USB3 in USB3 port.

This works for me. I booted 17.10 with this:
```
# Boot whatever is in the CD drive
menuentry "CD on (cdrom/dvd)" {
    set root=(cd0)
    chainloader /EFI/BOOT/grubx64.efi
}

```

Found I did not need insmod udf. Found Case was important. Just using my more common with flash drives /EFI/Boot did not work. But when using FAT32 case is not used, so must be used on the DVD/CD.
First thought I had to use /EFI/Boot/bootx64.efi as that is standard for UEFI boot directly from external drives. But got error on grubx64 not found. Since chainloading from grub, then it is not UEFI directly booting, so grubx64.efi is used, and DVD had both files.
And then found case was critical as leaving parts as caps still gave errors.

---

### Post by ajgreeny on 2017-08-30
I did make one last try using your final suggestion but that unfortunately gave me another error.
> ERROR:  the file /EFI/BOOT/grubx64.efi can not be found
Never mind; it was worth the try even though unsuccessful for my system;  I wonder why it worked for you and not me, perhaps it depends entirely on the boot system on the CD.

Is that different perhaps on a multiboot DVD with three live OSs on it when compared to your DIY burned DVD of 17.10?

PS:
I agree with you about the speed of DVD when compared with a USB live system; it is almost unusable, taking a lot longer to boot and then to run the OS.

---

### Post by oldfred on 2017-08-30
I had to mount DVD to see file & then realized case was different. You may have to mount your CD/DVD to see if grub is there and its exact case. Or make sure the multi-boot DVD has grubx64.efi in /EFI/BOOT before burning DVD.

I was a bit surprised that Ubuntu had the grubx64.efi in /EFI/BOOT. They must expect some may want to chain load?

---

### Post by ajgreeny on 2017-08-30
> **oldfred said:**
> I had to mount DVD to see file & then realized case was different. You may have to mount your CD/DVD to see if grub is there and its exact case. Or make sure the multi-boot DVD has grubx64.efi in /EFI/BOOT before burning DVD.

I was a bit surprised that Ubuntu had the grubx64.efi in /EFI/BOOT. They must expect some may want to chain load?
I think that is the difference I was wondering about.
The DVD I was using has the grubx64.efi file in /boot so perhaps I will try that, not /EFI/BOOT like a live Ubuntu iso file, which presumably transcribes to the same place on a burned DVD.

I haven't got any live DVDs of my own burning to check that, as like you I use USBs all the time these days, or more likely boot the .iso direct from grub2 on a USB; I used to have about 6 iso files on a single USB stick which all booted quickly and easily, but I now tend to check any live systems want to see or test using VBox, again booting the iso files direct into live systems then installing as VMs if it looks interesting.

In spite of my comments about not trying again I will have one more go with that new pathway to the grubx64.efi to see if that works or not.
Watch this space!

---

### Post by oldfred on 2017-08-30
Good luck.

I also directly boot ISO with grub2 loopmount. 
I used to use flash drives & still have one or two. Now usually have full install & a couple of ISO on a larger flash drive. Full install to flash drive does not even create any /EFI/boot folder in ESP on flash drive. Not sure then what grubx64.efi versions there are.

But most of the ISO I boot are on my SSD or HDD. And then I can easily & quickly install from one drive into the other drive. Have had issues of having to manually unmount /isodevice, but otherwise has worked well.

---

### Post by ajgreeny on 2017-08-30
Me again!

This time using /boot/grubx64.efi as the pathway in the grub stanza I did get as far as grub_rescue prompt but the system said it could not read the sector on the DVD, so this time I really have given up; I have already spent more time trying to figure this out than is worthwhile to me, and even though I imagine it would be possible, by trial and error, eventually to get it booting, I am not prepared to waste any more time just now.

Thanks for sticking with me on this; I have learned a lot about things that I knew little about before so it is not time completely wasted. I hope **scratch-monkey** might have learned something too.

---

