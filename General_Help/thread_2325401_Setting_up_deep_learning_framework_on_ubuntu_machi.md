---
title: "Setting up deep learning framework on ubuntu machine and accessing remotely"
date: 2016-05-22
forum: General Help
---

### Post by agusta2 on 2016-05-22
Hello,

I am going to work on a project for which I need to use some deep learning libraries. I have a PC with required hardware in school and I need to access it remotely during the summer. I was hoping I could install all the stuff I need on the machine and then access it remotely, so that I can run my algorithms on it. What would be the right way to do it? Also, when I have access to this machine can I also download/copy stuff into this machine  remotely? Will I need to install the server edition of ubuntu? Or can I simply ssh into it? The PC will be connected to the school network. I hope that should be okay from a security standpoint too? Any other points that I should keep in mind? 

Thank you.

-A

---

### Post by TheFu on 2016-05-22
ssh is the way, but I expect, and hope, that inbound ssh isn't allowed.  That would be poor security.  Talk to the IT/Firewall guys before you bother.

ssh-server works on any OS that has a network stack (except Windows). Ok, Windows has a 3rd-party ssh server, but the last version I saw wasn't patched.  On Linux, the distro/server/desktop doesn't matter.  Just need to ensure any firewalls are setup to allow ssh to the specific machine.  Be certain to secure the ssh-server - don't use passwords, don't allow unblocked, failed attempts, and definitely do not allow remote root to work. There are config settings for all of this - covered many times in other posts in these forums.

Don't know anything about "deep learning", sorry.

---

