---
title: "Hibernate is flaky"
date: 2015-09-27
forum: General Help
---

### Post by Ralph L on 2015-09-27
I am running Xubuntu 14.04 LTS.  I like to use hibernate, but it doesn't always resume correctly.  Most recently it seemed to resume ok--brought up the apps that were there during the hibernate shutdown, but just kept reading my disk forever.  Also, the cursor was frozen.  Finally after several minutes I had to power it off and then back on--of course I lost my apps.  When I search on the web I see lots of different problems with hibernate, but few concrete answers on how to fix it.  Some of the answers referred to editing /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla.  I don't even have that file in my system, yet hibernate works about 70% of the time.  Does xubuntu enable hibernate in some way other than through the use of that file.  I don't want to add that file if it is going to make hibernate worse.  Can anybody point me in the right direction that I can at least solve some of the hibernate problems.

---

### Post by kerry_s on 2015-09-27
well like it says here: [https://help.ubuntu.com/stable/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/stable/ubuntu-help/power-hibernate.html)

"it does not work in many cases", the reason it was disabled was because eventually it would cause drive corruption, which means a broken os & on & on ...

have you tried "save sessions for future logins" instead ?

---

### Post by Ralph L on 2015-09-29
kerry_s
Thank you very much for your response.  No, I wasn't aware of "save sessions for future logins" in Sessions and Startup.  I tried it, but it only partially worked.  Firefox alway came up with the message that firefox was already running.  Actually this isn't a big deal as all I had to do was click OK and firefox did its own recovery.  However, it wouldn't save and restart my libreoffice stuff.  This is more of a concern, but libreoffice (like firefox) has its own recovery feature.  Mousepad restarted, but lost the unsaved content (important).  Geeqie forgot about the file it was displaying (somewhat important).  So it is kind of like hibernate--sometimes works and sometimes doesn't.
Also, the web site you referenced says that for hibernate to work I should have the file  /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla.  I don't have it, yet xubuntu 14.04 has hibernate enabled in the shutdown menu.  Apparently xubuntu has another place to enable it.  Just to try something to fix the problem I created that file with this content: ```
[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.hibernate-multiple-sessions
ResultActive=yes
```
I will try it for a while.  However, the first time I tried it, it disabled networking and I couldn't restore it without another hibernate, so still flakey.
Do you know why hibernate never gets fixed??  It has been flakey like this for several years.  Does nobody else use it?

---

### Post by kerry_s on 2015-09-29
no i never use hibernate, it's to slow, a standard startup from shutdown is faster.
i only suspend during the day, i shutdown when i go to sleep.

i am using xubuntu 14lts & do not have hibernate in menu/dialog.

---

