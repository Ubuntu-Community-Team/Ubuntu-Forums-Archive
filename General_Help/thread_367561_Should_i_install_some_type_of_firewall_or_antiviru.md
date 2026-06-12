---
title: "Should i install some type of firewall or antivirus?"
date: 2007-02-22
forum: General Help
---

### Post by NOSintake on 2007-02-22
sorry if this is in the wrong section (network mayb?), but i was wondering if i should use any antivirus or firewall for my linux

---

### Post by nandasunu on 2007-02-22
its not really necessary, one of the great things about linux!

---

### Post by louis_nichols on 2007-02-22
The answer is most definitely NO. There are no known harmful viruses for Linux and the default Ubuntu install doesn't have any daemons that listen to incoming connections, so a firewall is unnecessary also.

Just sit back and enjoy! :)

---

### Post by sloggerkhan on 2007-02-22
If it makes you feel good, might as well.
If you think it's funny to spread viruses to windows computers, don't bother.

There is a firewall built in to Ubuntu, but it's not really obvious or configurable if you don't know about it. The easy front end to it is Firestarter, I think.

As far as AV goes, I don't believe there are any live viruses for linux existant. But having ClamAV or somethings similar can help make sure you don't spread stuff to friends on Windows.
Soo... yeah, no reason to have AV.

---

### Post by energiya on 2007-02-22
Antivirus? Not necessary. Firewall? That would be recomanded. If iptables seems hard to configure try (as sloggerkhan said) Firestarter.

---

### Post by Boomy on 2007-02-22
Use a hardware firewall, like a $15 home router. I would never expose myself without one. By default Ubuntu is very secure, but I like being behind a NAT box, just to keep all the garbage off my LAN. If you've never packet sniffed with and without a hardware firewall, you wouldn't believe how many attempts there are to access your ftp, smb, telnet, etc.

---

### Post by Bagboy23 on 2007-02-22
I don't know about the AV, but Firewall is a must. I learn't the hardway two weeks ago. If you're like me and install apps via repository, I installed a wifi detector thing and it came with dependencies that I didn't bother checking out. I just installed it. I noticed then my network became quite slow and only after telling a friend to look through we noticed that a service which used idle cpu power was being used to crunch number for some academic project. Although it appeared safe, it could have just easily been someones tool. Nevertheless, I did a complete format and now I check all my installs. It's long but safe.

---

### Post by equal on 2007-02-22
If you are connected to any Windows machines via homenetworking, it's not a bad idea to have ClamAV installed. It'll do more to protect your Windows PCs than your Linux one, but still a nice thing to do.

I've never run a firewall, but it's also a decent idea I suppose.

---

### Post by Gibbs on 2007-02-22
I detected 7 virus's with Aegis the other day. Although they were native Win32 ones and wouldn't effect Ubuntu (from using Wine/updates) to prevent the spread I think it's a good idea. I've found Aegis and AVG to be good.

Sure Ubuntu/most Linux distros are more secure then Windows by default but I would always have a firewall, even if it's just to monitor my traffic and activity. A firewall is always a good thing to have.

---

### Post by NOSintake on 2007-02-22
ok so basically no anti-virus, but firewall would be a plus, but again, not necessary? im assuming this "firestarter" is free just like everything else for linux

---

### Post by Maestro23 on 2007-02-22
> **NOSintake said:**
> ok so basically no anti-virus, but firewall would be a plus, but again, not necessary? im assuming this "firestarter" is free just like everything else for linux

Yes, it is just a GUI frontend for the iptables.  You can get it via Synaptic or apt-get/aptitude.

Read about it here: [http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by louis_nichols on 2007-02-22
> **NOSintake said:**
> ok so basically no anti-virus, but firewall would be a plus, but again, not necessary? im assuming this "firestarter" is free just like everything else for linux

Yes, firestarter IS free It's in the repos. Very easy to install and pretty easy to configure.

---

