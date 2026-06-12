---
title: "Apache issue with Kubuntu"
date: 2005-10-18
forum: General Help
---

### Post by drotter on 2005-10-18
I recently switched from mandrake 10.0 to Kubuntu and for the most part have been very happy with the results.  The is one major issue...
I had been running apache on mandrake and hosting a small server for our lab.  On the server it ran a small db search program.  On mandrake it ran with no problems.  All I had to do was allow cgi scripts to be run in the user directory and everything was fine.
With kubuntu nothing works.  Before I installed kubuntu I backed up the whole user directory, so it's exactly the same.  Now in the error log i get :
[Tue Oct 18 18:05:17 2005] [error] (2)No such file or directory: exec of /home/user/public_html/blast_cs.cgi failed
[Tue Oct 18 18:05:17 2005] [error] [client 127.0.0.1] Premature end of script headers: /home/user/public_html/blast_cs.cgi

I've run out of ideas...the only thing different is kubuntu...
Any idea?
Thanks in advance.

d

---

### Post by thierry13 on 2005-10-19
Hi,

It's not the same to configure apache under ubuntu and mandrake, why? I don't know.
1> is apache configured well on your system? what appears if you go to [http://localhost?](http://localhost?)
2> For cgi, some module need to be installed depending of the language you want to use, perl,php etc... it's possible it's installed by default in mandrake, but for sure it's not installed by default in ubuntu (neither apache)

let me know

---

### Post by drotter on 2005-10-20
Actually, you're right.  I finally got around to actually reading the cgi script that was causing all the problems.  It was looking for a module that wasnt installed.  But it highlights one of the reasons I like ubuntu so much.  Apt-get whatever and it was solved.

thanks for the relpy,

---

