---
title: "Install windows based programs requiring Java JRE"
date: 2008-06-20
forum: General Help
---

### Post by cedance on 2008-06-20
Hi,
I have this software "Visual Thesaurus" which I have been using in Windows for quite sometime and I recently made a dual boot with the idea to get acquainted with Ubuntu Linux and leave Windows! :)

However, this program is quintessential for me which requires Java JRE and It doesn't run if I install this using Wine in Ubuntu. It doesn't start. However, I have installed Java runtime environment in my system. Could any1 help me with this?

thank you,
cedacne.

---

### Post by etnlIcarus on 2008-06-20
> **cedance said:**
> Hi,
I have this software "Visual Thesaurus" which I have been using in Windows for quite sometime and I recently made a dual boot with the idea to get acquainted with Ubuntu Linux and leave Windows! :)

However, this program is quintessential for me which requires Java JRE and It doesn't run if I install this using Wine in Ubuntu. It doesn't start. However, I have installed Java runtime environment in my system. Could any1 help me with this?

thank you,
cedacne.
First thing to understand is WINE isn't *perfect* and it's API compatibility with Windows isn't even 50%. winehq.org is where you go to check application compatibility and to find any workarounds which are required to run the application you want. As I couldn't find a WineHQ entry for "Visual Thesaurus", after a quick search I assume it's a pretty obscure piece of software.

The second thing to make sure of is that you installed Java *for windows* and you didn't download the linux version (and that you didn't just install Java from the repos).

The third thing to try is *kthesaurus* and *GTK Aiksaurus*, which are native linux apps, which might make worthy substitutes.
If you search for these in either the, "Add/Remove Programs", programme or Synaptic Package manager, you can install them.

Hope I was of some help.

---

### Post by cedance on 2008-06-21
You dont know how useful this software is. You should look here to get an idea about what I mean. Its not like othe thesaurus softwares.
[http://www.thinkmap.com/visualthesaurus.jsp](http://www.thinkmap.com/visualthesaurus.jsp)

However, thank you for suggesting what I could do. I will try them!!!

cedance.

---

### Post by hosami on 2011-08-03
Thanks to etnlIcarus

I just want to say, having had the same problem, it got fixed after I installed WINDOWS version of JAVA.

[http://download.oracle.com/otn-pub/java/jdk/7/jre-7-windows-i586.exe](http://download.oracle.com/otn-pub/java/jdk/7/jre-7-windows-i586.exe)

---

