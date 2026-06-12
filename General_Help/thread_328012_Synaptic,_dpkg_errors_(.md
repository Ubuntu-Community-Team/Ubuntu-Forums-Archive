---
title: "Synaptic, dpkg errors :("
date: 2006-12-30
forum: General Help
---

### Post by tjay on 2006-12-30
I don't know what happened, but something went wrong and now I can't install anything with Synaptic. It always gives me this error:

```
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/odbcinst1debian1_2.2.11-13_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `mono-runtime': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/odbcinst1debian1_2.2.11-13_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

How do I fix this?

TJ

---

### Post by moma on 2006-12-30
Try to run these commands.

$ [COLOR="Green"]sudo apt-get install -f [/COLOR]
$ [COLOR="Green"]sudo   dpkg --configure --pending[/COLOR]

$ [COLOR="Green"]sudo apt-get --purge clean [/COLOR]

Litterature: [http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html)
+
[http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html](http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html)

---

### Post by Bider on 2006-12-30
Try reinstalling it.

> 

sudo aptitude install synaptic



---

### Post by tjay on 2007-01-05
Hey hey sorry for the late reply... It was my harddrive. Bad sectors all over the place. Until the replacement arrives I'm stuck with a 40GB :( Well at least it works now!

Cheers!

---

