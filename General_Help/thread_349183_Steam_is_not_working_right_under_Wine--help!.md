---
title: "Steam is not working right under Wine--help!"
date: 2007-01-29
forum: General Help
---

### Post by presbp on 2007-01-29
I used wine to install Steam from steam.exe but when I open up steam the steam window opens but all the buttons in steam that are supposed to have text have no text in them..  

I have attached the png images that show this.  Thanks

---

### Post by daemonoid on 2007-01-30
I found this workaround:

Missing fonts workaround
by Krzysztof Lichota on Saturday October 29th 2005, 19:00
When running from standard install no text is displayed.
There was an advice to install tahoma.ttf font but it is not freely available. So I worked around it in the following way:
1. Open .wine/system.reg in text editor.
2. Find key [Software\\Microsoft\\Windows NT\\CurrentVersion\\FontSubstitutes]
3. Add subkey:
"Tahoma"="Times New Roman"

---

### Post by nevin on 2007-02-08
yeah, the main problem is you need the text file... you could download it or copy it from a windows partition (like i did) and paste it to the blahblah/windows/fonts folder under your wine directory.  it'll work then... you might run into a problem trying to type in your user name and password, but i just right clicked in the field, clicked paste, and then it let me type.

oh yeah, i dont know if it'll work for you, but i couldn't get it to work so well with berly... but im using xgl for my ati card... so maybe it'll work for you, maybe not.

goood luck.

---

### Post by Steve H on 2007-04-15
I've suddenly got this problem as well. All i can think off is that i changed the Ubuntu system font properties using //System/Preferences/Fonts.

After that Steam doesn't show any fonts anymore, i can't see servers or games or anything....

---

### Post by Steve H on 2007-04-15
I have found that this was an issue caused by the latest update of WINE: found the answer here

[http://ubuntuforums.org/showthread.php?t=409286](http://ubuntuforums.org/showthread.php?t=409286)

and this did the trick:

> **gschoper said:**
> Same issue here after updating to 0.9.35. However, I was able to re-install 0.9.34 which was hanging out on my machine in /var/cache/apt/archives:

```
cd /var/cache/apt/archives
sudo dpkg -i wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb

```

gschoper

Good luck hope this helps

---

### Post by duke3z on 2007-04-22
I had everything working until the 7.04 release and the update of wine.  Now the STEAM installer is .msi instead of .exe.  Either why msi or exe wine should pick it up but it doesn't for some silly reason.  Is it just me or is anyone else facing this problem too?  What is up with COD2 and wine anyway??  will it ever play on Ubuntu?

---

### Post by Radomir on 2007-04-22
You need Tahoma font in your wine installation to run steam properly - copy tahoma.ttf from existing windows installation to /home/[username]/.wine/drive_c/windows/fonts/. Worked for me...
Sry, did not read the second answer. But as long as you have an existing legal windows install, it's legal to use the font.

---

### Post by Steve H on 2007-04-24
To use a .msi in WINE you have to use the following command (for steaminstall.msi):

> wine msiexec  /i SteamInstall.msi

As for COD2, keep checking the [_wine appDB _]("http://appdb.winehq.org/")site, they have all the currently running apps listed there. Alternatively, try running it and submit a report, so others can judge how well it works, or even help to get it working.

Hope that helps.

---

