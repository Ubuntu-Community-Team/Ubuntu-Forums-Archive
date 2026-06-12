---
title: "How to config idle suspend at login screen? (Ubuntu 19.04)"
date: 2019-08-19
forum: General Help
---

### Post by anville on 2019-08-19
I recently did a fresh install on Ubuntu 19.04 on a new NUC.  Things are going swimmingly, but one issue is still nagging me.  

If, directly after boot up, or if no one is logged in, and the login screen (I think it's gdm3?) is idle, eventually the black screen saver comes on, but I can see still see the mouse cursor, so the (ASUS) LCD display is still active.  What I'd like to happen is that after a set amount of time, say 10 minutes, the system should suspend/sleep, and I could then wake it with a key press.  
While searching, I've actually run into a number of posts with the opposite problem where they want the system to *not* suspend while idle on the login screen.  I should be so lucky :-)

Does anyone have a hint for me?  How active suspend-on-idle for the login screen, and how to maybe set the timing?

Thanks!

---

### Post by TheFu on 2019-08-20
Suspend?
/etc/systemd/logind.conf 

I don't know if this exists/works in 19.04.  I don't have 19.04 anywhere. Strictly LTS here.

---

### Post by anville on 2019-08-21
I tried fiddling values with logind.conf, but it didn't seem to do the job.

After some more searching though, I was able to find the seeds of the solution for me.

First, I needed to use su to switch to user "gdm":
[FONT=courier new]
   sudo su - gdm -s /bin/bash

[FONT=arial][/FONT]
[/FONT](If running in a non-GUI context, such as ssh, I also needed to run : [FONT=courier new]export $(dbus-launch)[/FONT]  )

Then I was able to set some gnome settings as the the user "gdm"
[FONT=courier new]
  GSETTINGS_BACKEND=dconf gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type suspend
  GSETTINGS_BACKEND=dconf gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 120[/FONT]

This sets the GDM3 screen to suspend after 2 minutes idle.  Verify the settings with "get" commands:

[FONT=courier new]  GSETTINGS_BACKEND=dconf gsettings get org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type
  GSETTINGS_BACKEND=dconf gsettings get org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout[/FONT]


These values can also be modified with GUI dconf-editor.  Before the su command, you need to run (as your regular user)
   [FONT=courier new]xhost +[/FONT]

and then after the change to gdm user via su, you can run:
   [FONT=courier new]dconf-editor[/FONT]

Be careful, though, with using this app.

---

### Post by TheFu on 2019-08-21
Off topic follows:
Be very careful using xhost + on a non-secured network.  Anyone can connect to your X/Server and have all sorts of fun.

sudo su - gdm -s /bin/bash
 could also be
**sudo -u gdm /bin/bash** or **sudo -i -u gdm /bin/bash** to get a fresh environment.

Something about sudo su just sits wrong with me for some reason. I have no facts to back up why. ;(
sudo su is the same as **sudo -s** 
sudo su - is the same as **sudo -i**
While I'm here. Don't use *cat* and never use *sudo gedit*.  *cat* is less useful than **tac** in the real world. Using sudo with most GUI programs will likely cause permissions problems in the user's HOME.  To edit system files, use a console editor like vim or nano with sudo 
or use **sudoedit**.
Sorry for digressing.  Whatever works that doesn't have unwanted side effects is the goal.

If the system doesn't use gdm, the userid for the login screen will be something different.  The DE is usually connected to the active DM, display manager.  Most DMs will have 'dm' in their process/program name, so search the process table to narrow the list down. On my system, 
```
/usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
```
is the X/Server process command line, so lightdm is the DM used.

I usually just login to the system and suspend when I'm going away more than 30 minutes if the machine is in a secure location.  In public locations, I either lock it up or take it with me - yes, even to the toilet in a cafe.

---

