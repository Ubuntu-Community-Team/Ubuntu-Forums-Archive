---
title: "Bip XChat and PuTTY"
date: 2007-05-07
forum: General Help
---

### Post by Mortuis on 2007-05-07
I am trying to get <a href="http://bip.berlios.de/">bip</a> to work so I can have a constant IRC and IM presance (connecting to my IM programs via <a href="http://www.bitlbee.org/main.php/news.html">Bitlbee</a>).  On my server, I can successfully connect bip to Bitlbee and IRC, and then successfully connect to bip with Irssi.  So I'm certain that end of the setup is working.

The problem I'm having is connecting to bip from a remote computer.  At work I use windows, so I was thinking I would use <a href="http://www.chiark.greenend.org.uk/~sgtatham/putty/">PuTTY</a>, open up a tunnel on the port bip runs on (7778), and then connect <a href="http://www.xchat.org/">XChat</a> to localhost/7778.  But it's not working.  I know I can tunnel through this server because I do so with my web browser, so I'm sure that part is working.

First I open a tunnel to port 7778 with PuTTY, then in XChat I enter:
> /server localhost 7778 mysupersecretpassword

XChat output:
> * Looking up localhost
* Connecting to localuser (127.0.0.1) port 7778...
* Connected. Now logging in...
* SSH-2.0-OpenSSH_4.2p1 Debian-7ubuntu3.1
* Protocol mismatch.
* Disconnected (Remote host closed socket).

/var/log/auth.log output:
> May  7 14:55:26 ubuntuserver sshd[12028]: Bad protocol version identification 'PASS mysupersecretpassword' from my.ip.address



I'm at a loss of where to go from here and would appreciate advice.

---

### Post by pizzutz on 2007-05-07
try running ssh-server on the normal port (22) and putty through that port.  I think you are getting a conflict because you are trying to run ssh and Xchat on the same port.

---

### Post by Mortuis on 2007-05-07
I didn't think to include that, but I'm actually running ssh on a different port.  31768 I think.

---

