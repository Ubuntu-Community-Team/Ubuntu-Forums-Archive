---
title: "How to setup and use aMule with no GUI"
date: 2008-02-11
forum: General Help
---

### Post by lafaki on 2008-02-11
Hi,

Has any of you managed to setup aMule and use it via aMuleWeb on Ubuntu server with not GUI?

So far I have successfully installed aMule with aMuleWeb. I have made an init-d script to automatically launch amuled (the daemon version of aMule) and amuleweb. I can access aMule via the web but it cannot connect to any servers because there is no way to setup aMule via web (server.met, connection settings, etc). The only instructions for the first-time setup that I have found refer to the aMule GUI. 

If you have managed to configure aMule in any other way without using the GUI, please let me know!

There should also be another way of configuring aMule by reusing config files of an already configured and working aMule installation. But that's a bit more tricky...

Thanks!
Akis

---

### Post by TitanKing on 2008-02-11
> **lafaki said:**
> Hi,

Has any of you managed to setup aMule and use it via aMuleWeb on Ubuntu server with not GUI?

So far I have successfully installed aMule with aMuleWeb. I have made an init-d script to automatically launch amuled (the daemon version of aMule) and amuleweb. I can access aMule via the web but it cannot connect to any servers because there is no way to setup aMule via web (server.met, connection settings, etc). The only instructions for the first-time setup that I have found refer to the aMule GUI. 

If you have managed to configure aMule in any other way without using the GUI, please let me know!

There should also be another way of configuring aMule by reusing config files of an already configured and working aMule installation. But that's a bit more tricky...

Thanks!
Akis

Quite honestly, I found aMule to be buggy and broken. I use eMule in wine, it seems to work perfectly. I have no idea what needs be done for terminal access...

---

### Post by lafaki on 2008-02-11
What is eMule in wine? Do you have any link for it?

I guess that it requires to have GNOM Desktop installed, right?
Does it also provide a Web interface?

---

### Post by TitanKing on 2008-02-11
> **lafaki said:**
> What is eMule in wine? Do you have any link for it?

I guess that it requires to have GNOM Desktop installed, right?
Does it also provide a Web interface?

1. What is eMule in Wine.
Wine makes the Windows version of eMule run on Linux.
Install Wine with apt-get install wine, download Windows emule and install it.
[http://www.winehq.org](http://www.winehq.org)

2. I guess that it requires to have GNOME Desktop installed, right?
Nope KDE or any other is fine.

3. Does it also provide a Web interface?
Yes it does have a web interface.

---

