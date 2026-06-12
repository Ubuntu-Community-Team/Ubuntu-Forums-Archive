---
title: "Strange Problem with Rebooting"
date: 2008-01-22
forum: General Help
---

### Post by neonpep on 2008-01-22
Hello, all.  I have a Toshiba Satellite A215-S4697 with a fresh copy of Gutsy installed on it.  I've got everything working, but the computer hangs when I reboot.  The laptop boots into Ubuntu fine from a cold boot, but if I reboot once it's running, it won't come up again.  I've searched the forums and didn't find anything like this.  Does anyone have any ideas why it boots fine from a cold boot, but not a reboot?

System Specs:
AMD Turion 64 x2
1 GB RAM
Fujitsu MHW2160B HDD
ATI Radeon X1200 Mobile
Ubuntu 7.10, 32-Bit Version

---

### Post by mikelito on 2008-01-22
do you have an ATI card and youjust installed the new 8.01 closed-source driver?

---

### Post by neonpep on 2008-01-22
I do have an ATI card (Radeon X1200), and I've installed xorg-driver-fglrx and xserver-xorg-video-ati from the repositories.  I should also clarify that my laptop hangs after the reboot, not before.  So, I'll see my Toshiba BIOS splash screen and everything, but instead of getting to where I can log in, it's just a black screen with a blinking cursor in the upper left corner.

---

### Post by simplysimple on 2008-01-23
i have the same issue...and also have the ati x1200. I tried running the new 8.1 catalyst driver and had great luck with frame rate in games but overall reverted back because it was buggy running virtual OS in virtualbox and also hung not only on bios but when rebooting or even logging out.

do you have  the io-apic error and cannot allocate resources 7/8 error on boot?

also what version is your bios....I upgraded to the 1.2 before ditching vista and switching to gutsy 64 i have a feeling that some of my issues reside with this bios upgrade. 

who knows...

---

### Post by mikelito on 2008-01-24
it seems neonpep doesn't have the issues due to the buggy 8.01 driver.

however in your case you might try the workaround on phoronix, I reported it into the forums at
[http://ubuntuforums.org/showthread.php?p=4183534](http://ubuntuforums.org/showthread.php?p=4183534)

cheers
m

---

### Post by simplysimple on 2008-01-24
Thanks for the reply...will try it out when I get home. /*fingers crossed*/

Let you know how it goes.

---

### Post by neonpep on 2008-01-24
Thanks for the suggestions, I'll check out that workaround.  As for my BIOS, my Satellite has BIOS v1.40 on it.  In a new development, I did notice something else with my problem in particular...the computer appears to hang after reboot with a blinking cursor, but if I leave it alone for about 5 - 10 minuts, it seems to try booting off a network (PXE boot).  It does this even after disabling network boot in the BIOS.

---

### Post by simplysimple on 2008-01-24
attempted the workaround over lunch...

i was able to stop atieventsd  running

  sudo /etc/init.d/atieventsd stop

but was unable to prevent it from loading at startup using the command

sudo for a in /etc/rc*/S*atieventsd; do mv $a ${a%???atieventsd}s${a#*rc?.d/s} done

error returned 

bash: sytax error near unexpected token 'do'

nonetheless i tried logging out since i had at least stopped it for the current session but alas it hung on log out and I was forced to power off manually

any suggestions would be greatly appreciated...if not I'm going to revert back to the proprietary driver

thanks for the help!!

---

### Post by neonpep on 2008-01-25
Well, I was fooling around with boot options and I added "noioapic" to my kernel boot options in /boot/grub/menu.lst  That seemed to do the trick (although I wasn't even aware that "noioapic" was even a valid option)!  I can now reboot my laptop without it hanging after showing the BIOS splash screen.  Thanks to all who made suggestions!

---

