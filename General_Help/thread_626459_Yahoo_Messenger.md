---
title: "Yahoo Messenger"
date: 2007-11-29
forum: General Help
---

### Post by ivan Finden on 2007-11-29
[B][I][COLOR="Green"]
I have been Ubuntu  but I cannot get Yahoo Messenger to install does anyone know how[COLOR="Red"] to get yahoo messenger installed[/COLOR][/I][/B][/COLOR]:confused:

---

### Post by scxtt on 2007-11-29
are you talking about this one specifically, or do you just want to be able to use the yahoo protocol?

[http://messenger.yahoo.com/unix.php](http://messenger.yahoo.com/unix.php)

---

### Post by paisleysdaddy on 2007-11-29
I'm having the same problem. I downloaded ymessenger_1.0.4_1_i386.deb from [http://messenger.yahoo.com/unix.php](http://messenger.yahoo.com/unix.php) and followed the instructions below. 

Debian Linux

   1. Save the file to your machine.
   2. Log in as root and type: dpkg -i ymessenger_1.0.4_1_i386.deb to install the application.
   3. Run /usr/bin/ymessenger from X Window to launch the application

After I run that, I got a few errors. I ran it using the package installer and it says "Error: Dependency is not satisfiable: libssl0.9.6. I ran apt-get and installed libssl0.9.8-dbg and still get the same message.

The errors I get from a terminal window are as follows....

bud@PC020189:~/Desktop$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
Selecting previously deselected package ymessenger.
(Reading database ... 115287 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

---

### Post by paisleysdaddy on 2007-11-29
I got it. Just had to install the exact versions of the dependencies. YM didn't like newer versions of libssl. It will accept the latest of xlibs.

---

