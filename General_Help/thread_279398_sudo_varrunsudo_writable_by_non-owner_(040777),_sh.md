---
title: "sudo: /var/run/sudo/ writable by non-owner (040777), should be mode 0700"
date: 2006-10-17
forum: General Help
---

### Post by yosiska on 2006-10-17
Hi, Everyone


Today I just have This Problem dunno why. (my 2nd day in Lynux World (**Ubuntu is my choice!! after reading lots of research!**))


"**sudo: /var/run/sudo/ writable by non-owner (040777), should be mode 0700**"
[B]
Meaning:[/B] I can not use Sudo nor GKsudo (Those fuctions are locked). So I was able to to fix it after reading "Official Ubuntu Book (Spent $34.99).


**WHAT I DID to fix that:**


[LIST]-
[/LIST]Open the terminal and type: **su** (You got that right just **[SIZE="4"]su[/SIZE]**)

[LIST]-
[/LIST]Type in your 'root password' not your log in to the ubuntu (create root password if you don't have one) by going to 

[LIST]-
[/LIST]System ===> Administration ===>Users and Groups ====>Enter your password to login to the system ===> in the user tab "check" Show all users and groups===>Highlight root ===>click Properties =====>enter password by hands===close the apps by clicking "OK" and "OK".

[LIST]-
[/LIST]**chmod 0700 -R /var/run/sudo/**  (make sure the last trailing slash is included)


That is it!!! Hope it helps!!

Good Luck!!

---

### Post by Glendon on 2007-06-11
Thanks for posting this. You just saved me a whole lot of headaches.

---

### Post by wajiw on 2007-07-07
helped me too! thanks!

---

### Post by marshh24 on 2008-01-30
Hi,
  Thanks for posting how to fix the root password.  It helped me while messing with the /var directory for permission issues on apache.  
Thanks again.

Marshall  :)

---

### Post by abuelitnt on 2008-03-18
This is the true spirit of free software. You, having kindly posted this, just saved me untold hours over something really simple.

#chmod 0700 -R /var/run/sudo/

> **yosiska said:**
> 
Today I just have This Problem dunno why...


I do now wonder why sometimes a simple sudo installation in Debian distros won't set the right permissions itself. Meh, I'm new so perhaps I'll learn. Thanks again Yosiska for taking the time!

---

