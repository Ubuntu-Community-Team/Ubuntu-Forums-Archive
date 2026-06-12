---
title: "startup program will NOT start"
date: 2012-10-17
forum: General Help
---

### Post by rattlehead on 2012-10-17
I have a perl script that I've been using as an autostart program since ubuntu10. I've always been able to add it to the ubuntu startup list pretty easily. In other versions of linux, if the startup doesn't work, I've been able to do it directly with inittab without issue.

In ubuntu12, inittab does not seem to exist. And the gnome-session-properties (the startup list) simply will not run it. There are no errors in any logs that indicate why. I have tried these variations of the command, all of which work by themselves in a terminal:

```
perl /opt/myscript/test.pl

gnome-terminal -e "perl /opt/myscript/test.pl"

gnome-terminal -e "/usr/bin/perl /opt/myscript/test.pl"

gnome-terminal -e "/usr/bin/perl /opt/myscript/test.pl" --working-directory "/opt/myscript"
```

Am I missing something? Truly, the only thing I haven't tried is modifying/running session properties as root, but that shouldn't be necessary (or desired).

I should note that there is a system error warning dialog that appears after startup, but it is completely unrelated and has been present since the clean install. According to the logs, it appears to be related to samba, specifically smbd.

---

### Post by rattlehead on 2012-11-08
Seriously? 3 weeks and no one has any ideas how to get a startup program to... work?

I researched further and delved into upstart, the new program ubuntu is using to handle startup applications and services. This is what I tried:

```

# test 3.0
#

description     "Test Service"
 
start on (local-filesystems
	  and started dbus
	  and static-network-up)
stop on shutdown

expect fork
respawn

exec perl /opt/myscript/test.pl


```

This doesn't work either. Checking the upstart status shows that the script is "started/running", but there's no indication of it in the system monitor or that it is actually processing anything. It seems to be a zombie.

Seriously, no one can help me get a simple script to run at startup? This shouldn't be this difficult... this is usually a 2 minute task, not a 3 week ordeal.

---

### Post by rnerwein on 2012-11-09
> **rattlehead said:**
> Seriously? 3 weeks and no one has any ideas how to get a startup program to... work?

I researched further and delved into upstart, the new program ubuntu is using to handle startup applications and services. This is what I tried:

```

# test 3.0
#

description     "Test Service"
 
start on (local-filesystems
      and started dbus
      and static-network-up)
stop on shutdown

expect fork
respawn

exec perl /opt/myscript/test.pl


```This doesn't work either. Checking the upstart status shows that the script is "started/running", but there's no indication of it in the system monitor or that it is actually processing anything. It seems to be a zombie.

Seriously, no one can help me get a simple script to run at startup? This shouldn't be this difficult... this is usually a 2 minute task, not a 3 week ordeal.

i guess it's a problem with your perl script. did that script needs a terminal ?
i copyed you script in /etc/init to another name, delete your exec perl ....
and insert there my scriptname: exec /home/richi/scripts/log_boot.sh
with the contence: /bin/echo "z.sh--> `date` : `who -r`" >> /home/richi/tmp/echox.txt

and this will work.
bye

---

### Post by rattlehead on 2012-11-09
No, its not the perl script. The same script has been run on the last 4 versions of Ubuntu, and works fine from a terminal. In the previous versions of Ubuntu, I merely had to add it to the startup list and it didn't matter whether I ran it in a terminal or not. Do I need to create a bash script to run the perl script?

---

### Post by rattlehead on 2012-11-28
Alright... after literally weeks and hours upon hours of research, with surprisingly little help from the community here... I have the solution to the problem.

The problem was that somehow the SETUID bit was set for the PERL command interpreter, and in that context, it refused to execute properly.

That being said, I still cannot get the upstart system to execute it properly, but the gnome-system-properties now works fine.

---

### Post by efflandt on 2012-11-28
Who is the Perl script supposed to run as.  If it is to run as root and does not have any output or a terminal you could try launching it from /etc/rc.local.  Although, if you do not have it configured to daemonize itself, it would be best to redirect stdout somewhere and redirect stderr to stdout, so that would also go to wherever you send stdout (like a log file to tell if it is working or errors).

---

### Post by BlinkinCat on 2012-11-28
> **rattlehead said:**
> Alright... after literally weeks and hours upon hours of research, with surprisingly little help from the community here... I have the solution to the problem.

Hi rattlehead,

Just a little reminder that may have attracted more attention to your problem.
You are perfectly entitled to Bump your thread each 24 hours. This would have brought your problem under notice to more people with a hopeful favourable response.

Cheers - :P

---

