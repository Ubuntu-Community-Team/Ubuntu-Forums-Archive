---
title: "Trouble Starting SSHD"
date: 2005-07-23
forum: General Help
---

### Post by tom purl on 2005-07-23
Hi, I'm fairly new to Ubuntu, so any help I can get would be greatly appreciated. 

I would like to run an ssh server on my Ubuntu desktop, so I did the following:
```
tom@ubuntu:~$ sudo apt-get install openssh-server
...
tom@ubuntu:~$ sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...                                   [fail]
```

The problem is that I don't even know where to start to troubleshoot this problem.  I tried looking at some of the log files in /var/log, but didn't find anything related to sshd.  I also checked dmesg, but nothing was written to that.  Finally, I check /usr/share/doc/openssh-server to see if I could find any docs that would help me, but I couldn't find any helpful information.  

Is there a way I can get more verbose output or a log file that will give me more information?

Thanks in advance!

Tom Purl

---

### Post by PeP on 2005-07-23
[QUOTE=tom purl]Hi, I'm fairly new to Ubuntu, so any help I can get would be greatly appreciated. 

I would like to run an ssh server on my Ubuntu desktop, so I did the following:
```
tom@ubuntu:~$ sudo apt-get install openssh-server
...
tom@ubuntu:~$ sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...                                   [fail]
```

The problem is that I don't even know where to start to troubleshoot this problem.  I tried looking at some of the log files in /var/log, but didn't find anything related to sshd.  I also checked dmesg, but nothing was written to that.  Finally, I check /usr/share/doc/openssh-server to see if I could find any docs that would help me, but I couldn't find any helpful information.  

Is there a way I can get more verbose output or a log file that will give me more information?

Thanks in advance!

Tom Purl[/QUOTE]
 did you
rm /etc/ssh/sshd_not_to_be_run

---

### Post by diffuser78 on 2005-07-24
[QUOTE=PeP]did you
rm /etc/ssh/sshd_not_to_be_run[/QUOTE]

Try this.


sudo apt-get install ssh

then run sshd from the terminal and make sure that sshd is running.

Thenu can remotely connect to ur Ubunbu from anywhere. I do it all the time and it works like a charm.

Take care

---

### Post by tom purl on 2005-07-24
Thanks for your help diffuser78 and PeP!

The problem ended up being that sshd was already running.  I feel pretty dumb for not checking that first, but it does seem odd that /etc/init.d/ssh wouldn't tell me that.  The same version of that script on Gentoo certainly does.  

Does anyone know of a way of getting more verbose output when running init scripts?

Thanks!

---

