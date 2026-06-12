---
title: "Kodi has taken over desktop"
date: 2018-01-29
forum: General Help
---

### Post by jediller on 2018-01-29
Have Kodi installed. When I exit Kodi, it logs me out of the desktop. When I log back in, it has Kodi up. From Kodi I can suspend, reboot, shutdown system or exit, but Kodi will be up waiting for me with no obvious way to return to my desktop.
I set Kodi to a Windowed version, but while Kodi became a Window in the corner of my screen, none of the rest of my desktop appears

How do I exit Kodi

I have used several versions of Kodi over the years, and none had this problem. Exit returned me to my system previously.

---

### Post by TheFu on 2018-01-29
Pick the desktop you want prior to login. The last selected desktop will be used unless it is changed to something else.  

Many people use dedicated machines for kodi, so the way it is setup is very convenient.

---

### Post by mastablasta on 2018-01-30
Kodi is a desktop interface basically. just focused in media content. it also has database at the back. but it is not just an app.

---

### Post by TheFu on 2018-01-30
After logging in with a different DE or window manager, you can run kodi from a terminal.  I do this from time to time.  **kodi-standalone** is the name of the program.  When run this way, exit will just shutdown kodi and leave the underlying DE/WM running.

---

### Post by jediller on 2018-01-30
I only have one user account defined. When I login to the account I have kodi. When I exit Kodi, it logs me out of the account. Hence I do not have a choice of desktops. I have one desktop that Kodi has 'taken over'

---

### Post by again? on 2018-01-30
You may only have one account but kodi also installs a session for just kodi which is accessible from the greeter
before you log in.
You can boot into the kodi session or your ubuntu session where kodi runs in a window or fullscreen.

Where the session menu is depends on your release.
Which ubuntu are you using?

---

### Post by TheFu on 2018-01-31
Thanks gruber2 for explaining better than I could.

At the login screen there is a "gear" icon for most Ubuntu GUI installs. Click that. Choose a different DE/WM.

Update: Yesterday, I was helping a friend change their GUI. After clicking the "gear" and selecting the alternate DE, he logged in and was shown the prior DE again.  Seems that more than a mouse click is needed on the DE selection in the "gear" to get it to "stick".  Afterwards, he wanted to switch back and had a similar problem. Clicking with a mouse wasn't sufficient to select a different DE/WM.  I wasn't driving, so I don't know what he did, but somehow he was able to select.

---

### Post by SeanKD on 2018-02-16
> **jediller said:**
> Have Kodi installed. When I exit Kodi, it logs me out of the desktop. When I log back in, it has Kodi up. From Kodi I can suspend, reboot, shutdown system or exit, but Kodi will be up waiting for me with no obvious way to return to my desktop.
I set Kodi to a Windowed version, but while Kodi became a Window in the corner of my screen, none of the rest of my desktop appears

How do I exit Kodi

I have used several versions of Kodi over the years, and none had this problem. Exit returned me to my system previously.

I ran into a similar problem after installing Kodi 17.6. When I rebooted my system for the first time after installing Kodi and logged in, I was logged into Kodi Standalone. There was no getting to the desktop. The problem turned out to be that when Kodi was installed it set up a Kodi Standalone logon session and made it the default session without notifying me, the user, that it was doing so. One solution is to select the logon session you want at the logon (Ubuntu on Xorg in my case) and it will become the new default. I chose another option - to remove the Kodi logon session by doing the following:

1) Open a terminal.

2) Type ```
cd /usr/share/xsessions
``` and hit ENTER.

3) To simply remove it, type ```
sudo rm kodi.desktop
``` and hit ENTER.

4) To remove it but maintain a backup, type ```
sudo mv kodi.desktop kodi.desktop.bak
``` which will rename 'kodi.desktop' to 'kodi.desktop.bak'. 

Now, when you reboot your machine, the Kodi Standalone logon session will no longer be listed as an available option.

---

