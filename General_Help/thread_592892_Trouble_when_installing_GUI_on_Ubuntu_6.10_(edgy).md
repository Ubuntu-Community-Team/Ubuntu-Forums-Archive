---
title: "Trouble when installing GUI on Ubuntu 6.10 (edgy)"
date: 2007-10-26
forum: General Help
---

### Post by jonkennedy on 2007-10-26
I have just upgraded my Ubuntu 6.06 LAMP Server to 6.10 (edgy), and then tried installing the GUI using the sudo apt-get install Ubuntu-desktop command. The installation for the GUI seemed to go smoothly, then I choose my resolution once it asked me, then restarted the server. Once I restarted, after it loaded the GRUB Loader, I got a black screen and nothing happens. Here are the specs for the computer that Ubuntu is currently running on:

500MHz Pentium 3 CPU
384MB RAM
160GB IDE Hard Drive

Could it be that Ubuntu's GUI takes up too many recourses for the computer to handle? I have used other Linux distributions on it before that have worked fine, such as SUSE and Fedora, but I'm not sure how many recourses Ubuntu uses.

---

### Post by dabl on 2007-10-26
It probably didn't auto-detect your graphics card correctly.  At that black screen, you may be able to Alt-F1 or Ctrl-Alt-F1 to a console, and proceed to log in at the text prompt.  If so, run the xorg configuration script

```
sudo dpkg-reconfigure xserver-xorg
```

On the first screen choose "NO" to auto-detect, and on the second screen choose "VESA" for the display type.  You can accept defaults for the rest of the keyboard and mouse types until you get to the monitor section.  Choose a comfortable resolution like 1024 x 768, and choose refresh rates that are within the specs of your CRT or LCD.  At the end of the script it will dump you back to the CLI.  Run ```
startx
``` and you should have a decent GUI.  :)

---

### Post by jonkennedy on 2007-10-26
It works! :KS Thank you so much for your help.

---

