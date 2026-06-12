---
title: "Wine restarts X"
date: 2007-01-11
forum: General Help
---

### Post by Icarus76 on 2007-01-11
Hi, this is my first post in this community.

I have a strange problem. I'm using Edgy and wine 0.9.29 in Gnome without no problem since his release. But today, every time i will run wine my X crashes and restart without apparent reason. Running winecfg gives me the same problem, uninstalling and reinstalling wine gives me the same problem.

How can i repair this?

Thanks in advance.

---

### Post by kebes on 2007-01-11
Does wine crash X with *every* application, or only with *some* applications?

For instance, try running wine on the example apps that they package with wine. In a terminal, go:

cd ~/.wine/drive_c/windows/
wine notepad.exe

Does even that simple app crash everything?


You mentioned that it only stopped working recently. Is this coincident with the recent upgrade of wine from 0.9.28 to 0.9.29 ? If so, this is very likely a wine bug and if you want to get back your previous functionality, you should consider downgrading to the previous version (until the next version of wine).

Try uninstalling wine and reinstalling a previous version. (Instead of using the up-to-date wine repository, you could use the version in the Ubuntu repository...). Does that fix it?


If *every* version of wine causes the crash, then I guess the problem is with your X environment. Have you changed anything about it recently? Enabled/disable a video driver, hardware acceleration, etc.? (Have you modified your xorg.conf recently?)

Edit: Oh... and welcome to the community!

---

### Post by Icarus76 on 2007-01-12
Uninstalling and reinstalling an older wine version didn't solve the problem. I didn't changed xorg.conf but the problem was there. I tried to reinstall nvidia drivers and bingo! seems like i erased a necessary driver symlink accidentally. 
Nvididia driver reinstalled and problem solved.

Thanks for your help.

---

### Post by LaneLester on 2007-01-13
> **Icarus76 said:**
> I tried to reinstall nvidia drivers and bingo! seems like i erased a necessary driver symlink accidentally. 
Nvididia driver reinstalled and problem solved.

Maybe that's my problem. Wine was working flawlessly for me in Edgy until I added a second monitor and used nvidia-settings to enable the second monitor. Now starting any program with wine causes X to crash back to the login.

I tried so many different ways to install the nvidia drivers that I don't remember what worked, and I'm afraid to reinstall. That's one reason I keep ignoring the upgrade to the newer linux files.

Later: Win4Lin would also crash X, so I bit the bullet and reinstalled Ubuntu from scratch. I had the important things saved, so it was not a hard job to get going again. I installed [Alberto Milone's nvidia driver](http://albertomilone.com/latest_nvidia_udsf_edgy.html). I did the right thing, because now everything is working: two monitors with independent desktops, GFX, wine, etc.

Lane

---

### Post by mmcmonster on 2007-01-13
I had the same problem.  Unfortunately, I've forgotten how to install the generic nvidia drivers that are in Dapper Universe.  So now I'm running the `nv` drivers in xorg.conf.

Why did this happen?  I certainly didn't mess around with the config files when this went haywire. :-(

---

### Post by LaneLester on 2007-01-13
I believe that nvidia-settings did something more than just write a new xorg.conf. Even going back to my pre-nvidia-settings xorg.conf did not fix the wine problem.

It's probably something simple that needs to be restored, but I'm not very hopeful about finding out what it is. I'm afraid I'm looking at a complete reinstall of Ubuntu. :( 

Later: See my added note in previous post above. All is well now.

Lane

---

### Post by mmcmonster on 2007-01-20
I'm not sure if this will help anyone else, but I had originally installed the nvidia drivers using envy.  So I just went back and reinstalled with envy and everything went fine.

---

### Post by hanman on 2007-01-21
I, too, had this problem with Wine and the nVidia drivers.  Reinstalling the drivers with Envy sorted everything out for me also.  Beryl will also cause the same behavior, just in case anyone else was having trouble with it and not Wine.

---

### Post by LaneLester on 2007-01-24
I did a complete reinstall of Edgy (for other reasons) and used Envy for the driver install. But I can't run Wine apps with two separate monitors set up as separate windows. Wine apps error out like this:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  70 (X_PolyFillRectangle)
  Serial number of failed request:  148
  Current serial number in output stream:  156

Lane

---

### Post by headchange on 2007-01-29
thanks a lot for the insight on this post helped out a lot, yeah i had the same problem, i didnt mess with any hardware drivers or any settings wine just kept crashing x, wineconfig did the same thing, but anyways thanks for the help

---

### Post by uboltun on 2007-06-07
Reinstalling nvidia driver fixed the problem for me. During the installation it complained something about 
"libglx.so is not a link".

---

