---
title: "Error with Updates"
date: 2008-07-10
forum: General Help
---

### Post by karlillo on 2008-07-10
Hi, I'm a noob at Ubuntu; I just installed it yesterday. I have the following problem. When I try to install the Updates I get this error:

[COLOR="Blue"]E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to 
correct the problem.

E:_cache->open()failed, please report.[/COLOR]

I'm running Ubuntu 8.04 LTS on a dual boot system with Windows XP SP2.

Please Help
Thanks

---

### Post by danwood76 on 2008-07-10
Open up a terminal and enter:
```

sudo dpkg --configure -a

```

It means that a file wasnt configured correclty when it was installed, this will sort it.

---

### Post by overdrank on 2008-07-10
> **karlillo said:**
> Hi, I'm a noob at Ubuntu; I just installed it yesterday. I have the following problem. When I try to install the Updates I get this error:

[COLOR="Blue"]E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to 
correct the problem.

E:_cache->open()failed, please report.[/COLOR]

I'm running Ubuntu 8.04 LTS on a dual boot system with Windows XP SP2.

Please Help
Thanks

 Hi and welcome, you need to use that command in the terminal located under applications, accessories, terminal. Use the command ```
sudo dpkg --configure -a
```
Edit to slow :P

---

### Post by karlillo on 2008-07-10
Thanks to both of you; the problem was fixed. :)

---

### Post by pounditflat on 2008-09-20
Awesome. Thank you so much !

---

### Post by Stroots on 2008-09-21
**Hi.  I'm also a noob, with the exact same problem.  When I try to download the updates or even install anything new,  I get this message:**

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

**I entered the above advice into the terminal and I get this:**

pauls@paul-desktop:~$ sudo dpkg --configure -a
[sudo] password for pauls: 

At this point, I am not able to type anything into the terminal and nothing is solved. 

Not sure where to go from here; any help is VERY welcome!

Thanks

---

### Post by karlillo on 2008-11-19
> **Stroots said:**
> **Hi.  I'm also a noob, with the exact same problem.  When I try to download the updates or even install anything new,  I get this message:**

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

**I entered the above advice into the terminal and I get this:**

pauls@paul-desktop:~$ sudo dpkg --configure -a
[sudo] password for pauls: 

At this point, I am not able to type anything into the terminal and nothing is solved. 

Not sure where to go from here; any help is VERY welcome!

Thanks

You have to type the password you use lo log-in to Ubuntu; it won't show on the screen, just type it correctly and press enter

---

