---
title: "Linux won’t boot without restart"
date: 2016-08-30
forum: General Help
---

### Post by retinuee on 2016-08-30
Dear all,
I am not very Linux or computer savvy in general, and I have shunned these forums for a long time for this reason. But I’m up against a strange situation, and I haven’t seen anyone online who’s had this happen to them. I’m now more curious then finding out why this is happening than even fixing it.

A friend I talked to about this suggested I film what’s happening, but I think I can explain it in writing.
 
Currently I am running Ubuntu 16.06 alongside Windows 10. I have a HP Pavilion 360 - 13-a200nt,  CPU Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz, 2201 Mhz. I updated my Bios on this computer to the final version on July 18 (and it hasn’t changed my situation). 

I'm attaching a [boot log fr]("https://docs.google.com/document/d/1UJ7fzfAkFm0rygJYRguYzfQdMdCM9ra49ojwjBFsKPc/edit?usp=sharing")om my computer(I’ve since updated the BIOS to the latest version, everything else’s the same). 

I’ve run  Ubuntu 14.04 on this computer for months as the sole OS, until I lost my hard drive to overheating (thanks to Ubuntu) and had to get a new hard drive. I had to send it to where I bought it from, and they changed the hard drive. I have no idea what they did what here’s what’s happpened since then:
You get a working Linux installation USB, and it boots into  GRUB and stops there. (Doesn’t matter what flavor Linux. ) It seems that the problem is not hardware related here. Because when you restart from another OS, you can use the laptop without shutting it down for days on end. 
 Here is what I mean:
Any (used different flavors of ubuntu, the boot info disc, and an arch Linux installation pen drive) Linux-system pen drive (created on Mac, Windows and Linux systems: tested and successfully used on other computers) when you start the computer boots into the GRUB menu regardless of your BIOS settings (this is to mean I’ve tried turning on or off secure boot, legacy/UEFI and various combinations).  But then it gives you a purple (I think this happens if the system you are installing or running is Ubuntu) or a black scree) when you continue on from GRUB. If you make any changes to the command line, (no splash, quiet splash..etc) it freezes at LOADING INITIAL RAMDISK.
Now, the reason why I ended up with a copy of Windows on my computer is because I noticed this: None of this happens when you restart the computer from any OS. 
For example, I now have Ubuntu 16 installed. I can start the computer, boot into Windows and then RESTART from Windows and boot into Ubuntu. From there on, I can –shutdown –r ubuntu and go back into ubuntu again. 
So to log into linux, I have to first go into Windows. Also, to be able to install Linux on this machine at any time, I have to have some version of Windows. 
I have read much on forums about boot problems. I can’t seem to find anything like this. I’ve tried different command line options, different kernels, different BIOS versions, different Linux flavors, I’ve tried the same thing with Windows 8 as the second OS (and I really don’t see why I have to have a second OS).  
I’ve read some on boot architecture but it’s really over my head. What is it that the machine does differently when it’s booting for the first time, and when it restarts after having booted into an OS? And how can this information help a rather simple-minded person?
I hope I’ve been able to explain the problem. Sorry for not being too technical, but I really love Ubuntu and hope this can be solved.

Best,
Baris

---

### Post by reese1379 on 2016-09-01
[I]"I&#8217;ve run Ubuntu 14.04 on this computer for months as the sole OS, until I lost my hard drive to overheating (thanks to Ubuntu)" 

[/I]There is no known technical reason why running a standard Ubuntu distro would ever overheat a harddrive!

---

### Post by retinuee on 2016-09-11
Hello reese1379,
Thank you for your response. 
I think it had a problem with ubuntu, because I'd read on forums that people had overheating problems with HP, though I never really tried to address it, so maybe it was a hardware thing. I am not ruling that out, but other people have had similar issues (giving a non-HP example [http://askubuntu.com/questions/491793/laptop-overheats-running-ubuntu-14-04](http://askubuntu.com/questions/491793/laptop-overheats-running-ubuntu-14-04))
Yet, separately, I can't log into my system if I don't restart the computer from any OS. Any ideas?

---

