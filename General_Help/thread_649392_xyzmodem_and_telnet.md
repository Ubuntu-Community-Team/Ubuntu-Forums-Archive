---
title: "x/y/zmodem and telnet"
date: 2007-12-24
forum: General Help
---

### Post by t0p on 2007-12-24
I've recently joined a Synchronet BBS (There's a list of Synchronet BBSes at [http://synchro.net/sbbslist.html]("http://synchro.net/sbbslist.html")).

I access the BBS through telnet, which I run in the gnome terminal.  I can upload and download files to/from the BBS by using FireFTP, the FTP add-on for Firefox.  However, I'd like to try using the xmodem, ymodem or zmodem protocols for file transfer instead.

I looked in Synaptic, and found lrzsz.  Synaptic says of this package:

> Tools for zmodem/xmodem/ymodem file transfer
Lrzsz is a cosmetically modified zmodem/ymodem/xmodem package

But when I've telnetted into the BBS and try to use the zmodem protocol to download a file, it doesn't work.  I assume that the gnome terminal doesn't work with lrzsz.

Does anyone know how I can use x/y/zmodem with telnet in Ubuntu?

---

### Post by dcstar on 2007-12-25
> **t0p said:**
> I've recently joined a Synchronet BBS (There's a list of Synchronet BBSes at [http://synchro.net/sbbslist.html]("http://synchro.net/sbbslist.html")).

I access the BBS through telnet, which I run in the gnome terminal.  I can upload and download files to/from the BBS by using FireFTP, the FTP add-on for Firefox.  However, I'd like to try using the xmodem, ymodem or zmodem protocols for file transfer instead.
..........
Does anyone know how I can use x/y/zmodem with telnet in Ubuntu?

Try the **qterm** package.

---

