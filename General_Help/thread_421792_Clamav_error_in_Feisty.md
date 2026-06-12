---
title: "Clamav error in Feisty"
date: 2007-04-24
forum: General Help
---

### Post by argusBR on 2007-04-24
I had Clamav working on Edgy. However, I noticed that my pop3 proxy (p3scan) began to deliver infected messages. I then tried to run:

```
argusbr@hobbit:~/Desktop$ sudo clamdscan eicar.com 

```

and I got (eicar.com is file infected with EICAR standard anti-virus test pattern):

```
/home/argusbr/Desktop/eicar.com: lstat() failed. ERROR

----------- SCAN SUMMARY -----------
Infected files: 0
Time: 0.001 sec (0 m 0 s)

```

I also tried to restart clamav-daemon, and this is the output I got (translated from portuguese):

```

argusbr@hobbit:~/Desktop$ sudo /etc/init.d/clamav-daemon restart
dirname: operator missing
Try `dirname --help' for more information.
dirname: operator missing
Try `dirname --help' for more information.
 * Stopping ClamAV daemon clamd                                          [ OK ] 
dirname: operator missing
Try `dirname --help' for more information.
chown: operator missing after `clamav'
Try `chown --help' for more information.
 * Starting ClamAV daemon clamd                                                 Running as user clamav (UID 114, GID 114)
                                                                         [ OK ]

```

I reinstalled Clamav through Synaptic, but the problem persists. Any ideas?

---

