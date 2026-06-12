---
title: "VNC from ubuntu client/viewer to mac os x el capitan vnc server"
date: 2016-10-21
forum: General Help
---

### Post by clymbon on 2016-10-21
I'm trying to run a VNC client on Ubuntu 16.04 against a VNC server on Mac OS X El Capitan (Version 10.11.6).

There is some information at the following link, but it seems to be for a different OS X version. Link: [https://help.ubuntu.com/community/AppleRemoteDesktop](https://help.ubuntu.com/community/AppleRemoteDesktop)

But it got me on the right path.  I configured VNC desktop sharing on the mac by going to System Preferences / Sharing and checking the "Screen Sharing" box.  Tried various options for "Allow access for: All users / Only these users" and also various options and set a password on the "Computer Settings" panel from the screen sharing panel.  (bad name)

I'm pretty sure the VNC server on the mac is working, because I am able to connect to the Mac with RealVNC client from a Windows PC.  Works fine.

However, I can't get a client on ubuntu to work.  I tried both "Remmina Remote Desktop Client" and "Vinagre".  Both give the same result.  When I click connect I get a username/password prompt (and tcpdump on the mac shows somthing is coming in), but no matter what I try for username and password, I get an authentication failure.

Here's one interesting thing, which might help debug this.  When I run RealVNC client on windows and connect to the mac, there is no username prompt - it's greyed out, just a password prompt.  Entering the password that I configured for desktop sharing at the "Computer Settings" panel on the mac works.  It brings me to a login screen that allows me to select a user.  I then log in to my account on the mac and Voila, I'm seeing the screen.

So... how do I make it work from my ubuntu box?

Any help appreciated!

Thanks,

Duncan

p.s. One more piece of info: downloaded RealVNC client for linux. It seems to work.

---

