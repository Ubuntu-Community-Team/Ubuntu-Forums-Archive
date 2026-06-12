---
title: "Session switching does not work"
date: 2008-05-17
forum: General Help
---

### Post by hfilter on 2008-05-17
I choose "Switch User" and login as another user. When I try to get back into my first session by hitting Ctrl-Alt-F7 the screen shows up with a blank white screen and only a mouse cursor.

I'm using Hardy on a Dell XPS1330 with Nvidia proprietary drivers.

Any help on troubleshooting this issue would be appreciated.

Thanks
Heinrich

---

### Post by hfilter on 2008-05-17
Hi all

I found a workaround [here]("https://bugs.launchpad.net/dell/+bug/160264")
This problem seems to be on the unlock screen. Apparently it is a Nvidia bug that affects pop-up screens
Even though the screen is white the cursor still changes to the "Insert" cursor when moved over the password field. If you click and enter password followed by "Enter" you get back into the session.

If anyone has information how to fix this problem please let me know.

Thanks
Heinrich

---

### Post by judabuddhist on 2008-05-18
The actual workaround from the above link is

> 
Go to System --> Administration --> Software Sources and select the Third-Party Software tab. Click on Add and enter the following line:

    deb [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) hardy main

Then click on Add again and enter the following line:

    deb-src [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) hardy main

Click on Close, then on Reload. Shortly your software updater will indicate that there are updates available for compiz. Install them, restart your machine, and voila!


I don't know how much of a hack this is, but it seems to be working for me.

---

### Post by DrClaw27 on 2008-05-31
If it's not a security risk for you can edit the preferences in the user switcher so that it doesn't lock the screen when you switch.

---

