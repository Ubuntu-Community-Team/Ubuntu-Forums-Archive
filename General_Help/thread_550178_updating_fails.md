---
title: "updating fails"
date: 2007-09-13
forum: General Help
---

### Post by torches on 2007-09-13
when I run sudo update-manager I get the following : 

~$ sudo update-manager 
warning: could not initiate dbus
current dist not found in meta-release file
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py:561: Warning: gsignal.c:1741: instance `0x8673648' has no handler with id `282'
  button.disconnect(id);
/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py:561: Warning: gsignal.c:1741: instance `0x86735d8' has no handler with id `280'
  button.disconnect(id);
~$ I found some old threads which had similar errors but could not resolve the isse through their leads. I have attached the output of the command 
$ sudo strace -v -s 999 -f -e trace=execve update-manager 2> /tmp/u-m.log

---

### Post by rsambuca on 2007-09-13
You can run it without sudo.

---

### Post by torches on 2007-09-13
it has nothing to do with running it in sudo mode.

---

### Post by mjehan on 2007-09-20
same problem here

---

### Post by g2g591 on 2007-09-20
try "sudo apt-get install -f"

---

### Post by mjehan on 2007-09-20
already done.... doesn't help!

---

