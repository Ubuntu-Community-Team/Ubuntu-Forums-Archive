---
title: "Grub recovery menu and boot graphics issues"
date: 2013-06-01
forum: General Help
---

### Post by Jonners59 on 2013-06-01
After upgrading from 12:10 to 13:04 on one of my old laptops (Medion) the image is "fuzzy".  The Grub menu is fine, but the recovery menu and the scripts that appear whilst it boots are also unreadable and fuzzy.  I originally was unable to boot past Grub on the new kernel, but solved the problem in the upgrade thread by changing the boot commands to "nomodeset", but that only fixed the Login screen.  This only affected the new kernel and I was not able to determine if it got bast the login screen, however this is irrelevant as that is now fixed.

Any ideas, please.

---

### Post by oldfred on 2013-06-06
Something with the video driver and default screen settings. But if you cannot read screens it becomes difficult to reset.

What video chip do you have? Some Intel need the exact video mode set as a boot parameter instead of nomodeset.

       Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

 Limited resolutions with Sandybridge graphics
[http://ubuntuforums.org/showthread.php?t=2057807](http://ubuntuforums.org/showthread.php?t=2057807)
With 11.04:SandyBridge
[http://ubuntuforums.org/showthread.php?t=1817374](http://ubuntuforums.org/showthread.php?t=1817374)
acpi_osi=linux pci=noacpi

Newer Intel may need this:

 Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

   For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

---

### Post by Jonners59 on 2013-06-07
Hiya Oldfred
Thanks for below.  I know it is an old card, as it is an old machine, if 10 years is old :)   How do I identify the card?  Just found the code.  Will try it later tonight or weekend. ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -C video
```[/FONT][/COLOR]

Thought I should add, when I first upgraded this machine from 12:10 to 13:04 it was so bad I could not even get to the Login in screen and was totally un-usable.  I managed to fix that myself taking heed of some of the advise you gave me a couple of years back - adding "nomodeset" to the parameters, however the Text and background image during the session between GRUB and Login Screen is still completely distorted and just shows colours and fuzzy text.  When in GRUB and select "Advanced", the menu is fuzzy and so is the "Recovery" menu.....

Whilst trying to fix this I joined another thread which was all about fixing graphics after upgrades ([http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)) and tried a number of things there as suggested.  I started a new thread because this issue had outlived that one.  I have pasted below a snapshot of what I did and what information it gave me.

[COLOR=#222222][FONT=Ubuntubeta]```
italy@italy:~$
```[/FONT][/COLOR]```
[COLOR=#222222][FONT=Ubuntubeta]uname-arLinux italy 3.5.0-28-generic #48-Ubuntu SMP Tue Apr 23 23:05:48UTC 2013 i686 i686 i686 GNU/Linux[/FONT][/COLOR]

[COLOR=#222222][FONT=Ubuntubeta]italy@italy:~$ cat /etc/lsb-release[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]DISTRIB_ID=Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]DISTRIB_RELEASE=13.04[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]DISTRIB_CODENAME=raring[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]DISTRIB_DESCRIPTION="Ubuntu13.04"[/FONT][/COLOR]
```


[COLOR=#222222][FONT=Verdana]Takenfrom working kernel. [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]PS:[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]Note[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]config file comment "greeter-session=[/FONT][/COLOR]**[COLOR=#222222][FONT=Verdana]unity[/FONT][/COLOR]**[COLOR=#222222][FONT=Verdana]-greeter"Note it talks of [/FONT][/COLOR]**[COLOR=#222222][FONT=Verdana]unity[/FONT][/COLOR]**[COLOR=#222222][FONT=Verdana]-I do not use Unity [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]soI changed it to [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]session=xubuntu, [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]itmade no difference[/FONT][/COLOR][COLOR=#222222][FONT=Verdana].[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono]```
cat/etc/lightdm/lightdm.conf > ~/Documents/lightdm.conf
```[/FONT][/COLOR]```

[COLOR=#000000][FONT=Ubuntu Mono]sudocat /var/log/lightdm/lightdm.log > ~/Documents/lightdm.log[/FONT][/COLOR]
```


[COLOR=#222222][FONT=Verdana][[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]CODE][SeatDefaults]greeter-session=unity-greeter[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]user-session=ubuntu[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]allow-guest=false[/CODE][/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]```
[+0.09s]DEBUG: Logging to /var/log/lightdm/lightdm.log[+0.09s] DEBUG:Starting Light Display Manager 1.6.0, UID=0 PID=1226
```[/FONT][/COLOR]```

[COLOR=#222222][FONT=Verdana][+0.09s]DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.09s]DEBUG: Using D-Bus name org.freedesktop.DisplayManager[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.67s]DEBUG: Registered seat module xlocal[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.67s]DEBUG: Registered seat module xremote[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.67s]DEBUG: Adding default seat[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.67s]DEBUG: Starting seat[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.67s]DEBUG: Starting new display for greeter[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.67s]DEBUG: Starting local X display[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.68s]DEBUG: X server :0 will replace Plymouth[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.71s]DEBUG: Using VT 7[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.71s]DEBUG: Logging to /var/log/lightdm/x-0.log[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.71s]DEBUG: Writing X server authority to/var/run/lightdm/root/:0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.71s]DEBUG: Launching X Server[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.71s]DEBUG: Launching process 1249: /usr/bin/X :0 -core -auth/var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -backgroundnone[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.71s]DEBUG: Waiting for ready signal from X server :0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.84s]DEBUG: Acquired bus name org.freedesktop.DisplayManager[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+0.84s]DEBUG: Registering seat with bus path/org/freedesktop/DisplayManager/Seat0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+4.97s]DEBUG: Got signal 10 from process 1249[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+4.97s]DEBUG: Got signal from X server :0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+4.97s]DEBUG: Stopping Plymouth, X server is ready[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+5.75s]DEBUG: Connecting to XServer :0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+5.75s]DEBUG: Starting greeter[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+5.76s]DEBUG: Started session 1324 with service 'lightdm-greeter', username'lightdm'[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+6.28s]DEBUG: Session 1324 authentication complete with return value 0:Success[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+6.28s]DEBUG: Greeter authorized[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+6.28s]DEBUG: Logging to /var/log/lightdm/x-0-greeter.log[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+6.28s]DEBUG: Session 1324 running command/usr/lib/lightdm/lightdm-greeter-session/usr/sbin/unity-greeter[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+12.16s]DEBUG: Greeter connected version=1.6.0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+12.16s]DEBUG: Greeter connected, display is ready[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+12.16s]DEBUG: New display ready, switching to it[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+12.16s]DEBUG: Activating VT 7[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+17.09s]DEBUG: Greeter start authentication for italy[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+17.09s]DEBUG: Started session 1854 with service 'lightdm', username'italy'[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+17.19s]DEBUG: Session 1854 authentication complete with return value 0:Success[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+17.19s]DEBUG: Authenticate result for user italy: Success[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+17.22s]DEBUG: User italy authorized[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+17.25s]DEBUG: Greeter start authentication for italy[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+17.25s]DEBUG: Session 1854: Sending SIGTERM[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+17.25s]DEBUG: Started session 1866 with service 'lightdm', username'italy'[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+17.25s]DEBUG: Session 1854 terminated with signal 15[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+17.34s]DEBUG: Session 1866 authentication complete with return value 0:Success[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+17.34s]DEBUG: Authenticate result for user italy: Success[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+17.37s]DEBUG: User italy authorized[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+924.03s]DEBUG: Greeter requests session xubuntu[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+924.03s]DEBUG: Using session xubuntu[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+924.03s]DEBUG: Stopping greeter[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+924.03s]DEBUG: Session 1324: Sending SIGTERM[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+925.81s]DEBUG: Greeter closed communication channel[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+925.81s]DEBUG: Session 1324 exited with return value 0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+925.81s]DEBUG: Greeter quit[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.30s]DEBUG: Dropping privileges to uid 1000[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.30s]DEBUG: Calling setresgid[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.30s]DEBUG: Calling setresuid[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.31s]DEBUG: Restoring privileges[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.31s]DEBUG: Calling setresuid[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.31s]DEBUG: Calling setresgid[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.75s]DEBUG: Dropping privileges to uid 1000[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.75s]DEBUG: Calling setresgid[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.76s]DEBUG: Calling setresuid[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.76s]DEBUG: Writing /home/italy/.dmrc[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.86s]DEBUG: Restoring privileges[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.86s]DEBUG: Calling setresuid[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.86s]DEBUG: Calling setresgid[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.99s]DEBUG: Starting session xubuntu as user italy[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+927.99s]DEBUG: Session 1866 running command /usr/sbin/lightdm-sessionstartxfce4[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][+928.68s]DEBUG: Registering session with bus path/org/freedesktop/DisplayManager/Session0[/FONT][/COLOR]
```

---

### Post by Jonners59 on 2013-06-13
I have nomodeset and an nVidia card, but it still does not work..

---

