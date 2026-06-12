---
title: "Some questions"
date: 2005-04-05
forum: General Help
---

### Post by zeu on 2005-04-05
1. I need oidentd installed, I tried to search apt but didnt find anything.
2. It seems I don't have any dev tools installed, like gcc.. 

exis@jen:~/Desktop/gftp-2.0.18 $ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

3. I followed ubuntuguide.org and wanted to install some stuff, this is what I got..

exis@jen:~/Desktop $ sudo tar jxvf Azureus_2.2.0.2_linux.GTK.tar.bz2 -C /opt/
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors

exis@jen:~/Desktop $ sudo apt-get install xmms
Reading Package Lists... Done
Building Dependency Tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate

So i can neither get azeureus nor xmms..

Can anyone help me with these problems?

---

### Post by WW on 2005-04-05
1. oidentd is in the universe repository.  See #3 in this HowTo thread: [http://ubuntuforums.org/showthread.php?t=3713](http://ubuntuforums.org/showthread.php?t=3713)

2. Install the **build-essential** package.  You can use Synaptic, or start a terminal and enter the command```
 sudo apt-get install build-essential
```

---

### Post by zeu on 2005-04-05
[QUOTE=WW]1. oidentd is in the universe repository.  See #3 in this HowTo thread: [http://ubuntuforums.org/showthread.php?t=3713](http://ubuntuforums.org/showthread.php?t=3713)

2. Install the **build-essential** package.  You can use Synaptic, or start a terminal and enter the command```
 sudo apt-get install build-essential
```[/QUOTE]
 I love you!
It finally worked out man, thanks alot dude.

---

### Post by zeu on 2005-04-05
[QUOTE=zeu]I love you!
It finally worked out man, thanks alot dude.[/QUOTE]
 wait i got another question, how do i configure oidentd?

---

### Post by BLTicklemonster on 2005-10-08
LMAO, they gave up. anyone want to tackle that one? I want to hit irc and ask questions.

---

