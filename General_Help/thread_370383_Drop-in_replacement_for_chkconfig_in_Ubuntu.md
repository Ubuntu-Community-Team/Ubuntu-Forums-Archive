---
title: "Drop-in replacement for chkconfig in Ubuntu?"
date: 2007-02-25
forum: General Help
---

### Post by motin on 2007-02-25
Often after using alien to convert rpms I run into the problem of /sbin/chkconfig not being available. 

I have in these forums found a lot of similar cli apps:

**update-rc.d**
Debians cli for this sake.

**sysv-rc-conf**
Supposed to be very like chkconfig. 

**rc-config**
A bash script found at [http://ubuntuforums.org/showthread.php?t=20583](http://ubuntuforums.org/showthread.php?t=20583)

**chkconfig for Debian systems**
```
$ apt-get install libnewt0.51
$ ln -s /usr/lib/libnewt.so.0.51 /usr/lib/libnewt.so.0.50
$ wget http://www.tuxx-home.at/projects/chkconfig-for-debian/chkconfig_1.2.24d-1_i386.deb
$ dpkg --force-all -i chkconfig_1.2.24d-1_i386.deb

```

Problems encountered:
**update-rc.d** - Doesn't use the same syntax at all. Found this: 
```
/sbin/chkconfig --add <prog>       
=>
# Runlevels are extracted from /etc/init.d/<prog>
update-rc.d <prog> start <SNN> <runlevels> . 
				   stop <KNN> <runlevels> .

```
...but I have no idea of what SNN nor KNN is so this doesn't help me much... :(

**sysv-rc-conf**
Not sure if this has the same syntax as chkconfig? Is this safe to use as a drop-in replacement? At least for simple tasks like add/del?

**rc-config**
Not sure if this has the same syntax as chkconfig? Is this safe to use as a drop-in replacement? At least for simple tasks like add/del?

**chkconfig for Debian systems**
Complains about package libnewt0 not being available. (libnewt0.51 found in Ubuntu is installed) - and refuses to install itself. 

So if anyone could supply some information on how to make the rpms scripts using chkconfig to work I'd be very grateful!

---

### Post by Tominator on 2007-03-07
I wish I had an answer for you. In fact, I have the same question. Any help anyone? Thanks, Tom.

---

### Post by slAoD on 2007-03-13
> **motin said:**
> 
...but I have no idea of what SNN nor KNN is so this doesn't help me much... :(


man update-rc.d is much more specific oriented and easy enough. So SNN and KNN is for starting or stoping a daemon (respectively). The NN stands for the order a specific daemon will start... so a number close to 0 will start the service early and a number close to 99 will start the service late...

an example of update-rc.d : update-rc.d service start 89 2 3 4 5 . stop 88 0 1 6
where 2 3 4 5 and 0 1 6 are the start and stop run levels of the specific service.

More about runlevels can be found here:[http://wiki.linuxquestions.org/wiki/Runlevel](http://wiki.linuxquestions.org/wiki/Runlevel)

Hope i helped you...

---

### Post by motin on 2007-03-25
Thanks, but it only helps me to maybe make one application working, it is not a solution to all those instances when chkconfig is required, and certainly not a solution for any newcomer to Ubuntu. 

I hope the answer lies out there still - anyone?

---

### Post by tomchuk on 2007-03-25
As I learned recently, update-rc.d was never intended as a tool for users to run. From update-rc.d(8 ):
> 
       Please note that this program was designed for  use  in  package  main&#8208;
       tainer  scripts and, accordingly, has only the very limited functional&#8208;
       ity required by such scripts.  System administrators are not encouraged
       to  use  update-rc.d  to  manage runlevels.  They should edit the links
       directly or use runlevel editors such as sysv-rc-conf and bum  instead.


update-rc.d is probably the closest thing to chkconfig though - a single scriptable command to manipulate runlevel symlinks. Though its syntax is troublesome at best: slAoD's example was almost correct, save for the missing period at the end. If you really want to use update-rc.d, I'd stay away from the detailed syntax in slAoD's example and just use "update-rc.d -f service remove" and "update-rc.d service defaults".

A far better solution is sysv-rc-conf: "sysv-rc-conf service on" and "sysv-rc-conf service off" will do what the previous update-rc.d commands did. Also, there is an interactive curses mode which is even nicer.


EDIT: Whoops, didn't read that this was for package scripts. Try making a symlink from /usr/sbin/sysv-rc-conf to /usr/sbin/chkconfig and see if that works. The syntax for each looks identical.

---

