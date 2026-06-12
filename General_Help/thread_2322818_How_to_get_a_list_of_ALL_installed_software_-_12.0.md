---
title: "How to get a list of ALL installed software - 12.04"
date: 2016-04-30
forum: General Help
---

### Post by t0p on 2016-04-30
I have a computer running 12.04.  I'm going to install the latest LTS.  I want a list of all the software installed on the 12.04 - not just the stuff that came from a repo or through synaptic, but *everything*.

[This page]("https://askubuntu.com/questions/17823/how-to-list-all-installed-packages") covers a variety of commands to get a list of installed software, but as far as I can tell it doesn't include a way to get *all* installed programs.  For example, on my 12.04 machine I installed truecrypt.  I don't plan to install it on the new LTS, but it's on the 12.04 so I need a list that shows truecrypt.  So I know *all* software is being listed.  None of the various ways to generate lists mentioned at [https://askubuntu.com/questions/17823/how-to-list-all-installed-packages](https://askubuntu.com/questions/17823/how-to-list-all-installed-packages) produces a list including truecrypt, so they may be missing other packages I downloaded from "unofficial" sources.

Can anyone help me out here with the command I need to generate the list I need?

Thanks.

---

### Post by Irihapeti on 2016-04-30
The command
```
dpkg --get-selections
```
includes everything that's been installed from a deb. It doesn't have to be through synaptic or exist in a repository somewhere. I have a couple of packages I've created locally and installed with gdebi, and they're included.

Packages that are installed by other means are trickier. You could look through /usr/bin, /usr/local/bin, ~/bin etc &#8211; but even then, if you have something in another folder in your home directory, it won't be found that way. Unless there's a way of searching for all executables, anywhere, the only thing I can think of is to keep track of them manually.

---

### Post by t0p on 2016-04-30
Unfortunately 
```
dpkg --get-selections
```
didn't come up with truecrypt (which is the test package for this experiment, even though I don't plan to install it on my new LTS when I get round to replacing 12.04).
So I am still no closer to finding the elusive command (if it exists at all - and one would imagine that someone had thought of this.  If I knew how, I might roll my sleeves up and get a-hacking.  But I don't know how... I don't even know what I'd need to do to make myself know how).  So, I'll wander the web and look for likely candidates... unless someone pops up on this forum and utters the magickal words!  Come on, greybeards: now is your moment to shine!!

---

### Post by nerdtron on 2016-04-30
> For example, on my 12.04 machine I installed truecrypt. 

So how did you install truecrypt? Using the standard method from the repository? Through a .deb? Did you compiled it?

---

### Post by vasa1 on 2016-04-30
> **Irihapeti said:**
> ... searching for all executables, anywhere, the only thing I can think of is to keep track of them manually.
I have dropbox and firefox installed locally and they are not registered with the system. The *file* command describes them as "executable":
```
$ file /home/vasa1/MyFox/firefox/firefox
/home/vasa1/MyFox/firefox/firefox: ELF 64-bit LSB **executable**, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.18, BuildID[sha1]=e064ac771001dbd47fbaba48a02173b259e3bfd1, stripped
$ file /home/vasa1/.dropbox-dist/dropbox-lnx.x86_64-3.18.1/dropbox
/home/vasa1/.dropbox-dist/dropbox-lnx.x86_64-3.18.1/dropbox: ELF 64-bit LSB **executable**, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.15, BuildID[sha1]=e6b27186c1c115e63a36269b68d7f5dcfb3866ea, stripped
$ 
```
Users could rig up some script to detect such files in their home folder or wherever.

---

### Post by t0p on 2016-04-30
I think I installed truecrypt via a .deb on their web site.  Though I might be wrong.  One thing for sure:  I didn't compile/build/etc it.

---

### Post by t0p on 2016-04-30
> **vasa1 said:**
> I have dropbox and firefox installed locally and they are not registered with the system. The *file* command describes them as "executable":
```
$ file /home/vasa1/MyFox/firefox/firefox
/home/vasa1/MyFox/firefox/firefox: ELF 64-bit LSB **executable**, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.18, BuildID[sha1]=e064ac771001dbd47fbaba48a02173b259e3bfd1, stripped
$ file /home/vasa1/.dropbox-dist/dropbox-lnx.x86_64-3.18.1/dropbox
/home/vasa1/.dropbox-dist/dropbox-lnx.x86_64-3.18.1/dropbox: ELF 64-bit LSB **executable**, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.15, BuildID[sha1]=e6b27186c1c115e63a36269b68d7f5dcfb3866ea, stripped
$ 
```
Users could rig up some script to detect such files in their home folder or wherever.
```
t0p@mars:~$ which truecrypt
/usr/bin/truecrypt

```
So truecrypt is in /usr/bin/truecrypt.  Not an unusual place for an installed program to dwell within, methinks?  If I'm wrong, let me know!!

---

