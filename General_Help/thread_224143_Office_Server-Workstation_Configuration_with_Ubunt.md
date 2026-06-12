---
title: "Office Server-Workstation Configuration with Ubuntu 6/5.10"
date: 2006-07-27
forum: General Help
---

### Post by quyne on 2006-07-27
Hi.

I recently got hired as the new admin for a IT business.  
The last guy there had installed Ubuntu 5.10 as Server and 4 workstations with the same Ubuntu.  I need someone to point me to an article or walkthrough for the following :

[LIST]
[*]Currently we are overstaffed with programmers, so some of these guys usually work at home.  However, when they show up, they must have a working environment ready in any available Workstation.
For example, today Thursday programmer A showed up and started working on workstation A.  If he comes tomorrow and workstation A isn't available, can he resume his "session" on another workstation ?  I believe that this could be possible using the server as a "session" repository, but I'm not familiar with the method or tool to use.

[*]  If what I asked above is possible, can a "session" be resumed outside of the office in a secure way. 

[*]  I'm planning to upgrade the workstations to Ubuntu v.6.  However there is some sensitive data on the server, and I believe that leaving it with Ubuntu 5.10 is the best for now.  Would the version change cause any problem with the whole "session" resuming?
[/LIST]

Thanks a lot,


Daniel

---

### Post by gborzi on 2006-07-27
Hello, I think you need to configure the Virtual Network Computing (VNC) for the programmers. I have never used it, so I can't be of much help for you. There are 2 howtos in the wiki, one for the simple VNC and another one for the secure VNC, that is what you need if the programmers have to work from home. The howto for secure VNC is here: [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH) .
There is also a similar program called freenx, but AFAIK it doesn't work on amd64.

Hope this helps.

---

### Post by quyne on 2006-07-27
Well, VNC could be an answer but I think that the network latency is a problem.  Perhaps I din't explain myself throughfully.  More than a Remote Desktop solution, what I require is a solution that enables you to download the home folder and/or configurations to a client when you log-on.  

Someone told me that I could use something like kerberos, to authorize users and get configurations.  At least that is how I understood that a network was working, way back when I were in College.  

If I can't find that, then I'll try VNC.

Thanks !!!

---

### Post by gborzi on 2006-07-27
Perhaps for the internal clients there is a quick and dirty solution. Make the server to also work as an NFS server and mount the home partitions of the clients on this NFS filesystem.

---

