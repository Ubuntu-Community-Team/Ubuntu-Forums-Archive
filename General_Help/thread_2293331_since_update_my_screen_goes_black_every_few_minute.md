---
title: "since update my screen goes black every few minutes"
date: 2015-09-04
forum: General Help
---

### Post by mike555 on 2015-09-04
For the last week or so my screen is going black, even with the power settings set to never and "Caffeine" set to not allow screen saver when Firefox is open.    perhaps I'm missing something, but it didn't go black before.    anything I can do?

I'm using 14.04 Xubuntu.

---

### Post by angrymoose on 2015-09-04
Is your monitor turning off or is the screen saver kicking in after x idle time and caffeine is failing to do its job ?

---

### Post by mike555 on 2015-09-04
My monitor is going black, but not turning off , I just move the mouse and it comes on ......   
 I went into settings and it was set to never blank the screen, I figure some update changed things, but I tried booting a older kernel  and it still blacks out in about 10 minutes ........
   And Caffeine doesn't seam to be working like it did before .....

---

### Post by yetimon_64 on 2015-09-04
> My monitor is going black, but not turning off , I just move the mouse and it comes on ......   That sounds a bit like a monitor DPMS setting.

Try the next command to see if it is enabled,
```
 xset -q | grep DPMS
```
If it is enabled, disable it with,
```
xset -dpms
```

On some set ups I have needed to turn DPMS off at start-up with an entry added to "Startup Applications". Though I would have thought caffiene should have taken care of this setting etc.

---

### Post by mike555 on 2015-09-04
Ok, ran the commands, DPMS was running so I ran "xset -dpms" ........ it didn't work, I restarted and ran "Xset -q grep DPMS" and it was running so it didn't save ........  maybe I should run SUDO?

---

### Post by yetimon_64 on 2015-09-04
No, to sudo. Just add an entry in Startup Applications in xfce to turn it off every start up. I noted when running xfce that is how I had to work around whatever setting/application that kept turning it back on, it is a real "pita" the DPMS setting constantly returning. Either write the command into a bash script _*or*_ just add the "xset -dpms" command as the exec line in a start up entry.

Hopefully someone will know how to fix whatever causes it in xfce, I haven't had to do the same in Unity, as once I set it as off it stayed off.

---

### Post by mike555 on 2015-09-05
The screen still blacks out, any more ideas? I like Xubuntu, but I hate the black screen , please help.

---

### Post by Dennis N on 2015-09-05
I used the method of this post in Xubuntu 14.04 and earlier with success, as did the person starting the thread.
[http://ubuntuforums.org/showthread.php?t=2253791&p=13172640#post13172640](http://ubuntuforums.org/showthread.php?t=2253791&p=13172640#post13172640)
and here is another case of the same:
[http://ubuntuforums.org/showthread.php?t=2256459](http://ubuntuforums.org/showthread.php?t=2256459)
with a successful outcome reported.

In Xubuntu 15.04, the newer xfce4 power manager (version 1.4.2) inhibits the DPMS, making this or xset unnecessary from my observations.

---

### Post by mike555 on 2015-09-05
Thanks so much, that worked .

---

### Post by Dennis N on 2015-09-05
Good to hear that it worked. As I mentioned, when you eventually move to 15.04 or beyond, the problem should no longer exist.

---

### Post by mike555 on 2015-09-06
Well damn, my monitor is blacking out again, I checked and DPMS is running ,even though I put   xset -dpms  in my startup.   I guess I'll have to update to 15.04    ............ if anyone has any ideas please let me know...

---

### Post by Dennis N on 2015-09-06
Well, that's surprising. I would expect one or the other fix would work. Do you have light-locker enabled and running as a startup application? It can blank the screen too. If so, disable it from it's settings dialog, or remove it from startup applications.

Did you check to be sure that xscreensaver is actually autostarting and running after you log in? I would use htop, and then filter for "screensaver" with F4 to eliminate everything else. You can also use it to check for light-locker running.

---

### Post by mike555 on 2015-09-06
I don't seam to have light-locker running, xscreensaver is not listed in my startup, should it be, and if so how.

---

### Post by Dennis N on 2015-09-06
Settings > Session and Startup > Application Autostart Tab
Click on "Add"
Fill in a name, a description, and command:

```
Name: Screensaver
Description: Screensaver and locker   
Command: xscreensaver -no-splash

``` 
Click "OK"

Log out and back in and it will start running. In the future it will start when you log in. I hope that fixes your problem. I also disable light locker in its settings dialog which seems to be enough to keep it from doing anything ("Enable Light Locker" set to OFF). If necessary, you can uncheck "Screen Locker" in the same Session and Startup dialog and it should not start at all.

---

