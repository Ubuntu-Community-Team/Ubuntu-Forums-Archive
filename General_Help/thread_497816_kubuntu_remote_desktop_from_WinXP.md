---
title: "kubuntu remote desktop from WinXP"
date: 2007-07-10
forum: General Help
---

### Post by morior on 2007-07-10
Ok within a network, I am trying to remotely connect to a Kubuntu pc from WinXp.  Until such time as I get more pc's switched over to Kubuntu.  I can find several things on how to do this with ubuntu and I have netsupport running on it just fine.  I can not find a way to make netsupport work so I am searching for an easy solution to be able to see and control the desktop remotely.  Assume correctly that I'm low level, but eager to learn.  ( I have been trying to get this working so my company can switch pc's to Kubuntu instead of Vista.)

---

### Post by bmorency on 2007-07-10
i have been using NX. It works very well. you can get it from [nomachine.com]("http://www.nomachine.com/download.php").

you need to download the nx client, nx node and then nx free. install them in that order. it messed up on me when i did in another order.

when they are installed open the terminal and type:

sudo nxserver --useradd Username   #<- user that you want to be able to login.

you can get the windows client on that site too. it will use SSH to connect (port 22)

---

### Post by morior on 2007-07-11
Ok I have installed everything, but where do I configure it from?  Where do I add the username from in a terminal?

---

