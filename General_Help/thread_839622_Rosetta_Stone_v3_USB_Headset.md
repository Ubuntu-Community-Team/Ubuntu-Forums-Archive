---
title: "Rosetta Stone v3 USB Headset"
date: 2008-06-24
forum: General Help
---

### Post by bcardarella on 2008-06-24
I was able to install Rosetta Stone with minimal difficulty. My issue now seems to be with the USB headset that comes with the package. When plugged in Ubuntu recognizes it as C-Media USB Audio Device. However I am getting no sound from the headset and the microphone does not work. (I have unmuted and increased the mic volume via the sound control panel)

I have also completely removed Pulse Audio so my only sound server is ALSA. Wine is configured to use ALSA, and I see a USB Device for the ALSA Wave Out but no USB Device listed for Wave In.

Does anybody have any thoughts?

---

### Post by abclemons on 2008-12-03
You can try the instruction is this post: [http://forum.winehq.org/viewtopic.php?p=15965]("http://forum.winehq.org/viewtopic.php?p=15965").

I have a Logitech Clearchat Pro USB headset, Wine 1.1.3, Ubuntu 8.04, using ALSA (I've tried with and without PulseAudio) - headset works in other most but not all apps. However, I've never got it close to working in RS. I am going to try support with the Rosetta Stone people to see if they have any advice for getting rid of the auto-detection of the mic and allow me to point to the device.

---

### Post by abclemons on 2008-12-04
The RS support has responded to me with the following:
> I apologize, but Ubuntu Linux is not a supported operating system for Rosetta Stone software. Please see our website for current system requirements...
I'm trying again, but I am guessing they're not going to be too much help. This is, sadly, yet another example of the need for these large companies to develop Linux native software. {sigh}. I'll keep canvasing for solutions though.


Cheers,

Aaron

---

### Post by Bleumunkie on 2008-12-04
another alternative, although quite a dirty one since it requires a windows install inside a VM.

you could use VirtualBox which is in the repo's, or you can download a .deb from the website.

Install a Windows Install - Install RS.   you can then configure VirtualBox to take over control of any USB hardware and pass control directly to the windows install.

This will let windows load its own drivers just like normal - and will allow RS to auto-detect the headset just like in a native windows install.


Although a "dirty" solution since instead of running RS in linux, your running it inside windows - inside linux, if RS auto detects the headset like that I believe its your only solution at the moment besides a dual-boot.

The benefit is you can just run the VM when you want to run RS - not have to reboot into Windows.

---

### Post by abclemons on 2008-12-05
@Bleumunkie, that's the verdict I've arrived at thus far. I've got VirtualBox installed, and I'm reaching for my pocketbook to to do something I haven't done in years (buy an OS). I'll keep faith that someone can come up with a different solution, yet my resolution is waivering.

---

### Post by Bleumunkie on 2008-12-06
Well, you shouldnt have to buy it.  Unless you built your computer yourself Odds are that you own a Windows XP license (look for the sticker on your computer somewhere)

You can "borrow" a friends CD to install the OS - its the license key you pay for anyways.

Even if you built your own computer - if you have one that has a license sticker on it that you also replaced the OS with linux you can use that license on the VM install.

I'm not a lawyer - but the way I've always understood the way Microsoft does buisness is that when you buy Windows, your buying the license to use it on ONE computer at a time.  Just because it comes pre-installed on a Dell doesn't mean it has to stay there.

I use a laptop with only Ubuntu installed as the Main OS.  I have windows installed in a VM - and I just used the key thats on the sticker.  Technically I own that license anyway.

Just my 2 Cents.

---

