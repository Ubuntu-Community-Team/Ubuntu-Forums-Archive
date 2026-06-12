---
title: "Many Issues with 16.04"
date: 2016-04-22
forum: General Help
---

### Post by adamtheguitarman on 2016-04-22
This is my list of things that worked fine in 14.04 that don't seem to now:

1) Cannot install third party .deb packages via the software center.  Have to use dpkg every time and apt-get install -f multiple times before it will actually work.
2) Software Center does not want to open.  This is hit or miss.  Sometimes it's just a blank white screen.
3) Nautilus will not launch.  I cannot launch it via the terminal or the Unity bar.  I have to restart the PC each time it breaks and it may or may not launch.  God forbid I close it during a session, I have       to reboot again.
4) Network does not show up properly in the top bar.  I am on a WiFi connection, but half the time when I connect it shows that I am either on a wired connection or that I have no connection at all.
5) apt-get update gets stuck.  I currently cannot use that command.  It gives no errors, it just sits in the terminal window and never does anything.

I know there are probably fixes for each of these things individually, but I don't understand why none of it works on a fresh install when 14.04 had no issues on a fresh install.  I also see no help topics for these issues, but I know others have to be experiencing the same issues!  My friend also has issues 1, 3, and 4.  I didn't want to have to reinstall 14.04 since I spent last night syncing my files with MEGA, but I may have no choice.  Anyone know if I'm just massively screwing something up and this can all be solved with a single fix?

My system is a Dell Latitude 6230 w/8Gb of DDR3, an i5 3320m @ 2.6 GHz, and a 128Gb Samsung SSD.  I have only installed three programs since installing Ubuntu - Unity for Linux, Geany, and MEGA.

---

### Post by grahammechanical on 2016-04-22
> Have to use dpkg every time and apt-get install -f multiple times before it will actually work.

That is a failure of the package maintainer. Are you trying to install a deb package that has not been updated to 16.04?

> Software Center does not want to open.  This is hit or miss.  Sometimes it's just a blank white screen.

I have not experience that at all since my development version of 16.04 first received Gnome Software.

> Nautilus will not launch.  I cannot launch it via the terminal or the  Unity bar.  I have to restart the PC each time it breaks and it may or  may not launch.  God forbid I close it during a session, I have       to  reboot again.

I have not found that to be the situation. Nautilus did go through a period where if it was maximised it would not restore to the smaller size again. And also there was a period where the menus would not appear. Both bugs seem fixed.

> half the time when I connect it shows that I am either on a wired connection

Network Manager is now under the control of systemd - RedHat software.

> apt-get update gets stuck.  I currently cannot use that command.  It  gives no errors, it just sits in the terminal window and never does  anything.

Something not right with your sources list?

Regards.

---

### Post by adamtheguitarman on 2016-04-22
I can't even open Nautilus.  It blinks a few times, the cursor changes for a few seconds, then it stops and won't open.  Don't know how there could be anything wrong with my sources, there was nothing installed the first time I tried it.  The network thing I can live with, I don't really care what it shows as long as I have a connection.  And I have no idea why Software Center shows a blank screen.  The few programs I've installed have shown that they are compatible with 16.04, the exception being Unity - I used the platform-agnostic build for that.

---

### Post by adamtheguitarman on 2016-04-26
Ended up reinstalling 14.04.  A clean 16.04 install did not help.  The fact that I sometimes cannot browse my file system or install ANY applications via the GUI is too much.  I usually wait for LTS releases because of the stability, but this one doesn't seem to be ready yet.

---

