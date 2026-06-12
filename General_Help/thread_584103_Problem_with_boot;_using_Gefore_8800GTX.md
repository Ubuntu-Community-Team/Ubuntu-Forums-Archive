---
title: "Problem with boot; using Gefore 8800GTX"
date: 2007-10-20
forum: General Help
---

### Post by darien42 on 2007-10-20
I have kind of an odd problem. Hopefully there is something that I can do to fix it. Here is the issue.

I updated to 7.1 and everything was working fine. No problems. I did some extra updates (updating the drivers for my video card; Geforce 8800GTX) and when I went to reboot the computer, the Ubuntu wouldnt normally start. It opens up a text based start, the screen flashes a couple of times and then it goes to a window stating that the monitor and the graphics card havent been set up properly. It gives me an option to configure it myself with some drop down menus and choose my monitor and GFX card. I choose the card, the monitor and configure the drivers but then I have to restart. At that point the Ubuntu will finally start but what sucks about this problem is that everytime I reset the computer AFTER i get into it, I have to do the who thing again.

Another thing is that I cant activate the restricted drivers to use the desktop enhancements. If I try to change the drivers, it will force me to reset them to the base drivers... in short it kinda sucks.

I tried to use envy but it keeps giving me an error of "There was an error in the installation process. You can see the log file /var/log/envy-installer.log"

I dont know what it is but for some reason, Gutsy doesnt like my computer. 


If there is anyone who can help, any advice would be greatly appreciated

Thanks,

Darien42

---

### Post by jrharvey on 2007-10-20
I have the EXACT same problem with an nvidia 8500 gt. Envy does not seem to work and the restricted drivers dont either. I have seen this problem ALOT with the gutsy release and im not sure if there is a fix yet but I hope there is soon. I dont really care about the desktop effects but I really need dual monitors and i cant do that with a generic driver.

---

### Post by darien42 on 2007-10-23
Anybody have any idea about this issue yet or is it still something thats in the works? 

Cheers,

Darien42

---

### Post by dirkdejager on 2007-10-24
I am having the same trouble with a 8500 GT. Please post if there is any help regarding this matter.

Dirk

---

### Post by dirkdejager on 2007-10-24
So,

I actually got the 8500GT in dual monitor mode to work by doing the following:

Downloaded the latest linux driver from Nvidia: ([http://www.nvidia.co.uk/object/linux_display_ia32_100.14.19_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_100.14.19_uk.html))

Followed the instructions on the following page:
([http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490))

Which actually worked out to be the following commands:

```

bash$ sudo aptitude install make gcc
bash$ sudo aptitude install pkg-config xserver-xorg-dev
bash$ sudo aptitude purge nvidia-glx
bash$ sudo aptitude purge nvidia-glx-new
bash$ sudo rm /etc/init.d/nvidia-glx
bash$ sudo rm /etc/init.d/nvidia-kernel
bash$ sudo rm /lib/linux-restricted-modules/.nvidia_new_installed

```

edit the file: /etc/default/linux-restricted-modules 
To say:
```

DISABLED_MODULES="nv nvidia_new"

```
Then reboot the machine into recovery mode, change to the directory where the newly downloaded Nvidia driver is. Run 
```

sh NVIDIA-Linux-x86-100.14.19-pkg1.run

```
Select to continue (Apparently Ubuntu uses different Runtime levels, so 1 is fine - [http://www.linuxquestions.org/questions/linux-newbie-8/running-without-x-server-464298/](http://www.linuxquestions.org/questions/linux-newbie-8/running-without-x-server-464298/))

Accept the license agreement, ensure you select the driver to automatically update the xconfig  file.

When complete, run startx!

Hope it helps.

Dirk

---

### Post by Qwerty_ on 2007-10-24
```
 sudo dpkg-reconfigure xserver-org
```

Might help to fix all of your issues.

---

