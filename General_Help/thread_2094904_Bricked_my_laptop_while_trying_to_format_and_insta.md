---
title: "Bricked my laptop while trying to format and install Ubuntu 12"
date: 2012-12-15
forum: General Help
---

### Post by davejonesbkk on 2012-12-15
So I wanted to format my old laptop which used to have Ubuntu 10 on it and Windows 7 (32 bit I think).

I downloaded the latest version of ubuntu and set it up to boot from a USB drive. I then booted from the USB drive, as I wanted to remove everything from my laptop I choose for the old Ubuntu 10 and Windows 7 to be removed and a fresh install of Ubuntu 12 to be setup, everything ran perfectly during the setup, I created my username and pw etc etc, then at the end it said I needed to restart which I did. After it restarted it froze on a startup screen showing Acer and F2 <setup> and F12<boot options>, I waited and waited, nothing happened, tried both the options, again nothing.

I then manually switched it off and tried again, same thing, tried another time with the USB stick removed, still nothing. By now I realised that something had gone wrong, I couldnt get off this screen and the laptop wasnt booting from the USB drive or anything so I grabbed my old Win7 disc to attempt to boot from that and install it, DVD drive wont open, nothing happens when I press the button.

Im out of options here, can anyone help? Would be much appreciated as I need to go away soon and must have access to a laptop :(

My Laptop:

Acer Aspire
Intel i3
2GB RAM

Prior to this it had the following OS:

Ubuntu 10
Win 7 - 32 bit

---

### Post by scbingham on 2012-12-15
You can manually open you dvd drive.

Near the eject button there should be a small hole.

Straighten a paper clip & push it into the hole & push against the mechanism. This should open the drive.

Hope that helps.

---

### Post by davejonesbkk on 2012-12-15
Thanks, that worked, however I just tried to boot with the Win 7 CD in and still the same screen comes up :(

---

### Post by Squirty on 2012-12-15
Have you tried installing again using usb drive? 
Possibly boot priority needs to be set to hard drive.
"Computer freezes on a startup screen": is it still possible to access setup or boot options? If that's the case, you can also startup using a ubuntu live cd..

---

### Post by jerome1232 on 2012-12-15
Shot in the dark, when my laptop got really weird on me, removing the battery for several seconds often fixed the weirdness.

---

### Post by davejonesbkk on 2012-12-15
I have tried restarting the computer with the USB drive with ubuntu boot files on which I used first time and its still the same. Same also even if USB not plugged in, nothing happens when I press F2 or F12...

I will try removing the battery also

---

### Post by Mark Phelps on 2012-12-15
Know it's a bit late, but this experience is one of the main reasons you should NEVER force a new Ubuntu version onto a laptop -- without first trying it in LiveCD or LiveUSB mode.

Version 12.10 introduces lots of changes over version 10.x -- some of which could very well be incompatible with the hardware in the laptop.

Also, Win7 is way too large to fit on a CD, so if it really is a CD, and it came with the laptop, then unless you made an image backup of Win7, or had an option to make a set of restoration DVDs, and did that, you will most likely have NO way to get Win7 back.

The forum is here to ask about these things BEFORE you go charging ahead and brick a machine!

---

### Post by Impavidus on 2012-12-15
Concerning laptops that don't get past the screen with the manufacturers logo, this remarkable solution came around here a few days ago: [http://ubuntuforums.org/showthread.php?p=12401315](http://ubuntuforums.org/showthread.php?p=12401315)

---

### Post by davejonesbkk on 2012-12-16
Tried removing the battery and everything now, nothing works.

Sorry I meant Win7 DVD not CD

What are my options now? Would a PC repair shop be able to do something?

---

### Post by pbrane on 2012-12-16
Installing an OS shouldn't 'brick' your laptop. It would be very rare these days for the kernel to mis-identify hardware to the point that it damages it. It sounds like your harddrive may have failed. You could try removing the harddrive and booting from the USB or DVD just to see if that works. It could also be RAM, If you have more than one RAM chip remove one and try that. then remove the other one. If you remove both you may still be able to proceed to the BIOS/EFI setup, that will tell you something. It could even be the DVD drive, if it's removable try that. The fact that it appears to hangs during POST makes it seem like a hardware issue, not software. I'm pretty sure the laptop is repairable, although it may cost you some money.

Did you try the 'cold finger' reset method? I have had that work for me.

In addition you may try removing any device that is removable to see if that is the culprit. Like Bluetooth, wireless or other plugin device.

---

