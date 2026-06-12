---
title: "Help with NFS...Please :)"
date: 2007-04-05
forum: General Help
---

### Post by knichel on 2007-04-05
I have a classroom and my student computers are all using NFS to mount the users /home dir from the server.  I have a laptop and my UID = 1000 on the laptop.  I wish to mount my /home dir from the server, but my UID on the server = 1003.  I need to be able to mount my dir and have read and write perms on my files.  

I am wondering if I should change my UID on my laptop to match the one on the server? (seems dangerous to me)

I appreciate any help you can give me.

Mike

---

### Post by wonk-o-matic on 2007-04-05
Been there...  If I knew then what I know now, I'd have done things differently.  

Here's a quote from [http://linuxgazette.net/issue50/misc/pollman/nfs.html](http://linuxgazette.net/issue50/misc/pollman/nfs.html)

"UID: One of the ways that nfs keeps track of who has access to what is the UID - the user identification. UID is the third entry in the passwd file. Mine looks like this: 

"jpollman:IxmI/XXxxrg/Y:501:100:JC Pollman:/home/jpollman:/bin/bash 

"Where 501 is my UID.  The UID for a person has to be the same for that person on all machines that will be using nfs. You can either make the UID the same in the passwd files on all machines, or you could use NIS - which is beyond the scope of this article. If you change the UID, you will also have to chown all that person's files as well. This is all a pain in the butt, but you only have to do it once. "

I'm not sure how well this technique works, and it feels dangerous to me, too.  I don't see any immediate problem, though, and if you have a live cd, it's easy enough to reboot and undo the damage.  

BTW, there are some security issues around NFS.  If a person is root on a machine, and connects through NFS to another machine, he can end up with root file priveleges on it.

---

