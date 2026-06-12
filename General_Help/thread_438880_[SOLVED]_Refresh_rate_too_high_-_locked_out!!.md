---
title: "[SOLVED] Refresh rate too high - locked out!!"
date: 2007-05-10
forum: General Help
---

### Post by mactece on 2007-05-10
I installed a new graphics card on my system - nvidia fx6200. I rebooted into Ubuntu fine then installed the 3rd party driver. This locked my screen at 800 x 600 with a refresh of 55Hz (KHz?) and wouldn't give me any other options. So I disabled the driver and rebooted. When I restarted I got the login screen but when the session started my screen went black with a "refresh out of range - 95Hz" message. Tried booting into a failsafe session but the same thing happened. 

Is there a terminal command I can use to set my screen resolution and refresh back to normal?

Thanks

David

PS posting message now (lunch break) but won't be able to try suggested solutions until tonight so please forgive me if you post a solution and I don't reply straight away.

---

### Post by ikonia on 2007-05-10
boot off the livecd, mount your disk and then edit the /etc/xorg.conf file to a lower refresh rate.

Booting fail safe should not cause you to have this problem though

---

### Post by renzokuken on 2007-05-10
alternatively, boot up, wait till it fails then press

Ctrl+Alt+F1 to get to a TTY terminal screen

login and enter

```
sudo dpkg-reconfigure xserver-xorg
```

follow the wizard and leave everything as it is until you get to the refresh rate screen and then change them to more approriate values, continue selecting everything else as it is.

reboot when finished and see what happens

---

### Post by scott_g on 2007-05-10
If you boot up using the live cd, then you can use the gtf tool.  Usage:

gtf vertres horrez refresh

or:

gtf 1280 1024 60

for 1280x1024@60hz.

Put the lines it produces in your xorg.conf file, under the monitor section, then reboot.  Make sure you have a corresponding resolution in your Modes section.

Good Luck,
Scott

---

### Post by mactece on 2007-06-18
Problem Solved - although I don't recommend the method.

New chip arrived the day after (XP2400 - dragging myself into the 21st century) so I installed that and when I rebooted  the bios reset a whole load of stuff. And lo and behold the problem with the graphics card was fixed. Not had any problems since. I'm now wondering if removing the card, rebooting and replacing would have done it also.

Thanks for everyone's help.

David

---

### Post by warcriminal on 2007-06-18
Another option is to boot into single user mode so that you can reset the graphics mode.

To get into single user mode follow these instructions;

[http://www.goitexpert.com/entry.cfm?entry=Reset-Linux-Password](http://www.goitexpert.com/entry.cfm?entry=Reset-Linux-Password)

 And then take Ikonia's advice to edit the /etc/xorg.conf file to a lower refresh rate.

---

