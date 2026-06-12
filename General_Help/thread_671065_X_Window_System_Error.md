---
title: "X Window System Error"
date: 2008-01-18
forum: General Help
---

### Post by LPGDEV on 2008-01-18
Hi there

I am trying to run azureus and I get the following error

Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-6-sun/jre/bin/java
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
[alert] Alert:3:Error loading plugin 'azemp' / 'com.azureus.plugins.azemp.EmbeddedMediaPlayerPlugin'
DEBUG::Fri Jan 18 10:53:21 GMT 2008::org.gudy.azureus2.pluginsimpl.local.PluginInitializer::loadPluginFromDir::916:
  java.lang.ClassNotFoundException: com.azureus.plugins.azemp.EmbeddedMediaPlayerPlugin
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginFromDir(PluginInitializer.java:851)
        at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginsFromDir(PluginInitializer.java:541)
        at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPlugins(PluginInitializer.java:348)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.start(AzureusCoreImpl.java:394)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.run(Initializer.java:301)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$1.runSupport(SWTThread.java:124)
        at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
        at java.lang.Thread.run(Thread.java:619)

Error loading plugin 'azemp' / 'com.azureus.plugins.azemp.EmbeddedMediaPlayerPlugin' : java.lang.ClassNotFoundException: com.azureus.plugins.azemp.EmbeddedMediaPlayerPlugin
The program 'SWT' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 343 error_code 11 request_code 148 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I also get an X Window System error when I try running another application called Player/Stage. 

Any ideas?

I am running Ubuntu 7.10 on a Dell laptop with Nvidia graphics card.

---

### Post by ksenos on 2008-01-18
Hi,

I got the same error when running azureus. Furthermore, the error also appears when running eclipse. This morning just before an update of xorg everything was running OK.

---

### Post by Tanker Bob on 2008-01-18
After accepting last nights update to the xserver, compiz (both 6.0 and 6.2) no longer works and nvidia's setup utility also crashes when trying to access OpenGL/GLX Information. Both executing compiz and the nvidia information acts like a ctrl-alt-backspace command. kde 3.5.8 composite window decarations still work OK. What did they break?

---

### Post by ironclaw on 2008-01-18
Wow... I thought it was my own problem when I received this when trying to run Azureus:
'The program 'SWT' received an X Window System error.'

I didn't think it was a widespread problem as Ubuntu froze on me when I was trying to play a media file, and I had to use the magic SysRq key to reboot the system. I naturally thought that the problem with Azureus had to do with the freeze and reboot.

Now that I think about, I too had an update of xorg this morning (it was morning for me in Asia), and I actually had several symptoms of problems, which I ignored... (I received some garbled screens from media files, still not certain if these problems are connected)

However, Compiz Fusion still works for me.

So, who can help us? (or point to somewhere else which deals with this problem?)

Edit: There are several other threads here on the same problem which can found easily with a search for 'x window system error', so it does seem quite widespread. I guess a solution would come out soon given the number of people it's affecting.
The errors are all the same:
```
The program '*affected program*' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
```
I think the problems only surfaced after restarting, so perhaps many who have updated but not restarted have not noticed the problems.

chunchengch in [this post]("http://ubuntuforums.org/showthread.php?t=671118") points out the two updates:
libxfont1 ---- from 1.3.0.0-0ubuntu1 to 1.3.0.0-oubuntu1.1
xserver-xorg-core --- from 1.3.0.0.dfsg-12ubuntu8 to 1.3.0.0.dfsg-12ubuntu8.1
I'm guessing it's the xorg update that's causing all the problems?

Check out [this Google search]("http://www.google.com/search?q="received an x window system error"&as_qdr=w") for "received an x window system error" in the past week. Problem is not restricted to Ubuntu?

Update: Downgrading the package xserver-xorg-core back to the previous version, 2:1.3.0.0.dfsg-12ubuntu8 before the security update worked for me as well, restart required to get the programs working again. Of course, I'm using this only as a temporary fix before it is actually fixed.

---

### Post by dm1024 on 2008-01-18
Same bug, just after today's update (about 5 hours ago).
It affects SWT, as I can see. For me this is Azureus (from apt-repo) and Eclipse (standalone, custom install).
NetBeans works well (it works with other java windowing subsystem).

---

### Post by puccio on 2008-01-18
Hello,

same issue for me. I updated the packages this morning (Europe time), and I can't launch any more many programs: Eclipse, VLC, gxine, ...

Here it is where I posted my problem:
[http://ubuntuforums.org/showthread.php?t=671108](http://ubuntuforums.org/showthread.php?t=671108)

Hope someone will come with a workaround soon :(

---

### Post by cmarcx on 2008-01-18
idem for me, after update and reboot, azureus not work
Tryied 2.5 and new Vuze, still the same...

[COLOR="Red"]The program 'SWT' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 360 error_code 11 request_code 145 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Azureus TERMINATED.[/COLOR]

I think I will definitly turn off updates....

---

### Post by cmarcx on 2008-01-18
getting back to 
xorg-core 2:1.3.0.0.dfsg-12ubuntu8(gusty) solve the problem

I have gone to synaptic manager, search for xorg-core
and force previous version...

---

### Post by dm1024 on 2008-01-18
There is updated version of sun-java-sdk in repo's. Looks like it was added a few minuts ago.
Right now I'm downloading it. Will report status.

---

### Post by puccio on 2008-01-18
downgrading **xorg-core** works for me :-)

Thanks!

---

### Post by ScdGigi on 2008-01-18
> **puccio said:**
> downgrading **xorg-core** works for me :-)

Thanks!

For me too.. But I hate downgrade to make something works!

Stay tuned

---

### Post by dm1024 on 2008-01-18
> **dm1024 said:**
> There is updated version of sun-java-sdk in repo's. Looks like it was added a few minuts ago.
Right now I'm downloading it. Will report status.

Didn't help. Downgrading...

---

### Post by fyo on 2008-01-18
NOT working for me. I'm getting the following error:

gdm_slave_xioerror_handler: Fatal X error - Restarting :0

ever since restarting after the last round of updates (this morning European time). The error occurs when starting any app that uses accelerated 3D graphics (apparently), e.g. Google Earth and a variety of games.

Downgrading to the old version of xorg-core (and restarting) did nothing for me.

---

### Post by keinpeil on 2008-01-18
> **puccio said:**
> downgrading **xorg-core** works for me :-)

Thanks!

Had the same problem. Downgrading xorg-core worked!

---

### Post by Rudi Völler on 2008-01-18
I had the same problem and tried to downgrade xserver-xorg-core. The downgrade using 
sudo apt-get remove xserver-xorg-core
and then 
sudo apt-get install xserver-xorg-core=version

seemed to work fine. Then I restarted the machine and now kde doesnt start?!? On the screen says:
```
Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/sda5) = sda5(8,5)
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot...

```
and then I get the login prompt....

Did I miss any steps during the downgrade that I can resolve? or do you guys have any suggestions on how I can resolve this issue?

thanks!

---

### Post by geofrank on 2008-01-18
How do I downgrade xorg-core?

---

### Post by jdong on 2008-01-18
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

Security team and archive administrators are aware and currently discussing this problem, and will soon pull the update (in a matter of minutes) from the archive servers.

For now, just sit tight until there's an update on the situation. I don't advise people to try to roll back to old versions of packages or otherwise home-brew fixes unless you want to risk making a mistake doing this and screwing up things even more.

As far as this fix, it's a security fix taken directly from the X.org team and several distros have chosen to adopt this patch. Upstream has been notified regarding this situation too.

---

### Post by geofrank on 2008-01-18
Nice! Do you have any idea how long it will take for a fix to come? I'm at work, waiting for my Eclipse to work properly, so downgrading is the only real solution if it's gonna take a long time.

---

### Post by neymac on 2008-01-18
I had the same issue.
I've got back to the previous xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8 and solve the problem.

---

### Post by Spyros_Gre on 2008-01-18
Same issue here in Athens Gr. Just an hour ago I restarted (i received updates in the morning) and...BANG! hehe hope they fix it soon cause I need eclipse!

---

### Post by cipi.ro on 2008-01-18
I just had the same problem when I tried to start Eclipse.
I've solved it by reverting from xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8.1 (gutsy-security) to xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8 (gutsy), using synaptic.

---

### Post by kitimail on 2008-01-18
apparently there's no need to downgrade.
i found a solution in the italian forum, and it just works.
edit the xorg.conf file adding  the line
```
Option "MIT-SHM" "no"
```
to the "Extensions" section. if such section is not present, just add it to the file:
```
Section "Extensions"
        Option "MIT-SHM" "no"
EndSection
```

---

### Post by LPGDEV on 2008-01-18
I fixed the azureus error with downgrading as well. However, I still get the following warnings

(SWT:5657): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1

(SWT:5657): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 17

GTK issue? I get similar errors/warnings when running the other program I mentioned.

---

### Post by Spyros_Gre on 2008-01-18
Just downgraded xserver-xorg-core and everything is fine!

---

### Post by wojTrek on 2008-01-18
> **kitimail said:**
> apparently there's no need to downgrade.
i found a solution in the italian forum, and it just works.
edit the xorg.conf file adding  the line
```
Option "MIT-SHM" "no"
```
to the "Extensions" section. if such section is not present, just add it to the file:
```
Section "Extensions"
        Option "MIT-SHM" "no"
EndSection
```

IT WORKS! Thanks!:KS

---

### Post by fyo on 2008-01-18
Disabling MIT-SHM *will* cause performance degradation, so remember to re-enable it once an official fix is provided!

---

### Post by ScdGigi on 2008-01-18
ok, modifing xorg.conf solve the problem and i have updated xorg-core..

> **fyo said:**
> Disabling MIT-SHM *will* cause performance degradation, so remember to re-enable it once an official fix is provided!

someone knows when an official fix will be avaible?

---

### Post by chomski on 2008-01-18
Downgraded xserver-xorg-core and I've got azureus back, been fighting with this all morning before checking the forum (DOH!)

Looking forward to a fix.:)

---

### Post by Izkata on 2008-01-18
Downgrading didn't work here.  And since the package is locked now (403 Forbidden), I can't re-upgrade to try modifying Xorg.conf  (I didn't do that in the first place because I -know- I'd forget to remove that line afterwards)

---

### Post by urosh2 on 2008-01-18
same here

---

### Post by anindya_m on 2008-01-18
Disabling the MIT-SHM extension as suggested earlier has temporarily fixed the problem. A few minutes ago an updated xorg package for gutsy has been posted on the security repository. I will try that on my gutsy system in a few hours. Still waiting for a feisty update...

---

### Post by sjd on 2008-01-18
I just tried doing the updates before reading this and (fortunately) got an access error - you don't have access on the xserver upgrade.

My question is, should I uncheck the xserver update and do the rest or just wait until someone posts the 'all clear' for the xserver update?

---

### Post by anindya_m on 2008-01-18
The problematic update has been pulled off the servers. It's probably better to wait for a day or so before you try to install again.

---

### Post by anindya_m on 2008-01-18
The update for feisty is out already. I just installed it and removed the MIT-SHM lines from xorg.conf. Everything seems to work now on my system :)

---

### Post by Izkata on 2008-01-18
As is Gutsy's update...  Although I'm getting a whole new error with Azureus now.

I just renamed ~/.azureus, and my new error disappeared.  Looks like something strange was in there...    =(

---

### Post by anindya_m on 2008-01-18
Interesting. Can you copy/paste the error message?

---

### Post by dm1024 on 2008-01-18
> **geofrank said:**
> How do I downgrade xorg-core?

I have walked to /var/cache/apt/archives and "dpkg -i xserver-xorg-core-<OLDER-VERSION-HERE>"

---

### Post by Izkata on 2008-01-18
> **anindya_m said:**
> Interesting. Can you copy/paste the error message?

Actually, I figured out it myself - yay!

Before checking online, I purged then reinstalled Azureus, 'cause I thought something got screwed up in it, being the only affected program I use regularly.  I had forgotten that the one in the repositories was version 2.5.0.0, while I had manually upgraded to 2.5.0.4 - that difference in JAR files, coupled with some of the plugins I had, seems to have been causing it.

After replacing the Azureus2.jar file with version 2.5.0.4, my new problems disappeared.

I don't have the error message anymore, but it kept changing - although it was always some kind of signal the process was receiving that cased a segfault.

---

### Post by jdong on 2008-01-18
> **sjd said:**
> I just tried doing the updates before reading this and (fortunately) got an access error - you don't have access on the xserver upgrade.

My question is, should I uncheck the xserver update and do the rest or just wait until someone posts the 'all clear' for the xserver update?

The access denied error is to prevent you from receiving the defective update. Access will be restored when a new set of fixed updates are provided.

---

### Post by Tanker Bob on 2008-01-18
I just installed the offered 8.2 update to xorg-core, but it is no better. My problems have multiplied. Neither compiz nor wine will work, both resetting the xserver. I have some daily data runs under wine, so this is a show stopper.

Further, it seems that updating to 8.2 purged the 8 version from /var/cache/apt/archives, so I no longer have a working xserver. I pray that the 8 version is availalbe somewhere on the web, otherwise I'm hosed and the "fixed" 8.2 is worthless.

---

### Post by Tanker Bob on 2008-01-18
OK, I found xorg-core version 8 on my Kubuntu install CD and downgraded. However, wine, nvidia config, and compiz still fail by restarting the xserver as in ctrl-alt-backspace. What other files need to be downgraded? I know that there were several that updated last night, but don't remember which ones.

---

### Post by mrpeenut24 on 2008-01-18
The new xorg-core is in the repos!  Thanks for such a quick release!  Not sure it works yet, but I would imagine that's the reason for the double release.

---

### Post by mrpeenut24 on 2008-01-18
Yep azureus works.  I would imagine it's been fixed.

---

### Post by Tanker Bob on 2008-01-18
OK, the xorg-core 8.2 patch works AFTER reinstalling the nvidia driver. The bad 8.1 update apparently breaks or overwrites some links for the nvidia setup. All is well now.

Good work by the xserver team in getting a regression package out quickly.

---

### Post by lpetrov on 2008-01-18
```
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
The program 'Eclipse' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 594 error_code 11 request_code 149 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I've just updated to the latest version of xorg core and i still have the problem. Do i have to restart X ?

PS: Again updated ~ 06:17 (GMT+2) and again not working, abit scared to reboot without a X :) So any new info on the prob ?

---

### Post by chiefmanyrabbitguteat on 2008-01-19
Same problem with VLC - Fixed with the update just now!  Thanks for the quick work, sure wish I could do more...

oh, and Yeah, I restarted X

---

### Post by ScdGigi on 2008-01-19
Last fix works for me.. i've also re-modified xorg.conf.. so.. good job!

---

### Post by Arrdee on 2008-01-19
After a quick restart, VLC works now! Awesome.

Bravo.

---

### Post by jdong on 2008-01-19
You've got to hand it to the developers involved with this -- identifying, fixing, and testing, and releasing a fix in less than 24 hours.

---

### Post by tim71 on 2008-01-19
Also got hit by this - and downgrading even to version 8 did not help anything. 
And disabling MIT-SHM did not help either - and all of this with the last update - 8.3...

Then I tried to change the driver in xorg.conf. With 'nvidia' xserver crashed, with 'nv' it was just blank screen and black windows - but with 'vesa' there was no problem. Obviously this was not the solution and I just reinstalled Nvidia driver. 

Installer threw a few error messages, but after reinstalling everything was OK... except for one thing - if MIT-SHM was disabled, there was no picture in any video player using xv or xvmc driver. The player window was just blank, but video was still playing and sound was there. OpenGL driver did not had this problem.

Finally I just tried to remove this MIT-SHM line from xorg.conf and guess what? Everything is fine - xv and xvmc are working again.

It seems like something broke in video driver with the first update and after that next updates were no good either, because the problem was elsewhere - in the broken driver. Things may be different for folks, who have installed the official driver from repository and not the latest version straight from Nvidia, like I have done.

---

### Post by Tanker Bob on 2008-01-19
The xorg-core 8.1 driver broke at least one symbolic link for nvidia drivers that caused access to glx functions and information to reset the xserver, amongst other problems. Once 8.1 was installed on an nvidia system, the nvidia driver either had to be reinstalled after installing 8, 8.2 or 8.3, or you had to fix the symbolic links manually. I had no problems after reinstalling the nvidia driver (using envy) for 8.2, and 8.3 upgraded just fine.

---

### Post by lpetrov on 2008-01-20
My Gutsy is ok now, i've restarted and everything is fine. The update from the last night works perfectly with any "hacks" like disabling, downgrading and etc :)

:guitar:

---

### Post by tim71 on 2008-01-20
> **Tanker Bob said:**
> The xorg-core 8.1 driver broke at least one symbolic link for nvidia drivers that caused access to glx functions and information to reset the xserver, amongst other problems.
This error was exactly like that - about broken link...

---

### Post by Robsteranium on 2008-01-21
To confirm: if you've updated Xorg and received the above error then you need to restart X to get things working again.  The above modifications to xorg.conf are now unnecessary as long as you update and restart.

```
sudo /etc/init.d/gdm restart
``` 

Latest version in the repository is currently:
xserver-xorg-core version 2:1.3.0.0.dfsg-12ubuntu8.3

---

### Post by nlz on 2008-03-27
I upgraded, downgraded, edited xorg.conf but still:
```

qnuf@mediaction:~$ gxine
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 326 error_code 8 request_code 140 minor_code 14)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

and

```
qnuf@mediaction:~$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 42 error_code 8 request_code 140 minor_code 14)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
qnuf@mediaction:~$ 
```

with xserver-xorg-core version 2:1.3.0.0.dfsg-12ubuntu8.3 and the following xorg.conf

```
Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection
```

what can i do?

---

### Post by nlz on 2008-03-28
just use openGL and you'll have no problems with X windows :

```
xine -V opengl 
```

*sweet*

---

