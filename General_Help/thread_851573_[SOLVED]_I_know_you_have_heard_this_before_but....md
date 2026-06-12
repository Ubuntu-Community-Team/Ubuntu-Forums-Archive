---
title: "[SOLVED] I know you have heard this before but..."
date: 2008-07-06
forum: General Help
---

### Post by ernesto55 on 2008-07-06
Hello everyone I am a typical noob who has no experience with Ubuntu 8.04
I am new to this site and didn't know where to post this but here goes.
When I try to run Synaptic Package manager I get this:

E: Type '(copy/paste' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Can someone give me some help while I am trying to learn how to use Ubuntu

---

### Post by wannadumpwindows on 2008-07-06
Looks like you tried adding some things to your sources.list file, and copied a little too much when you did.

Type this command in a terminal window

```
gedit /etc/apt/sources.list
```

And then paste the output here.

We can help you get it cleaned up when we know what's wrong.

---

### Post by ernesto55 on 2008-07-06
Hey thanks for the help
I found the problem under the source list at the top I removed the a(copy/paste text) and it fixed the problem.

---

### Post by ryanhaigh on 2008-07-06
Your /etc/apt/sources.list file has some stuff in it that should not be there. Open it up by pressing Alt-F2 and entering
```
gksudo gedit /etc/apt/sources.list
```
Copy the contents of that file into a post here and we will tell you how to edit it and get you back up and running.

---

### Post by ernesto55 on 2008-07-06
I have a question outside of this problem.
Under which forum can i get basic information about using the terminal window?

---

### Post by ernesto55 on 2008-07-06
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted

---

### Post by wannadumpwindows on 2008-07-06
> **ernesto55 said:**
> Hey thanks for the help
I found the problem under the source list at the top I removed the a(copy/paste text) and it fixed the problem.

No problem. 

Once your problem is solved, you should mark your thread as solved.

In the "Thread Tools" menu, there's an option to mark your thread as solved, that way, more people don't try to help with a problem you already fixed.

---

### Post by ernesto55 on 2008-07-06
Thanks will do

---

### Post by ryanhaigh on 2008-07-06
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

