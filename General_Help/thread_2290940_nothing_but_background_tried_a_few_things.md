---
title: "nothing but background tried a few things"
date: 2015-08-16
forum: General Help
---

### Post by rego2 on 2015-08-16
Would appreciate if someone could help

I got alot to do, moving soon, but helping someone out. When I got the laptop was nothing but a background.
created a folder to get to programs etc.
ctrl, alt f6 to get to terminal..I then
created another user; everything works fine within the other user but have to use sudos because it is not granted full power.
Oh yeah when I start the cpu it goes to (background only user) everytime 
would solve alot if I could get the background only user unity fixed but if I could get the cpu to start by asking what user to choose from that will help me out as a short cut. 
also when the cpu starts up says error: diskfilter writes are not supported         press any key to continue........
tried doing this to fix the diskfilter within the created user/not the main user [https://www.youtube.com/watch?v=g0aKXbOnYow](https://www.youtube.com/watch?v=g0aKXbOnYow)  but it took me to the same screen but with no writting or search button. 
let me know what you can help me with

---

### Post by TheFu on 2015-08-16
I'd guess it is a permissions issue or corruption of settings.  Have you been using sudo with GUI programs?

What do you mean by "start the CPU?"  If the PC is running, the CPU is already on.

---

### Post by jim_deadlock on 2015-08-16
Type "users" into your dash, run the Users (or Users and Groups if you have it) app, select the good user and click to change the password then choose "not asked on login". Delete the bad user. Done.

---

### Post by rego2 on 2015-08-16
forgot to mention I''m new to ubuntu; so I don't know all of the language.
As for as cpu I ment in general starting the computer!

---

### Post by TheFu on 2015-08-16
> **jim_deadlock said:**
> Type "users" into your dash, run the Users (or Users and Groups if you have it) app, select the good user and click to change the password then choose "not asked on login". Delete the bad user. Done.

Be careful that you leave a user with sudo escalation capabilities.  It is possible to remove that userid and while not the end of the world, it would be a hassle for someone new to Linux to fix - or if there is encryption involved, it could force complete data loss.  Be careful out there.

Might be easier to just mv ~/.config to ~/.config -old.

So "cpu" is the little chip. The thing you are talking about is the "case" or the "tower"... this is common across all computers that I'm aware.

Because I don't use stock "Unity" ubuntu, don't think I'm of much help. Sorry.  However, after the login, you should be able to logout, pick or type in a different userid and login with those credentials.

---

