---
title: "Is someone trying to hack my computer?"
date: 2007-12-12
forum: General Help
---

### Post by sr20ve on 2007-12-12
I've been trying to setup nfs on my network, but I'm running into permission issues. I was looking over my auth.log on the file server and it's full of these entries. Here are a few samples:

> Dec  9 05:23:20 box sshd[31876]: (pam_unix) check pass; user unknown
Dec  9 05:23:20 box sshd[31876]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.116.18.169 
Dec  9 05:23:22 box sshd[31876]: Failed password for invalid user dan from 203.116.18.169 port 48925 ssh2
Dec  9 05:23:25 box sshd[31908]: Invalid user james from 203.116.18.169
Dec  9 05:23:25 box sshd[31908]: Address 203.116.18.169 maps to pop2.angsana.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Dec  9 05:23:25 box sshd[31908]: (pam_unix) check pass; user unknown
Dec  9 05:23:25 box sshd[31908]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203.116.18.169 

> Dec  9 17:36:47 box sshd[11381]: Failed password for invalid user recruit from 221.143.51.106 port 44695 ssh2
Dec  9 17:36:49 box sshd[11448]: Invalid user alias from 221.143.51.106
Dec  9 17:36:54 box sshd[11448]: (pam_unix) check pass; user unknown
Dec  9 17:36:54 box sshd[11448]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=221.143.51.106 
Dec  9 17:36:55 box sshd[11448]: Failed password for invalid user alias from 221.143.51.106 port 53402 ssh2
Dec  9 17:36:57 box sshd[11514]: Invalid user office from 221.143.51.106
Dec  9 17:37:02 box sshd[11514]: (pam_unix) check pass; user unknown
Dec  9 17:37:02 box sshd[11514]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=221.143.51.106 

> Dec 10 06:28:26 box sshd[701]: (pam_unix) check pass; user unknown
Dec 10 06:28:26 box sshd[701]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.24.145.50 
Dec 10 06:28:28 box sshd[701]: Failed password for invalid user admin from 190.24.145.50 port 41422 ssh2
Dec 10 06:28:30 box sshd[737]: Invalid user admin from 190.24.145.50
Dec 10 06:28:30 box sshd[737]: reverse mapping checking getaddrinfo for corporat190-024145050.sta.etb.net.co failed - POSSIBLE BREAK-IN ATTEMPT!
Dec 10 06:28:30 box sshd[737]: (pam_unix) check pass; user unknown
Dec 10 06:28:30 box sshd[737]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.24.145.50 
Dec 10 06:28:31 box sshd[737]: Failed password for invalid user admin from 190.24.145.50 port 42202 ssh2
Dec 10 06:28:33 box sshd[768]: Invalid user admin from 190.24.145.50
Dec 10 06:28:33 box sshd[768]: reverse mapping checking getaddrinfo for corporat190-024145050.sta.etb.net.co failed - POSSIBLE BREAK-IN ATTEMPT!

Any help would be appreciated. I've made a few changes on my firewall to tighten security. And by the way, this is a very small home network. From the logs, it looks like a brute force attempt as none of the user names being tried exist, except root.

---

### Post by posterboy on 2007-12-12
Yes, that's probable. There are several pages on the web about securing ssh, one of the things always mentioned is to get it off port 22. These are scripts, and they hit 22 hoping to make a connection. An even better trick, is to force the use of passphrases, and deny passwords altogether. That's a stopper, unless the user is legitimate. 
HTH, and good luck.

---

### Post by r-mo on 2007-12-12
I got this a lot when I installed openssh, install and configure denyhosts and it will block them after a couple of failed auths.

[http://ubuntuforums.org/showthread.php?t=450853](http://ubuntuforums.org/showthread.php?t=450853)

---

### Post by sr20ve on 2007-12-12
Thanks, I'll look more into securing ssh and installing denyhosts.

---

### Post by bodhi.zazen on 2007-12-12
Your ssh server will get hammered. I had 100,000 hits on a server in the first month alone (of course a public server is more visible then a home server).

Ant those hist were *after* I changed the default port. As denyhosts will show you there are an abundance of crackers scanning for vulnerabilities all the time, this is a sad fact of the internet.

I advise 4 things :

1. Change the default port.

2. Access by keys only.

3. Restrict allowed users in /etc/ssh/sshd-config

4. denyhosts

See this wiki page : [uwiki]AdvancedOpenSSH[/uwiki]

---

