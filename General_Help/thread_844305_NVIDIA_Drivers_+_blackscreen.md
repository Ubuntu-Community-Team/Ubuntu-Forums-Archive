---
title: "NVIDIA Drivers + blackscreen"
date: 2008-06-29
forum: General Help
---

### Post by saddeh on 2008-06-29
Alright. I've been trying to solve this problem for over 3 hours now, and I'm well pissed.
First thing I have to mention is that I'm not that good at Ubuntu yet, so I know I've done stupid thing, but lets go.

I'm using Intel2Duo Core E6400 @ 2.13GHz, 1gb ram and NVidia GeForce 7600GT 256mb. 
I've had some drivers installed which were offered to me when I first installed ubuntu. Then I realised I had to upgrade them, so I downloaded an offical .run package (NVIDIA-Linux-x86-173.14.09-pkg1.run) from [www.nvidia.com](www.nvidia.com) and followed a tutorial on how to installed them. I turned off Xserver via CTRL+ALT+F1, had a cmd line where I've ran the package and followed on-screen instructions. All did well, I've been asked whether I wanted to compile ?core? or if I wanted to download it, so I said I wanted to compile it as it was said in the tutorial. Then I was asked if I wanted to reconfigure xorg.conf and I replied no, as was stated to do in the tutorial. Thats it. It said the installation was successfully completed and I exited it.

Next thing I saw was black screen for a minute, so I decided to reboot. Rebooted. Same thing, black screen. Rebooted twice. Went onto Live CD to google it, so CTRL+ALT+F1 worked, as it turned out that drivers didn't load Xserver properly? Not sure. Anyway, I had cmd line running and I was able to log onto my account and execute commands. After hours of surfing and talking to different people I've found different solutions. I've tried startx. I've tried to back up my xorg.conf. I've created a new conf from scratch via sudo dpkg-reconfigure xserver-xorg. I've tried to sudo apt-get install nvidia-glx, sudo apt-get update, sudo apt-get upgrade. Nothing worked. All I was getting is that black screen which could be turned off by pressing CTRL+ALT+F1 and thats it. I've ran out of ideas and patience, so I'm asking for your help here. 

Is there any work around to get back to the previous drivers I was using? To delete new drivers? To install them over the ones I have? Run ubuntu in something like safe-vga mode? I don't want to reinstall it, nor I'm giving up on trying.

I will be glad to listen to any suggestions and help you can provide. I will provide any additional info if needed. 

Thanks in advance, guys. I hope for the best.

---

### Post by Pjotr123 on 2008-06-29
1. Do this:
[http://ubuntutip.googlepages.com/nodisplay](http://ubuntutip.googlepages.com/nodisplay)

2. Then do this:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 )

What you did wrong, was that you tried to install a driver manually. That is very difficult and also very unnecessary.  :-)

---

### Post by saddeh on 2008-06-29
Pjotr123,
Thanks for your reply. 
However, this didn't work. I tried the recovery mode and tried 'Try to restore X-server', it finished. I rebooted and it didn't work. Then I did it again and tried not to reboot and pressed resume. Same effect.. I mean no effect. However, I found it interesting that I had two sets of kernel in GRUB menu.. the one ending with -16 and the other being -19 (unsure, but I think that is). Could that help? 
Anyway, I think its not the case as I've tried to restore xorg.conf before and it didn't help.
Hoping for your help.

---

### Post by saddeh on 2008-06-29
Gave up on it. Had to reinstall. Problem solved. Old drivers, but.. hey, at least it works.
The problem remains unsolved. Topic can be closed.
Thanks for efforts. ;)

---

### Post by Max Spain on 2008-06-29
If you're still interested, I just went through the trials of manually installing the latest Nvidia driver and I wrote down all the steps needed from a fresh 8.04 install.

---

### Post by saddeh on 2008-06-30
Wouldn't mind it, aye.

---

