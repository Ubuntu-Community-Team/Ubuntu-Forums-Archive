---
title: "Yet another nVidia annoyance - need help..."
date: 2008-05-14
forum: General Help
---

### Post by keforex on 2008-05-14
Ok, so everything is working fine when all of a sudden one of my screens stops working (it's working fine in Vista).

So I go to nvidia-settings and I get this message "You do not appear to be using the NVIDIA X driver. etc..."

So I run "nvidia-xconfig" as root and it doesn't solve the problem and I still get the same message when I try to run nvidia-settings. What should I do?

---

### Post by EXCiD3 on 2008-05-14
Does it show that you are using the nvidia driver when you go to System->Hardware Drivers?

---

### Post by keforex on 2008-05-15
Yes, it shows it's enabled and in use.

---

### Post by EXCiD3 on 2008-05-15
Interesting. Have you tried uninstalling the drivers and reinstalling them?

---

### Post by keforex on 2008-05-16
Yes, I did that and I still get the same error when trying to run nvidia-settings. It says "You do not appear to be using the NVIDIA X driver...." - I don't know what else to do, any ideas besides re-installing ubuntu?

---

### Post by EXCiD3 on 2008-05-16
I would recommend using EnvyNG to try to install the drivers, compiling them from source by hand ([http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/](http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/)), if that doesnt work you will probably want to reinstall unfortunately. I have seen several users having a lot of trouble with the nvidia driver on Hardy, especially with the legacy driver, but i wish you luck! ;)

---

### Post by The Minder on 2008-05-16
keforex,

I've had similar probs with Hardy and nVidia not co-operating.   I even sought advice on this board all to no avail.   Like you, I got the ubiquitous nVidia message about the x-server, but nothing would resolve the issue.   In the end, I did:
[INDENT]a clean install of Hardy on a new hard drive, and
installed Envy from Synaptic and let Envy install the nVidia drivers.[/INDENT]

Everything appeared to be working fine, I had the screen resolution I wanted and I had the advanced desktop effects.   I also had unpredictable system lockups that totally froze my computer with no error logs being generated.   Additionally, sometimes the color of a window would suddenly change to look like it was running 4 bit color, and then come back to normal as I deselected then reselected that particular window.

After trolling the forum(s) for an answer I finally gave up.   I removed the nVidia drivers and Envy and on the next system boot I selected the Grub option of fixing the kernel by reconfiguring the x-server... please note I am a Ubuntu noob and I may have screwed up on some of the terminologies.

Everything came up fine.   I have the resolution I want but not the advanced desktop features.   I can live with that as anything is better than an unstable system.   I recommend you forget all having Envy installing drivers or installing drivers manually and just let Ubuntu do it's thing.

Regards

---

### Post by keforex on 2008-05-16
Well... I finally gave up. I decided to re-install everything. This time I switched to Kubuntu (KDE 4) and so far everything is working fine. I don't have desktop effects, but at least it is very stable (so far).

This is a bummer, after all it was working fine for a while and all of a sudden it decided to not work anymore.

EXCiD3 - Before I gave up I did what you suggested but no luck. The Minder, thanks for the post.

Lets see for how long I will be a Kubuntu user. I hope it lasts longer than Ubuntu did.

---

### Post by EXCiD3 on 2008-05-16
Sorry to hear nothing worked. It seems that the nvidia driver is just not working well with most people's installations of Ubuntu this time around. Mine works fine but there are a LOT of other users that are having trouble. Hopefully they will fix this in the 8.04.1 release.

---

### Post by keforex on 2008-05-17
You know, there's a Linux distribution (or Ubuntu variation) that is made in Brazil that detects nVidia cards during the install process and configures everything. Why not do the same with all? (Ubuntu, Kubuntu, etc...) - This whole thing about installing Envyng is not very user friendly at all. Not because it's difficult, but because for someone that never used Linux before the foundation of how things work in Linux is not there.

I've been seeing THOUSANDS of posts here about black screens, wrong resolutions, etc... Until Linux distributions are able to detect and install drivers on their own during the install process I don't think people will be abandoning Macs or Windows. It's just way too much work before you can think about being productive with the machine. OS for Humans? I don't think so.

Sorry for the rant.

---

### Post by EXCiD3 on 2008-05-17
Haha, i agree. Unfortunately a lot of this has to do with hardware companies' lack of support for linux. Yes nvidia is creating drivers for linux, but only their 2D 'nv' driver is open-source and their 3D 'nvidia' driver is in no comparison close to the quality of the Windows drivers. And nVidia is a company with fairly decent linux support...just look at Broadcom and all the hassle users have to do just to get their wifi cards working. Its a pain to install and configure Linux without compatible hardware, and thats something new linux users didnt think about back when they purchased their computer.

Theres my 2 cents. ;)

---

