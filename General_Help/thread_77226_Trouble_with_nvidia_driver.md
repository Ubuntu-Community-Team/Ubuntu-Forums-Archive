---
title: "Trouble with nvidia driver"
date: 2005-10-16
forum: General Help
---

### Post by avallach on 2005-10-16
I'm having major trouble getting the nvidia driver to install.  I've read & followed the instructions posted in the HOWTO by tseliot.

Those instructions are for version 7667, which doesnt support my video card (an older Vanta), so I'm trying to install 7174.  Perhaps I should just do the apt-get thing and leave well enough alone but I had this working in Hoary.  There's something about getting that full-screen nvidia logo during startup that I just dig. :)

Anyway what happens is this.  I get the installer to complete & tell me everything's installed successfully.  I try to start gnome, and it tries 3x and fails.  I check my xorg log and find:

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***


Odd.  I did a little more troubleshooting, one page tells me to check the output of dmesg, which I do.  This is where I really get confused:

[4298914.634000] NVRM: The NVIDIA Vanta/Vanta LT GPU installed in this system is
[4298914.634000] NVRM:  supported through the NVIDIA Legacy drivers. Please
[4298914.634000] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[4298914.634000] NVRM:  information.  The 1.0-7667 NVIDIA driver will ignore
[4298914.634000] NVRM:  this GPU.  Continuing probe...
[4298914.634000] NVRM: No NVIDIA graphics adapter found!


What?  7667?  I didnt install 7667...why is it telling me 7667 doesnt support it?  Like I said I downloaded the 7174 which is apparently (based on the READMEs) the latest that supports my card...   So I do an nvidia-installer -i to find out what driver version is installed:


Welcome to the NVIDIA Software Installer for Unix/Linux


The currently installed driver is: 'NVIDIA Accelerated Graphics Driver for
Linux-x86' (version: 1.0-7174).

OK so I do have 7174.  How am I getting errors from 7667?  This was a completely fresh install of Breezy.  

I'm currently reinstalling Hoary to make sure I'm not trippin, and to prove to myself that I do in fact know how to install the driver and that this version does in fact support my card.  But any advice anyone here can give me would be appreciated.

---

### Post by taavi on 2005-10-16
[QUOTE=avallach]I check my xorg log and find:

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***[/QUOTE]

Ok. Maybe you should try look, if module named nvidia is loaded.

```
$lsmod | grep nvidia
```

If not, then try to modprobe it:
```
$sudo modprobe nvidia
```

---

