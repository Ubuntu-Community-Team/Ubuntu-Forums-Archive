---
title: "nessus trouble"
date: 2007-11-12
forum: General Help
---

### Post by anemptygun on 2007-11-12
Well I installed Nessus and I have been using it, but I would like to register it. I have been having some trouble registering it though. These are the instructions I received in my registration email.
> Your activation code for the Nessus plugin feed is XXXX-XXXX-XXXX-XXXX-XXXX


Linux and Solaris Users :
--------------------------

To activate your account, simply execute the following command :

/opt/nessus/bin/nessus-fetch --register XXXX-XXXX-XXXX-XXXX-XXXX 

So this is what I type to register it.

```

opt/nessus/bin/nessus-fetch --register XXXX-XXXX-XXXX-XXXX-XXXX

```

But I get the error...

```

bash: opt/nessus/bin/nessus-fetch: No such file or directory

```
Why would this be? Is the version of nessus that is in the add/remove programs different then other linux versions?

---

### Post by ddrichardson on 2007-11-12
Are you sure it's installed in /opt? dpkg -L packagename from the command line will tell you where it's installed if it was a deb.

---

### Post by anemptygun on 2007-11-12
This is the output i get from dpkg -L nessus

```
/.
/usr
/usr/bin
/usr/bin/nessus
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/nessus.1.gz
/usr/share/pixmaps
/usr/share/pixmaps/nessus.xpm
/usr/share/applications
/usr/share/applications/nessus.desktop
/usr/share/doc
/usr/share/doc/nessus
/usr/share/doc/nessus/changelog.gz
/usr/share/doc/nessus/TODO
/usr/share/doc/nessus/changelog.Debian.gz
/usr/share/doc/nessus/README.Debian
/usr/share/doc/nessus/TODO.Debian
/usr/share/doc/nessus/copyright
/usr/share/doc/nessus/README_SSL.gz
/usr/share/doc/nessus/WARNING.En.gz
/usr/share/doc/nessus/WARNING.Fr.gz
/usr/share/menu
/usr/share/menu/nessus

```

---

### Post by anemptygun on 2007-11-12
The packages I have installed are :
```

libnasl2
libnessus2
nessus
nessusd
nessus-plugins

```

---

### Post by bruce2000 on 2007-11-12
Maybe this is stating the obvious.. but have you simply missed the leading / off the command. It looks that way to me from what you have posted...

---

### Post by ddrichardson on 2007-11-12
> **bruce2000 said:**
> Maybe this is stating the obvious.. but have you simply missed the leading / off the command. It looks that way to me from what you have posted...The file you're trying to run is not installed according to dpkg - I'd contact the developers. Or try```

nessus --register XXXX-XXXX-XXXX-XXXX-XXXX
```

---

### Post by anemptygun on 2007-11-12
> **bruce2000 said:**
> Maybe this is stating the obvious.. but have you simply missed the leading / off the command. It looks that way to me from what you have posted...
lol maybe. will try asap.

---

### Post by anemptygun on 2007-11-12
I will try your advice too ddrichardson, as soon as I get back to my Ubuntu box.

---

### Post by bruce2000 on 2007-11-14
> **anemptygun said:**
> lol maybe. will try asap.

just call me eagle eye bruce:mrgreen:

---

### Post by anemptygun on 2007-11-14
> **bruce2000 said:**
> just call me eagle eye bruce:mrgreen:

sorry eagle eye bruce... it didn't work lol

---

### Post by anemptygun on 2007-11-14
> **ddrichardson said:**
> ...Or try```

nessus --register XXXX-XXXX-XXXX-XXXX-XXXX
```

sorry ddrichardson this did not work either. I might just have to contact the devs.

---

### Post by anemptygun on 2007-11-17
did anyone come up with anything?

---

### Post by hangfire on 2007-11-17
Try finding nessus:

find / -name nessus -print

Wait a while....

When you find it, run it with the full path that find prints, such as 

/dir1/dir2/etc/nessus

Of course, substitute for dir1, dir2 & etc!

-HF

---

### Post by anemptygun on 2007-11-20
gotacha! will try asap~!

---

### Post by anemptygun on 2007-11-26
I stumbled across this article...

[http://www.darknet.org.uk/2006/11/installing-nessus-on-debian-based-oss-like-ubuntu/](http://www.darknet.org.uk/2006/11/installing-nessus-on-debian-based-oss-like-ubuntu/)

After you have entered your e-mail address, the instructions on how to register will not work on Debian-based OSs.
On the eMail from the Nessus team, you will be instructed to this path: /opt/nessus/bin/nessus-fetch, however, the path should be replaced by /usr/bin, making the complete registration command: sudo /usr/bin/nessus-fetch --register XXXX-XXXX-XXXX-XXXX-XXXX
You should now have a complete and working installation of Nessus. Enjoy and remember, automatic scanners are not 1337! =)

---

### Post by stanz on 2007-12-19
The registration command IS ran just on the server.

---

### Post by wormser on 2007-12-27
> **anemptygun said:**
> I stumbled across this article...

[http://www.darknet.org.uk/2006/11/installing-nessus-on-debian-based-oss-like-ubuntu/](http://www.darknet.org.uk/2006/11/installing-nessus-on-debian-based-oss-like-ubuntu/)

After you have entered your e-mail address, the instructions on how to register will not work on Debian-based OSs.
On the eMail from the Nessus team, you will be instructed to this path: /opt/nessus/bin/nessus-fetch, however, the path should be replaced by /usr/bin, making the complete registration command: sudo /usr/bin/nessus-fetch --register XXXX-XXXX-XXXX-XXXX-XXXX
You should now have a complete and working installation of Nessus. Enjoy and remember, automatic scanners are not 1337! =)

That worked.  Thanks.

---

