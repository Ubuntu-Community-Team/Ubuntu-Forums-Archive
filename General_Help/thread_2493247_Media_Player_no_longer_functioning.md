---
title: "Media Player no longer functioning"
date: 2023-12-07
forum: General Help
---

### Post by redtoads on 2023-12-07
I have no idea what to do, I can no longer play/review uploaded videos on my computer.  Will not correct after multiple restarts.  Looking for help.

---

### Post by TheFu on 2023-12-07
I don't know what "media player" is, but haven't used the default player in about 10 yrs, perhaps longer.  I think it was gstreamer which I always found a pile of steaming do-do. We all have different opinions on software. That's fine if you like it.  Someone else will need to help.

install **smplayer** and **mpv**, then use those.
mpv is a CLI tool, but smplayer is a GUI that will use it, if you need a GUI.

If you want more of a kitchen sink solution, there's always VLC.  I'd suggest avoiding the snap package version, but that's because I don't like the constraints mandated by snaps.

Also, with video playback, whether you are using Wayland or Xorg could matter, so that information would be helpful to others seeking to be helpful.

The problem description if pretty vague.  Could be anything from file permissions to a dead GPU. No way to tell.

---

### Post by redtoads on 2023-12-08
Thank you but since this is a new issue I have no idea where to even look for a replacement software.  See enclosure.  That is what I get when I try to play video whether it has been uploaded to my pc or from my phone when it is connected to the pc.  I have not enjoyed Ubuntu/firefox since it was installed on my Dell.

I am quite certain this issue started after an update.

Also, half the time the SD card reader is unresponsive on my computer since Ubuntu has been installed (I did not install it, a tech did after replacing my hard drive two years ago).

---

### Post by TheFu on 2023-12-08
> **redtoads said:**
> Thank you but since this is a new issue I have no idea where to even look for a replacement software.  See enclosure.  That is what I get when I try to play video whether it has been uploaded to my pc or from my phone when it is connected to the pc.  I have not enjoyed Ubuntu/firefox since it was installed on my Dell.

I am quite certain this issue started after an update.

Also, half the time the SD card reader is unresponsive on my computer since Ubuntu has been installed (I did not install it, a tech did after replacing my hard drive two years ago).

Software is in the Ubuntu repos.  Use a package manager to install it.  

*Software Center* is the normal GUI package manager.  This is basic Linux stuff.   It should be in the menu, somewhere.
Or you can open a terminal and run a few commands. That's how I'd do it.

```
sudo apt update
sudo apt install mpv smplayer
```
Might need to logout and login again for SMPlayer do be shown in the menu.

BTW, that image suggested corrective action. Did you try it?  I'd guess the command would be
```
sudo apt install --reinstall totem
```
"Totem" is the program being used according to the message.  I'm not a fan, but Ubuntu has been shipping it as the default player for years. I don't know why, but that's their choice.  It doesn't hurt to have both installed.

Non-function software can be caused by all sorts of issues.  My first place to check would be the system log files. Plenty of information about problems are usually put there.  Google "ubuntu log files" for how to do that.

If you are really new to Linux, I'm not the best person to help.  Someone else who is a GUI-centric user would definitely be better than me.

---

### Post by redtoads on 2023-12-08
Thank you for your help.

---

