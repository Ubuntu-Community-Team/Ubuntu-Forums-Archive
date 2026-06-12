---
title: "Tor Update????"
date: 2005-08-16
forum: General Help
---

### Post by srijith on 2005-08-16
Can anyone point me the person in charge of maintaining Tor package? Ubuntu Tor package still seems to be stuck at 0.0.9.2. As one of Tor's developers puts it:

0.0.9.2 is 
> "Disgracefully insecure and seven months of date"

---

### Post by tom on 2005-08-26
I'm also *very* interested in an udated package. According to package info Peter Palfrader (weasel at debian.org) is maintaining the package. I tried to compile it by myself (checkinstall), but I'm sort of confused with the ubuntu/debian specific configuration process.

---

### Post by aetherane on 2005-08-29
I would like this a lot. I haven't been able to get the current packaged version of tor to run

---

### Post by tom on 2005-08-30
I finally got things to work ... in a quite an unusual way. According to a hint by the debian maintainer of Tor, Peter Palfrader, you can use the recent .deb of debian "woody". Just add 

```
deb   http://mirror.noreply.org/pub/tor woody main
```

to your sources.list. It works for me in ubuntu hoary too.

The [email]security@ubuntu.com[/email] people replied to my request. Martin Pitt pointed to the problem that there is no "universe" maintainer for the package. Matt Zimmerman stressed the point, that ubuntu does not guarantee security patches for "universe" packages and that they are not useful (in case of tor) also [-X .

For further information visit the following links:

Information about "universe": [http://www.ubuntulinux.org/ubuntu/components](http://www.ubuntulinux.org/ubuntu/components)
Information about "backporting" in general: [http://www.redhat.com/advice/speaks_backport.html](http://www.redhat.com/advice/speaks_backport.html)

If there is anyone able to backport the package for hoary, we need you!

---

