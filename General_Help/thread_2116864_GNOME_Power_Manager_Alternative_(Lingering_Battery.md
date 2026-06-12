---
title: "GNOME Power Manager Alternative (Lingering Battery Status Problem)"
date: 2013-02-17
forum: General Help
---

### Post by bluebrave on 2013-02-17
Ever since I upgraded from 10.04 to 12.04.1 (now 12.04.2) on my laptop, the battery status indicator has been non-functional.  Status is not reported (icon won't change when I pull the power cord), the charge level is inaccurate (doesn't change during use) and no warning is given when the battery is critically low (machine just shuts down).  I've previously  [documented the issue here]("http://ubuntuforums.org/showthread.php?t=2052156").  It seems that gnome power manager fails to update the battery power level after startup (it just reports what the level at startup was and never changes).

Since then, I've continued to seek a solution and patiently waited for one to no avail (tried reinstalling gnome power manager, refreshed the applet, altered power schemes, and reinstalled libnotify-bin notify-osd). 

Right now, I've added Jupiter (it does alter the power scheme when the power is unplugged - so somehow it is getting some sort of power status updates).  However, it doesn't really report battery status or give me warnings.

If anyone know a solution to get power manager working again please pass them on.  Otherwise, I would love to know of an alternative battery status program that can run in the panel and give me warnings ([I found one]("https://live.gnome.org/BatteryStatus") but it is not available for 12.04/precise).

---

### Post by bluebrave on 2013-02-19
Hoping someone can help.  I understand battery status seems to have been an issue with Ubuntu for a while but if anyone knows of an alternative monitoring program, I would love it.

Right now, I can't use Ubuntu on the laptop unless it is plugged in as there is no way of knowing when it will shut off on battery.

---

### Post by UltimateCat on 2013-02-19
Hi:

Go to System>Preferences>Power Management and

Within your Power Manager there should be a box you can check to give you the status of your battery.  (I think) there are 3 options to choose from-

This Power Management wiki may help.

[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)
[http://askubuntu.com/questions/tagged/gnome-power-manager](http://askubuntu.com/questions/tagged/gnome-power-manager)
[http://ubuntuforums.org/showthread.php?p=9677323](http://ubuntuforums.org/showthread.php?p=9677323)

Here is a few commands that you can try:
[http://askubuntu.com/questions/7485/battery-not-detected](http://askubuntu.com/questions/7485/battery-not-detected)

BTW XFCE is the one Power Manager that I use but I am not sure if you can use it in Ubuntu-

Hope this helps

---

### Post by bluebrave on 2013-02-19
UltimateCat - Thanks for the tips.  I've actually looked through those prior to posting (none worked for me).

On my power manager, I do have battery options (at least it is recognizing that I have a battery), however the battery status is also not updated (just stays the same).  I also noticed that the "show battery status in menu bar" drop down is always blank - I can select different options but none are ever saved.

Also, clicking on "power statistics" and details tab under the battery reveals that both "time to full" and "time to empty" always show 0 seconds.  Somehow the battery information isn't being transmitted on 12.04.

I will look XFCE and see if it is a workable solution - on an initial search it doesn't look like it is but I'll try a bit more.

---

### Post by bluebrave on 2013-02-21
Decided to try a couple of the above solutions again.  Still no luck (I was hoping I had missed something)...bummer.

At this point, I guess I will have to keep the laptop plugged in when using Ubuntu or use Win7 (I have a dual boot) when I can't plug it in somewhere.  If anyone has any other ideas/solutions, please share.

Since I'm still pretty new to this forum, does anyone know if it would be appropriate to post my question on availability of a different power manager app in the Ubuntu Application Development section or is that reserved for current apps rather than requests?

---

