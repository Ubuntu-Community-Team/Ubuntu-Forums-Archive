---
title: "lockout"
date: 2006-08-09
forum: General Help
---

### Post by so11i on 2006-08-09
Has anyone here used the "lockout" package?

If not, you can check it out at [http://thomer.com/lockout/](http://thomer.com/lockout/)

The author gives the following example for locking ip access using the lockout program:

    #!/bin/sh
    /etc/init.d/iptables load work
    cp /etc/lockout/sudoers.lock /etc/sudoers
    /etc/init.d/sudo stop
    /etc/init.d/sudo start

But in ubuntu neither iptables or sudo are located in init.d.

I actually don't want to reroute the iptables... I just want to block sudo access for my account for a certain period of time. So i'm mainly wondering whether it's equally good to use /usr/bin/sudo stop and start.

Also in the sudoers.lock file I've just commented out the %admin file. Would that do the trick?

Thanks for your help.... =-)

---

### Post by katja on 2008-07-05
bump

---

### Post by linfidel on 2008-07-05
I'm curious - why would you want to block yourself from using sudo?  I find it hard to imagine a reason to do this.  You can set the time that it remembers that you entered  the password, and make it forget quickly if you want.  Blocking yourself seems a bit drastic.

---

### Post by katja on 2008-07-05
Yeah - it's a last-ditch effort to keep myself from browsing the web when I need to be working.

From the website: "The real secret is that Lockout will first run a script that you write (to put up a different firewall configuration, to remove yourself from /etc/sudoers, or anything else that you believe will impose labor on yourself). After that, Lockout will change your root password (for a specified amount of time) to something random so that you can't secretly undo all those productive settings and be a lazy slacker again. When time is up, Lockout changes the root password back to its original and runs a script that undoes the other settings (firewall, /etc/sudoers, etc.) so that you can finally continue your peaceful slacking." (also here: [http://www.linux.com/feature/116324](http://www.linux.com/feature/116324))

---

### Post by linfidel on 2008-07-05
> **katja said:**
> Yeah - it's a last-ditch effort to keep myself from browsing the web when I need to be working.

From the website: "The real secret is that Lockout will first run a script that you write (to put up a different firewall configuration, to remove yourself from /etc/sudoers, or anything else that you believe will impose labor on yourself). After that, Lockout will change your root password (for a specified amount of time) to something random so that you can't secretly undo all those productive settings and be a lazy slacker again. When time is up, Lockout changes the root password back to its original and runs a script that undoes the other settings (firewall, /etc/sudoers, etc.) so that you can finally continue your peaceful slacking." (also here: [http://www.linux.com/feature/116324](http://www.linux.com/feature/116324))Sounds like you're wasting time trying to keep yourself from wasting time! :)  I think you need to learn self control so you don't need to do things like this.

How about a cron script to copy a hosts file redirecting your dns servers to devnull?

---

### Post by katja on 2008-07-06
> **linfidel said:**
> I think you need to learn self control so you don't need to do things like this.

How about a cron script to copy a hosts file redirecting your dns servers to devnull?

Self-control is not something I lack globally, I've just learned to pick my battles :).  At some point you start doing what works for you.

That sounds interesting, but I wouldn't know where to start with writing one.

---

### Post by linfidel on 2008-07-06
> **katja said:**
> Self-control is not something I lack globally, I've just learned to pick my battles :).  At some point you start doing what works for you.

That sounds interesting, but I wouldn't know where to start with writing one.I'm not sure it would work, but it wouldn't be hard, I don't think.  Do you know how to edit the hosts file, in /etc?  If so, you would create a shell script, which is simply shell commands (like a batch file in DOS) to copy the existing hosts file, then add a couple of lines to direct your DNS server to localhost or something.  Another script to restore the original.  Then schedule them using cron.

First step would be to try modifying the host file to make that part work.

---

