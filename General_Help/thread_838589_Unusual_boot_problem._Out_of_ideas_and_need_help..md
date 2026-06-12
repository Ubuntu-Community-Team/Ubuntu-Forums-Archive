---
title: "Unusual boot problem. Out of ideas and need help."
date: 2008-06-23
forum: General Help
---

### Post by SeTZerA on 2008-06-23
Hello everyone, 
I'm new to the forums, and new to linux too, used it for about a week but I'm not new to computers at all so this boot problem is a little odd to me, I figure I may just be missing some drivers or have some incompatable hardware for ubuntu 8.04.  Heres what I have so far:

My problem is that Ubuntu will not fully boot on this machine;
2500+ AMD Athlon XP (1833mhz), 512 RAM, AGP Geforce 5200 FX, and integrated AD1980 6 channel SoundMax audio (AC97 codec). with 3 HDD's installed, Ubuntu HD (6.4 gb) as primary slave.

 yet it will work in my other 2 older test machines fine. I've had it running on an older IBM system with a pentium 3 (733mhz), it boots up fine, uses integrated VGA and sound, and I've had no problems with it at all. It also runs on an older 1100 AMD Athlon XP pc with integrated VGA and sound.

On the machine I want it to run on (this one) it used to hang on the Ubuntu logo load screen with the orange bar, but now it doesnt, it gets passed that, and goes to the part where it starts with "Reading files needed to boot" etc. and gets stuck in 2 places.

The first, right after "PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level,low) -> IRQ 18" It shows me the following error message:

ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build-generic/sound/alsa-driver/pci/via82xx.c:581 : codec_read: codec 0 is not valid [0xfe0000]  (times 4, then halts)

Now I did look this up, and it has to do with my audio driver, which works fine for windows (though I had to install it manually for XP), the alsa-project.org site doesnt list the driver/codec for my system, so I disabled the Audio/Modem controllers in my BIOS, which stopped this message...however, problem #2 is:

Even after that, my system will continue on until "Starting bluetooth" and displays upto the point where it says:
"Bluetooth RFCOMM ver 1.8
NET Registered protocol family 17"

And from there all I can do is type things in, but nothing does anything at all, the system is completed brainless. I Control+Alt+Delete to reboot, but nothing else works.

I dont think the hang has to do with the audio, though I might want to fix that too if I end up with no sound when it finally boots, but I need some help as to what I can do to get it working on this pc, I dont get why it just boots right up on the older systems without any problems or hang time.  

Well, thank you for your time, I'll be back shortly to see what can be done :)

---

### Post by pytheas22 on 2008-06-23
Do you have any bluetooth devices?  If so, try unplugging them and see if it still hangs.  In fact, try unplugging everything you don't need...wireless cards, printers, everything except keyboard, mouse and monitor...and see if the problem still occurs.

If it does, we can figure out which module it's loading (must be related to bluetooth) that makes it hang, and prevent it from loading.  But hopefully it's simpler than that.  Either way, once we know more specifically where the problem lies, we can figure out a real solution for the audio and everything else.

---

### Post by SeTZerA on 2008-06-23
Hey pytheas22, 
Sorry about the late reply, I got your message about 15 minutes after you posted, and.. you were right, I had a USB Video capture device plugged in the back of this pc, the only non-essential device, and once I unplugged it, ubuntu loaded up with sound and all!  I should've known it was something simple like that, dont know why it was under bluetooth, but I really appreciate the help, thank you! :)

Once I find the "thank poster" feature this forum has, you'll be sure to get it!

---

### Post by pytheas22 on 2008-06-24
No problem and thanks for the thanks.  If you want to use the USB device that was causing the problem, provide more information about it and we can figure out why Ubuntu has problems with it (actually, thinking about this later, I think it's not Ubuntu so much as IRQ assignments in your BIOS).  If it's not important to you then don't worry about it, and enjoy Ubuntu!

---

### Post by SeTZerA on 2008-06-26
Well, I'll provide some more details about it just incase, I cant code, but that doesnt mean I cant contribute to the linux community!

The device that caused the problems is a Belkin USB Videobus II (2), video capture device, the driver is "nuvaud2.sys" provided by Zoran Ltd.  And it captures video for me using the windows movie maker applet. It did come with a belkin CD bundled with some video editing software, MGI Videosomething 4 if I recall correctly, but I always used the movie maker for my video editor so I cant say much about the bundled software, the driver came with the cd though, I have since lost the cd.

As for the IRQ settings, in my bios there are a few listed as reserved, but several are not listed, such as 22 or 18, which are the only IRQ mentions in my linux bootup near the errors.

I'm not too worried about it for me personally, I plan on keeping XP in order to edit any videos I might have, so unplugging it isnt a big deal.

Anyways, thanks again, and I hope that driver info is useful to you guys someday! :)

---

