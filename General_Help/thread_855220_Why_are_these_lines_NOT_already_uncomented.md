---
title: "Why are these lines NOT already uncomented??"
date: 2008-07-10
forum: General Help
---

### Post by Mark.H on 2008-07-10
I ran the cat '/etc/sysctl.conf file' command when i was having a look around my system and I got this output:

What interests me is:

Why are certain lines Not commented or commented, depending on what the case is. By default if it is to enable or disable for example, something as fundamentally important as to disable spoof protection..

at the bottom of this output a sentence says comment the next two lines to disable spoof protection,

Have I read this correctly or am I reading the output wrongly?

I am a keen learner so i appreciate all comments.

Output: 
$ cat  /etc/sysctl.conf file
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.  (Added in kernel 2.6.22.)
kernel.maps_protect = 1

# Increase inotify availability
fs.inotify.max_user_watches = 524288

# protect bottom 64k of memory from mmap to prevent NULL-dereference
# attacks against potential future kernel security vulnerabilities.
# (Added in kernel 2.6.23.)
vm.mmap_min_addr = 65536

##############################################################3
# Functions previously found in netbase
#

# Comment the next two lines to disable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling ([http://lkml.org/lkml/2008/2/5/167](http://lkml.org/lkml/2008/2/5/167))
#net.ipv4.tcp_syncookies=1
End:

 Is the best way to view and edit certain files to prefix, 'sudo cat' before the desired file name.

---

### Post by Gunman1982 on 2008-07-10
Uhm fundamenteley you **don't** want to disable spoof protection so those two lines are not commented (don't start with a # which would flag them as comments).

comment:
#command which is not executed
uncomment:
command which is executed

'sudo' <- lets you read/write system files which you can't access as normal user
'cat' <- reads a file, comparable to 'type' on dos, you can't edit files though
'nano' <- command line editor which I recommend to use on the command line since it lets you edit right away and you can see the control codes at the bottom ('^' stands for the ctrl button so ctrl+x quits the editor)

---

### Post by sdennie on 2008-07-10
You can find some information about the syntax of that file using:

```

man sysctl.conf

```

And a bit of information about what it's for with:

```

man sysctl

```

---

