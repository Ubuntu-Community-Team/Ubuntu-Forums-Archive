---
title: "ftp question"
date: 2008-03-13
forum: General Help
---

### Post by evilbuntu on 2008-03-13
im running server 7.10 and webmin with proftpd and was wondering if there was a way to set up one user out of many to only have access to a particular folder and not the rest..... i dont know how clear im being.

basically if i want one person to have full access to a directory but another to only see like 3 folders in the same directory. can i do this... can you help

thanks in advance

---

### Post by AgentZ86 on 2008-03-13
> **evilbuntu said:**
> im running server 7.10 and webmin with proftpd and was wondering if there was a way to set up one user out of many to only have access to a particular folder and not the rest..... i dont know how clear im being.

basically if i want one person to have full access to a directory but another to only see like 3 folders in the same directory. can i do this... can you help

thanks in advance

Yes, but I don't know how to advise instructions to do this.

On my server in my admin section I can create groups with certain permissions, and thus those users in each group can access only what I say.

So it's a matter of setting read,write,permissions, for your users, but I don't know enough about ubuntu server to advise further on this, but it can be done.

At least thats a start.

---

### Post by Rocket2DMn on 2008-03-13
You should be able to define a root directory for users/groups in the proftpd.conf file using chroot.  A brief google search shows this - [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html)

---

### Post by evilbuntu on 2008-03-13
> **AgentZ86 said:**
> Yes, but I don't know how to advise instructions to do this.

On my server in my admin section I can create groups with certain permissions, and thus those users in each group can access only what I say.

So it's a matter of setting read,write,permissions, for your users, but I don't know enough about ubuntu server to advise further on this, but it can be done.

At least thats a start.

is yoru server on ubuntu (or linux) period? cause any info you can give might start me off right

---

### Post by AgentZ86 on 2008-03-15
> **evilbuntu said:**
> is yoru server on ubuntu (or linux) period? cause any info you can give might start me off right

I"m using SME server from [www.contribs.org](www.contribs.org) 
It is linux and uses I think CentOS for it's OS
It has a simple console interface and also a server-manager you can access over the web, via ssh console

I considered using Ubuntu server myself, but it appeared that the webadmin would be perhaps more difficult then I would want to attempt to get working properly. But anyhow SME has soft raid for 2)mirrored IDE drives so it's not likely to lose a drive, and it can do tape backup etc. 

I'm sure ubuntu can do all of the same and perhaps even could be much better, but I'm just not familiar with it and really would want the webadmin working.

I wish there was a fully operational Ubuntu server with webadmin and some basic services like webmail,ftp,local dns resolving, etc. I"m in the process of installing my first Ubuntu server in the near future to toy with it, perhaps I can be of more help then.

---

