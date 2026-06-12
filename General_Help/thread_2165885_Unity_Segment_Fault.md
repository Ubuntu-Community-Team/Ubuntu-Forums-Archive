---
title: "Unity Segment Fault"
date: 2013-08-06
forum: General Help
---

### Post by stevedude on 2013-08-06
I came home today (August 6th) to a software update notification so I installed the update. I noticed unity was a part of today's update. After the update I clciked on the DASH icon and "poof" Unity disappeared. I am running Ubuntu 13.04 (Raring), 64-bit. 

I had to go into terminal mode to reboot the system thinking it just needed a reboot to complete the update process. Now I have no working Unity, just a blank desktop - no icons or status bar.

I opened a terminal and typed "Unity" and received a "Segmentation Fault" error (see below). I tried "unity --reset (which I found out is depricated) and "unity --replace" with no results. The following is the error I receive.

Can anyone assist with this? Thanks!

compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: no process found
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: widget
compiz (core) - Info: Starting plugin: widget
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unityshell
Segmentation fault

---

### Post by dr-akulavich on 2013-08-07
The same situation.

Ubuntu 13.04 x64 and latest updates.

---

### Post by pierre-bornancin-gmail on 2013-08-07
same thing for me....

---

### Post by stevedude on 2013-08-07
If anyone affected could go to: [https://bugs.launchpad.net/unity/+bug/1209303](https://bugs.launchpad.net/unity/+bug/1209303)

I have started a Bug Report with Launchpad. Your input would be invaluable. Thanks


** UPDATE ** Tried to install generic linux headers and removed/reinstalled my NVidia graphics drivers per [FONT=Cambria][SIZE=3][FONT=Cambria][URL="http://ubuntuforums.org/showthread.php?t=2070426&page=2"]http://ubuntuforums.org/showthread.php?t=2070426&page=2

[/URL][/FONT][/SIZE][/FONT]Current headers are 3.8.0-27-generic (not the ones shown in the above post)

Still not working....

---

### Post by stevedude on 2013-08-07
** UPDATE **

Ran ccsm and Unity Plug-in is "Enabled" so that is not the issue. Since the error message I received states "unity-panel-service: no process found", I tried to run this in terminal but got a lot of errors there, so I removed/purged unity-services and reinstalled it with no luck

Ran setsid unity and that does nothing after all of the above, so if anyone out there is listening, I've run out of ideas and desperately need help!

---

### Post by james-3 on 2013-08-10
I've had a similar experience with unity after some updates a few days ago. I have found no resolution.

---

### Post by stevedude on 2013-08-11
Closing this thread although it is NOT resolved. Created a bug report for those who come across this thread in the future [see above]. Try the links I posted prior. After perusing my Software Sources list, I noticed I had "Unity Experimental" as a software source and I have to believe that was my problem.

Ended up re-installing Ubuntu 13.04 (without formatting the hard drive) and that fixed the Unity issue, but created other problems for me (like programs not working right even after re-installing them) so I ultimately re-installed Ubuntu again, this time formatting the hard drive and restoring files from my backup. A pain in the *ss, but I could not resolve my issue in a timely manner.

---

### Post by barry.of.smithgmail.com on 2013-08-14
OK everyone who has this problem! I just got this problem, but I found a solution! And it keeps things (relatively) intact. Execute the commands below in order. Don't miss anything out. Once you're done,reboot or log out.

Uninstall and purge the troublesome packages:
> sudo apt-get remove --purge unity libunity-common libunity-protocol-private0 libunity9
Remove experimental PPA:
> sudo remove-apt-repository ppa:ubuntu-unity/experimental-certified
Update software sources:
> sudo apt-get update
Reinstall the original versions of the packages:
> sudo apt-get install libunity-common libunity-protocol-private0 libunity9
Then reinstall unity on its own to make everything run smoothly(ish):
> sudo apt-get install unity

Ok, you're done! Reboot now:
> sudo reboot now

This worked for me, I hope it works for you as well!

- Barry Smith

---

### Post by dr-akulavich on 2013-08-15
> **barry.of.smithgmail.com said:**
> OK everyone who has this problem! I just got this problem, but I found a solution! And it keeps things (relatively) intact. Execute the commands below in order. Don't miss anything out. Once you're done,reboot or log out.

Uninstall and purge the troublesome packages

Thanks for advice. I've removed **ubuntu-unity/daily-build **ppa via *ppa-purge* and restarted session:
> sudo ppa-purge ppa:ubuntu-unity/daily-build

And now everything is OK.

---

