---
title: "[SOLVED] Can't print with Gnome applications"
date: 2008-06-06
forum: General Help
---

### Post by Mateo on 2008-06-06
when I try to print in Evince and i select the printer I want to use, the "Print" button greys out!!!  What could be causing this.  I can print test pages with the Administration > Printing application but I can't print from Evince or Epiphany or Gedit or any of the "gnome" applications?  what is causing this problem!!

---

### Post by Mateo on 2008-06-06
bump.

---

### Post by Mateo on 2008-06-07
bump.

---

### Post by Mateo on 2008-06-07
bump.

---

### Post by Mateo on 2008-06-07
bump.

---

### Post by Mateo on 2008-06-07
bump.

---

### Post by Mateo on 2008-06-08
bump.

---

### Post by jmasgalas on 2008-06-19
How was this solved? I have the same issue.

---

### Post by editrix on 2008-06-19
jmasgalas, you're not the only one. And I think it's a recent thing, maybe to do with recent updates? Anyway, search around (including my post on the subject) and you'll see it's a problem waiting for a solution.

---

### Post by jmasgalas on 2008-06-19
I did do a search but didn't find much. You mean there is no workaround?

---

### Post by editrix on 2008-06-19
> **jmasgalas said:**
> I did do a search but didn't find much. You mean there is no workaround?

Not yet. Sigh!

---

### Post by jmasgalas on 2008-06-20
Can you point me to other topics about this or the bug report?

---

### Post by editrix on 2008-06-20
> **jmasgalas said:**
> Can you point me to other topics about this or the bug report?

Well, of course I can't find it now. I'm on dialup, and it just took 3 minutes for the launchpad page to load, so ...

If you want to go poking around there yourself:

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

or you can search through uboontu (the Search these forums most easily link in my sig). But I'll warn you, I didn't find any solutions.

Edit: It just occurred to me we really should be starting a new thread, since this one's marked solved. Or you might want to piggyback onto my thread [http://ubuntuforums.org/showthread.php?t=834212](http://ubuntuforums.org/showthread.php?t=834212). It's Kubuntu, but as you'll see it's also Gnome.

---

### Post by Mateo on 2008-06-20
My problem was related to the /etc/hosts file.  Apparently 127.0.0.1 has to be localhost, or it won't print.

---

### Post by editrix on 2008-06-20
> **Mateo said:**
> My problem was related to the /etc/hosts file.  Apparently 127.0.0.1 has to be localhost, or it won't print.

Thanks. Here's the relevant lines in my /etc/hosts:

127.0.0.1 localhost
127.0.1.1 darren

This what you mean?

---

### Post by jmasgalas on 2008-06-23
I have 127.0.0.1 as localhost but still can't print.

---

### Post by mempman on 2008-06-23
maybe it has something to with permissions..?

---

### Post by jmasgalas on 2008-06-24
I can't see anything with hosts or permissions(can't print as root or sudo either). I can remove and readd the printer but still does not fix it. Wierd thing is that from my laptop with the same printer, I can print fine. I have hardy on both my laptop and desktop. I also have all the updates installed on both.

---

### Post by editrix on 2008-06-24
> **jmasgalas said:**
> I can't see anything with hosts or permissions(can't print as root or sudo either). I can remove and readd the printer but still does not fix it. Wierd thing is that from my laptop with the same printer, I can print fine. I have hardy on both my laptop and desktop. I also have all the updates installed on both.

I'm quite convinced my problem has something to do with the networking setup, and I know it sounds weird, but maybe yours does, too. Can you check files like /etc/hosts and maybe /hostname and see if they're identical (except for the computer name, of course) in the two computers?

---

### Post by jmasgalas on 2008-06-27
Here is something new.

I noticed that on my laptop when I go to System>Administration>Printing and choose new Printer, it searches for printers and finds our network printers. On my desktop it never finds any printer and I have to choose the connection and tpye of printer. So it might be something with the network not sure what though. All host files and configurations look the same as my laptop.

---

### Post by jmasgalas on 2008-06-27
Using hp-tools it did discover the printer and had me choose it from a list but I still cannot print from gnome apps. This is frustrating to say the least.

---

