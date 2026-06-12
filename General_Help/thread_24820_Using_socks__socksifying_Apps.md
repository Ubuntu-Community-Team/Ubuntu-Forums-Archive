---
title: "Using socks / socksifying Apps"
date: 2005-04-08
forum: General Help
---

### Post by titus on 2005-04-08
Hi, 

I used to use a program called sockscap32 on windows to allow me to pass an application through a socks server, even if the program does not have native socks support.

I need to do the same thing under linux, but am having some problems.

I have seen an application called runsocks, but could not get this to work with fedora core 3. 

Can anyone help me get this working with ubuntu?

thanks,

titus.

---

### Post by titus on 2005-04-08
Okay, i've discovered dante-client, which seems to replace runsocks as far as functionality goes. Getting it set up is another matter though.

I'm having trouble getting the program to talk to the socks server. Here's the setup:

Box A - socks server v5 p1080 on local subnet
Box B - Ubuntu box with app (local)

Internet ---- Box A ----Box B ---- F ----Internet

F= restrictive firewall
The app is a game, which normall connects via tcp (high port - firewalled).

I need to somehow sockify the app to connect via the socks server on box B.

Any help greatly appreciated.

Titus.

---

### Post by titus on 2005-04-09
no gurus in here?

---

