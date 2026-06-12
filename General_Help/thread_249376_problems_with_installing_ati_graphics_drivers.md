---
title: "problems with installing ati graphics drivers"
date: 2006-09-02
forum: General Help
---

### Post by vzkid111 on 2006-09-02
I was getting xgl working when I realized I hadnt yet installing my ati graphics drivers for my radeon x1300, my comp is running a dual boot of ubuntu and windows, so I restarted, which is what a forum thread from the tazz forums told me to do (link is [http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)) i was just finished installing the first part of the drivers, it click ctrl+alt+backspace or something like that to reset my graphical interface but when I did, my monitor couldnt take and now it blinks      signal over range on my monitor (this is not what linux is doing) so I need help reseting my screen res, i think... but do you think installing the rest of the driver would fix the problem from the linux recovery kernel? thats what im going to try...

---

### Post by ruppmeister on 2006-09-02
vzkid, I am still a newbie but I think that I can help you out here a little. You said that you were in the middle of the install and it says that the signal is out of range. This means that the refresh rate on the monitor is too high. To fix this boot into recovery mode from the grub sreen. There it will boot you into a command line as root. Then follow these steps.

```
sudo apt-get update 
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

This should install the ATI drivers.

Then you might want to take a look at the xorg file. To do this just type

```
vi /etc/X11/xorg.conf
```

You are looking for the line that reads

Section "Monitor"
	Identifier "Monitor1"
	Option "DPMS"
	HorizSync 28-60
	**VertRefresh 43-60**
EndSection

Change the vertical refresh rate to something you know your monitor can handle. To change something in vi just type i and make the changes. Hit esc to stop editting and type ZZ to quit and save changes. Reboot with the command 

```
reboot
```

Let me know if this doesnt help. Check out this site if you need more help for driver [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

