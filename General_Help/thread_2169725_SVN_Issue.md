---
title: "SVN Issue"
date: 2013-08-23
forum: General Help
---

### Post by Spikerok on 2013-08-23
Hello,

A few days ago my server was taken down by a possible attack and since then ive experienced issues with my SVN.
I have SVN installed on my windows PC and linked to the linux server, now when I try to update SVN on my PC following messages are returned :
Message A) Unable to connect to a repository at URL 'svn://xxx.xx.xxx.xxx/mysite/trunk'
No repository found in 'svn://xxx.xx.xxx.xxx/mysite/trunk'

OR

Message B) Unable to connect to a repository at URL 'svn://xxx.xx.xxx.xxx/mysite/trunk'
Can't connect to host 'xxx.xx.xxx.xxx': No connection could be made because the
target machine actively refused it.

Ive tried using following guide : [http://www.everville.de/pages/howtos/linux/svnserve/index.html](http://www.everville.de/pages/howtos/linux/svnserve/index.html)
With it i've stopped and started the svn, which in result didn't help.

Originally, before I have made changes to the server message B would be showing up. After I have followed the guide above, message A started showing up. I have made message B to come back after applying following line from the guide: start-stop-daemon --stop --quiet --oknodo --exec /usr/bin/svnserve

How can this issue be resolve?

---

### Post by Spikerok on 2013-08-26
To fix this issue I had to do following steps:
1. start-stop-daemon --stop --quiet --oknodo --exec /usr/bin/svnserve - stop the server
2. /usr/bin/svnserve -d -T -r /var/subversion/ - start the subversion. The folder i selected contains my repos.

---

