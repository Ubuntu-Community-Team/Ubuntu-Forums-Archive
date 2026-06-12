---
title: "frepoops"
date: 2005-04-27
forum: General Help
---

### Post by lunos on 2005-04-27
some people can help me to install freepops, one demon for download email from [www.virgilio.it](www.virgilio.it), otherwise impossible.
I downloaded the binari .tar.gz
tar zxvf ...., cd new directory, sudo ./configure.sh linux, make install. one or two error appear in this end phase. bunt freepops don't work. one time working but with wynaptic call me that this packages is in conflict with other...
a lot of help to install freepops

---

### Post by bored2k on 2005-04-27
The process is this:

1. ./configure
2. make
3. sudo make install

If you encounter a problem during ./configure, read the last lines to know what you're missing.

---

### Post by lunos on 2005-04-27
thank's a lot.
I will try it
bye

---

### Post by Gandalf on 2005-05-21
[QUOTE=lunos]thank's a lot.
I will try it
bye[/QUOTE]
 to build it it's easy, first u need to install some packages
so
```

sudo apt-get install bison flex libc6-dev libcurl3-dev libexpat1-dev libidn11-dev libssl0.9.7 zlib1g-dev debconf

```

then
```

./configure.sh linux
make
sudo make install

```

turn it on (must be super-user
```

sudo freepopsd &

```

---

### Post by omiazad on 2005-06-09
[QUOTE=Gandalf]to build it it's easy, first u need to install some packages
so
```

sudo apt-get install bison flex libc6-dev libcurl3-dev libexpat1-dev libidn11-dev libssl0.9.7 zlib1g-dev debconf

```

then
```

./configure.sh linux
make
sudo make install

```

turn it on (must be super-user
```

sudo freepopsd &

```[/QUOTE]

I have downloaded [color=Red]freepops_0.0.28-1woody_i386.deb, libssl0.9.6_0.9.6m-1_i386.deb and libcurl2-ssl_7.9.5-2_i386.deb[/color] from some sources. After instelling[color=Red] libcurl2-ssl_7.9.5-2_i386.deb, libssl0.9.6_0.9.6m-1_i386.deb and freepops_0.0.28-1woody_i386.deb[/color] it's running successfully in my box, by writing the command sudo freepopsd & in command prompt.

[b]Hey Gandalf,
Netscape has changed something and I believe Freepops has some update for this by this time. Why don't you update your siemens-mobiles.org:2000 server?
[/b]

---

### Post by Gandalf on 2005-06-09
[QUOTE=omiazad]I have downloaded [color=Red]freepops_0.0.28-1woody_i386.deb, libssl0.9.6_0.9.6m-1_i386.deb and libcurl2-ssl_7.9.5-2_i386.deb[/color] from some sources. After instelling[color=Red] libcurl2-ssl_7.9.5-2_i386.deb, libssl0.9.6_0.9.6m-1_i386.deb and freepops_0.0.28-1woody_i386.deb[/color] it's running successfully in my box, by writing the command sudo freepopsd & in command prompt.

[b]Hey Gandalf,
Netscape has changed something and I believe Freepops has some update for this by this time. Why don't you update your siemens-mobiles.org:2000 server?
[/b][/QUOTE]
 i did not install any non-official plugins, but let me do it

//EDIT: download link is broken ( [http://www.freepops.org/en/viewplugin.php?plugin=netscape.lua](http://www.freepops.org/en/viewplugin.php?plugin=netscape.lua) ) i'll wait untill they fix it

---

