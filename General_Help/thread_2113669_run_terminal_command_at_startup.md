---
title: "run terminal command at startup"
date: 2013-02-08
forum: General Help
---

### Post by comoon on 2013-02-08
I am a very beginner to ubuntu. I have just installed ubuntu 12.0.4LTS in virtual box and try to run a start up script. But I have try many methods and all have failed.Bellow is my environment, please give any advise.
1st: add JAVA_HOME and GRAILS PATH in user main folder's profile file
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
export JAVA_HOME=/usr/java/jre1.7.0_13
PATH=$PATH:$HOME/work/grails-2.0.3/bin

2nd: because I want to run grails command at startup, so create shell file startD.sh
#! /bin/sh
cd work/comoon/code/grails-project
grails run-app

then what should I do to run this script in terminal at startup

---

### Post by comoon on 2013-02-08
Anyone Can help me please or I have posted it in the wrong category?

---

### Post by omeomi on 2013-02-08
> **comoon said:**
> Anyone Can help me please or I have posted it in the wrong category?

Please wait a bit longer (24h) before bumping your thread. 


You can add scripts to run at startup in System settings -> Startup Applications

---

### Post by zombifier25 on 2013-02-08
Or, the classic way, add it to .profile .

---

### Post by Lars Noodén on 2013-02-08
> **zombifier25 said:**
> Or, the classic way, add it to .profile .

That will run it when you open a terminal.  

If you want it to run (as root) when the machine starts up, you can add it to /etc/rc.local

When do you want it to run?

---

### Post by zombifier25 on 2013-02-08
> **Lars Noodén said:**
> That will run it when you open a terminal.

That would be .bashrc.
.profile will run when you log in regardless of sessions.

---

