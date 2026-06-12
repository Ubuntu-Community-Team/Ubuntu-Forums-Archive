---
title: "Locked out of ssh and sftp"
date: 2019-05-15
forum: General Help
---

### Post by mangonels on 2019-05-15
Using Ubuntu 16.04
Hosted on OVH - Kimsufi

I followed these instructions (that contained no warnings) in order to create a limited permissions account:
[https://wisdmlabs.com/blog/create-an-sftp-user-with-limited-access-on-ubuntu/](https://wisdmlabs.com/blog/create-an-sftp-user-with-limited-access-on-ubuntu/)

Quite a genious move, I know, as a result, I am now completely locked from accessing the OS and no longer have control. I don't even get the choice of logging in an account, not even a welcome message through SSH no connection through FTP. There's months of blocked work on the system.

In need of desperate help. I heard of something called OVH rescue mode, which I'll probably cling to if I don't get a better solution, but I have no idea how it works.

---

### Post by TheFu on 2019-05-15
Any VPS should provide console access to the VPS.  That will bypass any network issues that might have been created.

Using reputable resources when searching for answers is very important.  Also having a plan to back out any changes is smart.  It is possible to run sshd on multiple ports, so while you are testing on 1 port, you can come in through another.  But if you have console access (and you should), then it isn't a big deal.
Also, having a few different accounts is smart. Make certain they have crazy-long password, or better, different ssh-keys, for the access.  Something like deploy984345223427z is a good backup account userid.  It should be a hassle to use and not easy for someone else to guess or discover, since it is only for emergency access.

---

### Post by mangonels on 2019-05-15
Thanks for the advice. I'm obviously not a very experienced Ubuntu user, I locked myself out completely, so I guess my only choice is to use recovery options provided by kimsufi.

---

### Post by TheFu on 2019-05-15
> **mangonels said:**
> Thanks for the advice. I'm obviously not a very experienced Ubuntu user, I locked myself out completely, so I guess my only choice is to use recovery options provided by kimsufi.

This isn't about Ubuntu. It is all Unix stuff.  Don't get too tied to "Ubuntu" - linux is linux about 95% of the time. They are the same.  Slight differences happen with admin work, but pretty much ssh is ssh is ssh regardless of the Unix-like OS used. Well, except there are highly stripped down versions of ssh that IoT devices and routers use, but if you are using any of the popular Linux distros, ssh is ssh. All the same.

When you are just beginning, it is best to stick with websites that have "ubuntu" somewhere in the name. 
help.ubuntu.com, omgubuntu.com, ubuntuforums.org ... you get the idea. It takes time to learn the main, reputable sites, but that should get you closer.  Lots of the long-time posters here have blogs with reputable articles on how to do things.  My blog is less about exact commands and more about "what" and "why", since the exact commands change, but the reasons why don't.  LHammonds has some how-tos that go well beyond the 5 command setup solutions you'll find most places.  Setting up and securing a server is more like 50-150 commands, probably. Most of my setups are 95% automated to hook into my other infrastructure. 

Also, look for release-specific articles.  With every release, things change a little. Some things change a bunch. Since 2010, how to configure networks has drastically changed, most recently in 18.04.  Everything changed.

I'm on 16.04 on all my servers still. Just moved the last two from 14.04 in the last few months.  16.04 changed some network things in ways I didn't appreciate too.

Locking down ssh can be as simple or as complex as you need.  Depends on the attack vectors.  If you lock down ssh, that gets scp, sftp, and rsync (plus all the real backup tools based on librsync).

---

### Post by mangonels on 2019-05-16
I started the server in Kimsufi's Customer Rescue Service mode, which according to what I've read installs a new OS together with the old one, so I can actually see the other disk partitions with fdisk -l
If I'm just able to rewrite the file I modified, I presume I should be capable of fixing my control over the original OS... Allthough then I have to restart ssh and pray that it actually works propperly.
No idea how to do this, in which partition the file is, how to reach it, or if I can even edit it though.

I'm looking into it, but if anyone has any ideas please let me know.

For now I can see the disk partitions:
[IMG]https://i.imgur.com/En8qezl.png[/IMG]
[IMG]https://imgur.com/a/WCt5awh[/IMG]
[IMG]https://imgur.com/a/u2tbP0T[/IMG]

[IMG]https://i.imgur.com/VUl8ok3.png[/IMG]

Edit: The file I want to write (remove last lines from): */etc/ssh/sshd_config*

---

### Post by mangonels on 2019-05-16
Hey all, I consider this matter solved. If anyone's interested in the procedure of what I did, I left some updates:
[https://askubuntu.com/questions/1143816/fixing-a-ssh-and-sftp-lockout](https://askubuntu.com/questions/1143816/fixing-a-ssh-and-sftp-lockout)

---

### Post by oldos2er on 2019-05-16
Would you please mark your thread 'Solved' under Thread Tools at the top of the page? Thanks.

---

### Post by Guyofdoom42 on 2019-05-16
if you have physical access to the machine, can you just pop the drive out? If you can, you might be able to fix it that way - pull the data off, edit some files...

---

