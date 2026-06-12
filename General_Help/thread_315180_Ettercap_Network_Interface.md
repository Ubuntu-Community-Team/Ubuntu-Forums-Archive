---
title: "Ettercap Network Interface"
date: 2006-12-08
forum: General Help
---

### Post by deja2004 on 2006-12-08
Hello-

I've just set up Ettercap and, upon initial run, I can't seem to find my network cards. When I select "Unified sniffing" I have no option in the proceeding drop-down box. Is there a conf file somewhere or am I missing something?

---

### Post by aresgunther on 2007-01-03
Sorry, this answer is a bit late.  When you run ettercap from the terminal, specify the interface with the -i option.  You should type something like this:

```
[sudo] ettercap -i <network interface> -G
```

I hope that you have found this by now.


ares

---

### Post by fakie_flip on 2007-05-17
It is not working here. eth1 is my correct interface to the internet. I am sure.

```
root@ubuntu:~# ettercap -i eth1 -G

ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA


GTK support not compiled in ettercap

root@ubuntu:~# ettercap -i eth1

ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA


Please select an User Interface

root@ubuntu:~#
```

---

### Post by fakie_flip on 2007-05-22
I removed the package. I downloaded the source code, and compiled it with GTK support. Now it works fine.

---

### Post by 12345 on 2007-05-22
> **deja2004 said:**
> Hello-

I've just set up Ettercap and, upon initial run, I can't seem to find my network cards. When I select "Unified sniffing" I have no option in the proceeding drop-down box. Is there a conf file somewhere or am I missing something?

You MUST run as root!
(Fast all network appz need to be run as root in order to access network devices)

$ sudo ettercap -G

---

### Post by w2vy on 2007-06-14
Yes it must run as root.

It would be nice if it could ask for root password when you run it from the Application->Internet menu.

It says it "Integrates well" with desktop... this would be a nice improvement.

I'm tempted to chsnge privs of my network interface...

tom

---

