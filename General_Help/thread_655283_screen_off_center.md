---
title: "screen off center"
date: 2008-01-01
forum: General Help
---

### Post by Psyphre on 2008-01-01
Hey,

My XP, Vista and Ubuntu Gutsy are perfectly in the middle, however when I installed linux mint it was off centre (too far to right and too far down). I have installed the latest nvidia drivers using envy (which solved the problem for gutsy but not on linux mint). Because I dual boot, i cant just change the settings on the monitor, because all the other OS's are fine except mint.

Ive looked through the forums and found some people with similar problems, but just couldnt understand how they fixed it. Does anyone know how I can readjust the positioning of the screen?

Thanks.

---

### Post by rubicon on 2008-01-01
The only reason for screen to be off-center I see is video-drivers. What video-card do you have?

---

### Post by Psyphre on 2008-03-19
nvidia gainward 7900gs

I used the same method to install the drivers in mint as i did in ubuntu, with "envy".

---

### Post by lavinog on 2008-03-19
how is your monitor connected to the the computer (dvi or vga cable)?
if you use the auto adjust button on your monitor does it fix it?
what resolutions are you using on each distro.
some monitors store different positions for different resolutions.
I see this alot on some monitors...but it goes away if you use the dvi cable connection.

---

### Post by Psyphre on 2008-03-20
I use a vga cable that goes to a dvi adapter (cos the graphics card only has dvi).

Yes if i click the auto button on the monitor is will centre it, but then it wont be centred for xp or ubuntu. Its strange taht its only for mint.

I use 1680x1050 for everything.

---

### Post by lavinog on 2008-03-22
the timings might be different in mint. Maybe the difference is in xorg.conf
look in the monitor section for things like dotclock, htimings, vtimings or anything else


I take it your monitor doesn't offer a DVI connection.

---

### Post by Psyphre on 2008-03-23
Not sure, but i think it does. I just havent got a DVI cable. Would it really solve the problem if i did use DVI? Also, how big a difference is dvi in terms of quality over the standard cable?

---

### Post by lavinog on 2008-03-26
Switching to the DVI cable eliminated the need to hit the auto adjust button every time for me.

The quality is hard to notice for me except that the monitor uses the correct settings.

---

