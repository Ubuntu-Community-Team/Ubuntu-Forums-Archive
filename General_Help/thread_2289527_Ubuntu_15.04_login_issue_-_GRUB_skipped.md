---
title: "Ubuntu 15.04 login issue - GRUB skipped"
date: 2015-08-04
forum: General Help
---

### Post by humanoverdrive on 2015-08-04
Hey all,

I am having a rather strange issue that is presenting me from logging in normally. I am running Ubuntu 15.04 with full disk encryption LVM.

Until this issue started, when turning on my computer,I was first presented with the GRUB screen (after BIOS, etc), and then presented with a screen where I was able to enter my LUKS password to decrypt my disk. Great.

Now when I boot up my computer, after the BIOS screen, etc, my computer skips the GRUB screen altogether and proceeds directly to the screen where I am to enter my disk encryption password.  Unfortunately, not only does this preclude me from selecting different boot options from the GRUB, but it also prevents me from being able to log in at all, do to the fact that I am unable to type ANYTHING into the password field on this page.

Strangely, if I force my computer to power off and restart my computer, on restart, the GRUB screen now appears first again! After selecting my boot option, I am again presented with the LUKS password prompt; however, this time the prompt looks quite different.  I am then able to enter my password, decrypt my computer, and log on normally.  Unfortunately, this happens EVERY time I shut down my computer, so the next time I turn my computer on, I will get no GRUB, have to force my computer to power off, and restart... every time.

I am also having another issue, which I only mention here as I think there might be some possibility that they are related.  My other issue is that the restart feature does not work.  That is, when I attempt to restart my computer, Ubuntu appears to shut down, and then the screen goes black.  My computer freezes at that point and will remain black.  I never see the BIOS screen or anything else indicative of startup, just a constant black screen after I click restart.

Here are some pictures of what I am seeing on startup:
[LIST]
[*]Initial startup (after BIOS) - Immediately presented with LUKS password screen; NO GRUB and unable to type password: [ATTACH=CONFIG]263647[/ATTACH] 
[*]Force power off, reboot 2nd startup - Presented with GRUB after BIOS (picture here shows GRUB after selecting Advanced, so as to display current kernel version): [ATTACH=CONFIG]263648[/ATTACH] 
[*]Immediately after selecting Ubuntu from the GRUB, I am presented with the  following error, "[       0.900297] ACPI PCC probe failed. starting  version 219", which is displayed for a few seconds before automatically proceeding to the LUKS password screen: [ATTACH=CONFIG]263649[/ATTACH] 
[*]After the above error message disappears, I am presented with a visually different LUKS password screen; I am able to successfully enter the password: [ATTACH=CONFIG]263650[/ATTACH] 
[*]System then boots up normally. 
[/LIST]

I should also note that if I force a shutdown BEFORE entering the LUKS password (i.e. on the 2nd startup, but before entering the password), I will be able to boot "normally", first seeing the GRUB and then the fuc*ed up LUKS password screen I am showing in the 4th picture.


Any suggestions on what is going on and how I might go about fixing this? It's getting to be a real pain having to start my computer twice every time I want to boot up, haha.

Thanks!

---

### Post by oldfred on 2015-08-05
I do not know LVM nor encryption.

But is system UEFI or BIOS.

It is normal with only one install to not have grub menu. It knows you only want to boot the one installed system. 
Menu only shows if shut down was not normal as it sets a flag. And you never should force shut down with power switch.

You can get menu by holding shift key from BIOS until menu appears. 
Or if UEFI then you use Escape key usually several times.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by humanoverdrive on 2015-08-05
> **oldfred said:**
> But is system UEFI or BIOS.

As mentioned in my previous post, it is BIOS.

> **oldfred said:**
> It is normal with only one install to not have grub menu. It knows you only want to boot the one installed system. 
Menu only shows if shut down was not normal as it sets a flag. And you never should force shut down with power switch.

Not on any Ubuntu machine I've ever had. Every machine I've ever had, the GRUB would always appear on startup. My current machine used to do that before things started going wonky.

> **oldfred said:**
> 
You can get menu by holding shift key from BIOS until menu appears. 
Or if UEFI then you use Escape key usually several times.

This issue is occurring AFTER BIOS has started loading the OS, so I am no longer in BIOS when this issue occurs. The issue is occurring on the LVM disk encryption password screen, so that BIOS menu key sequence no longer works at that point.

---

### Post by oldfred on 2015-08-05
The shift key or escape key are grub menu keys that are seen by grub just after BIOS. Then that will show a menu.
There are grub settings to always show menu, but default with one install is to not show menu and with multiple boot always show menu.

You may be seeing a difference between a text boot where it asks for pass phrase or the gui boot?

---

### Post by humanoverdrive on 2015-08-05
> **oldfred said:**
> The shift key or escape key are grub menu keys that are seen by grub just after BIOS. Then that will show a menu.

Ok, but that still doesn't help because the GRUB never loads. I have tried all sorts of key combos on the frozen LUKS password screen (see the 1st image i posted in my first post), but my system becomes completely unresponsive at that point until I force a reboot.

> **oldfred said:**
> You may be seeing a difference between a text boot where it asks for pass phrase or the gui boot?

It does look like it might be a text boot when it finally works the 2nd time (see the last image i posted in my first post).

---

### Post by humanoverdrive on 2015-08-05
Also, I just tried Alt+SysRq R-E-I-S-U-B, and while this combo DID get me out of the LUKS password screen, it just brought me to a black screen with a blinking cursor, and this new black screen is also totally unresponsive. I can't type anything, holding shift doesn't open the GRUB... it's just stuck

---

### Post by oldfred on 2015-08-05
You have to press shift right after or at end of grub. Once it starts booting then the grub key will not work. 
Did you change grub timeout? Some users want it less than the standard 10 seconds, but if set to 0 you cannot get into grub menu. I set mine to 3 seconds, but then have to be quick if I want menu.

I would also remove quiet splash and add nomodeset on Linux line.

You an also press down arrow key. Grub remembers keys and that will change to the second entry in menu or recovery entry. But again has to be after BIOS but before grub has launched boot.

---

### Post by humanoverdrive on 2015-08-05
> **oldfred said:**
> You have to press shift right after or at end of grub. Once it starts booting then the grub key will not work.

You are not understanding me. The GRUB screen NEVER loads the first time i boot up, it skips straight to the unresponsive LUKS password screen. It goes straight from BIOS to the password screen without ever opening the GRUB. As for the GRUB timeout, I have not changed it at all as far as I know. How would I go about checking the timeout length? I feel like that probably isn't the issue though as I don't see how that could effect my ability to enter my LUKS password

---

### Post by oldfred on 2015-08-05
I said grub and meant BIOS. If grub still at default you should have 10 sec after BIOS until it auto boots.

You have to boot live installer to get into your system. Easier to add Boot-Repair and run its report as it will show all sorts of configuration and settings.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

