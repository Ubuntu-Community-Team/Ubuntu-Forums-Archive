---
title: "openssh remote login - Network is Unreachable"
date: 2013-09-02
forum: General Help
---

### Post by orangeman555 on 2013-09-02
I'm having an odd issue. 

When I do a login to a "remote"machine in my local network (the home) everything is fine. However when I try to log into a machine via the net (miles away :D) I get a "Network is Unreachable" seemingly no matter what I do. 


All computers involved have openssh server installed. 

What could I be doing wrong? 

(one unique issue in this situation is that I have internet which is wirelessly provided, but I'm unsure that applies)

---

### Post by papibe on 2013-09-02
Hi orangeman555.

There are several steps to accomplish that.

If you're unfamiliar with that concepts mention below, take a look at this is a very helpul [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

This would be the main steps:
[LIST]
[*]Set your server with a LAN static IP.
[*]Install openssh-server on your server.
[*]Test LAN ssh access to your server.
[*]Optional: change the standar ssh port (22) to a different, preferable higher value.
[*]Subscribe to a Dynamic DNS service. There are free and pay options. For example: DynDNS, no-ip, zoneedit, etc (check [here]("http://dnslookup.me/dynamic-dns/") for a longer list).
[*]Either install and setup the package ddclient, or (better if available) set your DDNS client in your router.
[*]Forward the ssh port in your router to your server.
[/LIST]
Now you are ready to test accessing your server over the internet.

Important: do not try to access your server using its public IP, or dynamic name from inside your own LAN. The proper way to test access is from outside your network. For example, an internet café, public library, a friend house, or using your phone or tablet's 3G service (be sure to NOT being connected to your LAN's WiFi though).

I hope that points you in the right direction, and let us know how it goes.
Regards.

---

### Post by orangeman555 on 2013-09-02
Thanks a lot! I'll check that out! 

Actually I've been logging into my dedicated server at bluehost to test the "incoming" side of things. I'll check out that video and hopefully get up to speed. Thanks a lot.

---

### Post by orangeman555 on 2013-09-02
This video is GREAT :D

---

### Post by HiImTye on 2013-09-04
here's the site I use yo check if my machine is reachable on my ssh port
[https://www.grc.com/x/ne.dll?rh1dkyd2](https://www.grc.com/x/ne.dll?rh1dkyd2)
it's a good idea to use a non-standard ssh port for outside your network to reduce the amount of attempts on your box. also, check out ubuntu's SSH Keys page ([https://help.ubuntu.com/community/SSH/OpenSSH/]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")) to make it more difficult to gain access, and denyhosts ([apt://denyhosts](apt://denyhosts)) to block repeat fails (protecting you from brute-force attempts)


[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

