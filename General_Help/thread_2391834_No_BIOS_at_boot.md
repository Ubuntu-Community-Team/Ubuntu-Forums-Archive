---
title: "No BIOS at boot?"
date: 2018-05-13
forum: General Help
---

### Post by frup on 2018-05-13
Hi,

I bought a new computer the other day and am having trouble accessing the BIOS. This is the first desktop non laptop machine I have used since 2003 and I'm quite surprised that the boot process does not seem to allow me access to the BIOS.

I have tried pressing F2, F12, Del as per the gigabyte motherboard instructions and no matter how much I press or mash them it boots without entering BIOS.

At first I thought this might have been due to using a wireless keyboard, but I have since tried a USB keyboard and the result is the same.

By unplugging the master hard drive I was able to force it to boot into a USB drive and have installed Ubuntu on the slave. What I can't do is now set up dual boot options.

I am happy to just use Ubuntu, it's what I've always done but I like to keep the default windows partition around.

What I can't work out is whether there is some setting such as the ultrafast boot that would be causing this. I am very reluctant to reset the CMOS using the pins - especially if that leaves me still unable to boot into BIOS.

I haven't yet tried booting with no drive.

A factor could be that I am using a TV screen via HDMI as my screen - though I don't see how this would stop keyboard input working during the delay.

Because it will boot to any random USB by default I'm a little unhappy with the security of this default set up.

Does anyone have any suggestions on how to access the BIOS? Long term adjusting SATA cables on boot is not going to be a good solution.

Cheers in advance. I've been using nothing but a phone for 2 years.

---

### Post by kerry_s on 2018-05-13
try powering off, hold the shift key while powering on.

---

### Post by yancek on 2018-05-13
If you just bought the computer, you should have some type of user manual.  If not, if it is from some major manufacturer, you should be able to find the boot option from a manual available online.  You haven't posted  the manufacturer of the Desktop so we'll just be guessing.   Do you not see a message on screen at boot indicating a specific key to press?  If not, that would be very unusual.  

You indicate that you were eventually able to access the BIOS to boot and install Ubuntu and then ask about dual boot but not what you are trying/wanting to dual boot.  Do you want to install another Linux, some other OS such as windows or did you by chance have some windows already installed?  If that's the case, which one?  How do you want to dual boot, each system on its own drive, both on the same drive?  Are you using an EFI system?  That's almost certain with a new computer.

You mention ultra fastboot, there is a setting for fastboot and different settings for hibernation if you have a windows 8/10 which need to be off to access from any Linux.  If by chance, you do have windows 8/10 installed, I would suggest you read the Ubuntu documentation at the link below which gives a lot of useful information.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by frup on 2018-05-13
Thanks for the help. I'll have a read of that documentation next chance.

I should clarify no bios screen is visible on boot. The HDMI screen doesn't receive the signal until after the os has already begun loading. In windows with a SSD this about 5 seconds. In Ubuntu on an old laptop drive it's a lot longer but still no change in visual output until after the os has begun.  This shouldn't stop the keyboard working though so the key presses suggest and tried should work but they don't. I have read that some ultrafast boot modes don't allow USB keyboard access either and I don't have a PS/2 keyboard anymore. 

I never got into bios. I disconnected the sata cables and it did boot to USB. Because of that using a second drive I was able to install Ubuntu. I realise now that I can switch the SSD with windows to slave and probably edit grub to get the right boot options from Ubuntu. That will solve the problem but doesn't let me secure the bios. 

I have the manual. I've read it. It would suggest you access bios as normal. It mentions the ultra fast boot settings etc but doesn't describe anyway to disable without access to bios.

The pc is this: 

[https://www.pbtech.co.nz/product/WKSGGPC10805/GGPC-Ghost-GTX-1060-Coffee-Lake-6-Core-Gaming-PC-I](https://www.pbtech.co.nz/product/WKSGGPC10805/GGPC-Ghost-GTX-1060-Coffee-Lake-6-Core-Gaming-PC-I)

**********************************
CPU
Intel Coffee Lake Core i5 8400 6 Core 2.8Ghz

RAM
8GB Crucial Ballistix Sport LT White 2400 MT/s

Storage
250GB Crucial MX500 (OS/Apps/Storage)

Graphics Card
GeForce GTX1060 Graphics Card 6GB

Wireless
Wireless b/g/n up to  300Mbps

PSU
500W MEPS PSU

OS
Microsoft Windows Home 10 64-bit (PB OS recovery stick Included)

Manufacturer Part No:WKSGGPC10805
PB Part No:WKSGGPC10805
Product Model:Ghost
************************************

Sorry I'll need to be at home with the manual to give the motherboard model but it's a gigabyte.

I tried with no drives connected and it doesn't intialise the HDMI output. Normally in the past with older computers this would have brought up an error with bios options. I don't know how to work out what's going on there.

I have since read there are some tools that might allow you to force a boot to bios from windows which might be the way I end up needing to do it.q

---

### Post by monkeybrain20122 on 2018-05-13
Maybe fast boot is on. You should be able to turn it off from Windows, then when you reboot you will be able to get into BIOS (or UEFI, whatever it is called now)

---

### Post by oldfred on 2018-05-13
There is Windows fast start up which is just hibernation.
And there is UEFI fast boot. UEFI fast boot assumes no hardware or configuration changes and immediately starts the system booting. Usually there is then no time to press any keys to get into UEFI or UEFI boot menu.

Cold boot may work. That is fully shutting system down, removing power (and battery if laptop) and holding power switch for 10 sec or so to totally drain any left over power. Then on boot immediately press correct keys.

My desktop locked up after multiple tries at booting an new UEFI install on an external drive. And all the cold boot suggestions did not work. I even jumper-ed motherboard reset pins &  removed coin battery on motherboard. Nothing worked.
But what did then work after all of the other things, was just disconnecting the default boot drive. Since then UEFI finally noticed default boot was not correct it let me into UEFI to change settings.

---

### Post by Autodave on 2018-05-14
Press and hold the F2 key. while holding F2, press the power button. Continue to hold the F2 key until the BIOS screen appears.

---

### Post by frup on 2018-05-14
From what I have read and tried I am pretty certain that ultra fast boot or fast boot are turned on.

However I am now fairly certain that the issue isn't really the ability to access the bios, especially by key presses.. I found you can force a boot into bios from windows via the recovery settings. I tried this. It reboots and the screen never resumes output.

This is also what occured when I booted with no drives attached.

I can only assume that the 65 inch 4k TV I am using as a screen doesn't have a minimum resolution that is compatible with the maximum resolution of the bios. (However I have been able to successfully get output in 1024*768 via ubuntu)

I'll guess I'll have to try find a smaller monitor and see if that works.

---

### Post by oldfred on 2018-05-14
There just was another user who had a 4K monitor and had to change from 60hz to 30hz to make it work.

---

### Post by frup on 2018-05-14
Thanks. I've emailed LG to ask if they have any solutions. The tv doesn't have options to set screen refresh rate. 

I am able to make Ubuntu operate at 30hz but restarting still doesn't show any screen output for the bios.

I have read that until drivers are loaded the GPU will default to 640*480 @ 60hz. 

Placing that setting in Ubuntu results in a black screen with a mouse pointer only. I'm not sure what to make of that if it shows that the screen can indeed output what I need.

At this point I guess I just need to find a proper monitor to try (my last monitor was a 17 inch crt from 2003 long thrown away) or wait to hear back from lg. 

I might take it back to where I bought it from and make them set it up how I want it or just deal with the fact that I can't configure it the way I want to or check that it's been updated with spectre/meltdown patches etc.

---

