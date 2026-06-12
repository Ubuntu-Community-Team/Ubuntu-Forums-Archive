---
title: "how to inhibit suspend while file transfer over lan"
date: 2022-10-29
forum: General Help
---

### Post by altescoon on 2022-10-29
Hi there.

On my new kubuntu 22.4 machine i try to figure out how to tell my system not to suspend while files are transfered over lan.
This machine is kinda media server, that means it provides a network shared folder. My raspi will read files from there (mostly videos), sometimes over hours. Of course i don't want the Kubuntu machine to suspend then (normally suspending after 15 min). I don't want to turn suspension off and on again by hand every time i transfer files.

Is there an easy way in 2022? Or do i have to handle scripts like the ones in [this seven years old thread]("https://askubuntu.com/questions/576525/is-there-any-way-to-make-ubuntu-not-to-suspend-while-a-download-in-progress").

Thanks for your answers :-)
  Peter

---

### Post by TheFu on 2022-10-29
[https://www.freedesktop.org/wiki/Software/systemd/inhibit/](https://www.freedesktop.org/wiki/Software/systemd/inhibit/)

---

### Post by MAFoElffen on 2022-10-29
If it were running Gnome, instead of Kubuntu, I would suggest "Caffiene".

---

### Post by #&amp;thj^% on 2022-10-29
> **MAFoElffen said:**
> If it were running Gnome, instead of Kubuntu, I would suggest "Caffiene".

It works with KDE5  :[https://store.kde.org/p/1212005](https://store.kde.org/p/1212005)

---

### Post by altescoon on 2022-10-30
Thanks for the links.
I tried caffeine on kubuntu 04.22 without success. It shows no icon. When i start icon manually via menu and fill the cup, there is no effect.
I didn't try caffeine plus yet. 
Before i try: Caffeine inhibits suspend and screensaver when active, right? Even, when machine is really idle (no lan-access, no video, no musicplayer...), right?

If right, then this is not what i search for. This would be just a kind of shortcut to disable suspend manually. 
I am looking for an automated service: suspend, when idle, but don't, when streaming over lan (or watching youtube or listen to music over musicplayer), then suspend, when streaming ends.

---

### Post by TheFu on 2022-10-30
> **altescoon said:**
>  
If right, then this is not what i search for. This would be just a kind of shortcut to disable suspend manually. 
I am looking for an automated service: suspend, when idle, but don't, when streaming over lan (or watching youtube or listen to music over musicplayer), then suspend, when streaming ends.

How does the server know when streaming ends and it isn't just an extended bathroom break?  Thinks that appear as constant streaming to us don't appear that way to the computers.

BTW, it is possible to setup a sleep process to run at any time of day, automatically.  If the system is already asleep, it doesn't do anything, so there is little harm in making the system sleep at midnight daily, automatically.  It is really the end of the world if the server runs an extra 2 hours before sleeping on nights you don't use it?

You'd probably want to setup Wake-on-LAN for the next morning, which could be a button on a phone or automated from a different device.  Or don't automate waking and have a desktop that you use check if you are active doing something every 15 minutes, then wake the server automatically for you.  

Of course, if the playback device(s) are computers/phones, you could download the media to them for playback and send the remote server to sleep when the downloads finish.  You could even automate the downloads daily using rsync and a specific file that contains the files to be pulled. With rsync, if the files are already fully downloaded, that wouldn't cause much traffic and the system would sleep quickly after the rsync is seen as complete.

Lots of options are available with just a tiny bit of scripting and cron use.

When I'm recording a presentation, I'll run this script to keep the screen active and shutdown the screensaver:
```
#!/bin/bash
xset s off &
xset -dpms &

# Disable the screensaver
/usr/bin/xscreensaver-command -exit

## ######
Do presentation stuff
## ######

# Enable the screensaver
/usr/bin/xscreensaver &
xset +dpms &
xset s on &

```
In the "do presentation stuff, just do the downloads.  Under Wayland, this won't work.  It wouldn't take much to disable power management and re-enable it at the bottom.  I also don't have any "notifier" enabled - I hate, hate, hate, those popups that different apps think we need to know.  I suppose I could just login using a different account that isn't connected to anything else on the system for presentation mode. This would allow recording a clean desktop - though I typically switch to a clean workspace for that.

---

### Post by ajgreeny on 2022-10-30
I have used Xubuntu with Xfce for several years and within the power-manager panel applet there is an option to select **[B]Presentation Mode**[/B] which I find verry useful when using my computer as a media-server.

It stops the machine starting the screensaver, but more importantly, also disables the power-manager from suspending the computer, very annoying if half way through watching a film or similar.
I have no knowledge of other DEs or their ability to make use something similar but there may be some way.

---

