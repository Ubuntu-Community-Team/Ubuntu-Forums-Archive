---
title: "USB power off from command line"
date: 2008-06-06
forum: General Help
---

### Post by geo909 on 2008-06-06
Hello everybody,

well, I'm probably looking something difficult but if you know please help.
Is there any command that actually turns off the USB ports of the computer?!

The reason I want something like this is because I have bought an external disk (seagate freeagent drive) that has a strange standby mode which only works in windows (I didn't know it before I bought it). 

 What happens in Linux is that after ~20 min of no usage, the disk enters in standby mode and cannot be accessed until it is unplugged(=power off) and replugged in.

 So if there is such a command, I would make a keyboard shortcut linked to a script that will

1)unmount the disk
2)turn off the usb ports (what I'm looking!)
3)opens them again
4)mount the disk again(if not automounted)

..so after this series of events, the disk will be accessible again.

That could be executed every 20mins if there's no action.


    Thanks a lot in advance

---

### Post by pointone on 2008-06-06
Does simply remounting the drive not work? It shouldn't be necessary to physically switch off the USB ports.

---

### Post by ajgreeny on 2008-06-06
If you search for seagate freeagent in the forums you'll find a lot of info.
Here's one thread which also points to several others.  You will be able to get the disk to spin again without bothering to do what you were asking about.
**[http://ubuntuforums.org/showthread.php?t=796814&highlight=seagate+freeagent](http://ubuntuforums.org/showthread.php?t=796814&highlight=seagate+freeagent)**
and here's another bit of info which may help from another site:-

For the user who is using the drive on linux who couldn't find a solution for the spindown problem, here is the solution: make sure you have the sdparm package installed. as root, do :
# sdparm -al /dev/sdd /dev/sdd: Seagate FreeAgentDesktop 100D
Direct access device specific parameters: WP=0 DPOFUA=0
Power condition [po] mode page: IDLE 0 [cha: n, def: 0, sav: 0] Idle timer active
STANDBY 1 [cha: y, def: 1, sav: 1] Standby timer active
ICT 0 [cha: n, def: 0, sav: 0] Idle condition timer (100 ms)
SCT 9000 [cha: y, def:9000, sav:9000] Standby condition timer (100 ms)
# sdparm --clear STANDBY -6 /dev/sdd /dev/sdd: Seagate FreeAgentDesktop 100D
# sdparm -al /dev/sdd /dev/sdd: Seagate FreeAgentDesktop 100D Direct access device specific parameters: WP=0 DPOFUA=0
Power condition [po] mode page:
IDLE 0 [cha: n, def: 0, sav: 0] Idle timer active
STANDBY 0 [cha: n, def: 1, sav

No idea about the details of all that, but it does show that there are ways around the problem.  Remember, google is your friend.

---

### Post by geo909 on 2008-06-06
Thanks, I'll try all that.

---

