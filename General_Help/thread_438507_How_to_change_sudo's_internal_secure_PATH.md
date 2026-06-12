---
title: "How to change sudo's internal secure PATH"
date: 2007-05-09
forum: General Help
---

### Post by xdcdx on 2007-05-09
Hello, I'm trying to change sudo's internal secure PATH.

I added the '/usr/sbin/bar' directory to the PATH variable in /etc/environment and rebooted.

This new path has the script, foo.sh. I can run it by typing 'foo.sh' when I'm a regular user. The command 'sudo /usr/sbin/bar/foo.sh' works fine. However 'sudo foo.sh' says: 'foo.sh: command not found', and it won't work either in the 'sudo -i' bash.

If I modify the path on /etc/bash.bashrc, it works on the 'sudo -i' bash, but 'sudo foo.sh' continues not to work.

This is because in Ubuntu's sudo was compiled with the SECURE_PATH option, and so it disregard the user's PATH; it has an internal secure path instead.

I checked this running 'sudo env', and the secure PATH is this one:         PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin"

I tried the following things and none worked:

-  Adding the following option to the Defaults line in /etc/sudoers 
          secure_path="/usr/sbin/bar:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin"
the option secure_path went unrecognized

- Adding the following options to Defaults in /etc/sudoers 
           reset_env,keep_env=PATH 
the options are recognized, but the PATH remains the same

- These workarounds don't seem to work either:
a) sudo -i foo.sh
b) sudo env PATH=$PATH foo.sh


There is more info in these bugs:
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/50797](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/50797)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=85123](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=85123)


What can I do, apart from recompiling sudo?

---

### Post by Levander on 2007-06-09
Dunno if you're still watching this thread, but you can do like I just did.  Place a link inside the secure path to the program you want to run.  I'm putting the links in /usr/local/bin/.

---

### Post by xdcdx on 2007-06-10
Yeah, I thought about that, it's a good workaround. Still, I'd prefer chaging sudo's path.

Cheers.

---

### Post by Levander on 2007-06-10
Me too, what I put above I consider a work around.  The guys who posted in the bugs you linked to know how stupid it is to not be able to override the PATH.  Just whomever, if anyone, is responsible for changing it, hasn't yet.

---

