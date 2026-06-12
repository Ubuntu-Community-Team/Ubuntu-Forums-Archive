---
title: "Is there a PureAdmin apg-get package?"
date: 2005-04-06
forum: General Help
---

### Post by DCBA25 on 2005-04-06
I just installed pureftpd on my hoary ubuntu.
I can't seen to find a PureAdmin apg-get package to work.
Could you please help me? I'm very fresh to linux, and want real bad to quit microsucks.
ThanX.

P.S. Sorry, but i posted in the wrong section, could you please move it? Sorry, it's my first post here  :oops: 
Please help me setup a ftpserver here.

---

### Post by p!=f on 2005-04-06
Hi and welcome on the forums.
There's no Ubuntu package for pureadmin, hopefully you have several choices.
1) Download the sources, unpack, debianize it and create the package.
2) Download the sources, unpack, run ./configure, make, make install
2) ```

[~] > wajig unofficial pureadmin
Lines suitable for /etc/apt/sources.list

         deb http://people.debian.org/~rcardenes sid main
         deb-src http://people.debian.org/~rcardenes sid main
         deb http://people.debian.org/~rcardenes woody main
         deb-src http://people.debian.org/~rcardenes woody main

1 sites and 1 packages matched. Search took 11.563 seconds.

```
Unfortunately, that site doesn't work for me now (perhaps later). You add the first line to your /etc/apt/sources.list, run apt-get update and you should be able to install it.
3) Ask someone to create the package for you and post it here ;)

Hope it helps. Good times with Ubuntu.

---

### Post by DCBA25 on 2005-04-06
Thanks.
But i'm affrain i'll mess it up, because i still have software that doesn't work. And i'm affraid it may get to messy...

How/Where  can i request someone to compile a Ubuntu PureAdmin package?

---

### Post by darksides on 2005-04-06
Try using cvs....I use it by this way. \\:D/ 

```

#### PUREADMIN ####
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/purify login
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/purify co purify
################

```

sh autogen.sh
make
sudo make install

---

### Post by p!=f on 2005-04-07
[QUOTE=DCBA25]
How/Where  can i request someone to compile a Ubuntu PureAdmin package?[/QUOTE]
Here it comes...
Unzip the attachement with gzip first...
```

[~] > gzip -d pureadmin_0.2.2-1_i386.deb.gz

```
... and install
```

[~] > sudo dpkg -i pureadmin_0.2.2-1_i386.deb

```
It's quickly packaged but should be working. Hope it helps.

---

### Post by DCBA25 on 2005-04-07
Worked like a charm!   \\:D/ 

Thanks!   O:)

---

