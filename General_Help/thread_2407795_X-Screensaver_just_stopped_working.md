---
title: "X-Screensaver just stopped working"
date: 2018-12-09
forum: General Help
---

### Post by Nosphky on 2018-12-09
On 18-04, the screensaver worked with no adjustments needed or made to the default settings it had when initially part of the distribution. In the last couple of days, it just stopped working.
What controls the screensaver and where would I look to try to fix it ?

---

### Post by anarchy-x on 2018-12-09
Maybe try hitting alt+F2 and type "xscreensaver". If it's not running the settings loading banner will pop up. If it is.. nothing will probably happen. If nothing pops up and you have it installed then hit alt+f2 and type "killall xscreensaver" then run dialog again and "xscreensaver".

---

### Post by Dennis N on 2018-12-09
> **Nosphky said:**
> On 18-04, the screensaver worked with no adjustments needed or made to the default settings it had when initially part of the distribution. In the last couple of days, it just stopped working.
What controls the screensaver and where would I look to try to fix it ?

Ubuntu Studio 18.04 would use Light Locker as a 'screen saver' by default. Xscreensaver is not automatically installed. So look for Light Locker settings dialog in your main menu.

---

### Post by Nosphky on 2018-12-10
Thanks anarchy-x and Dennis N -  although the xscreensaver process was shown as running after boot-up (it is one of the autostart applications), there must have been something wrong. Killing the process and restarting did make it work.

I also checked with synaptic and Light-Locker is also installed. I always make a clean installation rather than updating the os - 14-04 then 16-04 and last install was 18-04 back in May. I never ever installed the xscreensaver myself - it was always the default and it worked fine until last Saturday when I noticed it wasn't working. When I rebooted Sunday, it didn't work, nor today. But killing the process and restarting did fix it.

Since there have been a load of small updates from ubuntu over the past few weeks, I wondered if one of those had caused my trouble.
Thanks guys.

---

### Post by Nosphky on 2019-04-09
Since I last had this problem in Dec 2018, xscreensaver has worked fine -- until about a month ago. Then I noticed that some days it worked fine and then the next day, no screensaver.  (machine is turned off at night and rebooted each day)

It seems to 'kick-in' on random days and not work on other random days. When it isn't kicking in to display some of its fine illustrations, I check and the xscreensaver process always appears to have started and to be running normally. It is in the startup menu to be launched at start up.

On days when it doesn't display a screensaver graphic, killing the process and relaunching it still doesn't guarantee that it will kick in on an idle machine.

Any ideas where I can look to see what could be interfering with xscreensaver ?

---

### Post by Nosphky on 2019-04-17
I found a hint that Power Manager applications had been known to interfere with xscreensaver. I work on a desktop machine so I never had any use for a Power Manager but when I checked, it is part of the UbuntuStudio distro. Nothing in Power Manager seemed to be configured to do anything (I certainly didn't configure it because I didn't know it was there) but I removed it completely.

Since then, so far so good - xscreensaver now functions as it should. If Power Manager was there from installation of 1804 UbuntuStudio, it certainly didn't interfere with xscreensaver in the first few months. So maybe there was some 'improvement' or update feature changed in Power Manager which caused it to interfere - or maybe the problem will turn out to be nothing to do with Power Manager.

Time will tell.

---

### Post by oldrocker99 on 2019-04-17
If your screen goes black after a period of time, it will prevent xscreensaver from working, or showing the screensaver. I simply went to the Power Manager and set it that the screen never goes blank. The screensaver then works just fine.

---

### Post by Nosphky on 2019-04-19
Thanks, oldrocker.  I don't know if the screen ever went blank after a period of time. I never set it so and I deleted Power Manager so I can't check now.

Something must have changed to my setup or an update upset Power Manager because from the summer when I installed 1804 as a fresh installation, the xscreensaver worked fine until around December when I started this thread.  I never saw the screen go blank - it just kept displaying what I last worked on before I left the machine.

Since I deleted Power Manager, xscreensaver has worked perfectly. So I'm going to wait a couple more days and if still working well, I'll mark the thread solved.

---

### Post by Nosphky on 2019-04-22
Well, another couple of days and all's well so I reckon the problem must have been linked with Power Manager.

---

