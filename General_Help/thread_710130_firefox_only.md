---
title: "firefox only ?"
date: 2008-02-28
forum: General Help
---

### Post by delta_9 on 2008-02-28
hello.  I have a need to have a box that when it starts up only displays Firefox in full screen and is locked this way.  The purpose is to stop people messing up a public access computer. I do not want people to have access to desktop menus only Firefox (damn public never know what they will do).  They also have a need type up documents so i will just set up hot keys to start open office  that would save me a lot of time. 

is this possible  ? sure it would have to be  if so any one know how ? or got a better idea ?

---

### Post by Circus-Killer on 2008-02-28
the only thing i could suggest is maybe create a user with even less privileges than normal user, that is also in its own group. make sure that the new user you create has only access to the essentials, mostly only read and execute privileges.

you could also then, once you've got the user set up the way you want it, make a safe backup of the /home/user contents. so if anyone messes with the files in there, you can easily just delete and re-add the user to the system.

not sure if it will work as securely as you wanted, but i'm sure it would be secure enough.

---

### Post by kesman on 2008-02-28
also you should use some other window manager than gnome or kde or xfce. Maybe fluxbox or windowmaker, since every application is usually launched with right-click on the desktop, and you can customize the menu to only contain firefox and openoffice in them.

---

### Post by .nedberg on 2008-02-28
Does it have to be firefox? Opera has a feature called kioskmode. I use it for kioskstations at work. Never had a problem with it.

Read more about it [here.]("http://www.opera.com/support/mastering/kiosk/")

---

### Post by delta_9 on 2008-02-28
thanx guys for your suggestions i will keep pondering about what would be the best action to take with solving this problem 
.nedberg  thank you for another option i will check that out right now. as any browser is fine.

nerdberg i could kiss you this *sounds* perfect i will try it out and if it works to my liking for those who are interested and did not click the link general gist of Opera's Kiosk Mode 

Opera can be run in kiosk mode, which is a mode mainly suited for information stands. Such stands are typically found in libraries, airports, bank offices, or shopping malls. The information stand will run a browser that lets the user browse for the necessary information, but denies access to the computer and browser settings. After a period of inactivity, the browser should reset and return to a specified home page.

The following document applies to desktop versions for Windows, Linux, Mac, FreeBSD, and Solaris. It was last updated for Opera version 9.0.

---

