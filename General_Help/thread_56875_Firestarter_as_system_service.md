---
title: "Firestarter as system service"
date: 2005-08-14
forum: General Help
---

### Post by unclben on 2005-08-14
I recently installed Firestarter, and I want to make sure it runs as a protected system service at all times (i.e. run when any user, or no user, is logged in, and only sudoers can mess with it). The online documentation says then when Firestarter is installed via apt-get (I used Synaptic, same diff right?) that it is automagically configured to run as a system service. Given all that, I have two questions...

1) Does 'system service' mean the same functionality as I requested in my first sentence? I'm new to sysadmin-type functions in Linux, so my knowledge of terminology is terrible.

2) How can I check to make sure Firestarter is always running? I tried variations on 'ps' (including -a, -c, -aux, -e) and none of them showed me what I needed.

TIA.

---

### Post by varunus on 2005-08-14
Actually, firestarter is just a frontend to linux's built in firewall called "iptables".  Firestarter/iptables does indeed start up on every startup; in fact, if the firestarter GUI isn't on, the firewall is still on.  The only way to disable the firewall is to open the firestarter GUI and choose "stop firewall".  This is for safety reasons; you can't be hacked if you forget to load firestarter.

---

### Post by jasmuz on 2005-08-14
Hey there
Synaptic is a front end to apt-get.
Yes, the term system service means that only root or sudoers may modify or stop the service. And will run without the need to login any user.
If you want to check if the process is running just type ps aux | grep firestarter

Hope this helps

---

### Post by unclben on 2005-08-14
Wow, that was quick. Thanks!

jasmuz: I tried your 'ps' | 'grep' command. With the GUI running, it returned several processes. After closing the GUI, it only returned my grep command. See how I'm still paranoid that it's somehow not running?

edit: typo

---

### Post by dsethuraman on 2005-08-14
the easiest way to do it is to go into system, preferences and then session. in that,adding firestarter under the startup tab and firestarter will start every time you logon automatically. you will have to change the permission to let the user start it without sudoing.
see the discussion in the link below: it works fine for me.
[http://ubuntuforums.org/archive/index.php/t-13659.html](http://ubuntuforums.org/archive/index.php/t-13659.html)

---

### Post by lakcaj on 2005-08-14
As already stated, firestarter is just a front-end to iptables.  If you want to see what iptables rules are active, use the following:

```

iptables -L

```

You can do this at any time, and depending on what changes firestarter is making, that command will reflect those changes.

---

### Post by unclben on 2005-08-14
> 1) Add firestarter to /etc/sudoers:
add: "username ALL=NOPASSWD:/usr/sbin/firestarter"
right after "username ALL=(ALL) ALL"
where "username" is YOUR user name

2) Add it to the start up programs in your session conf:
Go to System->Prefs->Sessions and click the tab "Start up programs" (the last)
and add: "gksudo /usr/sbin/firestarter" as command.
This is from the thread that dsethuraman linked to. Let me see if I understand this correctly...(1) Says that user 'username' does not need a passwd to run anything in path '/usr/sbin/firestarter'. (2) Takes advantage of (1) to let 'username' run firestarter without a passwd, thereby allowing it to be automated at startup.

Is that right? So 'username' must be a sudoer, but doesn't actually need to enter a passwd? That seems kinda counter to the purpose of sudo, since then an attacker who had access under 'username' could then control firestarter. Right? (Can you see that I'm unsure of myself?  :neutral: )

Thanks for all the help so far.

---

