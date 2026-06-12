---
title: "Periodically reinstalling Ubuntu because I lose my desktop..."
date: 2016-10-12
forum: General Help
---

### Post by john_ladasky on 2016-10-12
I have now had a certain problem occur three times.  My system boots fine, and gives me a splash screen and login prompt.  After I type my password, the desktop clears, and my Unity launcher never appears.  I'm looking at the background screen and nothing else.  It's not a black screen, the Ubuntu background graphic is displayed.  And I have a mouse cursor that I can move around.  But there's nothing to click.

It occurred once with Ubuntu 14.04 x86-64.  This prompted me to upgrade to 16.04 x86-64.  Unfortunately, the same crash symptom has now happened twice with 16.04.  These crashes have occurred several months apart.  I don't think that they occurred at any special times, such as after kernel updates. 

Years ago, I remember having a vaguely similar problem.  I was instructed to exit the GUI and open a terminal using Ctrl-Alt-F1.  I had instructions that would halt and restart LightDM.  That got me out of a few jams back then.  My current problem must be different. Ctrl-Alt-F1 doesn't respond, so I can't try restarting LightDM.  Nothing works except hitting the reset or power buttons.

Rebooting the system doesn't change anything, so I have to reinstall Ubuntu!  Reinstalling the OS isn't so bad, but my applications are another story.  That takes hours.  I am considering writing a script to install everything I need...

My hardware is about a year old: a Gigabyte Z97X motherboard, a Corei7-4790K CPU, an NVidia GTX 750 GPU, 16 GB RAM.  Normally it runs perfectly.  I am pretty sure this is a software problem.  Intermittent software problems are hard to debug, I know.  Any suggestions as to what I should investigate?  Thanks.

---

### Post by T.J. on 2016-10-13
> **john_ladasky said:**
> I

Years ago, I remember having a vaguely similar problem.  I was instructed to exit the GUI and open a terminal using Ctrl-Alt-F1.  I had instructions that would halt and restart LightDM.  That got me out of a few jams back then.  My current problem must be different. Ctrl-Alt-F1 doesn't respond, so I can't try restarting LightDM.  Nothing works except hitting the reset or power buttons.

Rebooting the system doesn't change anything, so I have to reinstall Ubuntu!  Reinstalling the OS isn't so bad, but my applications are another story.  That takes hours.  I am considering writing a script to install everything I need...

My hardware is about a year old: a Gigabyte Z97X motherboard, a Corei7-4790K CPU, an NVidia GTX 750 GPU, 16 GB RAM.  Normally it runs perfectly.  I am pretty sure this is a software problem.  Intermittent software problems are hard to debug, I know.  Any suggestions as to what I should investigate?  Thanks.



Sounds like either a bad video driver or a misconfiguration.  What driver are you using?

---

### Post by john_ladasky on 2016-10-13
Hi TJ,

Thanks for your reply. Some of my work depends on CUDA, so I always install and use the NVidia proprietary GPU driver that Ubuntu has tested.  Currently, my system is operating with NVidia driver version 361.42.

---

### Post by T.J. on 2016-10-15
> **john_ladasky said:**
> Hi TJ,

Thanks for your reply. Some of my work depends on CUDA, so I always install and use the NVidia proprietary GPU driver that Ubuntu has tested.  Currently, my system is operating with NVidia driver version 361.42.

I have noted a certain strange behaviour using the Nvidia driver in 16.04 - that it will on occasion backup and then delete the /etc/X11/xorg.conf file. Naturally, this will raise all kinds of vysnc and other issues with the Nvidia driver after a reboot.  I have not discovered the source of it as of yet.  It is not present in Debian - and seems to be a bug in Ubuntu.  I have not filed a bug report without knowing the cause.  I mention it because if the file is not present - you may experience side-effects as well.  Naturally, restoring or recreating the file and then rebooting returns the machine to a usable state.

---

### Post by john_ladasky on 2016-10-21
Thanks TJ, please post a followup if you learn more.  

For now, I will have to watch for another failure of this kind. If it should happen, I plan to boot from the install DVD, check the hard drive for a missing /etc/X11/xorg.conf file, and restore it from my most recent backup if I should find it missing.  Hopefully xorg.conf isn't a file that changes significantly and/or often.

---

### Post by john_ladasky on 2016-11-10
Hi TJ, and anyone else who may be reading this.

I didn't have a repeat of my failure, but out of curiosity, I went looking for /etc/X11/xorg.conf.  I realized that my backups don't include the /etc folder.  Also, I wanted to see exactly what kind of information is contained in that file.

Well, hey, I don't have a file called xorg.conf anywhere in my filesystem.

I do have a folder called /usr/share/X11/xorg.conf.d with a bunch of files in it.  That's not quite the same thing.  Any thoughts?  At the risk of repeating myself, my system is currently running fine.

---

### Post by alexjpowell on 2016-11-10
Maybe uninstall and reinstall X

---

### Post by T.J. on 2016-11-10
By default, there is no xorg.conf file.  If there is no file, it auto-detects the necessary hardware, which may not always be what you want if you have an unusual configuration.  How you create that file depends on your hardware.  With Nvidia, it is the nvidia-xconfig utility, run using sudo.  For example, if you want to force the Nvidia driver to stop tearing, you need to create the file and enable full compositing.

---

### Post by alexjpowell on 2016-11-10
/usr/share/doc/xserver-xorg-video-intel/xorg.conf

---

