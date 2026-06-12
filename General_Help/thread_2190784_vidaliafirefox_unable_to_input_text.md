---
title: "vidalia/firefox: unable to input text"
date: 2013-11-29
forum: General Help
---

### Post by faust99 on 2013-11-29
I wonder if anyone would be able to assist me in solving the problem of not being able to input anything into firefox when I use it with vidalia/tor. I've tried all the bundles that are available on the TOR website but they are all the same in this regard. However, inputing with the mouse is possible (e.g. copying text from another program and pasting it in). Please advise.

---

### Post by faust99 on 2013-11-29
There seems to be issues with Vidalia/FFox and iBus. A solution can be found at the bottom of [this]("https://trac.torproject.org/projects/tor/ticket/9353#comment:38") page and also [here]("http://askubuntu.com/questions/375826/keyboard-doesnt-work-with-tor-browser/377321#377321").

---

### Post by Damico on 2014-01-23
I couldn't find a bug report using Launchpad on this installation issue, so I filed one for the team:
Title: [Tor Browser Bundle on Ubuntu 13.10 is useless until/unless one manually kills the ibus process]("https://bugs.launchpad.net/ubuntu/+bug/1272032")

---

### Post by Damico on 2014-01-25
i was told we're supposed to choose the PACKAGE to file this bug against.
So, they said to figure out what package is causing the problem.
Does anyone know?

> 
                        Thank you for  taking the time to report this bug and helping to make Ubuntu better.   It seems that your bug report is not filed about a specific source  package though, rather it is just filed against Ubuntu in general.  It  is important that bug reports be filed about source packages so that  people interested in the package can find the bugs about it.  You can  find some hints about determining what package your bug might be about  at [https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage).  You might also ask for help in the #ubuntu-bugs irc channel on Freenode.
 To change the source package that this bug is filed about visit [https://bugs.launchpad.net/ubuntu/+bug/1272032/+editstatus](https://bugs.launchpad.net/ubuntu/+bug/1272032/+editstatus) and add the package name in the text box next to the word Package.
 
              

---

### Post by Damico on 2014-01-25
It appears to be "something" in Debian, but nobody knows for sure, apparently, from my read of the bug report.

 Here's the latest append, to that bug, for example:
-----< quote >-----
 Is anyone on Ubuntu 13.10 brave enough to try installing the Debian  ibus and dbus packages (one at a time, so we know which is the culprit)  to see if they fix this issue? You can download them from &#8203;[http://ftp.ca.debian.org/debian/pool/main/d/dbus/dbus_1.7.10-2_amd64.deb](http://ftp.ca.debian.org/debian/pool/main/d/dbus/dbus_1.7.10-2_amd64.deb) and &#8203;[http://ftp.ca.debian.org/debian/pool/main/i/ibus/ibus_1.5.4-1_amd64.deb](http://ftp.ca.debian.org/debian/pool/main/i/ibus/ibus_1.5.4-1_amd64.deb), but you may need to also pull in several dependencies and ibus input method subpackages too.

 The reverse (trying the Ubuntu 13.10 ibus and dbus packages on  Debian/testing) would also be helpful. An https version of the ubuntu  pool can be found at &#8203;[https://mirrors.kernel.org/ubuntu/pool/main/](https://mirrors.kernel.org/ubuntu/pool/main/).
-----< / quote >-----

---

