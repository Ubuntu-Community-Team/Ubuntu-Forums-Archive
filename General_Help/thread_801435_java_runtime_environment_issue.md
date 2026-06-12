---
title: "java runtime environment issue"
date: 2008-05-20
forum: General Help
---

### Post by 1omgz on 2008-05-20
Well i installed "jre-6u5-linux-i586-rpm.bin" and i converted it to a .deb through alien.


i opened the .deb than installed it fine. than java applications like runescape worked for a day than just stopped...

now everytime i go to a java application after trying it says " additional plugins required, click here to download" ... and its the same thing i downloaded already.

i even re-installed it.  What i dont get is that it worked for a day, than just stopped...

:confused:


Can ANYONE help make it so i can use java apps again, thanks

I AM RUNNING : ubuntu 6.06

---

### Post by MaindotC on 2008-05-20
I'm not sure wy that issue is happening but it seems you have an incomplete java installation.  Java is included in the "ubuntu-restricted-extras" package and I've installed it on different machines several times and it works fine.  The restricted-extras package will also install some other things such as video codecs to view WMP files and Flash for Firefox.  Please look at the package if you have any questions.

Install it by typing the following:
```

sudo apt-get install ubuntu-restricted-extras

```

Keep me updated.

---

### Post by 1omgz on 2008-05-20
It didnt work...


i get

```
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing zope-cps (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

And i am running 6.06

---

### Post by MaindotC on 2008-05-20
It's bad enough you're still using 6.06 but instead of a fresh, clean install start trying the suggestions from this [Google search]("http://www.google.com/search?q=E%3A+Dynamic+MMap+ran+out+of+room&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a").

---

