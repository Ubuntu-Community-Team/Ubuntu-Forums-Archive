---
title: "Runlevels?"
date: 2005-10-19
forum: General Help
---

### Post by Randy Sparks on 2005-10-19
I'm a Red Hat and SUSE user, and have recently switched to Ubuntu. :) 

Can anybody explain how runlevels are organised under Ubuntu? Within RH and SUSE, runlevel 1 is single-user, 3 is all services + bash shell, and 5 is GUI. 

I understand that under Ubuntu, runlevels 2-5 are all exactly the same and that the running of Xorg is triggered by the presence of GDM...? But that's where I get a bit confused. Any help appreciated.

ps Are there any other important differences compared to RH/SUSE in the distro? I know about the sudo difference.

---

### Post by skoal on 2005-10-19
Randy,

runlevels 2-5 here are all the same.

Basically, /etc/rc**X**.d/S21**Y**dm symlink is how your X session gets started (where X is any runlevel from 2 to 5 and Y is either g or k, for gdm or kdm, respectively).

You can make a custom runlevel 3 (terminal session, no X) by simply removing that symlink /etc/rc3.d/S21gdm.  You could use BUM (Boot Up Manager) as well.  Search the forums on that tool.

You can customize any of those runlevels 2 to 5 as you see fit.  *I would recommend leaving 2 alone*.  Just customize 3 to 5 and change the 'initdefault' level in /etc/inittab to whatever you want.  I don't even use runlevel 2 (the default).  I made my own custom X session in runlevel 5 and use that instead.

As far as other differences between Ubuntu and Suse or Redhat, we don't use lizards or hats for our logo.  Other than the obvious apt-get vs. yum or whatever, that's really about all I can think of at the moment...

\\//_

---

### Post by Randy Sparks on 2005-10-19
Thanks for your help. If there isn't one already, somebody should prepare a brief primer for those switching from Red Hat/Mandrake/SUSE to Ubuntu. It would be a technical beginner's guide. 

I might just do that as a forum post as I progress into Ubuntu. Here's what I've noted so far:

- installation vastly simplified, with no need for package choices
- no user-accessible root account by default (can be added later if user wishes)
- sudo must be used for admin tasks, with user's password as authority
- runlevels different, as above
- dpkg-reconfigure *packagename* is useful for configuring hardware outside of the tools provided by Gnome
- Synaptic and/or apt-get can be used for package installation instead of yum (although I used to use apt-get under RH and SUSE anyway, as I think many advanced users will)

Anybody got any more? :smile:

---

### Post by bonzodog on 2005-10-19
have you read the ubuntu guide yet?
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by Randy Sparks on 2005-10-20
Yes. That's a handy reference guide but it doesn't provide a neat, quick, "nutshell"-style guide to Ubuntu for those already experienced in Linux. Like I say, something like a "Top 10 things to know if you're switching to Ubuntu" would be handy for somebody like me, and perhaps many others.

---

