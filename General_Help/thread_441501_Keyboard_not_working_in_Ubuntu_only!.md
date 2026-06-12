---
title: "Keyboard not working in Ubuntu only!"
date: 2007-05-12
forum: General Help
---

### Post by redsp1der on 2007-05-12
Help,

Just today my keyboard stopped working for Ubuntu. It works fine during booting, on the GRUB menu and in Windows.

Once I get to the Ubuntu login screen, nothing. I tried booting to two different kernels and even into safe mode but Ubuntu is not registering any  input from my keyboard.

I also tried moving it to different usb ports and rebooting but it didn't help either.

Everything was working fine yesterday and I haven't updated or changed anything.

---

### Post by redsp1der on 2007-05-12
Ok, I just pulled out an old PS/2 keyboard and it works.
So, I guess for some reason Ubuntu has decided it doesn't like USB keyboards anymore.

This is so frustrating. If I had updated or fiddled with something I could be mad at myself for screwing something up but to just stop working out of the blue, why?

I need my keyboard back. please help.

---

### Post by eurgain on 2007-05-12
Did you change ANYTHING AT ALL between the boot following which your keyboard last worked and the boot following which it did not?

I mean ANYTHING AT ALL --  software, hardware, you name i!  It is far more likely down to something that you changed than a random event!

Pre-boot, many BIOSes cause a USB keyboard to emulate a PS/2 keyboard, but then drop this emulation once they hand over to the OS.  Some BIOSes have an option to maintain this emulation, even after handover.  It tends to be controlled by an option in the BIOS setup called something like "Legacy USB emulation".  If you turned this off, it is possible that the installed OS is now confused, since it is used to dealing with a USB keyboard that pretends to be a PS/2 keyboard.

A

---

### Post by redsp1der on 2007-05-12
I don't think I was did anything yesterday except surf the net.

The last thing I remember along those lines was an update I think it was for automatix2 yesterday or the day before but I pretty sure the system had been shut down and restarted a couple times since that update w/o a problem.

If I plug the PS/2 keyboard and boot into Ubuntu is there any diagnostic stuff I could do to see what the problem might be?

I haven't touched my BIOS in quite a while. I am going to go take a look at it.

This USB keyboard is new but I have been using it for a couple of weeks just fine.

---

### Post by redsp1der on 2007-05-12
I looked at my bios and I found options for:
USB EHCI Controller
OnChip USB
USB Keyboard
USB Mouse

They were all enabled and I am sure I have never touched those options anyway.

---

### Post by eurgain on 2007-05-12
I wonder why you are apparently rebooting the machine so often.  Do you have some problems with instability?

IME, the only reason to reboot is because of an unmissable kernel update or because the electricity has failed!

A

---

### Post by redsp1der on 2007-05-12
For one, energy is expensive. I don't like having PC using 100 watts of power all day if Im not using it.
I tend to turn on my PC when I need it and turn it off when I am done. the fact that it eats 10 watts of power even when its turned off bothers me enough.

Also, I decided to play a game in windows so I have to switch back and forth on occasion.

Otherwise, my system has been quite stable.

---

### Post by strabes on 2007-05-12
Plug both of the keyboards in at the same time, log into ubuntu, run "lsusb" and paste the output here.

---

### Post by eurgain on 2007-05-12
> **strabes said:**
> Plug both of the keyboards in at the same time, log into ubuntu, run "lsusb" and paste the output here.

Good idea!

You could also do:

# tail -f /var/log/messages

then plug and unplug the USB keyboard to see whether the USB subsystem recognises it.

That you said you used Windows to play a game almost counts me out on this one.  The OS can have access to the BIOS, and I really have no idea whether Windows allows user-space programs to access the BIOS - it could do but it would be very stupid if it did.

I have no experience of using machines that have Windows installed, and running Windows certainly falls well within my question about did you do ANYTHING AT ALL between boots.

Post the source code of Windows here, and we may be able to give you a definitive answer ... 

... in a while  ;-).

A

---

### Post by redsp1der on 2007-05-12
I entered "lsusb" into the terminal and all I get is a blinking cursor. There is no output.

FYI, this keyboard is the only USB device I use. My mouse is USB but I use the PS/2 adaptor it came with.

---

### Post by redsp1der on 2007-05-12
I tried "# tail -f /var/log/messages"

and nothing happend except when I un/replugged the keyboard its LED lights did not come back on.

---

### Post by redsp1der on 2007-05-12
I didn't think about it before but one of the last things I remember doing yesterday was uninstalling and reinstalling my antispy/virus and firewall to update it in Windows.
I didn't mention it before because I trying to think of what i was doing in Ubuntu.

Reinstalling those apps in Windows wouldn't effect Ubuntu would it?

Jeez, I can feel it coming. I'm going to have to completely reinstall Ubuntu and rebuild the whole thing because of a KEYBOARD.

---

