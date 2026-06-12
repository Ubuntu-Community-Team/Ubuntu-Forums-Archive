---
title: "Default bash environment?"
date: 2007-10-22
forum: General Help
---

### Post by TruckStuff on 2007-10-22
I've just installed Ubuntu Server on a new box and am baffled by the bash startup/login process on Ubuntu.  It is completely different from any other distro I have ever used.  My primary question basically boils down to this:

Where in the hell are the default environment variables set???

This is a server, so 98% of the work is done through SSH.  When I login to the box, I get a default environment that has variables predefined, such as HISTCONTROL, HOME, PATH, etc.  In every other distro I have used, bash sources ~/.[bash_]profile, which sources /etc/profile, which then sets up  the environment.  From the best I can tell, Ubuntu sources ~/.profile, which sources /etc/profile, which sources /etc/bash.bashrc, which defines some variables, but never exports them to the env as best I can tell.  I'm quite certain that this is all done magically some where in the login process, but for the life of me, I cannot find any documentation about *how* this is accomplished.  /etc/environment has not impact on these variables, not does /etc/login.defaults or /etc/security/pam_env.conf.  I am quite baffled ATM.

Guidance please?

---

### Post by mahousaru on 2007-10-22
A users shell is set in 

/etc/passwd

It is on the very end

*Edit*

Opps sorry, and I should read your post properly as that wasn't what you asked for :p

---

### Post by TruckStuff on 2007-10-23
> **TruckStuff said:**
> Where in the hell are the default environment variables set???  So I've stumped the entire board?  Does no Ubuntu user actually use the terminal?  Or have we all turned into Mac types where "terminal" is a bad word?

---

### Post by cressie176 on 2008-03-11
You're not alone!

I get exactly the same problem, but only with the server edition (Ubuntu 7.10). I've added JAVA_HOME to /etc/environment, /etc/profile and /etc/bash.bashrc

Following reboot if I log on locally JAVA_HOME is set in the terminal and available to any bash scripts that I run. If I log on via ssh it's still set in the terminal (e.g. echo ${JAVA_HOME} has output), but not available to any bash scripts.

It's preventing me from starting my app server remotely.

---

### Post by cressie176 on 2008-03-11
The following seems to work...

Instead of using /etc/environment add the variables to /etc/profile and use export, e.g.

export JAVA_HOME=/usr/lib/jvm/java-6-sun

---

