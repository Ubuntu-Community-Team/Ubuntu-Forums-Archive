---
title: "Ubuntu windows shares"
date: 2013-07-16
forum: General Help
---

### Post by Vinca on 2013-07-16
Hi everyone,

ubuntu has this problem where windows shares stop working. Shortly after install.  I've experienced it on every version since 8.04 shortly after installation.

For the first few weeks, shares work when you click "browse network."  all the computers in the network appear top-level, you don't even have to browse deeper.

then it all stops.

Note that ubuntu does not come with anything samba by default, no samba packages are installed.  So don't go telling me to install samba and mess around with smb.conf, that always makes it worse for me (of course it works with the IP of the computer you want to connect to smb://xxx.xxx.x.x but no longer with names in the nice top-level format out of the box.

What is this problem? How can I fix it? Why does everyone talk about samba when it obviously isn't needed (at least for the first few weeks)

If you don't believe me, create a live USB and boot it.  You'll see two things:

1. NOTHING samba is installed
2. perfect windows networking

then install it and watch it fail in a few weeks...?

Let me know if anyone has heard of or fixed this. Here's someone who had it happen before their eyes (second comment):

I get this error as described, after it stops working. [http://askubuntu.com/questions/287546/unable-to-access-windows-share-in-ubuntu-13-04](http://askubuntu.com/questions/287546/unable-to-access-windows-share-in-ubuntu-13-04)
And the first person to respond tells them to deal with samba... lol bad answer

I can confirm that dpkg.log shows no changes in any samba or networking related packages.  So I didn't uninstall it or anything.  "sudo service samba start" yields that I don't have samba (whoa no way)

vinca

---

### Post by theDaveTheRave on 2013-07-16
Vinca,

I agree that linux is often very strange when it comes to networking!

I normally find that I can see all the windows terminals in a network, even if I can't browse to them.

I've never experienced your particular problem of having them all dissappear.

Where are you located ? do you have this issue at work or at home ?

I know from experience that ubuntu has a strange issue with network configuration, seems to use a different network mask to the windows terminals.

If you are on a home network ensure that the dchp server (normally the box from your ISP) is serving the details to the pcs corrcectly.

confirm the IP of the pcs that you need to see and confirm that you can ping to them, if so you could then use [nmap]("http://nmap.org/book/man.html")
which should give you details of the pc you want to connect to (ie OS etc)

David.

ps. pay attention with nmap, as some ISP / Sys Admins don't like people using it (it can be seen as trojan or possible DOS, hack) and you could get yourself blacklisted, especially if you are running it to probe a lot of pc / server systems on a regular basis.

---

### Post by Vinca on 2013-07-16
good call, it was a DNS problem, I just changed from DHCP to manual and set google 8.8.8.8 as DNS. It's all good.

Let this be a lesson to people who have networking problems, NEVER INSTALL SAMBA if you're an end user and don't care about running a server, print share, etc.

Thanks so much David.

---

### Post by Vinca on 2013-07-16
duplicate.........

---

