---
title: "auto-login without (K)DM"
date: 2007-01-10
forum: General Help
---

### Post by ashrack on 2007-01-10
Recently found that KDM takes a lot of time to start when U boot the machine. And since I use auto-login anyways I was thinking of removing KDM and just setup kUBUNTU so that it would automaticly did the following:
loged me in the system
and started X (startx, kwin)

How do I do that?

---

### Post by der_joachim on 2007-01-10
You can set the default runlevel in /etc/inittab (in Dapper that is, I do not know about Edgy). The runlevel you want, is different between distros, but I think it's 2. 

I do not know about autologin in console, but when logged in, your .bash_profile file handles any automagically starting scripts and apps. 

You will have to edit your .xinitrc to automatically start KDE.

---

### Post by ashrack on 2007-01-10
.xinitrc is already properly set. So I only type STARTX and it startx KDE!
But as per auto-login I don't know how.

---

### Post by thor918 on 2007-01-17
I wanted to autostart startx instead of gdm, so what I did was add startx at the end of "rc.local"
pico /etc/init.d/rc.local

that works okey for me ;)

that would run it as root. 
so perhaps you need something userswitching before it runs startx?

---

### Post by bodhi.zazen on 2007-01-17
Auto Login:
	[http://doc.gwos.org/index.php/Automatic_Login_No_Authentication](http://doc.gwos.org/index.php/Automatic_Login_No_Authentication)
	[http://www.ubuntuforums.org/showthread.php?t=303319](http://www.ubuntuforums.org/showthread.php?t=303319)

---

### Post by thor918 on 2007-01-19
Perhaps you should try using gdm instead...
autologin using gdm was quite easy!
I just tried this and it works

/etc/X11/gdm/gdm.conf
	
   AutomaticLoginEnable=true
   AutomaticLogin=USER

Exchange variabel USER with the user that are going to be autologged in


from my test it seemed quite fast. But still it may use more resources than what @bodhi.zazen mentioned

---

