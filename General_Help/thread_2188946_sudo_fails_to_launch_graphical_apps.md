---
title: "sudo fails to launch graphical apps"
date: 2013-11-19
forum: General Help
---

### Post by Holmes.Sherlock on 2013-11-19
I'm running Ubuntu 12.04.

When I'm trying to lunch gedit as root
> sudo gedit
it displays the following error.
```
Cannot open display: Run 'gedit --help' to see a full list of available command line options.


** (gedit:5478): WARNING **: Command line `dbus-launch --autolaunch=40e5b014a389091e8620426d0000000e --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.

```

If I try > gksu gedit
it displays the following error.
```
Cannot open display: Run 'gedit --help' to see a full list of available command line options.

```

If I try > gedit from console, it gets launched perfectly.

---

### Post by papibe on 2013-11-20
Hi Holmes.Sherlock.

I recommend using 'gksudo' to run GUI apps as root.

As the times you ran sudo and gksu, you may have created or changed ownership of some files. May be not, but just to cover all angles, I would run this just to make sure:
```
sudo chown  -R  youruser:youruser  ~/
```
Regards.

---

### Post by Holmes.Sherlock on 2013-11-20
> **papibe said:**
> 
I recommend using 'gksudo' to run GUI apps as root.

If I run > gksudo gedit, I get
```
Cannot open display: Run 'gedit --help' to see a full list of available command line options.

```

Earlier sudo/gksudo was working fine. Yesterday I updated a lot of packages and this problem started.

---

### Post by papibe on 2013-11-20
Are you trying to open GUI apps from a remote ssh connection? 

If so, you just may need to set the DISPLAY variable:
```
DISPLAY=:0 gedit
```
Just a thought.
Regards.

---

### Post by Holmes.Sherlock on 2013-11-20
> **papibe said:**
> Are you trying to open GUI apps from a remote ssh connection? 

No, trying to run on my local system.

---

### Post by Holmes.Sherlock on 2013-11-20
I solved the problem myself by following this [thread]("http://askubuntu.com/questions/175611/cannot-connect-to-x-server-when-running-app-with-sudo"). There are two alternatives:


[LIST=1]
[*]**xhost local:root** - To allow the root user access to the X server. **sudo DISPLAY=$DISPLAY gedit /etc/profile** - To point the command to the right DISPLAY.
[*]Above change is temporary, per session basis. To make it permanent, add the following at visudo: **Defaults env_keep="DISPLAY XAUTHORITY"**
[/LIST]
Now can anyone tell me how it was working fine before the update without any one of the above changes?

---

