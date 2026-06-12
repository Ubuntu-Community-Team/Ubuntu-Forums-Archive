---
title: "Error after login: Cannot write bytes: broken pipe"
date: 2015-09-18
forum: General Help
---

### Post by omoikane2 on 2015-09-18
It all started when I was going to launch GIMP (GNU Image  Manipulation Program). But it didn't, and suddenly nothing worked  anymore. I could not even shut my laptop down from unity.  So I forced it by holding down the ON/OFF button until the laptop was  off.  After re-starting the laptop and logging into into my account, Ubuntu  froze at the white screen you sometimes see for a short moment (at least  that is what I see usually) before you see your normal desktop. In this  state it seems to be able to load my user account since software liky  redshift is turns the screen redish.  I then did nothing, just listening how the fan started spinned faster  since the CPU were used more, when suddenly the initially white screen  turned black screen with an error message:
  Cannot write bytes: broken pipe.
  I tried all the solutions I could find in the web:
  Go to shell using  CtrlAltF1
  
[LIST=1]
[*]re-installing Ubuntu desktop: [http://itsfoss.com/fix-unity-freezes-after-login-ubuntu-14-04/](http://itsfoss.com/fix-unity-freezes-after-login-ubuntu-14-04/) 
[*]re-installing graphics driver: [using link]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD") (here could be a problem, since even before I run into this problem  today I the CPU needed to work hard to show e.g. vimeo movies) 
[*]reinstalled xserver-xorg by typing: 
  sudo apt-get install --reinstall xorg 
[*]mount -o remount,rw,errors=remount-ro / 
[*]logging in with Unity 2d gave me the same white screen and after long the same error message 
[*]I can log in with the Guest account but well, all my files not  there. When I log out again from guest, I see the black screen with the  error message Cannot write bytes: broken pipe for a sec. again before I get into the Log in window. 
[*]removing all .Xauthority files from home directory with: sudo rm .Xauthority* 
[*]typing startx gave me the message:
  xauth: file /home//.Xauthority does not exist Fatal server error: Server is already active for display 0
  ......(some more text).......
  Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyxinit: giving up xinit: unable to connect to X server 
[/LIST]
  But all of that lead to nothing so far. It didn't change anything. Only that now when I press CtrlAltF1 to get to CLI I see an error at the log in: Plymouth command failed. Pressing Enter  gives me the normal authorization login wihout out the Plymouth error  for the shell (so that does not give me access to my account).
  Technical Data:
  Laptop: [here]("https://www.sony.de/support/de/content/cnt-specs/VPCSE2S1E/list")
  OS: Ubuntu 12.04 dual boot with Windows 7

not sure if this info gives any hints, but when check defunct programes with 
  ps -ef | grep defunct
  I get:
  00:01:49 gnome-settings- <defunct>
00:01:42 nm-applet <defunct>
00:01:44 nautlius <defunct>
00:01:50 notify-osd <defunct>
00:01:40 update-notifier <defunct>
00:00:00 grep --color=auto defunct

Important to add, as I just found out when checking my /var/log/Xorg.0.log:
  ....(text)....
[821.609] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPRTED-13.35.1005
....(text)....
[823.270] (II) Module intel: vendor="X.org Foundation" compiled for 1.13.3, module version = 2.21.6 Module class: X.Org Video Driver
ABI class: X.Org video dDriver,version 13.1
[823.270] (II) fglrx(0): pEnt->device->identifier=0x7f...blablabla
[823.271] Fatal server error:
[823.271] atiddxProbe: fail to probe inel VGA device

---

