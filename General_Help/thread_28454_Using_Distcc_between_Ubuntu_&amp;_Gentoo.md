---
title: "Using Distcc between Ubuntu &amp; Gentoo"
date: 2005-04-20
forum: General Help
---

### Post by Bonescraper on 2005-04-20
Hi, this is my first post and i am in trouble.

I wanted to use distcc on both my distros, as the gentoo one will use the ubuntu computer to merge its packages. The problem is not on my gentoo (as far as i know how distcc works on gentoo), but on my ubuntu box. I don't really understand how to use distccd. On gentoo the command "distcc-config" allows you to add hosts easily but from nom, i do not know where to put my hosts.

Whenever i tried things, i've got on my gentoo shell :

"distcc[5416] (dcc_build_somewhere) Warning: failed to distribute, running locally instead
distcc[5418] (dcc_build_somewhere) Warning: failed to distribute, running locally instead
distcc[5420] (dcc_build_somewhere) Warning: failed to distribute, running locally instead"

Can someone help me ??
Thx

ps : sorry for my lack of words, but i am french

---

### Post by tomdeb on 2005-05-09
i m trying to do that as well and here is what i got

/etc/default/distcc allows you to specify the networks allowed to connect to your distcc server via the viarable ALLOWEDNETS

also change the variable STARTDISTCC to true and then start your distcc server by the command :

```
/etc/init.d/distcc start
``` 

then on fallow this on your gentoo box :

[http://www.gentoo.org/doc/en/distcc.xml](http://www.gentoo.org/doc/en/distcc.xml)

still having some errors afterwards, i ll post once i found all the solutions

---

### Post by Xylene on 2005-05-29
Anyone get this working? I have the same problem.

---

### Post by zigford on 2005-10-28
I use Gentoo as my server and Ubuntu as my desktop.
To get distcc working between the two was really quite simple.

I assume you have knowledge of how portage works and how ubuntu works.

**[SIZE="4"]Section 1 - Setting up Distcc on gentoo.[/SIZE]**

**a) Install distcc and distcc-config**

```
emerge distcc
emerge distcc-config
```

*If distcc-config is masked then 

```
echo "sys-devel/distcc-config ~x86" >> /etc/portage/package.keywords

```
**b) Configure distcc**

```
vi /etc/conf.d/distccd

DISTCCD_OPTS="${DISTCCD_OPTS} --allow 192.168.0.0/24"
```

Modify the above line to suite your subnet.  I assume your doing this on a lan.

```
distcc-config --set-hosts "192.168.0.77 192.168.0.36 192.168.0.10"
```

Modify the above line to include the distcc helper ip addresses.

**c) Configure gentoo**

```
vi /etc/make.conf

FEATURES="distcc"
```

**d) Start distcc**

```
/etc/init.d/distccd start
```

**e) Finally, check which version of gcc your gentoo is running.**

```
gcc -v
```

**[SIZE="4"]Section 2 - Configure the helpers[/SIZE]**

**a) Install distcc**

```
sudo apt-get install distcc
```

**b) Configure distcc**

```
vi /etc/defaults/distcc

STARTDISTCC="false"
ALLOWEDNETS="192.168.0.0/24"


```

Change the STARTDISTCC="false"
to
STARTDISTCC="true"

Change the allowednets network id to correspond with your local lan.
[B]
c) Check which version of gcc you are running[/B]

gcc -v

If you have the same version of gcc as your gentoo install, then you can simply run:
```
/etc/init.d/distcc start
```

If you do not, then follow on with the next step
[B]
d) Install required gcc and g++[/B]

Example, to install gcc 3.3
```
sudo apt-get install gcc-3.3 g++-3.3

```
**e) Create a distcc binary directory with links**
From here on in, the version will be refered to $version, please substitute this with your version number of gcc

```
mkdir -p /usr/lib/distcc/$version   <-------Make this ther version
cd /usr/lib/distcc/$version
ln -s /usr/bin/gcc-$version gcc
ln -s /usr/bin/g++-$version g++
ln -s /usr/bin/cc cc
ln -s /usr/bin/c++ c++
```

**d) Set and export your new distcc path**

```
PATH="/usr/lib/distcc/$version:$PATH"
export PATH
```

**e) Crank up distcc**
```

/etc/init.d/distcc start
```

And emerge merily away

---

