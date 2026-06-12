---
title: "Ubuntu 13.04 shutdown freezes and won't proceed"
date: 2013-05-04
forum: General Help
---

### Post by drunkenbrawler on 2013-05-04
Hi,

I upgraded my laptop today to Ubuntu 13.04 and noticed that after I try to shutdown the laptop, it starts shutting down, the ubuntu screen with little dots appears and then the screen goes dark. The shutdown process freezes there. The screen is dark but it is not off. The fan is running at steady speed. I have waited for 8-10 minutes but it just stays in that stage.

The problem was not there on Ubuntu 12.10. I fresh installed 13.04 today and problem has started. It appears consistently at every shutdown. I have to press and hold the power button to turn off the laptop forcefully.

Following is my configuration:

Dell XPS 15z laptop
intel i5 processor 2.4 GHz with 6 GB RAM
Nvidia GeForce GT 525M

Please let me know if I should post more info.

Thanks

---

### Post by dino99 on 2013-05-04
if you want to know what is happening, you can:
- remove "quiet splash" from /etc/default/grub , then update grub again
- glance at the logs for usefull warnings/errors  (.xsession-errors & /var/log/)

to force the shutdown process:  open a terminal and run  ```
sudo shutdown -h now
```

---

### Post by drunkenbrawler on 2013-05-04
Hi,

The problem seems to have gone away after I installed Bumblebee. 

Thanks for the reply. This thread can now be closed.

---

### Post by pestucky on 2013-05-06
I am having the same freeze on shutdown with Ubuntu 13.04, occasionally.  Except in my case the Ubuntu screen appears with the little dots, and the dots just continue and continue for many minutes, until I finally shut it down with the power button

---

### Post by Vixx_Daru on 2013-05-10
> **pestucky said:**
> I am having the same freeze on shutdown with Ubuntu 13.04, occasionally.  Except in my case the Ubuntu screen appears with the little dots, and the dots just continue and continue for many minutes, until I finally shut it down with the power button

I am having the same problem after I upgraded my Ubuntu from 12.10, and everytime I shutdown, it just freezes at the Ubuntu splash screen until I shut it down manually with the power button.

---

### Post by gusduenas on 2013-05-13
> **Vixx_Daru said:**
> I am having the same problem after I upgraded my Ubuntu from 12.10, and everytime I shutdown, it just freezes at the Ubuntu splash screen until I shut it down manually with the power button.

Same problem with me I have a fresh install of ubuntu 13.04 on a laptop dell latitude d520 everything appears as ok, I even have tried to edit the dispatcher voice or something and turns out it kills my sound...now I'm looking for a possible answer, please advice.

Gus

P.d: when I press shutdown or even restart it stall on a terminal about the dispatcher and I have to shutdown manually with the power button on my laptop. ehen I press shutdown on the top menu (even in the terminal) it will stall on the ubuntu dots and it will go for more than 5 minutes until I have to shutdown manually...

---

### Post by ramon76 on 2013-05-16
Same problem for me on HP EliteBook 8540w, I've always to shout down manually by pressing the power button

---

### Post by GBB1 on 2013-05-20
Same problem on Asrock Vision 3D with Ubuntu 13.04 freshly installed. Had to revert to Ubuntu 12.10..

---

### Post by AnotherNoob on 2013-05-20
Same problem on Dell inspirion N5010 , even on SSD with fresh install.

---

### Post by bogan on 2013-05-20
Hi!, **All,**

I too have the Ubuntu red and white dots splash screen. unendingly sequencing on shutdown, until forced to quit. That is on five different installations of 13.04, which shut down completely normally until Wednesday or Thursday of last week.

It does not respond to the usuall Keystrokes - 'Ctrl +Alt+t', 'Ctrl +Alt+F1-7', Ctrl +Alt+Del'.

But to save having to use a Power-off shut down, it does respond to 'Alt Gr+PrintScreen/Sys Req'. and shuts down immediately.

Edit : Contrary to other Posts reporting similar shutdown freezes, mine does shutdown normally from a terminal, using: 'Sudo shutdown -h now'.

Chao!,** bogan**.

---

### Post by Red Planet on 2013-05-26
Hi! My laptop freezes every time I switch it off or reboot. It may have happened after upgrading to Kubuntu 13.04.

> **dino99 said:**
> if you want to know what is happening, you can:
- remove "quiet splash" from /etc/default/grub , then update grub again


It was a very useful piece of advice. How to see the list of the processes which cause the problem?

My output before getting stuck

```
* Killing all remaining processes...
modem-manager [1067]: <info> Caught signal 15, shutting down...

* Deactivating messages swap...
* Unmounting local filesystems...
umount2: Device or resource busy
umount: /dev/sda7 busy - remounted read-only
umount2: Device or resource busy
umount: /var: device is busy.
    (In some cases useful info about processes that use the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy

umount: /run/lock: not mounted
umount: /run/shm: not mounted
* Will now restart
```

I have tried the following modes.


[LIST=1]
[*]GRUB_CMDLINE_LINUX_DEFAULT="noacpi"
[*]GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq"
[/LIST]

There was no any effect. My laptop model is Asus UL80VT.
/dev/sda7 is /usr

[B]Solved.
[/B]
I solved my problem having installed Nvidia driver. Here is [the guide]("http://dragly.org/2012/05/04/installing-the-nvidia-driver-in-kubuntu-12-04/") I used. Although I got > ERROR:root:Could not find any typelib for AppIndicator3
after executing > jockey-text -e xorg:nvidia_current I rebooted the system I didn't have any problems up till now.

---

### Post by bogan on 2013-05-26
Hi! **Al**l,
As a matter of interest, since the recent kernal updates, my computers now go through exactly two sequences of flashing red & white dots, in the Shutdown splash screen, and then shut down with no text displayed.

Chao!,** bogan.**

---

### Post by zukeprime on 2013-06-06
I've had the same problem on an old laptop (HP Pavilion, ZV5000, 2Gb RAM) that I use as an experimental platform.  On any Ubuntu distribution, the computer would not shutdown/restart on command.  I tried a variety of solutions, but managed to get it to work with the following:

Modify /etc/modules
     sudo nano /etc/modules

add
     apm power_off=1

    Edit Grub:
     sudo nano /etc/default/grub
    
change the line
     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
    to
     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_os_name=Linux acpi_osi=Linux acpi=force apm power_off=1"
    
and now just update grub
     sudo update-grub

Interestingly, and probably something I should add to the ongoing bug reports (if I could find it), I DID NOT experience this problem after installing the Ubuntu 13.04 minimal install, with xubuntu-desktop.  During this install process, I installed Xubuntu-Desktop with --no-install-recommends and manually added required modules per this thread [http://ubuntuforums.org/showthread.php?t=2140793](http://ubuntuforums.org/showthread.php?t=2140793) and [http://flux242.blogspot.com/2013/05/minimal-xubuntu-desktop-installation.html](http://flux242.blogspot.com/2013/05/minimal-xubuntu-desktop-installation.html)

I'm relatively new to Linux, so I can't even begin to guess what the difference is between the full Xubuntu and the minimal install with Xubuntu-desktop to cause this shutdown/restart issue.

edit:  I want to add that video drivers had absolutely nothing to with this issue in my case.  

I hope this helps someone!
ZP

---

