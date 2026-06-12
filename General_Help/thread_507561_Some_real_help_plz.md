---
title: "Some real help plz"
date: 2007-07-23
forum: General Help
---

### Post by Obscene on 2007-07-23
I'm a new beginner user on liniux
till now it's going good with me
but some problem occured when I try to install anything (updates or programs)

Here's the text shown in error box :

E: gnome-media: subprocess post-installation script returned error exit status 1
E: sound-juicer: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured

by the way it's ubuntu 6.06 LTS

Thx for U and wish for ur help

---

### Post by apjone on 2007-07-23
Hi, please use a more descriptive title in future.

1) Open a terminal (Applications > Accessories > Terminal)
2) Type
```
sudo apt-get install -f
```
3) Enter your password when asked
4) Read any out put carefully and decide what ou need to do. If you are stuck post the output her.

More Info:

      -f, --fix-broken
              Fix;  attempt  to  correct  a system with broken dependencies in
              place. This option, when used with install/remove, can omit  any
              packages  to permit APT to deduce a likely solution. Any Package
              that are specified must completely correct the problem. The  op&#8208;
              tion is sometimes necessary when running APT for the first time;
              APT itself does not allow broken package dependencies  to  exist
              on a system. It is possible that a system&#8217;s dependency structure
              can be so corrupt as to require manual intervention (which  usu&#8208;
              ally  means  using dselect(8) or dpkg --remove to eliminate some
              of the offending packages). Use of this option together with  -m
              may  produce  an  error  in some situations. Configuration Item:
              APT::Get::Fix-Broken.

---

