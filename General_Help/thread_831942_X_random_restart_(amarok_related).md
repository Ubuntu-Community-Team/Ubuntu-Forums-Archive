---
title: "X random restart (amarok related?)"
date: 2008-06-17
forum: General Help
---

### Post by Joje on 2008-06-17
I'm using Ubuntu 8.04 32-bit on an almost new computer with Core 2 Quad, more than enough memory and a GeForce 8800GTS.

For some reason X seems to restart randomly. Any time I might be thrown out to the graphical login screen. It might be two minutes between restarts, and there might be a few hours, or even days. I think it might be related to amarok as I've never experienced the problem while not running amarok, but I'm almost always running amarok so I can't be sure. I also have the problem that sometimes my computer just freezes up totally and I can't seem to do anything but a hard reboot. This might be another symptom of the same problem as I've never experienced this while not running amarok either.

I also have the problem that Kaffeine sometimes crashes when I resume a video I've paused, this never happens in vlc or totem. It also seems to be totally random.

Also, Ktorrent crashes randomly now and again.

Could there be a Gnome vs. KDE-programs problem?

Anyhow, if anyone recognizes any or all of these problems, please help me :)

---

### Post by ftmichael on 2008-09-16
I'm having the same exact problem, but I don't have Amarok installed.  I'm using Ubuntu (with GNOME) Hardy.  Generally I'm running Pidgin, Firefox, and Audacious, but I have no idea what's causing X to randomly restart.

Michael

---

### Post by thomaskmfdm on 2008-09-20
I was recently experiencing similar random restarts of X (having the same result as ctrl+alt+backspace). I was able to solve this problem by installing the latest nvidia drivers using envy:
1. Download Envy from here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Get EnvyNG if you use Hardy otherwise get the other version.


2. Right-click the downloaded file and "open with Gdebi" or whatever it says to install it.

3. If it happens to error out on a dependency problem, just note down what file it lacks, and use the console window to apt-get it. Then try again with Gdebi to install Envy.

4. When Envy is installed, you can run it either of two ways:

(a) open the console and enter "sudo envy -t" (this is particularly useful after a kernel upgrade!)
(b) Click on the purple Envy icon in your System folder

Follow the instructions to install the latest Nvidia driver. :guitar:

Others have also experienced this problem it is discussed among other places in these topics:
[http://ubuntuforums.org/archive/index.php/t-674993.html](http://ubuntuforums.org/archive/index.php/t-674993.html)
[http://ubuntuforums.org/showthread.php?t=674660&page=2](http://ubuntuforums.org/showthread.php?t=674660&page=2)

Since Envy seems to solve this problem in almost all cases, it appears to be related to the nvidia drivers.

---

### Post by ftmichael on 2008-09-20
And once again I'm really sorry I bought an nVidia product.  I used Envy to get the latest driver, and it's too soon to know whether that's fixed the X crashing problem, but it's caused a new problem: The title bar of various windows doesn't show up unless I minimise the window and bring it back up.

Highlighting a different window and then coming back to the previous one *sometimes* gets rid of the title bar again.  Windows that aren't highlighted seem to always have the title bar; it's only the window that's highlighted that has a problem, and only sometimes.  See [http://ftmichael.transboys.info/storage/Pictures/screenshots/screenshot-20sept2008.png](http://ftmichael.transboys.info/storage/Pictures/screenshots/screenshot-20sept2008.png) - or the attachment - for an example.  The chat window in the top left is highlighted; the title bar should be purple, but as you can see, it's grey and the title text is invisible.  Changing tabs sometimes makes the title bar appear, and sometimes makes it disappear, seemingly at random.

**ETA:** A new development - title bar is sort of only half there on a highlighted window.  It's just happened once so far, but I got a screenshot.  See [http://ftmichael.transboys.info/storage/Pictures/screenshots/screenshot2-20sept2008.png](http://ftmichael.transboys.info/storage/Pictures/screenshots/screenshot2-20sept2008.png) and check out the IM window on the bottom left.

Michael

---

### Post by thomaskmfdm on 2008-09-23
I have also, been having this, but I believe I also had it before installing the new drivers.  Clicking on the title bar repeatedly after a minimize and restore seems to restore it.

---

### Post by ftmichael on 2008-10-26
Bump.

I'm still having the problem with the window title bars in Intrepid RC.  It'd be really nice to see a fix for this.

X is no longer restarting itself, though.

---

