---
title: "bind9 dynamic dns update"
date: 2013-01-17
forum: General Help
---

### Post by Wismerhilll on 2013-01-17
hi,

i'm trying to setup a samba4 domain controler using these guidlines [http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04]("http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04"), but i have an error when reaching the step 5.  if i try to start bind9, it fails and this comes out in the syslog 
```
Jan 17 13:43:48 DC-Lissi named[2003]: adjusted limit on open files from 4096 to 1048576
Jan 17 13:43:48 DC-Lissi named[2003]: found 3 CPUs, using 3 worker threads
Jan 17 13:43:48 DC-Lissi named[2003]: using up to 4096 sockets
Jan 17 13:43:48 DC-Lissi named[2003]: loading configuration from '/etc/bind/named.conf'
Jan 17 13:43:48 DC-Lissi named[2003]: /etc/bind/named.conf:13: unknown option 'tkey-gssapi-keytab'
Jan 17 13:43:48 DC-Lissi named[2003]: loading configuration: failure
Jan 17 13:43:48 DC-Lissi named[2003]: exiting (due to fatal error)
```

i've been searching for a while now and i can't seem to find anything usefull to solve this problem.

thanks for your help,

regards

---

### Post by Trapped on 2013-01-18
Hi,

I've got the same error after upgrading my Debian 6 system today. Please check your BIND9 version. It must be 9.8.x, not 9.7.x.

FYI: I don't know about the Ubuntu repos, but in the latest Debian release there is a bug, that dlopen is not enanbled in the package, which is necessary for Samba4, but it seems to be fixed and deployed soon. [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=692416](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=692416)

Still, you can compile your own version of BIND9.

---

### Post by Wismerhilll on 2013-02-14
thanks trapped,

my bind version is indeed 9.8.1.

compilation isn't my strong point though and I haven't found any other source of information since last time.

since you're the only one who posted so far (4 weeks already) I'm starting to think the whole community thing might be overrated but we'll see.  it might be because the problem is either uninteresting or uncommon, and I'm sure it will get fixed sometime.

The problem still remains a it was.](*,)

anybody pls help[-o<

regards

---

### Post by Wismerhilll on 2013-03-07
hi, i've finally found out how to solve the problem.

it is so simple that i was looking for a solution in recompiling the whole stuff.

the howto says to add the line in the /etc/bind/named.conf file, but it is an option, and therefor it needs to go in the /etc/bind/named.conf.option file.

that simple

how do i tag this one as solved ?

---

### Post by Habitual on 2013-03-07
Under Thread Tools @ top_of_page

---

### Post by capscrew on 2013-03-07
> **Habitual said:**
> Under Thread Tools @ top_of_page

Except it's broken right now!  See [**_[COLOR="#0000CD"]http://ubuntuforums.org/showthread.php?t=2121377[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2121377") for a workaround.

---

