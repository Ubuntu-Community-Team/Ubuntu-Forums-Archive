---
title: "SHUTDOWN &amp; RESTART disappeared from menu &quot;SYSTEM --&gt; QUIT...&quot;"
date: 2006-12-06
forum: General Help
---

### Post by sarbor77 on 2006-12-06
Hello from Sweden!

I have problem after haveing to use the power-button to shutdown ubuntu,  since the computer "stalled" when a OpenOffice document opened at the same time as I tried to use SHUTDOWN... (Maybe I did some updates before that as well).

Anyway, when I now try to SHUTDOWN or RESTART my computer, the 2 options have disappeared from the menu "SYSTEM --> QUIT..."

Can I get them back???


Now I'm using:
[INDENT]sudo shutdown -h now
sudo shutdown -r now
[/INDENT]

or 

[INDENT]Alt-R to restart
Alt-S to shutdown
[/INDENT]


I sent this also to UBUNTU FORUM SWEDEN, but there I only got: "Are you running xgl and compiz/beryl perchance?" What is that? 

(I have an 8 year old computer, Pentium 2, 350 MHz and 192 MB. I installed Ubunut 5.10 and then updated to 6.10 one week ago. No other programs have been installed.)

In [http://www.ubuntuforums.org/showthread.php?t=242210]("http://www.ubuntuforums.org/showthread.php?t=242210") GoBien recommands [http://www.ubuntuforums.org/search.php?searchid=7677217]("http://www.ubuntuforums.org/search.php?searchid=7677217") but this link is not valid any more. Is there a way to get this information from this topic aka solution???



I search this forum and found:
[http://www.ubuntuforums.org/showthread.php?t=269878]("http://www.ubuntuforums.org/showthread.php?t=269878")
[http://www.ubuntuforums.org/showthread.php?t=262202]("http://www.ubuntuforums.org/showthread.php?t=262202")

but I couldn't find any help there either.

Please help me,

// Sara.

---

### Post by strabes on 2006-12-06
from beryl-project.org: > Beryl is a combined window manager and composite manager written in C using OpenGL to provide acceleration. It is designed to be highly flexible, extensible, and portable, while all the while keeping in mind that the users knows how they want their desktops to act better than we do.

A problem with xgl/beryl is that it removes the shut down and restart buttons from the quit menu. I don't know how to fix this.

btw these commands are faster anyway: ```
sudo halt
sudo reboot
```

---

### Post by sarbor77 on 2006-12-06
But is this something that has been installed by UBUNTU using "SYSTEM -> ADMINISTRATION -> UPDATE MANANGER"? 

I have only installed recommanded updates for UBUNTU. I haven't installed Beryl as far as I know...

(It seems like BERYL uses a lot of memory and extra stuff. I don't think my 8 year old pentium 2 computer with only 192 MB can handle it.)

If it's installed, can I check that in any way?

Can I uninstall it easy? how?

---

### Post by sarbor77 on 2006-12-06
After downloading updates from UBUNTU today... it started to work again!!! I haven't done anything today that might help you solving this problem.. Strange!!!

Anyway, here is what I have done during the days:

1. Made changes according to:

> The fix (from [http://forum.beryl-project.org/topic-4863-1](http://forum.beryl-project.org/topic-4863-1) ) was to add to **/etc/gdm/gdm.conf-custom**:

[servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX).
1=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true

and to make two changes in **/etc/gdm/gdm.conf**. 
First replace "0=Standard" with "1=Standard" 
then set GdmXserverTimeout=50 (around line 200). 

The catch is that this takes away your ability to fallback on a non Xgl login.

2. Restarted my computer 4-5 times.

3. Verified that "Show action menu" is checked in the LOGIN WINDOW (SYSTEM -> ADMINISTRATION -> LOGIN WINDOW.

4. Changed the LOGIN WINDOW to another.

So far nothing helped... then after update today:

5. Used UBUNTU update (SYSTEM -> ADMINISTRATOR -> UPDATE MANAGER) and then installed all updates.

---

### Post by strabes on 2006-12-06
apparently for some reason you had XGL installed...?

---

### Post by atlas95 on 2006-12-08
Yeah, they are back too :D
I have custom gdm like 2 post top :)
Thanks you :)

---

### Post by atlas95 on 2006-12-11
Can we reduce boot time?

---

