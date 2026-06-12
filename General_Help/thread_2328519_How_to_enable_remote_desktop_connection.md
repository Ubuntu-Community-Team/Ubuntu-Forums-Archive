---
title: "How to enable remote desktop connection?"
date: 2016-06-21
forum: General Help
---

### Post by tlnt-game-high on 2016-06-21
Hi I am relatively new to Ubuntu.

I have installed GNOME, Lubuntu, and normal Ubuntu desktops. I am look to enable remote desktop connection on my Ubuntu Server v14.04 and be able to remote in from my Windows 10 Home laptop. I would prefer not to use vnc, if there is any other way. Going through either the desktop or command line is fine I am familiar with both. 

Thank you so much for your help.

---

### Post by TheFu on 2016-06-22
Welcome to the forums.

* Use openssh-server.
* Setup ssh-keys.
* On Windows, use the newest, patched, putty or run a tiny VM with a Linux desktop inside and use straight X/Windows - that would be 
$ **ssh -X userid@server-ip program to be run** - this will run just the single program with a single window, but you can launch anything, including a terminal and run any other GUI programs inside it. Works great on a LAN, but over a WAN, you need a more efficient protocol like NX.  For that, use x2go. 

x2go is a client and server setup that leverages ssh for network tunneling. It is 2-3x faster than VNC or RDP and 1000x more secure than either. Install the "server" following the PPA instructions at the x2go website.  Install the client on the client machines following the client installation instructions there too.  On Windows, you'll want to install the full font-package too. It will make life easier.  I've used x2go from 4 continents - just tuned the connection to make the compression higher for lower bandwidth situations.  Over the WAN, I usually just set it to ISDN speeds and all connections everywhere work great (except video playback).  Inside the LAN, video works ok, not great. For normal work, coding, email, web browsing - the performance is great anywhere.

If you want to really learn Linux, you'll want to learn in a directed manner, not 1 issue at a time which can be confusing. There's a great, free, PDF ebook, that you can downlaod and work your way through ... it can be purchased at any bookstore too - this isn't a college student assignment - a good author made the book.  [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) has a link.

---

