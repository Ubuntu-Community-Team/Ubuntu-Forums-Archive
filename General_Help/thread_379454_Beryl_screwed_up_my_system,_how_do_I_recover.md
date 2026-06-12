---
title: "Beryl screwed up my system, how do I recover?"
date: 2007-03-08
forum: General Help
---

### Post by SouthernGorilla on 2007-03-08
Ok, here's the deal. I added the beryl-project repository to Synaptic and downloaded beryl. I could not get it to work at all. After a reboot beryl worked halfway, but I got an error message "could not initialize HAL" on bootup. The wallpaper was also absent. I went back into Synaptic and completely removed all the beryl-related packages I had installed. Now I still get the HAL message when I boot, the desktop background is blank, and Nautilus crashes when I try to run it. Nothing else has changed except beryl. I went into Synaptic and reinstalled the HAL packages, that didn't work. I did everything through Synaptic, so I couldn't have messed up a command line or something.

---

### Post by DagMan on 2007-03-08
Did you follow a guide that had you create a beryl login session for GDM and if so did you remember to switch back to Gnome?

Did you follow a guide that had you add anything to preferences->sessions and didn't remove it yet?

Have you tried to log into a failsafe gnome session and if so, how did that go?

---

### Post by SouthernGorilla on 2007-03-09
I forgot, I initially followed the instructions on the beryl wiki [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia") except I did not use the script. I then used Synaptic to get some additional packages, including heliodor, but that didn't help.

Looking further down the wiki it seems the problem may be the added line about the glx visuals confusing the xorg.config. I have the latest nvidia driver installed, which required removing the nvidia-glx file, which it seems beryl needs. The wiki looks like it works around this, but I'm too tired right now to sort it out, especially since I've had trouble with X crashing before and don't feel like opening that can of worms right now. I'm going to remove that line from the xorg.config file and see if that doesn't fix my current problem. Maybe after I wake up my head will be clear enough to figure out what I screwed up the first time. Why do I feel like I'm learning to tie my shoes again?

---

### Post by SouthernGorilla on 2007-03-09
I don't have a clue what's going on here. Something is screwed up somewhere and I can't track it down. Here are the symptoms so far.

1) The screen boots up in the wrong resolution. I have it set both with the nVidia settings and Gnome display settings to be 1680x1050, but it boots at 1050x728 which looks like somebody drew it with crayon. I've shut down X and run ```
sudo nvidia-xconfig
``` and ```
xrandr --size 1680x1050
``` but it still boots wrong.

2) The desktop background does not come up. I don't even get the default background that came with Ubuntu, just a blank tan screen. The header bar and taskbar are still there.

3) I still get the "Failure To Initialize HAL" message even after going through Synaptic and reinstalling all the HAL packages I could find.

4) Nautilus will not open. Whether I try it through **Places->Home Folder** or by opening the Run Application window with F2 it crashes and brings up the bug reporting tool.

I did check the **Preferences->Sessions** window, nothing unusual shows there.

I also checked the System Monitor to see if something was running in the background, everything is fine.

I've only been running Linux for about three months now, I've reached the end of my diagnostic ability. I don't even know where to begin looking for a solution. I did try X.org. I did Google the HAL issue and found out it's been a known bug since before Edgy was released, but the solutions I found did not work. I can't find anything out of place anywhere on my system, but something is obviously wrong.

Please don't take this as an attack on Beryl. I've seen the pictures online, I know it can work on Ubuntu, and I'm sure I did something wrong during the installation. I just want to fix it. I'm wondering if successfully installing Beryl might not be the best solution to the problems I'm having.

---

### Post by DagMan on 2007-03-09
I usually don't click on a thread that has beryl in the title.  It's worked fine for me but I had it turned off all the time so I didn't keep it on my system in the end.

Can you boot into a normal Gnome session or a Failsafe Gnome session without the Hal error?  I'm at a loss of how to fix that as well.  With X, as I remember there's an X package installed to run beryl and perhaps that needs to be rolled back assuming you don't want beryl for now.

There's lots of beryl problems posted in the help section if you haven't searched yet.  I think if Hal doesn't run under gnome and you're **not** looking to run beryl though, then you should post a thread about it as a HAL problem, without beryl directly in the title.  It will get more attention that way and would be more accurate to what's happening.  Same with the video but a differant thread too.

---

### Post by SouthernGorilla on 2007-03-10
Heh, funny thing is I reinstalled Beryl and it works fine. I solved the resolution problem, put a bandaid on it really. Instead of setting the nVidia settings on "Auto" I set them for the resolution I wanted. Works fine now. The auto setting should work, it's supposed to pick the highest setting the monitor supports, but it's working so I'm not sweating it. The HAL issue has me stumped. I've Googled it like I said, but didn't find anything helpful. Same with the Nautilus crash. Every time I try to open Nautilus it flashes a message about the CD/DVD creator crashing and brings up the bug report tool. I don't see how it's connected to Beryl, but it wasn't doing it before.

I'm gonna keep searchin'. Sooner or later I'll find an answer.

---

### Post by cmost on 2007-03-10
It never ceases to amaze me the number of Linux novices who try to install Beryl; screwing up their systems in the process.  Folks, Beryl is considered cutting edge.  It is beta software in rapid development and only approaching a 0.2 release.  Further, many of its cool effects are created by less than standard programming practices (e.g., hacks.)  If you want a 3D Linux desktop and whiz-bang visuals, then please use Compiz, preferably the version available in the Ubuntu repository.  While still beta software itself, it's a bit more solid in its programming and less prone to problems in my experience.

To those about to lambaste me for recommending Compiz over Beryl please be advised that I'm a happy Beryl SVN user and I haven't had any trouble with it myself.  I am, however, a more experienced user and I am comfortable editing my xorg.conf, compiling kernel modules and troubleshooting nvidia driver issues or other problems that might arise with the X server.  Screwing up one of these may make Linux novices hate their Linux experience and go running back to Windows with the thought that Linux itself is buggy, unreliable and somehow to blame.

---

### Post by SouthernGorilla on 2007-03-10
For the most part, I agree. If I had paid better attention to things I would have noticed that Beryl was not yet ready for prime time and would have avoided it. However, I did get it working.

I'm certainly a novice, but I've already handled several issues that would have caused others to switch back to Windoze in a heartbeat. I've editied my xorg.conf file more times than I care to think of already, installed the nvidia driver, edited the fstab,  and spent more time in the command line than I could keep track of moving, copying, and changing things to get my system where it is. It's been almost twenty years, but I was president of the computer club in high school and a half decent BASIC programmer, so I probably have a bit of an edge over most new users. In fact, I built this computer myself, got the BIOS set up properly, and got it all working together (except the soundcard, thanks Creative Labs). There's no doubt I have a long way to go before I consider myself fully competent, but I'm a fast learner.

---

### Post by isecore on 2007-03-10
I'm running Beryl from the Beryl repos. SVN 0.2 something or other. Works fine, but ones mileage might vary.

However, as for the "unable to initialize HAL" i've got that as well. However in my experience it was completely unrelated to Beryl. I used to get it whenever i automounted some SAMBA-shares in /etc/fstab. Every time during boot when my machine tried to mount them the HAL-daemon would freak out and die. I have no clue why, but I found that the solution was to have them "noauto" in fstab and just mount them manually after everything is up and running. Works fine for me, I reboot like once a month at most.

Dunno if this helps you or anything. Just wanted to input that as far as I know HAL is unrelated to whatever Beryl-woes you might have. Hope this gives you some kind of clue as to where the problem might be.

---

### Post by SouthernGorilla on 2007-03-10
> **isecore said:**
> I'm running Beryl from the Beryl repos. SVN 0.2 something or other. Works fine, but ones mileage might vary.

However, as for the "unable to initialize HAL" i've got that as well. However in my experience it was completely unrelated to Beryl. I used to get it whenever i automounted some SAMBA-shares in /etc/fstab. Every time during boot when my machine tried to mount them the HAL-daemon would freak out and die. I have no clue why, but I found that the solution was to have them "noauto" in fstab and just mount them manually after everything is up and running. Works fine for me, I reboot like once a month at most.

Dunno if this helps you or anything. Just wanted to input that as far as I know HAL is unrelated to whatever Beryl-woes you might have. Hope this gives you some kind of clue as to where the problem might be.
Yeah, the HAL issue is my main problem now, Beryl runs fine. I just checked the fstab, nothing new there. I don't have any removable media and both DVD drives are set "noauto". You do bring up an interesting point, though. If it's the CD creator in Nautilus that's causing the crash, that would be a HAL-related issue, right? So both problems could just be a symptom of the same thing, just have to figure out what that is exactly.

---

### Post by isecore on 2007-03-10
> **SouthernGorilla said:**
> You do bring up an interesting point, though. If it's the CD creator in Nautilus that's causing the crash, that would be a HAL-related issue, right?
I'd say that sounds like a possibility.

---

### Post by SouthernGorilla on 2007-03-10
Found another thread that at least solved the Nautilus problem. ```
root@happy-desktop:/home/happy#  sudo /etc/dbus-1/event.d/20hal start
 * Starting Hardware abstraction layer hald                                     root@happy-desktop:/home/happy# sudo /etc/init.d/dbus restart
 * Stopping System Tools Backends system-tools-backends                  [ ok ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [fail] 
 * Stopping Hardware abstraction layer hald                              [ ok ] 
 * Stopping system message bus dbus                                      [ ok ] 
 * Starting system message bus dbus                                             Failed to start message bus: The pid file "/usr/var/run/dbus/pid" exists, if the message bus is not running, remove this file
root@happy-desktop:/home/happy# rm /usr/var/run/dbus/pid
root@happy-desktop:/home/happy# sudo /etc/init.d/dbus start
 * Starting system message bus dbus                                      [ ok ] 
 * Starting Hardware abstraction layer hald                                     run-parts: /etc/dbus-1/event.d/20hal exited with return code 1
 * Starting System Tools Backends system-tools-backends                  [ ok ] 
root@happy-desktop:/home/happy# 
```Nautilus no longer crashes when I open it. Now to see what happens when I reboot.

---

