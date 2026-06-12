---
title: "Information - Problem with putty on Ubuntu that worked on Windows XP?"
date: 2006-07-04
forum: General Help
---

### Post by iccEC on 2006-07-04
Hi all,

I'm new to the Linux (whole *nix scene actually) and decided to actively start playing with Ubuntu as my linux of choice.

This post is just an information thread to help people in case they stumble on the putty problem that I stumbled on Ubuntu 6.06.

Basically, I was trying to setup my Ubuntu system to connect with putty to a distant SSHd server configured while using my password-protected private RSA key that I is stored on my USB key.  Although I could connect (and authenticate) to the SSHd server with no problems, nothing was being rerouted to my tunnel.  Interestingly enough, this same setup would work flawlessly with WindowsXP (and Vista).

After searching on the forums, there is a command ("sudo netstat -plantu") that lets you see the ports that are active on your Ubuntu system.  Once putty is connected, I was able to realise that my putty connection was the only process listening with "tcp6".

To fix the problem, you need to change to tcp type in the *PUTTY* configuration in the CONNECTION/SSH/Tunnels window and explicitly select IPv4 (NOT Automatic).

Voilà, everything works like it used to now!

I hope this can help anybody that was stuck like I was.

iccEC

PS: To be honest, I don't know if this is an Ubuntu or Putty problem, or just normal use, but I figured I'd mention it anyway :)

---

### Post by Demogorge on 2007-04-28
Just worked for me on Feisty. Remove the tunneling entry and remake it with IPv4 checked. I did a lot of searching before stumbling on this solution.  Thanks!

I even found a bug report about it:
[http://bugs.launchpad.net/ubuntu/+source/putty/+bug/67488](http://bugs.launchpad.net/ubuntu/+source/putty/+bug/67488)

Guess that can be closed.

---

