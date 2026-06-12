---
title: "Can't access /etc/X11/xorg.conf"
date: 2005-03-28
forum: General Help
---

### Post by LongTooth on 2005-03-28
Wanting to disable the Nvidia splash screen on boot-up, I altered the /etc/Xll/xorg.conf by using this step from the How To on Nvidia.

" Add the following line just below the Driver "nvidia" line If you don't want the nVidia Splash logo to show at start up.

Option "NoLogo" "on"

On reboot, the GUI does not start. Of course I get an error message.  Using 'sudo dpkg-reconfigure xserver-xorg' I follow the instructions. But that doesn't help. The error message: "Xserver-Xorg post inst warning; Not updating /etc/X11/xorg.conf; file has been coustomized. 

I'm back at the sign on prompt. I know I'll have to delete the 'NoLogo' 'On' I added but I have no access to that file. After logging on I startx but it mentions the added No Logo on I inserted as the reason for not starting. And trying "sudo gedit /etc/X11/xorg.conf" will not let me in. 

I know I can fix my screw-up if I just had a little help from my friends:)

By the way I'm using Hoary.

Thanks.

---

### Post by sunscape on 2005-03-28
Try sudo pico /etc/X11/xorg.conf

You can not use gedit unless you are running X

Also, if you want to re-create your xorg.conf file, and the file is customized, then you must first delete the custom file. So, a quick sudo rm xorg.conf will do the trick. I suggest you backup the file first if you made any changes you wish to keep.

---

### Post by LongTooth on 2005-03-28
Using Pico did it. Not realizing I couldn't run gedit without the xserver, Pico or other editors like Pico are needed to do work like this. It was hell learning Pico on the fly but I did. Well, enough to correct my blunder. 

At the logon prompt I did so and with 'sudo pico /X11/xorg.conf' I was able to delete the line I added which prevented the Xserver from coming on line and save my correction to the file. My Hoary is back and I'm breathing a sigh of relief. 

Things I've learned as a result:

1. Leave well enough alone. (Doubt I will. Thank heaven for the forum).
2. Learn an editor like Pico just in case. You can bet your bottom dollar I will.

Thanks

P.S. Just how do I get rid of the Nvidia splash? So much about leaving well enough alone:)

---

