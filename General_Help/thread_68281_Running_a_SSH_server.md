---
title: "Running a SSH server"
date: 2005-09-22
forum: General Help
---

### Post by harisund on 2005-09-22
I am running Ubuntu on my laptop in the school dorms. 

I want to know what application I will need to be able to telnet into this machine or SSH into this machine. 

In my desktop machine at home (not in the school dorms) I have installed FileZilla FTP server, and whenever I want some data that is not in my laptop but in my home desktop, I ask my mom to boot the computer, give me the ip, and I login and retrieve my data from school.

Now I want to know the equivalent for a GNU/Linux machine. I want to know how to enable my laptop to listen on SSH ports and telnet ports, so that I can access it from outside.

Is there some sort of a SSH server?

Thanks a bunch

With regards
Hari

---

### Post by KingBahamut on 2005-09-22
apt-get install openssh-server to install the proper ssh server. 

Youll need to foward 22 for ssh to the machine if you can do it. 

Ultimately , you can use SFTP to move data and files the same way you would with ftp as well. 

the openssh client is installed by default, so no worries there.

If you use a windows machine to access that system externally I recommend Putty, its basic , and does just about anything you need.

---

### Post by bsussman on 2005-09-22
that would be openssh-server

Install with your favorite package manager ( as long as it is apt based (Synaptic, kynaptic, etc.)

Make sure it is configured as you want it (for example, I would never allow password challenge):

Some snips from my config off my firewall:

 ```
PasswordAuthentication no
PubkeyAuthentication yes
```

This is not a complete config...

---

### Post by harisund on 2005-09-22
So OpenSSH is what I need.. 
Thank you a real lot.. 

I will try it and let you know .. 

Thank you once again

Regards
Hari

---

