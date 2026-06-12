---
title: "Web server alternatives"
date: 2005-08-25
forum: General Help
---

### Post by endtime on 2005-08-25
Sorry that's not a very good title, I couldn't think of a good way to summarize my question, which is as follows:  My ISP (Comcast) doesn't allow me to run a web server - I discovered this when I tried to log in from college one day and it wasn't working, and then I read the T&C on their site.  I want a way to download files from the PC in my room (6 year old Dell P3 500Mhz, runs Hoary fine BTW  :smile: ) to my PC in my dorm at college.  Is there a way to do this without violating Comcast's rules?  Thanks...and if there's any more useful info I can provide please let me know.  I have a SonicWall at home BTW, my dad installed it to stop my little brother looking at rude websites, but I have admin access on it so I don't *think* it will be a problem.

---

### Post by amohanty on 2005-08-25
VNC...

Do you have a static IP?

AM

---

### Post by nocturn on 2005-08-26
Just use SSH for it (It has a command, SCP to tranfer files, there are GUI's for it and Nautilus supports it).

A lot of ISP's block access to ports below 1024, what you could do is have SSH listen on something like 2022 to get arround it.

If you need access from a Windows PC, Putty is a great client.  I heard that WinSCP is a nice GUI frontend.

---

### Post by az on 2005-08-26
... And so that you know exactly where to go (what the IP address of your box at school is, since it will change often, unless you are paying for a static ip...)
Go to dyndns.org and register for a free account.  Pick a domani name (like pickles.dyndns.org or something) and then install ddclient on the box.  Use use the settings you just registered (domain name, username, password)

So then, instead of finding out what ip address your box currently has, it will be accessibel by doing

ssh [email]me@pickles.dyndns.org[/email]
(where "me" is you)

---

### Post by endtime on 2005-08-26
[QUOTE=azz]... And so that you know exactly where to go (what the IP address of your box at school is, since it will change often, unless you are paying for a static ip...)
Go to dyndns.org and register for a free account.  Pick a domani name (like pickles.dyndns.org or something) and then install ddclient on the box.  Use use the settings you just registered (domain name, username, password)

So then, instead of finding out what ip address your box currently has, it will be accessibel by doing

ssh [email]me@pickles.dyndns.org[/email]
(where "me" is you)[/QUOTE]
 Thanks guys....I have a static IP at home but at school it changed once or twice last year, hasn't changed so far in my dorm for this year.  I run Ubuntu at home but only Windows at school.

I don't really need to access my PC at school from home, and I don't think I could anyway - my Uni blocks access from off campus (annoying).  I'll look into Putty and try and get SSH working here.  Thanks for the help.

---

### Post by spin2cool on 2005-08-28
One more option is to just set Apache to use port 8080 (or some other high port).  Then the webserver should work fine, but you'll have to type something like http://<your ip>:8080 /myfiles/

---

