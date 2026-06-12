---
title: "My audio is out of sync for example in youtube please help"
date: 2012-10-18
forum: General Help
---

### Post by Codeless on 2012-10-18
I found this advice

Did you install the package called ubuntu-restricted-extras? You can do this in the Software Center or, if you prefer the to use the command-line, then by running sudo apt-get update followed by sudo apt-get install ubuntu-restricted-extras.

If you have ubuntu-restricted-extras, then verify that a Flash plugin is actually installed by checking for the adobe-flashplugin or flashplugin-installer packages. If neither is installed, install one of them. If you're running the 64-bit version of Ubuntu, installing adobe-flashplugin is preferable. (But don't have them both installed at the same time.)

If you're running the 64-bit version of Ubuntu and you find that you have flashplugin-installer installed and the problem continues, then try removing it and replacing it with adobe-flashplugin.

If none of the above works, check to see if you're using the HTML5 beta on YouTube! by going to [http://youtube.com/html5](http://youtube.com/html5). Theoretically, and eventually, this should perform uniformly better on Ubuntu. But right now, it might not work well. So if it's turned off, you can try it and see if it works better. If it's turned on, try turning it off and seeing what happens.

~~~~~~~~~~~~~~~~~~~~~~~
Unfortunately I'm stupid and could only do the first paragraph... what are linux commands for checking and installing the plugins? I tried

ziggletooth@Pengu:~$ sudo apt-get install adobe-flashplugin
[sudo] password for ziggletooth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'adobe-flashplugin' has no installation candidate
ziggletooth@Pengu:~$ 

guess that wasn't it... help me out guys

html5 didn't work

---

### Post by arandomstring on 2012-10-18
Well first off, are you running 64 bit?

Also, try installing the other package they recommended, namely, flashplugin-installer
You can do this two ways, either through the software centre or through the terminal. To do it through the Software Centre just search for "flashplugin-installer" and click install on the correct package. To do it through the terminal run this command:
```
sudo apt-get install flashplugin-installer
```

Then you should be good to go. After this try checking out Youtube and see if the problem has been fixed (I imagine it will be) if not, continue following the steps you have listed. Try turning HTML5 on at [http://youtube.com/html5](http://youtube.com/html5) and see if things run better. I remember having a similar problem in the past but I forget the fix (I'm pretty sure I just waited for an update to either firefox or the Flash plugin)

Also, what browser are you using? Have you tried using different ones?

---

### Post by Codeless on 2012-10-18
> **madkristoff said:**
> Well first off, are you running 64 bit?

Also, try installing the other package they recommended, namely, flashplugin-installer
You can do this two ways, either through the software centre or through the terminal. To do it through the Software Centre just search for "flashplugin-installer" and click install on the correct package. To do it through the terminal run this command:
```
sudo apt-get install flashplugin-installer
```

Then you should be good to go. After this try checking out Youtube and see if the problem has been fixed (I imagine it will be) if not, continue following the steps you have listed. Try turning HTML5 on at [http://youtube.com/html5](http://youtube.com/html5) and see if things run better. I remember having a similar problem in the past but I forget the fix (I'm pretty sure I just waited for an update to either firefox or the Flash plugin)

Also, what browser are you using? Have you tried using different ones?

I'm running 32-bit. I did what you said and this was the output

ziggletooth@Pengu:~$ sudo apt-get install flashplugin-installer
[sudo] password for ziggletooth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ziggletooth@Pengu:~$ 

furthermore I went to the software centre and used the search then clicked on adobe flash plugin 10 and it said

there isn't a software package called "adobe-flashplugin" in your current software sources

I did try html5 and it didn't work

I audio is out of synch in firefox and chrome. Doesn't chrome have the latest version installed by default? do you have any suggestions

---

### Post by arandomstring on 2012-10-20
Hmm, try uninstalling  flashplugin-installer with ```
sudo apt-get remove --purge flashplugin-installer
``` then try installing adobe-flashplugin with ```
 sudo apt-get install adobe-flashplugin
``` I don't know if that will work, but it's worth a shot. If flashplugin-installer doesn't install just reinstall  flashplugin-installer with ```
sudo apt-get install flashplugin-installer
```

EDIT: I found  two forum posts that may help you. Be careful when running commands listed in these though, I'm not sure what they do exactly. 
Anyway, [this thread]("http://ubuntuforums.org/showthread.php?t=1613606") describes your problem and someone else posted [this thread]("http://forums.linuxmint.com/viewtopic.php?f=42&t=60485") saying it contained the fix.

---

### Post by Codeless on 2012-10-22
> **madkristoff said:**
> Hmm, try uninstalling  flashplugin-installer with ```
sudo apt-get remove --purge flashplugin-installer
``` then try installing adobe-flashplugin with ```
 sudo apt-get install adobe-flashplugin
``` I don't know if that will work, but it's worth a shot. If flashplugin-installer doesn't install just reinstall  flashplugin-installer with ```
sudo apt-get install flashplugin-installer
```

EDIT: I found  two forum posts that may help you. Be careful when running commands listed in these though, I'm not sure what they do exactly. 
Anyway, [this thread]("http://ubuntuforums.org/showthread.php?t=1613606") describes your problem and someone else posted [this thread]("http://forums.linuxmint.com/viewtopic.php?f=42&t=60485") saying it contained the fix.

I'm sorry I can't follow these instructions

A. Menu > Preferences > Startup Applications > uncheck "PulseAudio Sound System", PulseAudio Sound System KDE Routing Policy" and "Volume Control"
B. Menu > Administration > Services > uncheck "pulseaudio"
C. Remove pulseaudio, related packages and configuration files

I have cog icon > startup applications then the only thing there is vboxclient.

ubuntu is my guest os

whatever I did only destroyed the sound but thats ok I have a snapshot

I am really new to linux how would I uncheck this stuff on my ubuntu 12.04 distro in vb

---

