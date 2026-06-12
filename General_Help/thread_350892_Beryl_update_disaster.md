---
title: "Beryl update disaster"
date: 2007-02-01
forum: General Help
---

### Post by bazcor on 2007-02-01
I have just received a number of updates for the Beryl desktop. These have made Beryl unusable, with all windows stuck in one place on the screen. One of the updates threw up an error message and didn't install, this was the plugins update.

Has anyone else experienced this and is there a way back to a working system?

TIA .. Barry

---

### Post by pyrforos on 2007-02-01
same problem here!With the last two updates the same thing!broken system!please guys help!
ati radeon 9550 - kubuntu edgy

---

### Post by db9s on 2007-02-01
same here!!!!

---

### Post by db9s on 2007-02-01
i manually got it to install plugins but even after that, Beryl stopped working!
these are the messages I got for system compatibility check (remember I had it working before the update)


```

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing


```

---

### Post by JamieC on 2007-02-01
I saw the updates earlier and was weary of installing them (considering they were also broken last time). I was awaiting such a thread before performing the updates, so thanks for the heads up guys.

---

### Post by tocleora on 2007-02-01
I *just* got Beryl working yesterday.  Excited about the update I received this morning... Mine failed too.  Here's a screen shot of what I see.  The gdk error came after I tried to reset the window border with emerald.  The other error was actually one I got before.  *sigh*

---

### Post by tocleora on 2007-02-01
> **JamieC said:**
> I saw the updates earlier and was weary of installing them (considering they were also broken last time). I was awaiting such a thread before performing the updates, so thanks for the heads up guys.

So how did they get fixed?

---

### Post by Waappu on 2007-02-01
Hi

Install and updates from Treviño&#8217;s SVN repository is working ok to me. Use this at own risk if you don't use these repos already

Type in terminal ```
gksudo gedit /etc/apt/sources.list
```
Change your current Beryl repos to these ones
```
deb http://3v1n0.tuxfamily.org edgy beryl-svn
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn
```
then type in terminal```
wget http://3v1n0.tuxfamily.org/DD800CD9.gpg -O- | sudo apt-key add -
sudo aptitude update
sudo aptitude upgrade
sudo aptitude remove beryl-settings-bindings
sudo aptitude install beryl
```

If still some problems you can try reset all Beryl plugin settings typing in terminal
```
mv ~/.beryl ~/beryl_setting_folder_backup
```

Hope this helps

---

### Post by ronmarley1 on 2007-02-01
I just uninstalled beryl and beryl-core and resinstalled and all is fine now.

---

### Post by JamieC on 2007-02-01
> **tocleora said:**
> So how did they get fixed?

Further updates were released to patch the bugs created by the previous update. Some people resorted to using Synaptic to downgrade  the packages and lock the version until the fixed packages were available in the repositories. 

There is also a thread at the [Beryl forums](http://forum.beryl-project.org/viewtopic.php?f=36&t=2977&hilit=) and a [bug report](http://bugs.beryl-project.org/ticket/1092) has been submitted.

---

### Post by shareMenaPeace on 2007-02-01
Hi, im curious i installed beryl yesterday for the first time it is version 0.2.0 beta2 and i dont got updates yet -- works quiet ok sometimes i need to restart it.

---

### Post by glabouni on 2007-02-01
> **bazcor said:**
> is there a way back to a working system?

it's pretty simple: stop running beryl-manager till this is fixed.

I'assume you've added beryl-manager to load at session start.

beryl-manager man page (in Options section) reads: 
> --no-force-window-manager
don&#8217;t replace running window manager at start

--no-force-decorator
don&#8217;t replace an eventually running decorator

this has been [pointed out to me by Ramses de Norre]("http://ubuntuforums.org/showthread.php?t=348766"):
> **Ramses de Norre said:**
> Yes you're absolutely right. And I think the fastest way to stop beryl from starting is aliasing beryl-manager to ```
beryl-manager --no-force-window-manager --no-force-decorator
``` which would make that although beryl-manager is started it wont load his window manager nor emerald.)

---

### Post by eooon on 2007-02-01
This is from a post on the official forums: (removes Beryl, reinstalls, stops update) It worked fine for me, even kept my old settings!

After the upgrade, I got the same issues. If I ran "beryl" I got non-power-of-two textures missing; "beryl" gave me a segmentation fault.

I managed to roll back to the previous version like so:
Code:

# Remove bad packages
dpkg -l | egrep "beryl|emerald" | cut -d\  -f 3 | xargs aptitude remove

# Install last version
aptitude install {beryl-manager,beryl,beryl-settings,beryl-plugins,beryl-core,beryl-plugins-data,beryl-settings-bindings,libberyldecoration0,libberylsettings0,emerald-themes,libemeraldengine0,libberyldecoration0,emerald}=0.1.99.2~0beryl1

# Prevent apt from upgrading to the bad version
(aptitude search beryl; aptitude search emerald) | cut -c5- | cut -f1 -d" " | while read i; do aptitude forbid-version ${i}=0.1.9999.1~0beryl1;done

---

### Post by tocleora on 2007-02-02
This is what I love about Linux... In Windows if I installed an update that crapped out the app I would have to communicate with the software company and hope they get it fixed in a timely manner.  With Linux, you can just go to a forum like this, someone has a work around.  Thanks to this thread I had it back up and running fairly shortly after the initial update that broke it.  Now if I can just get that Porsche and Scarlette will start returning my calls, I'll be set. :D

---

