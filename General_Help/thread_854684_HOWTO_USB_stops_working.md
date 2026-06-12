---
title: "HOWTO: USB stops working"
date: 2008-07-09
forum: General Help
---

### Post by lisati on 2008-07-09
One topic that crops up from time to time in these forums is what to do if devices connected by USB stop working when the computer has been turned on for a while, but come right when the computer is rebooted.

The following solotuion is what I used when my USB mouse and USB keyboard worked fine at startup but stopped working after a while. I have successfully used it on a Toshiba A100 laptop running Ubuntu 7.04, a.k.a. "Feisty".
[I][SIZE="3"][B]
Disclaimer:[/B] The success (or otherwise) of the following solution will depend on your hardware and possibly which version of *buntu you are using. For example, starting from version 9.10, Ubuntu uses grub2, which does not use menu.lst [/SIZE]
Feel free to add your feedback to this thread and alternative solutions.
[/I]


[LIST=1]
[*]From a terminal, type ```
gksudo gedit /boot/grub/menu.lst
``` You will be asked for your password - don't worry if your password doesn't show, this is normal. Just type in your password as usual, and it will be accepted.
[*]When the editor opens, scroll down to the line which reads > # defoptions=quiet splash and change it to read ```
# defoptions=quiet splash acpi=force irqpoll
```
[*]Save the file, exit the editor
[*]From the terminal, type in ```
sudo update-grub
```
[*]Restart your computer.
[/LIST]

---

### Post by fedex1993 on 2008-07-11
this probley should go in tutorial section of the forums. Cool guide thoe.

---

### Post by yetihehe on 2008-07-23
I have better problem. When I work for a moment, usb mouse hangs. But everything still work's ok. When I try to unplug it and plug it in back, I only have message in dmesg about unplugging mouse (nothing else, no errors). When I plug it back, it doesn't have power. I tried plugging other mouse in other usb ports, but it looks like after this first unplug no mouse will get power from usb (they only flash for very short moment and then nothing, also nothing new in dmesg). All this time other usb devices (keyboard and bluetooth) work ok. I tried noapi, acpi=force, irqpoll, pci=nomsi and all_generic_ide in all combinations, but to no avail. It started today, yesterday computer was working for the first time with new motherboard (and graphics) without any problems for full day. I attached dmesg, lsmod and lsusb. In dmesg I cut some lines of errors from sde disk, "these are not errors you are looking for", this is just second disk of my raid0 array acting funny, it still works ok). Does anybody have any ideas I could try?

---

### Post by yetihehe on 2008-07-27
Solved. It looks like AMD Cool'n'Quiet has issues with cpu frequency changing, which may corrupt usb devices. Disabling it solved problem (it started when I disabled boinc for a moment, less cpu utilisation - mobo lowered frequency). Motherboard asus m3m-hd/hdmi with nforce 750a chipset.

---

### Post by geclos on 2008-09-23
My USB Mouse also freezes in the screen.

everything works except the pointer. 

I also have the IO APIC bug problem i supose that must be a relation between both problems.

My motherboard is an asus p5nsli

please someone can help i really need linux to work in the university...

please give me ideas.

thanks

---

### Post by kokkus on 2008-09-23
I typed it in the terminal but all I got was a blank (brand new document).
Any solution?

---

### Post by Liametc on 2008-10-01
yeah followed the steps, really easy thanks. 
thought id solved it until a second ago when the keyboard and mouse froze again! 

i dont think hard restarting is doing my computer any good. this is bloody annoying!

---

### Post by rebeltaz on 2009-12-06
> **lisati said:**
> ```
gksudo gedit /boot/grub.menu.lst
```

I know that this is an old thread, but shouldn't this read: 

```
gksudo gedit /boot/grub/menu.lst
```

with a '/' between grub and menu instead of a '.' ?

---

### Post by lisati on 2009-12-10
> **rebeltaz said:**
> I know that this is an old thread, but shouldn't this read: 

```
gksudo gedit /boot/grub/menu.lst
```

with a '/' between grub and menu instead of a '.' ?

Well spotted, fixed.

N.B. Won't work with grub2 as installed with 9.10, which uses a different format for its options

---

### Post by rebeltaz on 2009-12-10
> **lisati said:**
> Well spotted, fixed.

N.B. Won't work with grub2 as installed with 9.10, which uses a different format for its options

:guitar: 

So how do you do you do this in grub2?

---

### Post by lisati on 2009-12-16
> **rebeltaz said:**
> :guitar: 

So how do you do you do this in grub2?

No idea. I've still got Jaunty.

---

### Post by rebeltaz on 2009-12-17
> **lisati said:**
> No idea. I've still got Jaunty.

That's OK... Actually the problem was with the BIOS. I am running this on a Dell Dimension E520. From a DOS boot disk, I ran the BIOS update from the Dell web site and I have not had a single problem since. So if anyone else with an E520 has a similar problem - upgrade your BIOS.

---

### Post by forestwalker101 on 2010-01-18
> **lisati said:**
> One topic that crops up from time to time in these forums is what to do if devices connected by USB stop working when the computer has been turned on for a while, but come right when the computer is rebooted.

The following solotuion is what I used when my USB mouse and USB keyboard worked fine at startup but stopped working after a while. I have successfully used it on a Toshiba A100 laptop running Ubuntu 7.04, a.k.a. "Feisty".
[I][B]
Disclaimer:[/B] The success (or otherwise) of the following solution will depend on your hardware and possibly which version of *buntu you are using. Feel free to add your feedback to this thread and alternative solutions
[/I]


[LIST=1]
[*]From a terminal, type ```
gksudo gedit /boot/grub/menu.lst
``` You will be asked for your password - don't worry if your password doesn't show, this is normal. Just type in your password as usual, and it will be accepted.
[*]When the editor opens, scroll down to the line which reads  and change it to read ```
# defoptions=quiet splash acpi=force irqpoll
```
[*]Save the file, exit the editor
[*]From the terminal, type in ```
sudo update-grub
```
[*]Restart your computer.
[/LIST]


I have a very similar problem but when i type in the first line of code above i just get a blank editor window.

---

### Post by stanleytberry on 2010-03-13
Please.

I just installed 9.1 desktop on an old Compaq laptop on which a USB mouse worked with W2K.  Now it doesn't work.  How do you do this with GRUB2?

Thanks.

---

### Post by rebeltaz on 2010-03-15
> **forestwalker101 said:**
> I have a very similar problem but when i type in the first line of code above i just get a blank editor window.

menu.lst is not used on GRUB2...

---

### Post by lisati on 2010-03-15
> **rebeltaz said:**
> menu.lst is not used on GRUB2...

+1. I've added a note in the first post to the effect that starting with 9.10, Ubuntu uses a new version of grub.

---

### Post by stanleytberry on 2010-03-19
OK.  Installing 9.10 desktop from the live CD on an HP/Compaq nc6000:

1) if I click install from the first screen, and plug in a USB mouse and/or keyboard AFTER the install is complete and it's rebooted from the installed system, the USB mouse and/or keyboard DO NOT work ... but a USB drive does work
2) if I run from the CD and install from within the running 9.10, and plug in a USB mouse and/or keyboard AFTER the install is complete and it's rebooted from the installed system, the USB mouse and/or keyboard DO NOT work ... but a USB drive does work
3) if I first plug in a USB mouse and/or keyboard and install from the first screen, the USB mouse and/or keyboard DO NOT work ... but a USB drive does work
4) if I first plug in a USB mouse and/or keyboard and then run from the CD and install from within the running 9.10, the USB mouse and/or keyboard WORK both before and after booting from the installed system

This resolves my problem.

---

### Post by nomalab on 2010-10-13
> **rebeltaz said:**
> So how do you do you do this in grub2?

With Grub2 the file to edit is /etc/default/grub.

1. From terminal type:

```
gksudo gedit /etc/default/grub
```2. Scroll down to a line which reads:
> 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"and change it to read:```


GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force irqpoll"
```3. Save the file, exit the editor.

4. From the terminal update Grub configuration by typing:

```
sudo update-grub
```5. Restart your computer

---

### Post by nomalab on 2010-10-13
Happy to report that adding "acpi=force irqpoll", as suggested, seems to have solved the problem on my Toshiba Satellite Pro L100. 1 hour from reboot now and USB mouse is still working (usually dies after 10 minutes or so). I was also able to format a USB memory stick with GParted, unplug it, plug it back in... 

Thank you, lisati!

---

### Post by JuliusRaphael on 2010-10-17
Hi I also have the this problem and I've tried what you wrote but I didn't work. I figured if I post all of my grub file maybe you can find something that is wrong with it:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force irqpoll"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"





Hopefully you can help me, I just installed Ubuntu last night and haven't got time to start playing with due to this issue. 
Thank you / J

---

### Post by nomalab on 2010-10-18
> **JuliusRaphael said:**
> Hi I also have the this problem and I've tried what you wrote but I didn't work.

I noticed from another thread that you managed to solve it:

> **JuliusRaphael said:**
> My problem solved when I updated the bios.

Do you still have the "acpi=force irqpoll" bit in Grub configuration? Are things working if you remove those (now that you have updated the BIOS)? Just curious, that information could help someone else.

---

### Post by TNT1 on 2010-10-18
I have this problem with usb like this, but I have discovered it is only when I plugin mmy blackberry to charge it. Seeing as I hate the bastardberry with a passion the isuue was simple to resolve, I intentionally bricked the BB, and took it back to the service provider and swapped it for a Nokia.

---

