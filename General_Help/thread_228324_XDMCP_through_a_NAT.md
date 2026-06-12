---
title: "XDMCP through a NAT?"
date: 2006-08-03
forum: General Help
---

### Post by lastexyle on 2006-08-03
I have XDMCP set up with GDM and it works fine on a LAN, but I need to connect from outside my network (which is behind a NAT firewall.

I've forwarded ports 177 and 6000-6010 but I still can't connect from outside, what else do I need to do?

---

### Post by aparsons on 2006-11-06
bump.  i'm interested in this, too.

---

### Post by bio-aveiro on 2008-03-26
I'm having the same problem... I also fwd the router ports and nothing!

Any hint?

Is it possible to do a remote login throught X11 FWD?  :confused:

Tks

---

### Post by MrNougat on 2008-03-31
I have been attempting this for a couple weeks now, to no avail.

Smoothwall firewall
Ubuntu 7.10 inside NAT
XMing client remote, also behind NAT

According to many forum posts in many places, you should not use XDMCP over the internet, because it is insecure.  It transmits passwords in clear text.

This is apparently the last word on configuring XDMCP: [http://tldp.org/HOWTO/XDMCP-HOWTO/index.html](http://tldp.org/HOWTO/XDMCP-HOWTO/index.html) -- but I, as a newerish Linux user am finding it difficult to follow.  Besides which, the sections which call for editing specific files in Ubuntu 6.06 refer to files that do not exist on my Ubuntu 7.10 installation.  It also discusses using Gnome or KDE as an aside, focusing purely on X.

Now, mind you, I have XDMCP working just fine on the local network.  It's just the going through the NAT firewall that's not working.  I also have forwarded 177UDP and 6000TCP.

From what can gather, you also need to go to System > Administration > Login Window.  There, in the Remote tab, you need to do Style: Plain with face browser.  Otherwise you can run into weird display issues.  You may also need to modify the keyboard layout after you log in the first time.  I saw a post somewhere saying you'd need to go to the security tab and deselect "Deny TCP connections to the XServer," but that has no effect.

Again, I know it's insecure.  I know that it cannot be tunneled through SSH because it uses UDP.  I just want to know why it's not working, insecure or not.

---

### Post by papayo on 2008-04-30
No way with Xming. Even if you portforward UDP 177 and TCP 6000 on your firewall and you set on your local machine the DISPLAY variable to the public IP of your firewall, xming sends your private IP to the remote server (something like 192.168.x.y).
Initial negotiation over the UDP 177 succeds (it is initiated by your computer). However, the following TCP 6000 connection from the remote machine to your computer is initiated remotely. So the remote server looks for the IP Xming has communicated to it during the initial UDP 177 negotiation, that is your local IP (192.168.x.y), which of course is not reachable.

One package that allowed me to successfully do XDMCP through NAT, is the commercial StarNet's XWin32.

By the way, SSH does work, provided you do X11 forwarding (PuTTY does it very well).

Papayo

---

