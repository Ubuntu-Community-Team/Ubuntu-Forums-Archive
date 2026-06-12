---
title: "Can't get an upstart script to execute automatically or manually"
date: 2013-08-20
forum: General Help
---

### Post by wolfgang-rumpf on 2013-08-20
I have a service that I typically execute in the command line by typing the command (sequenceserver).  I'd like to automate this for startup using upstart, so I wrote a simple upstart script (sequenceserver.conf) and put it in my /etc/init directory.  I've tried several variations on this script as well, and none of them seem to work.  I do the sudo initctl reload-configuration after editing, and the initctl list to show services, and this still does not show up, nor does initctl start sequenceserver manually start it, nor does it start on bootup:

description "start and stop sequenceserver"

start on runlevel [2345]
stop on runlevel [!2345]

script
sequenceserver
end script

I've also tried replacing the script with a call to a shell script that does execute if run manually:

script
cd /home/wolfgang/scripts
./sequenceserver.sh
end script

Nothing seems to work.  What am I doing wrong?

---

### Post by SweetAurora on 2013-08-20
Have you tried adding the command(s) to "/etc/rc.local"? It's usally a failproof method of starting or running any command on startup and login.

---

### Post by wolfgang-rumpf on 2013-08-20
If I put them in rc.local, how is that different than putting them in init.d and running rc-update?  I was under the impression that Upstart is the "preferred" way, moving forward, of starting processes - but hey I'm just a noob.  :D

---

