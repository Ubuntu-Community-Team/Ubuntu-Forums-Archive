---
title: "Help Configuring Boot Applications"
date: 2012-12-27
forum: General Help
---

### Post by waco001 on 2012-12-27
Hi guys, I'm new to Ubuntu Server but I was wondering if anyone could help me configure my systems boot? What Im really asking for is if anyone could help me autologin into the os and run a sh script from there... One more thing is that how would I be able to see what is on the screen when I ssh into the server is the same thing that is actually showing up on the server? Thanks :confused:

---

### Post by waco001 on 2012-12-28
Anyone? :/

---

### Post by waco001 on 2012-12-28
bump

---

### Post by Bucky Ball on 2012-12-28
Setting a server for auto-login is probably not a good idea (unless it is not connected to the outside world and only serving your LAN). 

Please wait 24 hours before bumping your thread, but it can be bumped by adding any new information you find or progress report ...

---

### Post by ryankidman on 2012-12-28
you need special server for auto log in

---

### Post by waco001 on 2012-12-28
> **Bucky Ball said:**
> Setting a server for auto-login is probably not a good idea (unless it is not connected to the outside world and only serving your LAN). 

Please wait 24 hours before bumping your thread, but it can be bumped by adding any new information you find or progress report ...

Oh Sorry for bumping, but could you help me configure the auto login and how to run a shell script on login?

---

### Post by steeldriver on 2012-12-28
An ssh session is a separate tty session - it has nothing to do with what appears on the physical screen of the server

What exactly do you want to do? is it something you could perhaps do with a cron job on the server rather than an interactive login? If you really do need to execute a script on login, you could call the script from your .profile or .bashrc

---

### Post by Myoldmopar on 2012-12-28
Yeah, I'm not sure about the auto-login on server edition, I've never used it.  If your script does not require privileges then adding it to your profile file, however there are several files out there:

.bash_login
.bashrc
.profile
/etc/profile

I thought about taking the time to look up when each of these get hit, but I thought I'd leave that for you or others.  The key point is that you may not want your script to run EVERY time you open a terminal window.  

If your script requires admin privileges then you probably need to add it to cron or use an init script '/etc/rc..'.

This is pushing my knowledge, but hopefully these will be discussion points if nothing else.

Cheers

---

