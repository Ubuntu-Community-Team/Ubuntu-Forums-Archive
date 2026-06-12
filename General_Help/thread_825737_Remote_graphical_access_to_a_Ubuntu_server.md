---
title: "Remote graphical access to a Ubuntu server"
date: 2008-06-11
forum: General Help
---

### Post by maverickmint on 2008-06-11
Hi,

I am an Ubuntu user for the last 1 year and very happy with it. I would like to migrate my entire IT infrastructure to Linux. My current setup is a Windows 2003 server which acts as a terminal server and around 8 clients connecting to it using RDP client and share printers between them. The software I use for my business is Tally Financials (multi user version) and it is working fine with Wine. I have tried FreeNX but it is restricted to 2 clients only. Is there any other way to replicate the same infrastructure using Ubuntu.

Thanks for your help in advance.
:confused:

---

### Post by HermanAB on 2008-06-11
SSH with X forwarding can do what you want.

Cheers,

Herman

---

### Post by maverickmint on 2008-06-11
Would you please guide me how to do that? All the clients are using Internet to access the server and printers also need to be shared :-(

---

### Post by prestomation on 2008-06-11
Your clients are using windows?
Download a free windows X server ([[COLOR="Blue"]xming[/COLOR]]("http://sourceforge.net/projects/xming/") is good)
Simply point it to your server.  It will do integration so the app appears to be running locally.  It will be slower then freenx, freenx is the same thing, only compressed.

If they are using *nix simply
> ssh -X [email]user@hostname.com[/email] appname
The -X tunnels X.  You can leave out the appname and simply use a shell over SSH.  Any programs you then run will pop back to your display.

I hope that gets you started.

[I just found this post which goes in a little more depth if you need it]("http://ubuntuforums.org/showpost.php?p=4167263&postcount=14")

---

### Post by HermanAB on 2008-06-11
For Windows, I second Xming with PuTTY.  The Xming web site had a link to PuTTY the last time I was there, but Google will find "Greenend PuTTY" for you.

---

### Post by maverickmint on 2008-06-11
Thanks for the responses.

I would like to move my entire IT infrastructure to move to Linux, even clients.

---

