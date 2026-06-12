---
title: "Remote Application Access"
date: 2013-06-07
forum: General Help
---

### Post by blackping on 2013-06-07
Hi All

I want to install Linux/Ubuntu on a server based overseas whereby multiple users can make use of a "desktop icon" that directly connects them to an application installed on the Linux server over the internet. The application can be executed multiple times (multiple instances). The user must be able to open the application in multiple instances from the users desktop with an internet connection. I am still getting my feet wet with Linux and I want to start from the basics up to being able to confidently deploy such a service as indicated above. What I am aiming to achieve is as follow:

Installing and configuring Linux on the Server 

Developing/employing the necessary tools to enable multiple users to access the application via a secure framework from their local pc/laptop (win 7/8) 

Administrative rights to monitor,disable,create ID's that are specific to each user with application access to the server via there "desktop icon"

Even if this might be a monumental task I know that all of the above and more can be done  therefore I would appreciate it if any advanced users can provide me with a clear cut list as to where I can start to work my way to obtain the skills to be proficient enough in Linux and other open source software or proprietary software to enable me to execute the task at hand. 

Thank you for your assistance it is kindly appreciated.

---

### Post by HermanAB on 2013-06-07
SSH with X forwarding is probably what you want.
ssh -X -C -c blowfish user@server programname

---

### Post by btindie on 2013-06-07
Using X-Forwarding over the internet might be quite painful.

See this post [http://ubuntuforums.org/showthread.php?t=2100574&p=12434048#post12434048](http://ubuntuforums.org/showthread.php?t=2100574&p=12434048#post12434048) and [http://ubuntuforums.org/showthread.php?t=2100574&p=12437515#post12437515](http://ubuntuforums.org/showthread.php?t=2100574&p=12437515#post12437515)

and also [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

