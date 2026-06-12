---
title: "Safety"
date: 2005-06-23
forum: General Help
---

### Post by peter07 on 2005-06-23
1) How can I check my system is safe?? - no spyware, adware, open ports, dangerous modules, programes etc. 

2) Can I decrease my system safety adding some modules to kernel?? For example I've tried to install TV Tuner and I've used sudo modprobe or something. Can it be dangerous ???

---

### Post by shakin on 2005-06-23
[QUOTE=peter07]1) How can I check my system is safe?? - no spyware, adware, open ports, dangerous modules, programes etc. 
[/QUOTE]

You're safe on all accounts by default. No software in the repositories has spyware or adware and no Linux web browser is currently known to allow either to install on your computer. System security would prevent them from doing anything too bad anyway. Using Synaptic you can install Firestarter if you feel the need for a firewall.

[QUOTE=peter07]
2) Can I decrease my system safety adding some modules to kernel?? For example I've tried to install TV Tuner and I've used sudo modprobe or something. Can it be dangerous ???[/QUOTE]

sudo can be dangerous in the sense that it will let you do anything, including harm your system. It will not allow viruses or spyware onto your computer.

---

### Post by peter07 on 2005-06-23
> sudo can be dangerous in the sense that it will let you do anything, including harm your system. It will not allow viruses or spyware onto your computer.

Then if I've used sudo and my system is still working I'm safe. I couldn't allow anybody to acces my PC using sudo command?? 

But what about spyware, adware, viruses. There's no such things in Linux?? 

Should I install firestarter ( special firewall ) ??

---

### Post by shakin on 2005-06-23
[QUOTE=peter07]Then if I've used sudo and my system is still working I'm safe. I couldn't allow anybody to acces my PC using sudo command?? 

But what about spyware, adware, viruses. There's no such things in Linux?? 

Should I install firestarter ( special firewall ) ??[/QUOTE]

My reply was messed up, but I fixed it and I answer the virus and spyware question.

Sudo has nothing to do with allowing other people access to your computer. Most people use it every day. If somebody else has your user account password and you've installed SSH then they could use your user account to login to the system and the run sudo to elevate their priviledges. They could also do this without you installing SSH if they were able to sit down at your computer.

Just don't give your user account password to anyone.

---

### Post by tdell on 2005-06-23
You can do a quick online check here:

[http://uk.trendmicro-europe.com/consumer/housecall/housecall_pre.php](http://uk.trendmicro-europe.com/consumer/housecall/housecall_pre.php)

Tom

---

### Post by Martin Witte on 2005-06-23
Here's another test for testing how open your ports are : [https://image.grc.com/x/ne.dll?bh0bkyd2](https://image.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by nocturn on 2005-06-24
[QUOTE=peter07]1) How can I check my system is safe?? - no spyware, adware, open ports, dangerous modules, programes etc. 
[/quote]

First off, there is very little malware for Linux and virtually none that spreads automaticly.  
You can use chkrootkit or rkhunter to check your system for potential breaches.

> 
2) Can I decrease my system safety adding some modules to kernel?? For example I've tried to install TV Tuner and I've used sudo modprobe or something. Can it be dangerous ???

If you stick to the modules that are already on the system, there is no safety issue.

---

### Post by peter07 on 2005-06-24
Ok, thx for help 

Chkrootkit hasn't found anything, I hav'nt got ssh server installed.

Thats mean I am safe - for now :)

---

### Post by peter07 on 2005-06-30
But what about firewall. Should I install firestarter??

I've used [http://uk.trendmicro-europe.com/con...usecall_pre.php](http://uk.trendmicro-europe.com/con...usecall_pre.php) - all ports seem to be closed.

What about Nessus ??

---

