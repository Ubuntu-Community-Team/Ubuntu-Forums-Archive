---
title: "Awstats - 403 Forbidden"
date: 2014-05-12
forum: General Help
---

### Post by ELMIT on 2014-05-12
I cannot figure it out what gone wrong.

I have installed awstats and setup as [https://help.ubuntu.com/community/AWStats](https://help.ubuntu.com/community/AWStats) says. I had to use a + infront of ExecCGI to reload it without error.

I used first /usr/lib/cgi-bin/awstats.pl -config=awstats.home.example.biz.conf -update   but since that gave me an error:

Error: Couldn't open file "/var/lib/awstats/awstats122013.tmp.25223" for write: Permission denied
Setup ('awstats.home.elmit.biz.conf' file, web server or permissions) may be wrong.
Check config file, permissions and AWStats documentation (in 'docs' directory).


I used sudo.

It finished without error, but now the web site is not available:

Forbidden

You don't have permission to access /awstats/awstats.pl on this server.


What did I do wrong? How to fix it?

---

### Post by ELMIT on 2014-05-12
In the error log I found:

AH01630: client denied by server configuration: /usr/lib/cgi-bin/awstats.pl

---

