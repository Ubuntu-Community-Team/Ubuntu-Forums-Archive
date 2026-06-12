---
title: "Flash not working on Firefox (Precise Pangolin)"
date: 2013-01-13
forum: General Help
---

### Post by clealily on 2013-01-13
Hi, this is my first post.

 I've been trying to get Adobe Flash to work since an (update manager) update about 2 weeks ago. I've tried:

- uninstalling and reinstalling thru Synaptic, Software Center, Adobe site
- removing the latest version and installing the 11.1 version (32-bit machine)
- using the Flash-Aid add-on
- moving and replacing flashplayer.so files in various places
- installing hal library 
- installing  ubuntu restricted extras
- Re-installing Firefox
- Installing Chromium
- Editing values in /etc/adobe/mms.cfg 

I currently have the latest flash installed (through Software Center), and trying to play a youtube video shows a grey window with a message  "The Adobe Flash plugin has crashed".  Youtube videos WILL play if they are HTML5 (I am in the HTML5 trial).

However, I am able to get youtube Flash videos to play without sound by pressing my "printscreen" button while the video window is loading. Weird. 

If anyone knows a solution or has a similar problem, I'd welcome the advice.

Thanks so much,
Clea

*EDIT* - Hardware specifications

Processor: Intel® Core&#8482;2 Duo CPU T6400 @ 2.00GHz × 2 
Graphics:  Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
OS Type: 32-bit

---

### Post by claracc on 2013-01-13
You don't add enough information, what graphics card do you have?, what is your hardware specifications?.

You can try some od the tips addressed in this link: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683), in particular you go to the section entitled: Troubleshooting- adobe flash player.

---

### Post by clealily on 2013-01-13
> **claracc said:**
> You don't add enough information, what graphics card do you have?, what is your hardware specifications?.

You can try some od the tips addressed in this link: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683), in particular you go to the section entitled: Troubleshooting- adobe flash player.

Hi, thanks for the reply. I went to the link you provided and followed the steps for updating, but the problem remains the same.

My hardware specifications are below.

Processor: Intel® Core™2 Duo CPU T6400 @ 2.00GHz × 2 
Graphics:  Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
OS Type: 32-bit

---

### Post by claracc on 2013-01-13
Do you have ubuntu-restricted-extras installed?

In a xterm: sudo apt-get install ubuntu-restricted-extras

---

### Post by clealily on 2013-01-13
> **claracc said:**
> Do you have ubuntu-restricted-extras installed?

In a xterm: sudo apt-get install ubuntu-restricted-extras

Yes it's already been installed, it was one of the first things I tried. It didn't seem to change anything though.
Is there anything else I can try?

---

### Post by claracc on 2013-01-14
You can try some of the workarounds addressed in this thread:
[http://ubuntuforums.org/showthread.php?t=1985689](http://ubuntuforums.org/showthread.php?t=1985689)

Particularly, comment 4, which says the adobe flash crash is fixed with his procedure.

---

### Post by clealily on 2013-01-14
> **claracc said:**
> You can try some of the workarounds addressed in this thread:
[http://ubuntuforums.org/showthread.php?t=1985689](http://ubuntuforums.org/showthread.php?t=1985689)

Particularly, comment 4, which says the adobe flash crash is fixed with his procedure.

Hm, this did not seem to change anything either. I followed the procedure in comment 4, and also tried other things like changing the value of 

EnableLinuxHWVideoDecode=0 

to "1", and also changing the the GPU override to "false", but neither worked. 
Also, I reinstalled Flash with Flash-aid again, to no avail.

Thanks for your help by the way, Claracc. Do you have any other suggestions?

(Just to add, I have previously uninstalled and reinstalled Firefox, and also installed Chromium, but Flash would not work in either case.)

---

### Post by mastergunner on 2013-01-29
Did you get this to work?

---

