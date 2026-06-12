---
title: "Reboots (Maybe Logout)"
date: 2007-04-06
forum: General Help
---

### Post by Traks on 2007-04-06
My computer seems to be "randomly" rebooting or possibly logging out.  I am fairly new to Linux so I lack the fundamental knowledge as to troubleshoot the issue with the OS or Apps.  I will leave my computer and when I come back it is at the Login screen.

The only thing I can think that was changed with the system was I ran and "apt-get upgrade" and it updated some applications and such.

in /var/log/messages I found:

> Apr  5 21:13:11 Ubu -- MARK --
Apr  5 21:15:43 Ubu gconfd (topher-8621): Received signal 15, shutting down cleanly
Apr  5 21:15:43 Ubu gconfd (topher-8621): Exiting

With no activity for 15 minutes prior to that and I was not at my computer at that time either. 

It is because of this and the fact it was not happening two days ago I am fairly confident it is not a hardware issue.

Any help would be appreciated.

-Cheers
Topher



EDIT//

Issues resolved. Problem with a new update with Nvidia and GLX.

Solution:

From astoltz in  [http://ubuntuforums.org/showthread.php?t=403164](http://ubuntuforums.org/showthread.php?t=403164)


> From the command line it's:

```
cd /usr/lib/xorg/modules/extensions/
sudo mv libglx.so libglx.so.backup
sudo ln -s libglx.so.1.0.9755 libglx.so
```


Then either a reboot or just re-start X with ctrl-alt-backspace
Reply With Quote

---

### Post by mac.ryan on 2007-04-06
AFAIK gconfd is the **g**nome **conf**iguration **d**eamon. So, it should be the applet applying "on the fly" changes of settings to your system.

In other words: gconfd shouldn't be the "bad guy", it is only the one executing a command.

I have no clue - though - on how to track what is the program that issues the command... :(

---

### Post by Traks on 2007-04-06
Yea, I guessed that it wasn't the culprit, but I do not have any ideas or knowledge to trackdown the offending program. :( 

-Cheers

---

### Post by Maestro23 on 2007-04-06
Check your log files in [COLOR="Red"]/var/log[/COLOR]

---

### Post by Traks on 2007-04-06
Thats what I've been looking at, but I am not sure exactly what to look for.  I guess maybe
> Apr  6 09:53:09 Ubu gdm[11407]: Error reinitilizing server
Apr  6 09:53:10 Ubu kernel: [17249190.916000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Apr  6 09:53:10 Ubu kernel: [17249190.916000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Apr  6 09:53:10 Ubu kernel: [17249190.916000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
Apr  6 09:53:12 Ubu gconfd (topher-11470): GConf server is not in use, shutting down.
Apr  6 09:53:12 Ubu gconfd (topher-11470): Exiting

In Syslog   ???

I appreciate all help  Thanks


-Cheers

---

### Post by mac.ryan on 2007-04-07
While googling in search of ideas on how to help on this, I found this thread on launchpad:

[https://bugs.launchpad.net/gnome-session/+bug/65971](https://bugs.launchpad.net/gnome-session/+bug/65971)

To me it looks like your problem and the one in the thread might be correlated... (the logs are very similar)  anyhow I still didn't put the reference to the bug in this reply (the box under the editing one), as I was not sure. If you think this is the case, maybe it might help if you would edit the reference in your original posting...

---

### Post by Traks on 2007-04-07
I have done a little more playing around and I feel it is the screen saver that boots me out of X.

If i go  System > Preferences > Screensaver I immeditaly get booted.  I assume that when my screensaver kicks in in when I get booted while idle.

Is there a CLI way to diable screensaver??

---

### Post by Traks on 2007-04-07
After poking around the forums and piecing stuff together it appears it was a common problem with Nvidia/GLX  I found the solution here:

[http://ubuntuforums.org/showthread.php?t=403164](http://ubuntuforums.org/showthread.php?t=403164)

from astoltz
> From the command line it's:
Code:

cd /usr/lib/xorg/modules/extensions/
sudo mv libglx.so libglx.so.backup
sudo ln -s libglx.so.1.0.9755 libglx.so

And if your original libglx is up one directory like twoflush, then add one last command
Code:

sudo mv libglx.so ..

Then either a reboot or just re-start X with ctrl-alt-backspace
Reply With Quote

---

