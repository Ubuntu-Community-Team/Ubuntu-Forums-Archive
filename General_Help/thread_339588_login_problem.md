---
title: "login problem"
date: 2007-01-16
forum: General Help
---

### Post by ComunisTico on 2007-01-16
hi i got a problem with ubuntu/kubuntu...

i was trying to install xgl/beryl with the guide on ubuntuguide 
> [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

i followed it by the book ad at the end the pc freezed and i had to reboot the pc i couldent log in,  neither in ubunto xgl/beryl nor kubuntu...  i put the username and password and it keept returning to the same point. 

all i can do is login ubuntu via console with  "startx"  i try to "startkde" and it gives me some things and t keeps giving me error.

when i open a terminal on ubuntu once loged in i cant use it without being root, try to get of root and closes me the terminal...


if anyone knows how i can go back or atleast letting me log on normaly id apreciate it thnks

---

### Post by riven0 on 2007-01-16
Try uninstalling Beryl. If you can log into root, do that. 

Hit CTRL + ALT + F1, login and type** sudo -s -H**. If this doesn't work, try to gain access by going to Recovery Mode in Grub. Again, log in as root: **sudo -s -H**

Now, get rid of Beryl:

> apt-get autoremove beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings emerald emerald-themes

Get rid of the xgl startup script:

> rm -r /usr/bin/startxgl.sh

Open the xsession manager and get rid of the XGL entry:

> nano -w /usr/share/xsessions/xgl.desktop

> Delete this entry:
[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

Now reboot, and when you get to the login screen, make sure you go to Sessions >> Gnome and then log in.

---

