---
title: "ubuntu won't load from HDD. How to solve it?"
date: 2015-12-30
forum: General Help
---

### Post by alex484 on 2015-12-30
I had issues with my OS and so I pulled HDD out of old PC, connected  it through USB to another PC and installed Ubuntu. It worked fine. Now I  moved the HDD over to the old PC and It won't boot (even though before formatting the disk I could boot into ubuntu). All I have now (with or without HDD/battery) is  the boot menu (please, see the image at the link), pressing enter keeps  refreshing the window. At the starting logo page it says: F2 for BIOS and F12 for boot menu, but no matter what I press (I can hear beep if I press F2 or F12 though) it takes me to the same page.

Any help to make the PC operational again is much appreciated. I'm a  silly researcher with little programming background. Please, provide  step-wise instructions.



[IMG]http://i.stack.imgur.com/W7TZH.jpg[/IMG]

  Any help to make the PC operational again is much appreciated. I'm a  silly researcher with little programming background. Please, provide  step-wise instructions.

---

### Post by oldfred on 2015-12-30
Is new system UEFI and old system was BIOS?
Did you install boot loader to external drive when on old system, or was boot loader on old systems hard drive?
That looks more like an UEFI boot menu, not grub2's boot menu.

Can you boot live installer on this system, so we can run Boot-Repair's summary report. Without lots more info very difficult to resolve issue.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by alex484 on 2015-12-30
> **oldfred said:**
> Can you boot live installer on this system, so we can run Boot-Repair's summary report. Without lots more info very difficult to resolve issue.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thank you for your reply. I can't boot anything on this PC. I can plug this PC's HDD to another PC as USB and boot from this HDD. Is it what you mean here?

---

### Post by brian-mccumber on 2015-12-30
Usually when an operating system is installed on a computer it installs software/drivers specific to that computer. The reason it will boot when you plug it into the computer you installed it from is because it was installed for that computer. Why would you install an operating system from a different computer than the one the hdd is supposed to go with? You should just use the live cd/dvd, or usb installer to reinstall the OS while the hdd is attached to the computer that will be using it. If your old computer will not boot up from Ubuntu live then there is probably a hardware problem with it.

---

### Post by alex484 on 2015-12-30
> **brian-mccumber said:**
> Usually when an operating system is installed on a computer it installs software/drivers specific to that computer. The reason it will boot when you plug it into the computer you installed it from is because it was installed for that computer. Why would you install an operating system from a different computer than the one the hdd is supposed to go with? You should just use the live cd/dvd, or usb installer to reinstall the OS while the hdd is attached to the computer that will be using it. If your old computer will not boot up from Ubuntu live then there is probably a hardware problem with it.

Thank you for the clarification. This old PC (my personal 2 years old I-7 laptop) worked just fine before (I could boot into ubuntu on HDD before I reinstalled it using this HDD and another PC - I used this approach because I could not reach BIOS to force the PC to boot from a USB) and so I exclude (but ready to test) any hardware problem. I can't boot from anything CD/USB, no matter what I plug in I get the screen you can see above. I think I have BIOS set to boot from: 1 HDD, then something else. But now I can't access even BIOS.

---

### Post by oldfred on 2015-12-30
If newer UEFI system, you  may have fast boot on in UEFI.
Fast boot setting means you do not have time to press any key to get into UEFI, but have to use Windows entry or grub entry. Best to always turn off or set a delay if dual booting.
My system allows different setting for fast boot with cold boot as normal, and warm (reboot) boot I can set a 3 sec delay so I have time to press a key.
Most systems will revert to a normal boot where system is checked for new/changed hardware and you have time to press a key, if you totally cold boot. Turn off power, remove battery if laptop, hold power switch for 10 sec or so and then boot & immediately press correct key for your system to get into UEFI/BIOS.

Some systems have a reset pin hole on bottom of laptop, some require you to jumper pins on motherboard, if nothing else works.

---

### Post by brian-mccumber on 2015-12-30
I did a little research on the Fujitsu laptops and it seems like ALOT of people have this problem with not being able to get to bios especially after hardware changes like adding more ram. If you have a usb keyboard, hook that up to your laptop and see if pressing f2 on it will take you to your bios menu if resetting the cmos like oldfred said doesn't work.

---

### Post by oldfred on 2015-12-30
Some perhaps similar systems? Have not reviewed threads lately but they may discuss issues.
Often vendor uses same or similar UEFI settings across many or all models, only difference is which options are installed.

 Some systems require password to turn off UEFI
Fujitsu lifebook ah512. Secure boot options blocked in bios - UEFI password required
[http://ubuntuforums.org/showthread.php?t=2171114](http://ubuntuforums.org/showthread.php?t=2171114)
 Fujitsu Lifebook A512 [SOLVED] Dualboot pre-installed win 8.1 and Ubuntu 14.04.1 
[http://ubuntuforums.org/showthread.php?t=2254442](http://ubuntuforums.org/showthread.php?t=2254442)

---

### Post by alex484 on 2015-12-30
@[**[COLOR=#000000]brian-mccumber[/COLOR]**]("http://ubuntuforums.org/member.php?u=1996809"). I have laptop Fujitsu Lifebook A-series, AH532/G52 (8GB RAM, I-7) the hardware is without any changes just as I bought it. I tried a usb keyboard (pressing F2 gives a beep sound, same sound I get if I press F2 on the native laptop keyboard)
@[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711"). I removed power cable from the laptop, removed battery, pressed and held the power button for 20 seconds. Then, I re-connected power and immediately pressed power button and kept F2 down (I could hear the beep). Got the same screen...

---

### Post by brian-mccumber on 2015-12-30
Well I found this guide that may help you with your particular laptop. It seems there are some pins under the ram that can be jumped to reset it so you can enter bios again.

If you want to try this fix - [http://www.linlap.com/fujitsu_lifebook_ah532](http://www.linlap.com/fujitsu_lifebook_ah532) the instructions are under **Notes:**

---

### Post by alex484 on 2015-12-31
I definitely learned something new today. Thank you very much for the awesome support! The issue was solved as suggested by [**[COLOR=#000000]brian-mccumber[/COLOR]**]("http://ubuntuforums.org/member.php?u=1996809") (the link contains very clear details).

---

