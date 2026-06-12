---
title: "Gnome screensaver settings problem - 12.10"
date: 2012-10-25
forum: General Help
---

### Post by timbalisto on 2012-10-25
I recently did a clean install of Ubuntu 12.10, and I followed a post-installation guide for installing xscreensaver. I purged gnome-screensaver, installed the needed xscreensaver files, and wrote a startup script to auto-start xscreensaver with no splash. Everything worked fine, but I didn't like the look of the lockscreen that xscreensaver used. So I reinstalled gnome-screensaver, did a killall of xscreensaver, and changed the startup script to launch gnome-screensaver instead of xscreensaver. 

I'm unable to find the settings for gnome-screensaver. Typing  "gnome-screensaver" in the dash yields no results. Typing "screensaver" in the dash only gives me the settings for xscreensaver. 

Here is the result of typing "sudo gnome-screensaver" in the terminal
```
tim@lappy:~$ sudo gnome-screensaver

** (gnome-screensaver:20076): WARNING **: Couldn't get presence status: The name org.gnome.SessionManager was not provided by any .service files
```Here is the original startup script for xscreensaver in /etc/xdg/startup/
```
[Desktop Entry]
Name=Screensaver
Type=Application
Exec=xscreensaver -nosplash
```I would like to know how to get to the gnome-screensaver settings.  Any help is appreciated, thanks.

---

### Post by timbalisto on 2012-10-26
Bumpity bump-bump. 

Bumpity bump-bump. 

Look at that thread go.

---

### Post by JOHNNYG713 on 2012-10-26
It cant find it because it isn’t there !:( the daemon is, but not the application, That is why you have to use xscreensaver ! there is no gnome screensaver application at this time.

---

