---
title: "[SOLVED] Screen resolution problems and blurry text"
date: 2008-05-21
forum: General Help
---

### Post by hfp on 2008-05-21
Hey, everyone.  I just found out about Ubuntu last night.  A friend told me it was great.  This is my first experience with Linux so please forgive my ignorance :-)  I'll try to stick with it.  Unfortunately, I have a small problem.  The resolution on my screen doesn't seem to be working right.  When I minimize a window, that window goes to the bottom of the screen and out of sight.  I can drag my mouse to the bottom of the screen and find it blindly, but I know that is not the best way.  Also, the text on the screen is not nearly as sharp as it was on vista.  It's hard to distinguish the letter "n" from "m".  Now it's somewhat blurry and of much worse quality.  I appreciate your help.

When I go to the resolution settings, I am unable to change them, yet they are actually correct, or at least what the monitor prefers, and the same settings that vista uses.  I am also unable to change the special effects settings.  Any ideas?  My monitor is a 20 inch HP flat screen. Thanks so much.

---

### Post by overdrank on 2008-05-21
> **hfp said:**
> Hey, everyone.  I just found out about Ubuntu last night.  A friend told me it was great.  This is my first experience with Linux so please forgive my ignorance :-)  I'll try to stick with it.  Unfortunately, I have a small problem.  The resolution on my screen doesn't seem to be working right.  When I minimize a window, that window goes to the bottom of the screen and out of sight.  I can drag my mouse to the bottom of the screen and find it blindly, but I know that is not the best way.  Also, the text on the screen is not nearly as sharp as it was on vista.  It's hard to distinguish the letter "n" from "m".  Now it's somewhat blurry and of much worse quality.  I appreciate your help.

When I go to the resolution settings, I am unable to change them, yet they are actually correct, or at least what the monitor prefers, and the same settings that vista uses.  I am also unable to change the special effects settings.  Any ideas?  My monitor is a 20 inch HP flat screen. Thanks so much.

Hi and welcome, have you installed the drivers for your graphics card and what is the model? You can look at the hardware drivers located under system, administration. You can find you graphics model with the command ```
lspci 
``` in the terminal located under applications, accessories. Look for VGA.

---

### Post by hfp on 2008-05-21
> **overdrank said:**
> Hi and welcome, have you installed the drivers for your graphics card and what is the model? You can look at the drivers manager located under system, administration. You can find you graphics model with the command ```
lspci 
``` in the terminal located under applications, accessories. Look for VGA.

Thanks, overdrank.  I do not believe I have installed the drivers for my graphics card.  I followed your instructions to find the graphics card model with the command lspi and the following came up:

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Multimedia video controller: Conexant CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
01:06.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
ubuntu@ubuntu:~$

---

### Post by overdrank on 2008-05-21
Ok you should be able to use the restricted drivers in the  Hardware drivers  mentioned before. Reboot the system as directed after installation then get the nvidia-settings and you should be good to go. Good luck!

---

### Post by hfp on 2008-05-21
> **overdrank said:**
> Ok you should be able to use the restricted drivers in the drivers manager mentioned before. Reboot the system as directed after installation then get the nvidia-settings and you should be good to go. Good luck!

How do I get to the restricted drivers in the drivers manager section?  I went to Nvidia's website and downloaded the driver that I think is appropriate for me: NVIDIA-Linux-x86_64-169.12-pkg2.run

But I don't know how to install that driver.  I appreciate your help, overdrank.

---

### Post by overdrank on 2008-05-21
> **hfp said:**
> How do I get to the restricted drivers in the drivers manager section?  I went to Nvidia's website and downloaded the driver that I think is appropriate for me: NVIDIA-Linux-x86_64-169.12-pkg2.run

But I don't know how to install that driver.  I appreciate your help, overdrank.

HI and as I stated in my earlier post #2
You can look at the  hardware drivers  located under system, administration.

---

### Post by hfp on 2008-05-21
> **overdrank said:**
> HI and as I stated in my earlier post #2
You can look at the drivers manager located under system, administration.

When I go to system, and then administration, drivers manager is not there.  The closet thing to it is Hardware Manager.

---

### Post by overdrank on 2008-05-21
> **hfp said:**
> When I go to system, and then administration, drivers manager is not there.  The closet thing to it is Hardware Manager.

Ok I am sorry I am assuming you are using Hardy 8.04. What version are you using, look under system, about Ubuntu.

---

### Post by hfp on 2008-05-21
> **overdrank said:**
> Ok I am sorry I am assuming you are using Hardy 8.04. What version are you using, look under system, about Ubuntu.

It says "This version (Hardy Heron) was released in April 2008 so its version number is 8.04."

When I go to System, and then to administration, I only see the following:

Authorizations
Hardware Drivers
Hardware Testing
Install
Language Support
Login Window
Network
Network Tools
Partition Editor
Printing
Services
Software Sources
Synaptic Package Manager
System Log
System Monitor
Time and Date
Update Manager
Users and Groups

---

### Post by overdrank on 2008-05-21
> **hfp said:**
> It says "This version (Hardy Heron) was released in April 2008 so its version number is 8.04."

When I go to System, and then to administration, I only see the following:

Authorizations
Hardware Drivers
Hardware Testing
Install
Language Support
Login Window
Network
Network Tools
Partition Editor
Printing
Services
Software Sources
Synaptic Package Manager
System Log
System Monitor
Time and Date
Update Manager
Users and Groups

Hi and you are correct, my mistake it is hardware manager. there you can enable your drivers.

---

### Post by hfp on 2008-05-21
> **overdrank said:**
> Hi and you are correct, my mistake it is hardware manager. there you can enable your drivers.

Sorry, I made a mistake earlier.  Hardware manager is not there.  I must have seen hardware driver and update manager and accidently put them together.  What I see is what I wrote in the previous post.

---

### Post by Bakon Jarser on 2008-05-21
Oops, misread earlier post.

Deleted!

---

### Post by hfp on 2008-05-21
> **Bakon Jarser said:**
> That's okay because he meant go to hardware drivers.

Once I go to hardware drivers I'm not sure what to do.  There is nothing listed in the Component Column.  I am not sure what to do from here.  Thanks for your patience.  I have just been running ubuntu off the cd.  Maybe I should install it completely on my computer.

---

### Post by Bakon Jarser on 2008-05-22
Okay, we're getting somewhere.  The restricted driver is not even installed which is why you can't enable it.

See post #5 in this thread.

[http://ubuntuforums.org/showthread.php?t=796090](http://ubuntuforums.org/showthread.php?t=796090)

---

### Post by hfp on 2008-05-22
I solved the problem.  Apparently all I had to do was install ubuntu to the hard drive.  Ubuntu must not want to install certain drivers unless ubuntu is installed completely onto a system, instead of just running off the cd.

After it was installed completely, the option to install the Nvidia drivers came up in the top right corner without me even telling it to.  I installed them, along with the other updates, restarted the computer, and now everything looks nice and crisp.  The resolution is correct also.  Everything fits well on the screen now.  Thank you, overdrank and Bakon Jarser.  I greatly appreciate your help.:popcorn:

---

