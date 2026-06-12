---
title: "Ubuntu Security Issue"
date: 2007-04-21
forum: General Help
---

### Post by wunian on 2007-04-21
I am new to Ubuntu (Linux) and experienced Windows user. I need some input for the below:

Do I need to install any firewall and antivirus on Ubuntu 7.04 to secure my system from intrusion and virus attack?

Thanks.
wunian

---

### Post by Nineball on 2007-04-21
At most a firewall, but the one you already have probably isn't compatible. Pretty much all viruses I've seen are coded specificially to attack Windows, not Linux, so I guess you could say viruses are incompatible with Linux.

One of the firewalls I've heard good things about is Firestarter. ([http://www.fs-security.com/](http://www.fs-security.com/)) See if that works for you, I'm sure there are others if you don't like it, though.

---

### Post by dreadlord_chris on 2007-04-21
> **wunian said:**
> I am new to Ubuntu (Linux) and experienced Windows user. I need some input for the below:

Do I need to install any firewall and antivirus on Ubuntu 7.04 to secure my system from intrusion and virus attack?

Thanks.
wunian

Unless you are in a mixed-networking environment with Windows boxes there is **very** little need to worry about virus' on Linux systems - **at the moment**

Googling *linux virus* - will give you some idea as to the current state of affairs concerning the topic.

For a Linux Anti-virus app - [ClamAV]("http://www.clamav.net/")

As for a _firewall_ - Ubuntu already comes with one built-in, it's called [iptables]("http://www.netfilter.org/projects/iptables/index.html"). By default Ubuntu installs with **no** open ports - this can be confirmed here: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Configuring IPtables can be rather daunting to for the beginner - luckilly there are several GUI front-ends to make the job easier - Firestarter (linked by Nineball) is probably the easiest for new users.

---

### Post by wunian on 2007-04-21
Thanks nineball and dreadlord_chris.

I 'Google' around and already installed Automatix2 where both ClamAV antivirus and Firestarter Firewall could be installed through Gnome Security Suite.

---

