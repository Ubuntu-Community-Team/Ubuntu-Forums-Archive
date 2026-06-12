---
title: "After Hardy upgrade: compiz will only start with sudo"
date: 2008-04-27
forum: General Help
---

### Post by toobitz on 2008-04-27
So i'm one of the (I guess) many, many fellows who, once again, after upgrading Ubuntu, is left with the joyful task of figuring out how to get Compiz working again while it worked like a charm before upgrading. So...

I've got a Thinkpad T43p with the following video card:
```
01:00.0 VGA compatible controller: ATI Technologies Inc M24GL [Mobility FireGL V3200] (rev 80)
```

I was using the Open Source "ati" driver before upgrading and I acutally would like to continue to do so, but when I try to start compiz after upgrading in a terminal with compiz --replace &, I get:
```
Checking for Xgl: not present.
Found laptop using ati driver.
Found laptop using radeon driver.
Detected PCI ID for VGA: 01:00.0 0300: 1002:3154 (rev 80) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "switch_windows"
```

Xorg.0.log is here: [http://ubuntuusers.de/paste/204459/](http://ubuntuusers.de/paste/204459/)
the output of glxinfo is here: [http://ubuntuusers.de/paste/204461/](http://ubuntuusers.de/paste/204461/)
and here's my xorg.conf: [http://ubuntuusers.de/paste/204463/](http://ubuntuusers.de/paste/204463/) 

Of course I also tried to use the fglrx driver, tried both methods (using the driver/package provided by Ubuntu and tried building the driver by myself). None of these methods worked, when using the self built driver, I get a segmentation fault when entering "fglrxinfo" in a terminal..

I just don't get it why my previous configuration won't work anymore! But what's really strange is the following: when I enter the following
```
sudo compiz --replace &
```
then compiz will actually start and emerald too, with the following output:
```
Checking for Xgl: not present.
Found laptop using ati driver.
Found laptop using radeon driver.
Detected PCI ID for VGA: 01:00.0 0300: 1002:3154 (rev 80) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Couldn't find a perfect decorator match; trying all decorators
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

What's going on here? Anyone has a hint because I'm at a complete loss now...

---

### Post by akshar_patel_47 on 2008-04-27
If you're saying that the by using the code compiz is starting.. then go to system-> preferences-> sessions and add that code as a command in the startup programs. This will solve your problem.

---

### Post by toobitz on 2008-04-27
> If you're saying that the by using the code compiz is starting.. then go to system-> preferences-> sessions and add that code as a command in the startup programs. This will solve your problem.

Thanks for your reply! I know I could do that but I certainly don't want compiz to be running as root! And after using it like that for a couple of hours now, it doesn't "feel" all that good to me - e.g. the "Put" option from Compiz (Initiate Window Picker) doesn't work with the mouse movements...

---

### Post by toobitz on 2008-04-29
sorry 'bout the bump - but does anybody have any idea about this?

---

### Post by Rocket2DMn on 2008-04-30
You can try reinstalling compiz with
```
sudo apt-get remove --purge compiz
sudo apt-get install compiz
```
A lot of people have been having problems with compiz, and they have been extremely difficult to troubleshoot.  Seems to especially be a problem on systems that upgraded rather than fresh installs.

---

### Post by toobitz on 2008-04-30
Thanks Rocket2DMn, I halfway figured it out - you're right, these problems are really difficult to track down and yes, upgrades tend to cause problems too (I was having troubles with Compiz after all previous 2 or 3 upgrades).

My problem was that in my environment, the following variable was set:
```
LD_LIBRARY_PATH=/usr/lib/xorg
```
On my system, this directory contains the following files:
```

lrwxrwxrwx 1 root root     26 2007-10-23 19:12 /usr/lib/xorg/libGL.so -> /usr/lib/xorg/libGL.so.1.2
lrwxrwxrwx 1 root root     26 2007-10-23 19:12 /usr/lib/xorg/libGL.so.1 -> /usr/lib/xorg/libGL.so.1.2
-rw-r--r-- 1 root root 783362 2007-10-23 19:12 /usr/lib/xorg/libGL.so.1.2

```
So far, so good. Now obviously, the problem is that these files are also in /usr/lib!
```

lrwxrwxrwx 1 root root     10 2008-04-30 09:48 /usr/lib/libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root     12 2008-04-30 09:48 /usr/lib/libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 root root 394924 2008-04-06 00:06 /usr/lib/libGL.so.1.2

```

I have no idea where the files in /usr/lib/xorg come from, they don't belong to any package whereas the /usr/lib/libGL.so* files belong to the libgl1-mesa-glx package. And because my LD_LIBRARY_PATH was overriding the /usr/lib/libGL.so* ones, I was using these apparently old mesa GL libraries in /usr/lib/xorg...

Now I solved the problem by removing the /usr/lib/xorg/libGL* files - voilà, I can start Compiz again, with no problems at all.

---

### Post by Prof_NARF on 2008-06-20
> **toobitz said:**
> 
[...]
Now I solved the problem by removing the /usr/lib/xorg/libGL* files - voilà, I can start Compiz again, with no problems at all.

Hi, I had the same problem. But I solved it a little different. I don't think it is a good idea to delete these libraries. Maybe metacity won't work after that.

I solved it by editing my /etc/profile file. It contained the wrong LD_LIBRARY_PATH declarations. Just delete the lines containing LD_LIBRARY_PATH and if present the call to ./etc/ati/ati-fglrx.sh.

This solved the problem for me. Now I don't get the segmentation fault when calling fglrxinfo or glxinfo.

Hope that helps.

Greetings, Prof_NARF

---

### Post by megadik on 2008-07-16
Hi

I've got the same problem as toobitz, reproducable.
It's a Fujitsu/Siemens e8210 laptop.

I tried to remove the symlink libGL.so.1 -> /usr/lib/xorg/libGL.so.1.2 i /usr/lib/xorg whith somewhat success but 2d-performance became poor and Compiz did actually start and ran quite ok but not as neat as before upgrade.

glxgears produced about 250 FPS compared to about 4400 FPS through sudo.

When i did "export LD_LIBRARY_PATH=" glxgears could be started as myself with good performance and compiz --replace began to work.

The overall performance is now good, i tried a movie in VLC in a large window and all tricks whith rotating cube ran flawless and neat.

If it's interesting I installed Beryl and ATI proprietary driver from ATI in 6.06TLS, upgraded to previous (7.04?) whith success (switched to Ubuntu restricted ATI at this point) and ran into these problems in 8.04.

****** Disclaimer *******
I'm not a native English speaker/writer and therefore my language could be detected as "rude" or "unpolite". This not my intentions.

---

