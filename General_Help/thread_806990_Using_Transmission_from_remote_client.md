---
title: "Using Transmission from remote client"
date: 2008-05-25
forum: General Help
---

### Post by zaobz on 2008-05-25
Hi,
I would like to control my PC at home from work, for downloading torrents and stuff while I'm away.

Prob is, say I ssh home, and start downloading using Transmission. When I close the connection, Transmission will just quit along with it (obviously, i guess...)

How do I let Transmission keeps running in the background?

TIA!

---

### Post by HalPomeranz on 2008-05-25
Try the "nohup" command.  Just put the word "nohup" in front of your normal command line.  nohup prevents your command from being terminated when your SSH session goes away.

---

