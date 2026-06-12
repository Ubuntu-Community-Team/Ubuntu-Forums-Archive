---
title: "Synaptic crashes, help please!"
date: 2012-12-11
forum: General Help
---

### Post by unsapo on 2012-12-11
Hello.
  This is the problem: after typing the password and entering correctly  it crashes. I can't take a screenshot (I think the os didn't recognized  the keyboard entirely -it's a laptop-), but the message log is: 
  "An error occurred
  The following details are provided:
  E: dpkg was interrupted, you must manually run 'dpkg -configure -a' to correct the problem.
  E:_cache->open()failed, please report."
  The thing is that when I manually type the command I get this:
  dpkg: error: unknown option -o  Type dpkg --help for help about installing and deinstalling packages 
[*]; Use `dselect' or `aptitude' for user-friendly package management; Type dpkg -Dhelp for a list of dpkg debug flag values; Type dpkg --force-help for a list of forcing options; Type dpkg-deb --help for help about manipulating *.deb files;  Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !   I'm running on Lubuntu 12.10



Thanks in advance!

---

### Post by NightsShadeQueen on 2012-12-11
-a, not -o :D

also you're running it with sudo, right?

---

### Post by Impavidus on 2012-12-11
No, it's a different error. Type:```
sudo dpkg --configure -a
```Pay attention to the spaces and the double dash in front of configure. With a single dash dpkg interprets it as```
dpkg -c -o -n -f -i -g -u -r -e -a
```which gives you an error because option -o doesn't exist.

---

### Post by Androzani1 on 2012-12-11
Does the Lubuntu Software Centre work?

---

