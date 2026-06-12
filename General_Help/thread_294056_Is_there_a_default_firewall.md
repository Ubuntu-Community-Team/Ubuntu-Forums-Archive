---
title: "Is there a default firewall"
date: 2006-11-06
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-11-06
I have had Frostwire installed on my other ubuntu machines and no problem. Tonite I installed Frostwire on machine with Ubuntu and when I start up frostwire , it says Frostwire has detected a firewall. This is a fresh install (tonite) of Edgy and I know I did not put a firewall. How can I find it and get rid of firewall? Thanks!! :???:

---

### Post by Sef on 2006-11-06
I don't believe that there is a firewall installed by default.  If there is, it would be firestarter.  In the terminal, (Applications > Accessories > Terminal), type firestarter and see if it pops up.

---

### Post by lrdjester on 2006-11-06
I am wondering the same thing.

I am not able to remotely connect to my Kubuntu or my Ubuntu Server.  I am getting a connection refused trying to ssh to them.

I am behind a firewall here and have little need of it for the Kubuntu.

Also, I am looking to switch all my Suse boxes to Kubuntu or Ubuntu (depending on the function).

I see no tools to maintain a firewall.  I am installing firestarter on the Kubuntu, but if it is a GUI, what is my recourse for Ubuntu server?

---

### Post by lrdjester on 2006-11-06
Firestarter is acting if as there is no firewall installed/configured.  Is this normal?

---

### Post by lrdjester on 2006-11-06
More information.  I created a rule to allow ssh.  It still fails, but there is no report of an event.  However, when I tried to ftp, I did get an event logged.

I removed the allow rule for ssh and now I get an event in firestarter.  Seems as if there is a second firewall installed.

---

### Post by podunk on 2006-11-06
From the way I understand it, there is sort of a default firewall that runs all the time called iptables. Firestarter is merely a front it to configure it.

For some reason in firestarter in order to see the events you have to click the "Events" tab, then click reload.

The iptables home page is here:
[http://www.netfilter.org/](http://www.netfilter.org/)

to be honest, I really didn't understand what they were on about. :-) I just clicked on stuff til it worked. I checked to make sure it was still secure after my "adjustments" by visiting 
[www.grc.com](www.grc.com)
and visiting the Shields up page.

About the ssh thing, I would have to configure my router for that, or at least that the way I understood the docs that came with the router.

---

### Post by hikaricore on 2006-11-06
> **lrdjester said:**
> More information.  I created a rule to allow ssh.  It still fails, but there is no report of an event.  However, when I tried to ftp, I did get an event logged.

I removed the allow rule for ssh and now I get an event in firestarter.  Seems as if there is a second firewall installed.

Just a silly question... are you using a router?  I know in my linksys I had to setup port forwarding for ssh, http, and ftp ports to be able to access my pc from elsewhere.

---

### Post by jdong on 2006-11-06
Maybe a dumb point, but is the SSH server installed? (sudo apt-get install openssh-server). Unlike some other distros, Ubuntu does not ship with a running SSH server by default.

---

### Post by IusedTObeSOMEONEelse on 2006-11-06
~$ firestarter
bash: firestarter: command not found.     This is a new install and I have not installed a firewall. frostwire was not showing firewall a couple of days ago

---

