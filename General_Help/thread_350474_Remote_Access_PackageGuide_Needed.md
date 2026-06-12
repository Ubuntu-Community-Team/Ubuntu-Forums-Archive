---
title: "Remote Access Package/Guide Needed"
date: 2007-01-31
forum: General Help
---

### Post by jonjonz on 2007-01-31
There needs to be a solid how to guide on setting up Ubuntu for remote access that works every time  and  does not require extensive programing background to set up.  I have tried the various Hamachi/VNC posts found here, but none of them have worked for me, and no one has responded to requests for assistance.

It is the first area I have run into with Linux where things have not worked better and faster than in Windows.  The Hamachi build for Windows is really slick and super easy to install and use.

I have been very happy with my linux/Ubuntu experience so far, setting up a LAMP server and getting various projects online has been smooth and uneventful in a good way.

I have been fiddleing with the Hamachi linux version on Ubuntu for days now with no progress.

I am hoping that sometime soon there will be a remote access package and an Ubuntu guide for this that is rock solid and works as it says on the tin.

---

### Post by glabouni on 2007-01-31
depends on what kind of remote access you want. 

if you only need a shell, just install ssh and openssh-server package

if you want to share access to your desktop while you are logged on, there an option to do so in session preferences from the menu if I remember correctly; your desktop will be available through vnc.

if you're looking for a remote x session, you'll need to configure xdmcp. have a look at these:
[http://wiki.ltsp.org/twiki/bin/view/Ltsp/XDMCP](http://wiki.ltsp.org/twiki/bin/view/Ltsp/XDMCP)
[http://tldp.org/HOWTO/XDMCP-HOWTO/](http://tldp.org/HOWTO/XDMCP-HOWTO/)

if you're looking for VPN, I can't help you, I haven't digged into it yet.

---

### Post by jonjonz on 2007-02-01
Thanks for the tips, I will try them out.

I was hoping for some kind of gui, but line mode will work.  

I tried Hamachi because that is what we use in my office to to remote desktop on our windows boxes.  

:D

---

### Post by Marsolin on 2007-02-02
Do you need a VPN? If the answer is no then Hamachi isn't the answer. VPN should be simple to set up and already installed in Ubuntu. I can't give you specific instructions because I use Kubuntu and the only change you need to make to be able to remotely access the system is load Krfb and select allow uninvited connections from the configuration page. I assume that there is something similar in Ubuntu.

---

