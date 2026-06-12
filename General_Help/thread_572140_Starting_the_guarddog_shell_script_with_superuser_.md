---
title: "Starting the guarddog shell script with superuser priviliges."
date: 2007-10-10
forum: General Help
---

### Post by larryfroot on 2007-10-10
Hi People...

Am having probs starting guarddog with superuser priviliges. Being a noobie I did some hunting around and changed the permissions on any guarddog **file** in /etc/network, etc/ppp and etc/init.d to myself as user and my group using chown. I thought changing the permissions would enable me as humble user to run it...as a user it opens but in a highly restricted mode. Prob a silly thing to do (chown-ing those files) and I will be returning them to root:root as soon as. 

I am assuming that the shell script in etc/init.d is the file to execute to start guarddog simply because it is in folder init.d

So type this into my terminal:

larry@ubuntu:~$ sudo /etc/init.d/guarddog start
Setting up guarddog firewall...done.

And then start the application and it still starts in restricted mode! I also reloaded it, then restarted it (on the command line) and then tried to run the app as a GUI again. Same result...can only be run in superuser mode and I get restricted mode.

I am using xubuntu fiesty 7.04 with a limited number of Gnome and KDE apps thrown in, btw

Anyone any ideas...help...please and thank you!

---

### Post by ramjet_1953 on 2007-10-10
Before going down that road, why exactly do you need to change iptables?

Unless you require port forwarding, the standard configuration of iptables gives you a secure firewall without any need to fiddle.

I'm not sure if you are aware of this, but packages like GuardDog and Firestarter are only GUI front-ends for iptables.

Unless you have a genuine reason for wanting to alter iptables, stay well away from it and you will not have any problems.

What is the old adage? "If it isn't broken, don't try to fix it".

Regards,
Roger :cool:

---

### Post by larryfroot on 2007-10-12
Roger, as soon as I read your reply I realised what a complete plonker I was...

However I was tempted by synaptics description of guarddog:

"Guarddog is a firewall configuration utility for KDE. It is aimed at two
groups of users: novice to intermediate users who are not experts in TCP/IP
networking and security, and those users who don't want the hassle of
dealing with cryptic shell scripts and ipchains/iptables parameters."

That sounded good to me...

I made my decision to install guarddog as I was used (in windows) to easy access to a GUI user panel where I could see what was set up and what wasn't. With iptables alone all I could -presumably - do was to look at a configuration file and scratch my head! 

Anyways I removed Guarddog...

I still - even after your words of wisdom - would like to use Guarddog...simply for the feedback which would give me peace of mind and the illusion of control..  ;-)

And now I do have a question scratching away in the back of my mind...how do you run a GUI app under sudo...do you need to somehow log in as root...or wave a sprig of honeysuckle over /usr/bin/iptable chanting some wystical manker stuff? 

Curiosity...a little knowledge is a dangerous thing. And there are plenty of us ex windows users out there who are a tad blithe when it comes to utilising a little knowledge.

---

### Post by ramjet_1953 on 2007-10-12
I can understand where you are coming from.

One thing that you need to come to grips with, when using Linux, is that for 99.9% of the time, you are logged in as a user, not an administrator.

That is the beauty of Linux and one of many reasons why it is so secure.

If you want to run a GUI for iptables, with root privileges on your desktop, while you are connected to the Internet, you are opening up yourself  to security issues as you have opened a door to the root file system.

Both GuardDog and Firestarter allow you to customise your firewall. The GUI running in root mode is not required after the changes have been made. In fact, as stated above, to do so is a security risk.

Before you decide to go into this any further, I would recommend that you have a bit of a look around on Google and read up on firewall configuration and the pitfalls for those of us who want to fiddle with firewalls, before we fully understand what we are doing. I classify myself well and truly in that camp and unless I really have a need to change iptables, I will leave well alone.

Regards,
Roger 8)

---

