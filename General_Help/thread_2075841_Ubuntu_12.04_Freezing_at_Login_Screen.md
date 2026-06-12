---
title: "Ubuntu 12.04 Freezing at Login Screen"
date: 2012-10-24
forum: General Help
---

### Post by Hx1349 on 2012-10-24
Ok I installed ubuntu 12.04 x64 on my Toshiba Satellite C655D (AMD e-300 APU / HD6310 graphics. 4GB ram) I dual boot it alongside windows. When I get to the login screen, my computer will completely freeze, and all I can do is a hard reset. Sometimes I will be able to log in, but within 10 seconds after logging in, I will end up completely freezing again, and the only option is a hard reset. I've tried installing GDM as the login manager (or whatever it is) have tried doing ctrl alt f1 at the login screen, and even then, it freezes after a few seconds, and I've also tried booting with nomodeset / acpi off. The drivers I have installed are the FGLRX proprietary ones if that helps, on a previous installation, the default drivers were installed, and i would still run into problems with freezing.

The only solution I have been able to find is by booting into windows, and then doing a reboot (not shutting down) and booting into ubuntu, but even then, that is not a worth while solution. Just for the note, I have reinstalled ubuntu 12.04 a few times after running into the same error countless times. I even tried an xubuntu version, and 12.10, all of which give me the same annoying problems, sometimes even booting from the live CD's / USB causes me to freeze and end up at a hang.  

Really find this frustrating since I've been playing around with ubuntu since 9.04 was released, and even with newer versions, I still always run into tons of bugs and instability's. Anyone have a solution?  Im posting this because i've searched and asked on other forums, and none of them solve my problem.

---

### Post by sienile on 2012-10-24
Run memtest at boot. Sounds like you have some bad RAM.

---

### Post by Hx1349 on 2012-10-24
> **sienile said:**
> Run memtest at boot. Sounds like you have some bad RAM.

i'm more than positive that it's not bad ram, or related to ram period.  this computer isn't even 6 months old yet, and i've never had one problem with microsoft windows.  the thing is, it only lets me login to ubuntu when i first boot into windows and then restart the computer.  if I shutdown, or turn the computer on and try going  into ubuntu, it will just freeze within 15 seconds of being at the login screen.

just for the note, i've ran memtest once before, and there were no issues, for either of the sticks of ram.  so as i said, it can't be the ram that is causing this problem.

---

### Post by bvt on 2012-10-25
I'm having a similar problem.  Started with some 12.04 update.  I tried to reinstall 12.04, and installed 12.10 and Mint 13.  Sometimes I can open a new window, but only the terminal is useful.  No windows can be moved around.  I know its not my computer as I have made a dual boot and Windows 7 works perfectly.  I made sure my ATI graphics drivers were up to date, and also have a GTX 550 TI Nvidia card.  If I install Nvidia current, I can't even get a Ubuntu splash screen.

Until something is fixed, I'll be a reluctant Windows guy.  


MSI 880GM-E43 Motherboard with AMD Athlon X4 640, 8 Gig Ram

---

### Post by Hx1349 on 2012-10-26
> **bvt said:**
> I'm having a similar problem.  Started with some 12.04 update.  I tried to reinstall 12.04, and installed 12.10 and Mint 13.  Sometimes I can open a new window, but only the terminal is useful.  No windows can be moved around.  I know its not my computer as I have made a dual boot and Windows 7 works perfectly.  I made sure my ATI graphics drivers were up to date, and also have a GTX 550 TI Nvidia card.  If I install Nvidia current, I can't even get a Ubuntu splash screen.

Until something is fixed, I'll be a reluctant Windows guy.  


MSI 880GM-E43 Motherboard with AMD Athlon X4 640, 8 Gig Ram

yeah, i've looked all over google for solutions to this problem, and each given solution just doesn't work or explain how to fix the problem or what causes it.

i've also tried running backtrack 3 and backtrack 5 on my computer, and it just won't work, it ends up hanging during boot.  

im guessing this has to be a bad lack of hardware support / driver support, if windows runs fine..

---

