---
title: "Do I need Firestarter?"
date: 2007-08-09
forum: General Help
---

### Post by nvteighen on 2007-08-09
I know this is a recurrent question; I've searched (or better, researched) a lot about this in the forums and found many answers or many kinds... Some say Firestarter is needed, only if you run a server, but then some say that you may run a server without knowing it... So, the only conclusion I could draw is that the need of Firestarter depends on what you do with your PC.

I use my computer primarly to write stuff, surf the web and read mail. Also, I like to test the programs in the repos (including some games), though generally I uninstall them almost immediately. I don't use peer2peer networks, but my Ubuntu PC shares a wireless connection  with 3 Windows PCs (2 XP & 1 Vista).

So, what do you recommend me? Firestarter or to stick with the default Iptables settings?

Thanks!

---

### Post by stchman on 2007-08-09
> **nvteighen said:**
> I know this is a recurrent question; I've searched (or better, researched) a lot about this in the forums and found many answers or many kinds... Some say Firestarter is needed, only if you run a server, but then some say that you may run a server without knowing it... So, the only conclusion I could draw is that the need of Firestarter depends on what you do with your PC.

I use my computer primarly to write stuff, surf the web and read mail. Also, I like to test the programs in the repos (including some games), though generally I uninstall them almost immediately. I don't use peer2peer networks, but my Ubuntu PC shares a wireless connection  with 3 Windows PCs (2 XP & 1 Vista).

So, what do you recommend me? Firestarter or to stick with the default Iptables settings?

Thanks!

From everything I have read/been told is that Ubuntu stealths all ports by default.  Unless you are doing something out of the ordinary I don't see the need.

---

### Post by eentonig on 2007-08-09
default iptables in Ubuntu are wide-open.

But for what you're using the Pc, I wouldn't bother spending the time to set up iptables. You're fine.

---

### Post by nvteighen on 2007-08-09
> **eentonig said:**
> default iptables in Ubuntu are wide-open.

But for what you're using the Pc, I wouldn't bother spending the time to set up iptables. You're fine.

So, I'm fine... that's good to know. Thank you very much!

But now, just to know a little more, can you tell me some (common) programs that may need Firestarter? So I can avoid them... or install Firestarter before them if I really need to.

Thank you both for your answers!

---

### Post by RedSquirrel on 2007-08-09
> **nvteighen said:**
> But now, just to know a little more, can you tell me some (common) programs that may need Firestarter? So I can avoid them... or install Firestarter before them if I really need to.


I'm not aware of any programs that need firestarter (i.e., it has no dependants).

---

### Post by nvteighen on 2007-08-10
> **RedSquirrel said:**
> I'm not aware of any programs that need firestarter (i.e., it has no dependants).
I didn't made myself clear enough, I think.

I was not asking about dependencies, but about programs that open ports/run servers automatically and thus I may need Firestarter.

---

### Post by eentonig on 2007-08-10
as long as you don't install server applications like apache (webserver), openssh (ssh server), etc... you'll be fine.

In short, without too much technical mambo-jambo. As soon as you or someone else can use an application to connect from the internet to your pc, you might start thinking about firestarter.
You connecting to someone else (webbrowsing, telent, ssg, ftp, torrent, ....) isn't a problem.

---

### Post by matigol on 2007-08-10
Vista or Xp needs Firestarter.

Ok..... I go out...

:lolflag:

---

### Post by Darkriser on 2007-08-10
I'm asking for clarification.
Is Firestarter only a GUI for iptables or does it have any other advantages?

Any ideas?
Thanks a lot.
Marcel

---

### Post by nvteighen on 2007-08-10
> **eentonig said:**
> as long as you don't install server applications like apache (webserver), openssh (ssh server), etc... you'll be fine.

In short, without too much technical mambo-jambo. As soon as you or someone else can use an application to connect from the internet to your pc, you might start thinking about firestarter.
You connecting to someone else (webbrowsing, telent, ssg, ftp, torrent, ....) isn't a problem.

So, in summary, I should be careful with any package including a server.

Thank you very much!

---

### Post by nvteighen on 2007-08-10
> **Darkriser said:**
> I'm asking for clarification.
Is Firestarter only a GUI for iptables or does it have any other advantages?

Any ideas?
Thanks a lot.
Marcel

Yes, Firestarter is just **another** GUI for iptables. (there's also Guarddog, for KDE)

---

### Post by eentonig on 2007-08-10
It has one other feature, and that is that it gives you a nice GUI to see the current active connections. And allows you to see the log of blocked packets.

But, basically. Yes, it's just a GUI to work with ip-tables.

---

