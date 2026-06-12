---
title: "Problems with apt-get on 17.10"
date: 2018-04-18
forum: General Help
---

### Post by equal on 2018-04-18
Hey folks. A while back I was trying to install Acestream manually, and I added its repo to my system. Ever since, I get errors when I try to apt-get install or upgrade. I didn't see anything unusual in my keys, or in my /etc/apt/sources.list. To be safe, I deleted my sources.list completely, and generated a new barebones one. Same issue. 

Here is the output I get with doing apt-get upgrade: 

```
:~$ sudo apt-get update
Get:1 http://repo.acestream.org/ubuntu trusty InRelease [2,181 B]
Hit:2 http://ca.archive.ubuntu.com/ubuntu artful InRelease 
Get:3 http://ca.archive.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]
Err:1 http://repo.acestream.org/ubuntu trusty InRelease       
  The following signatures were invalid: E1254F21D636B7EFDE41D2AF50E2BCF0E3805CD8
Get:4 http://ca.archive.ubuntu.com/ubuntu artful-updates InRelease [81.7 kB]
Reading package lists... Done                                 
W: GPG error: http://repo.acestream.org/ubuntu trusty InRelease: The following signatures were invalid: E1254F21D636B7EFDE41D2AF50E2BCF0E3805CD8
E: The repository 'http://repo.acestream.org/ubuntu trusty InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

I know the issue is that acestream.org entry, buit it's not in my sources: 

```
#-----------------------------------------------------------------------------$
#                            OFFICIAL UBUNTU REPOS                            $
#-----------------------------------------------------------------------------$


###### Ubuntu Main Repos
deb http://ca.archive.ubuntu.com/ubuntu/ artful main restricted universe multi$
deb-src http://ca.archive.ubuntu.com/ubuntu/ artful main restricted universe m$

###### Ubuntu Update Repos
deb http://ca.archive.ubuntu.com/ubuntu/ artful-security main restricted unive$
deb http://ca.archive.ubuntu.com/ubuntu/ artful-updates main restricted univer$
deb-src http://ca.archive.ubuntu.com/ubuntu/ artful-security main restricted u$
deb-src http://ca.archive.ubuntu.com/ubuntu/ artful-updates main restricted un$




                               [ Read 16 lines ]

```

Any ideas on how to fix this?

---

### Post by &amp;KyT$0P# on 2018-04-18
Did you check the files in [FONT=Courier New]/etc/apt/sources.list.d[/FONT] ?

---

### Post by cruzer001 on 2018-04-18
You have a mix of PPA versions.  You should only install versions for your current system, Artful 17.10.

PPAs will not be located in your sources.list, but in /sources.list.d

I suggest you install "ppa-purge" and remove those PPAs that are not 17.10

```
sudo apt install ppa-purge
```

[https://www.google.com/search?client=ubuntu&hs=CcL&channel=fs&ei=Re3XWtXDD-vd0gK245SIBA&q=ppa-purge&oq=ppa-&gs_l=psy-ab.1.0.35i39k1l2j0l8.554634.560630.0.565408.37.13.0.0.0.0.498.1666.0j6j1j0j1.9.0..2..0...1.1.64.psy-ab..31.6.1438.6..0i67k1j0i22i30k1j0i131k1j0i131i67k1j0i131i46k1j46i131k1.230.xiBshxFqKv4](https://www.google.com/search?client=ubuntu&hs=CcL&channel=fs&ei=Re3XWtXDD-vd0gK245SIBA&q=ppa-purge&oq=ppa-&gs_l=psy-ab.1.0.35i39k1l2j0l8.554634.560630.0.565408.37.13.0.0.0.0.498.1666.0j6j1j0j1.9.0..2..0...1.1.64.psy-ab..31.6.1438.6..0i67k1j0i22i30k1j0i131k1j0i131i67k1j0i131i46k1j46i131k1.230.xiBshxFqKv4)

If you need further assistance please post:
```

ls /etc/apt/sources.list.d/*.list
```

---

### Post by equal on 2018-04-18
Eeeeesh. Thanks guys, got it figured out!

---

