---
title: "All OSs fail to load, HD or Live USB."
date: 2017-07-19
forum: General Help
---

### Post by javierdl on 2017-07-19
Thanks to oldfred and yancek I just got my main computer fixed.
However, my oldie pc needs some fixing too :(

This is the status: 
Basically below shows the Grub2 choices I went through.
1. It loads Grub2.
2. Did pass Memtest86.
3. Entered "nomodeset" before "quiet splash". Hit F10 to boot: This only starts a blinking underscore on lower left corner while menu remains above.
4. Advanced options- Ubuntu, with Linux 3.19.0-84-generic. Loading Linux 3.19.0-84-generic ... Loading initial ramdisk. Loading is interrupted by black screen with only a blinking underscore in upper left corner.
5. As above but with : (upstart). Same result.
6. Ubuntu 14.10 (14.10) (on /dev/sdb8). Same result.
7. Advanced options for Ubuntu 14.10 (14.10) (on /dev/sdb8). Ubuntu (on /dev/sdb8). Same result.
8. Windows Recovery Environment (loader on /dev/sda1). It loads the Windows logo and it starts the circuling dots animation, but only 1 shows before it's halted.
9. Windows 7 (loader) (loader on /dev/sdb1). Loading is interrupted by black screen with only a blinking underscore in upper left corner.


Ubuntu Live USB 
1. Check disc for defects - This only starts a blinking underscore on lower left corner while menu remains above.
2. On 2nd visit, pressed tab to access options. Entered "nomodeset" before "quiet splash". Hit Enter: same result as above.
3. Try ubuntu without installing - Screen blinks, this also only starts a blinking underscore on lower left corner.


1. Boot Repair Disk - result same as above.

What could be the problem?

Thanks guys

---

### Post by oldfred on 2017-07-19
Ubuntu 14.10 (14.10)is one problem. It expired July 2015.

Kernel 3.19 is either 15.04 or Ubuntu 14.04.3. 
If 15.04 also obsolete. 
And 14.04.3 would have to be updated to latest Enablement Stack.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Does current live installer, either new 14.04 or 16.04 work on this older system.
What are specs of this system? CPU, RAM, video card/chip? Brand/model?

---

### Post by javierdl on 2017-07-19
Oh yeah, I had failed to mention that the Ubuntu Live USB is 16.04.

I think my motherboard is EPU, not EFI. AMD Phenom II X3 710, 8Gb ram, motherboard= [http://www.asus.com/Motherboards/M4A78E](http://www.asus.com/Motherboards/M4A78E).
I'll go check on the video card now...

---

### Post by oldfred on 2017-07-19
I has internal AMD graphics which I only know a little about.
AMD is rewriting drivers, obsoleted some so not sure what driver may be best for your system.
I believe Radeon was last supported with 14.04.
 Radeon: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
AMDGPU: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)
AMDGPU-PRO: [https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)

---

### Post by javierdl on 2017-07-19
The graphics card is an EVGA Geforce GTX 560.

So, you are saying I should update the drivers, right?
If so, how can I do that when even USB drives won't load? No matter what I try it always brings me to that blinking underscore.

---

### Post by BenginM on 2017-07-19
Salutations!

when did this issue first happend , after an upgrade! i don;t now why your ubuntu installtion is on (on /dev/sdb8 .. while window is on sda , you installed ubuntu on a usb drive!

No, you enter nomodeset after "quiet splash" , in recovery mode it automatically uses nomodeset .. but in this menu highlight your ubuntu defualt (first) entry  installation in the GRUB menu ,  hit 'e' look for the line with quiet splash , add nomodeset after quiet splash -- .. press Ctrl+X or F10 to reboot into ubuntu with that kerenl boot parameter .

[ATTACH=CONFIG]276059[/ATTACH]

while you at it , it's worth doin' a file system check on both .. but for now will await for your response to oldfred.

---

### Post by BenginM on 2017-07-19
Well i was a bit late on this , but now am catchin' up .. 

for the Nvidia GTX 560 , you may need to try using the kernel boot parameter :

 nvidia.modeset=0

or

nouveau.modeset=0

Instead of 'nomodeset'  ... try that when you highligh the first defualt ubuntu entry in grub , also from the liv cd , try it with the 16.04 live usb first , if it doesn't get you to the live session , you might need to burn the 14.10 live usb and try again .. if are able to reach the live session then great , at this point it's a better to backup your files , and then try to repair boot from the live usb using :

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

and paste the result link here .

---

### Post by lammert-nijhof on 2017-07-19
You have the same problem with Windows, so start thinking about a HW problem. Take the video card out and try to boot using the internal graphics.

---

### Post by BenginM on 2017-07-19
Actually what lammert said makes more sense , disable the discrete Nvidia GPU in the BIOS,  and boot with the Integrated  ATI Radeon HD 3300. in that case you won't need to use the kernels boot parameters ... if you still unable to boot into the installatlled desktop , do backup and reformat install ubuntu 16.04. that's the quick fix , or you do insist on keeping the current installed system , then use boot repair form the live usd.

---

### Post by QIII on 2017-07-19
@Sary.sa:

Please do not post large images.  Some of our users have slow internet connections or data limits.  Please use the attachment functionality provided by the paperclip button in the toolbar above the text entry area.  This will place an expandable thumbnail image in your post.

Users may then decide if they want to view the entire image.

Thanks.

---

### Post by BenginM on 2017-07-19
Noted , thanks QIII .

---

### Post by javierdl on 2017-07-19
I just removed the graphics card, and I'm using the integrated motherboard video. I'm still stuck with the blinking underscore. Plus for some reason, Grub2 no longer loads. 
I tried to load the Live USB drive, using "nouveau.modeset=0" but to no avail. I get the blinking underscore.

I don't mind reinstalling Ubuntu. However, I fail to see how that's going to address an issue that's affecting Ubuntu and Windows, both in the local drives and in the USB. 
And about reinstalling Ubuntu, that's assuming doing it from a DVD works.

---

### Post by BenginM on 2017-07-19
Good Question , however you seems to have a deeper problem .. grub use to load and now for some reason doesn't ..   , the thing is we can't tell if Windows is installed in UEFI mode while ubuntu is installed in Legacy mode , or vis versa or what exactly .. we're trying to troubleshoot in the dark here , without seein' logs it's hard to tell ..

So, first we need to get you to load the live usb/cd successfully to preform a file system check to make sure the hard disk is not failing and to be ale to fix ubuntu's and windows partitions .. you can do a file system check when you're able to reach the GRUB menu - advance option - recovery mode .,, from there you'll few options to fix things .. 

now , you said grub doesn't load , what do you see on the scree .. do you see 

grub>; , or grub-rescue>; , or just GRUB ..

either way , here is the long fix 

[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

but even so , you should be able to boot from the live cd/usb .. to fix the partitons you'll need to use boot-repair form the live session :

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

##

i wont you to try this .. if you have any other usb devices attached de-attach it , and go to the BIOS and set the boot option order to USB , you need to move it up the order .. save & exist  and try to boot from the usb again you might need to shout down the machine ,, there is also a function key that the BIOS point you on the screen to select a boot option .. we need to know what we're working with , so please tell us the options you have for usb in the BIOS .. another thing that came to mind is , some BIOS have an option to boot for WindowsXP , and you can select the option " other " with it .. see if that is in your BIOS![URL="https://help.ubuntu.com/community/grub%20rescue%3E"]

[/URL]

---

### Post by javierdl on 2017-07-22
[COLOR=#111111][FONT=Ubuntu]Stripped it down to nothing but 1 memory stick of 2Gb, and 1 DVD player. This time it went a tad further: It loaded 2 small icons at the bottom of a purple screen, of a keyboard on the left, and a circle with a person inside on the right. Then it went to the usual blinking underscore. 
However by plugging the HDs back, I've got the Grub back. The Ubuntu choice at the top brings me right away to that blinking underscore. But going with Windows recovery, triggered an event to try to repair it.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] 
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Unfortunately it stayed showing that same message with the circling dots for over an hour. 
Could it be that the problem lies with either the motherboard, or the CPU? I mean, what else is left?[/FONT][/COLOR]

---

### Post by oldfred on 2017-07-22
The accessibility icons (the two little icons at bottom) are from BIOS boot screen of the installer, you often have to press any key to be able to add nomodeset or other boot options with f6.
Do you still have DVD/flash drive installer first in boot order and in system?

If only Ubuntu installed (or seen so far by grub), you have to hold shift key until grub menu appears. If UEFI boot you press escape key from UEFI screen, if UEFI fast boot not on. 

With either AMD or nVidia you probably need nomodeset.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by javierdl on 2017-07-22
[FONT=Ubuntu][COLOR=#111111]Ooops, looks like I had already posted that...

Thanks oldfred.
The thing is, I had already tried both "nomodeset" and "nouveau.modeset=0" with no effect.


[/COLOR][/FONT]

---

