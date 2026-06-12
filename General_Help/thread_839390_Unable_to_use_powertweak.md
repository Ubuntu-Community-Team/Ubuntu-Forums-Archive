---
title: "Unable to use powertweak"
date: 2008-06-24
forum: General Help
---

### Post by x1a4 on 2008-06-24
Hi,

I just installed all the powertweak packages but none of them work.  

When I start the powertweakd daemon it returns no error, but it's not running.  I tried starting it using these two methods:
```
/etc/init.d/powertweakd start
/usr/sbin/powertweakd
```

It does create the powertweakd socket and .pid file in /var/run/, but ps tells me it's not running. 

When I try to run gpowertweak or lspowertweak it exits with return value 139: 
```

Error creating socket to : /var/run/powertweakd	Connection refused
Segmentation fault
Exit 139

```

Those of you who have the same problem, please don't reply saying so.  The more replies in a thread the less likely it is somebody who knows how to fix this will read this thread, assuming we're being helped, and move on to somebody else.

---

### Post by eljota on 2008-11-13
powertweak must run on superuser and the command to run the program is gpoweartweak. You can do this:
```
sudo gpowertweak
   -or-
(i think this works 2) gksu gpowertweak
```

---

### Post by x1a4 on 2008-11-14
I was running it as root.  That's not it.

---

### Post by Runaway1956 on 2008-11-29
> **x1a4 said:**
> I was running it as root.  That's not it.

Did you get it sorted out?  I have just installed the package, to see what it could do.  There was no indication anywhere just what the proper command was.  Google found this page for me.

Modifying eljota's advice, I opened a terminal window, did sudo -s then ran gpowertweak.  Thanks, eljota, this got me up and running.....

Though there isn't a lot to manipulate with the program.  The only changes that I found that actually worked, and I felt comfortable diddling with were latency settings on NIC's.  ;)

---

### Post by sigurnjak on 2008-12-14
How do you actually make changes with power tweak ?

I  am curious about my cpu .It tells me it is running at 2.4 gigs but that is capable of 2.8 . Also i am running ibm  server pc so they are not friendliest  to tweak .

---

