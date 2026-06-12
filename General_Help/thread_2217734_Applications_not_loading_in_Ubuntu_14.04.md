---
title: "Applications not loading in Ubuntu 14.04"
date: 2014-04-18
forum: General Help
---

### Post by Bradley_Ware on 2014-04-18
I am fairly new to Ubuntu so can you please explain any fixes in detail.

I have just installed Ubuntu 14.04 and have encountered issues with applications not loading. I would start the application and the icon would popup in the lefthand toolbar but no gui will appear on the screen. I have also attempted to run the apps from within the terminal and the same problem occurs. I have recreated this problem so far with Gnome System Monitor and Wine but i assume there any more apps that are not working. 

Any help will be appreciated.

---

### Post by Mark Phelps on 2014-04-18
IS this specific to Wine related apps? Would be useful to know that.

---

### Post by 23dornot23d on 2014-04-18
Any applications that you find are not working ...... type the name in a terminal and see if you can get them to run
there ...... as more information will come back about why they are not running.

Usually you can find what to type in the terminal in the properties of the application in question as a example below .......

> 

K53SV:~$ gnome-system-monitor

** (gnome-system-monitor:2953): WARNING **: SELinux was found but is not enabled.




---

### Post by Bradley_Ware on 2014-04-18
This is not just wine related apps. I also have the problem with Gnome System Monitor

I did run gnome system monitor from within the terminal and i got the error shown in the previous post. I attempted to fix that error by following steps shown in another post and that got rid of the SElinux error but now when i run that command, it just freezes the terminal.

---

### Post by carl4926 on 2014-04-18
One thing I make sure I do after installing Wine. Is reboot.

I'm find stuff works really well in wine with 14.04. Better than ever.

No other issues (except chromium which a known regression from upstream)

---

### Post by Bradley_Ware on 2014-04-18
I have also managed to recreate the issue with Oracle Virtualbox so this is definitely not related to Wine.

---

### Post by Bradley_Ware on 2014-04-18
Update: I have reinstalled 14.04 from live usb and the issue still occurs
            I have also installed 12.04 then done the upgrade to 14.04 and it still occurs
            The apps that are affected appear to be random. I have  installed apps from the terminal and software centre and some work and  some dont 
      [SIZE=1]         The apps that are working are Gparted  Patition Editor and Google Chrome however VLC Media Player, Oracle VM  Virtualbox, Virtualbox(from the software centre) don't work[/SIZE]


Any ideas?

---

### Post by Bradley_Ware on 2014-04-18
Bump

---

### Post by carl4926 on 2014-04-18
> [COLOR=#000000] I have also attempted to run the apps from within the terminal and the same problem occurs.[/COLOR]And what feedback did you get from the terminal

The issues you relate are unique to you, so I can only assume it's hardware related.

Can you confirm the behaviour in 12.04?

---

### Post by Bradley_Ware on 2014-04-19
Solved
The issue was the use of an external monitor as my laptop monitor is broke,  however the laptop monitor was still enabled in system settings. I turned off the built in display and now everything works perfectly.

---

