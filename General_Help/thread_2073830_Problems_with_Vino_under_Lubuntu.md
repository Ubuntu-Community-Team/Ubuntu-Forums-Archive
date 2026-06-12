---
title: "Problems with Vino under Lubuntu"
date: 2012-10-20
forum: General Help
---

### Post by samuelellis on 2012-10-20
Good morning/Afternoon

I have just installed Lubuntu version 12.04.1 on a box i am setting up but i am having trouble with Vino the VNC server

basically Vino is installed and works fine but it wont start at logon, the server starts if i run /user/lib/vino/vino-server from a command line so i know it is configured correctly but i just cannot get it to start at logon

I have followed this link ( [https://wiki.edubuntu.org/Lubuntu/RemoteDesktop](https://wiki.edubuntu.org/Lubuntu/RemoteDesktop) ) to set up VNC but when i access the desktop session settings to add vino to startup i cannot see an option to do it 

Sorry for the daft question but last time i setup VNC on Ubuntu was perhaps 4 years ago so i have completely forgotten how to do it

---

### Post by ajgreeny on 2012-10-20
I presume your problem is more related to how to autostart programs in Lubuntu so I will offer this in the hope that it helps.

There are several ways to autostart programs in Lubuntu.
Include command to start apps for just one user in the list in:-
**/home/*<user>*/.config/lxsession/Lubuntu/autostart**   eg,    
```
parcellite            #(This is the normal command for parcellite but you could use the full path, /usr/bin/parcelite)

```
Other applications for all users can go in **/etc/xdg/autostart** as the .desktop configuration file which you can copy from **/usr/share/applications** for the app you want.

Finally you can add an entry to **/etc/xdg/lxsession/Lubuntu/autostart**  in form    
```
@nm-applet
@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@xfce4-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
@notap  #(this is my shell script to stop trackpad tap-to-click, which I copied to /usr/bin)
```
I am not completely aware of the reasons for the last two options for placing entries, but I assume there must be a reason for the different places.  Try them out to see which works best for vino, which I know nothing about so can not tell you more in any detail.

---

### Post by samuelellis on 2012-10-20
that is brilliant, adding the command to /etc/xdg/lxsession/Lubuntu/autostart seems to have fixed it

Cheers fella - its always the daft things you forget isnt it

---

