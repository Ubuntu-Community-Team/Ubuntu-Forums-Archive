---
title: "why occasional kernel panic at boot?"
date: 2015-08-18
forum: General Help
---

### Post by yoshii on 2015-08-18
EDIT:  Solved--> [http://ubuntuforums.org/showthread.php?t=2291176&p=13375302#post13375302](http://ubuntuforums.org/showthread.php?t=2291176&p=13375302#post13375302)
[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

Occasionally when I boot up my laptop with Ubuntu Studio v14.04.3 I get a kernel panic and have to hard poweroff the computer.  It then runs OK on the second try, but a few times it started up with fsck doing a repair.  
Is this normal behavior for a system?  I have no idea where to look for issues or to fix it more.  Sometimes I can go for several weeks without issues.  Is it just hardware fussiness of the laptop?...like bad IRQ's shuffled around each time?  After successful bootup, usually everything is fine.  But I did notice Firefox crashing on startup lately too.  But not every time... wierd.  

Thanks in advance.  

EliteBook 6930p 4 GB RAM.

---

### Post by dino99 on 2015-08-18
some times ago i got such issue also; and it took lot of time to thing about the ram voltage that was set on 'auto' into the bios; setting it manually to the recommended voltage for the ram model (setting hidden on that ami bios: need to set first the cpu voltage on 'manual' to see the ram voltage setting; indeed i've not tweaked the cpu voltage.)
and now i never get a kernel panic; before i was getting one at each cold boot.

---

### Post by Bucky Ball on 2015-08-18
*Thread moved to **General Help**.*

You might like to have a look at the setting dino99 talks about. Your issue can also be a sign of failing hardware, generally RAM or hard drive.

If you have more than one stick of RAM you can experiment by taking one out and booting with the other one only a few times. If all good, swap the sticks and try with the other. If still all good, probably not the RAM. You can also choose to run a memtest at boot. Be prepared, it takes awhile to complete. Sometimes a loooong while.

---

### Post by yoshii on 2015-10-19
I read this to get some ideas for solutions:  [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

OK, today I started getting Kernel Panics again and I did some research on the effects of disabling HyperThreading or disabling ACPI.  My BIOS doesn't let me change any of the settings Dino99 was talking about nor related settings.  But I am able to disable ACPI or all of ACPI except HyperThreading in the Grub2 settings and also in menu.lst which I use with Grub4DOS (from Puppy Linux).  

Right now I use Grub4DOS as a boot menu and when I boot into Puppy Linux I never get kernel panics.  But sometimes I do with Ubuntu Studio which is my default bootup menu item.  So what I did was append " acpi=off" to the kernel command line within menu.lst .  I also tried " acpi=ht" as an alternative which didn't harm anything, but didn't help.  Similarly, I tried these types of settings in the Grub2 config.  

I ended up with this:  

...
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off"
...

I got rid of the "quiet splash" option because I like to see the text based boot up which Grub4DOS does by default.  In Grub4DOS, this usually means that I can see all the initial commands during boot up instead of the splash screen and errors are shown too.  But Grub4DOS is different from the Grub2 config and seems independent from it.  Also Grub4DOS is only available from within PuppyLinux LiveCD's and this isn't a common thing for Ubuntu users necessarily.  But I keep a partition of PuppyLinux handy in case Ubuntu fails and I need a way to troubleshoot the system.  I also keep the LiveCD handy.  

Anyways, disabling all of ACPI except for HyperThreading still didn't fix everything, but disabling ACPI entirely does allow the system to boot smoothly and it also disables HyperThreading by default.  
I have read that this can make a system possibly slower yet cooler.  Also I read that this can enable some really old programs to become compatible if they weren't compatible with HyperThreading systems.  
Also, I read that this doesn't mean that ACPI doesn't work, it might instead mean there's a problem with something else in the BIOS I guess(?).  The info was in here:  [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

i also downloaded Boot-Repair in case I ever need that.  

Anyways, the problem is solved for now I hope.  I just need to make sure that my audio programs aren't too slow and if they are, how to use them differently to get decent results.  
My computer is an old Core2Duo from around 2010.
[B]
IMPORTANT:  Oh... one other thing... from reading doing in terminal:   dmesg > results.txt
I opened up results.txt in gedit and saw a BIOS error happening and the error message recommended disabling PNPBIOS so I did that too within menu.lst for Grub4DOS.  
> 
0.145515] pnp: PnP ACPI: disabled
[    0.145557] PnPBIOS: Scanning system for PnP BIOS support...
[    0.145606] PnPBIOS: Found PnP BIOS installation structure at 0xc00f9f10
[    0.145649] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9f3e, dseg 0xf0000
[    0.145695] PNPBIOS fault.. attempting recovery.
[    0.145736] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[    0.145784] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[    0.145833] PnPBIOS: Check with your vendor for an updated BIOS
 [/B]

There are not BIOS updates available for my system as far as I know.  I think I tried that already.  
The other caveat of disabling ACPI is that some software interfacing to power functions isn't there, but that's alright with me.

---

### Post by Bucky Ball on 2015-10-19
Did you try the suggestion in the output and also add 'pnpbios=off' to the kernel line? Unsure what other effects that may have apart from a more stable system, of course ... :-k

---

