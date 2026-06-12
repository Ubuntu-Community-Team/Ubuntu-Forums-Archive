---
title: "Software Installation"
date: 2006-11-30
forum: General Help
---

### Post by Dr Small on 2006-11-30
Ok. I downloaded Tor from here:
[http://archive.ubuntu.com/ubuntu/pool/universe/t/tor/tor_0.0.9.2.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/universe/t/tor/tor_0.0.9.2.orig.tar.gz)

And extracted the file in "My Recieved Files", under /home/drsmall/
and I opened the terminal and typed:
cd "/home/drsmall/My Recieved Files/tor/"
and then typed ./configure (as it said in the INSTALL file)

and here's the output:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... no
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Does anyone know how to fix this? as I am new to Ubuntu and don't know how to make this right, so step by step instructions would really help me.
Thanks,
Dr Small

---

### Post by druhboruch on 2006-11-30
Do you have build-essentials installed?

---

### Post by 23meg on 2006-11-30
Tor is in the repositories; you should use the version in the repositories if you don't have a specific reason to build from source. [Make sure you've enabled the Universe repository]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html"), and type```
sudo apt-get install tor
```

---

### Post by aysiu on 2006-11-30
23meg is right. You're hurting yourself unnecessarily. Read more here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Dr Small on 2006-11-30
Ok. I just enabled Universe Repository, as the instructions stated on that webpage, and then ran the command in the terminal, and it asks for a password, and won't let me type. It does that for anything that I try running the sudo command. I don't know how to get around this....

Dr Small

---

### Post by 23meg on 2006-11-30
The password won't be shown on the screen, if that's what you mean with "it won't let me type"; just type it and hit enter.

---

### Post by Dr Small on 2006-11-30
Cool. You are awesome!
Thanks a million.

Dr Small

---

### Post by Dr Small on 2006-11-30
Ok. Just one more thing. Maybe I'm stupid, and if I am, I give you every right to call me so, but how do I run tor now? It said:

Setting up tor (0.1.0.16-1ubuntu2) ...
 * Starting tor daemon (tor)... Nov 30 19:42:49.967 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.


So I figure it installed and is running, but how do I close it, or even open it? I mean, I looked through the applications menu, and couldn't find it.

Maybe I type "tor" in the run application box?

Dr Small

---

### Post by 23meg on 2006-11-30
Tor will run as a daemon and you need to configure your applications to use it. With a browser, the recommended way is to use it through Privoxy. See [this page]("http://tor.eff.org/docs/tor-doc-unix.html.en") for instructions.

See [this page]("http://monkeyblog.org/ubuntu/installing/") for more on installing applications.

---

### Post by Dr Small on 2006-12-01
I know how to use tor, as I have used it on Windows, and know how to configure Firefox to run with it.

What I would like to know, is how to stop the daemon, through a command.
I tried killall tor, but it said:

tor(4707): Operation not permitted
tor: no process killed


So, if there is some command that will end the daemon, it would greatly help, as I don't like restarting the computer just to end it.

Dr Small

---

### Post by Dr Small on 2006-12-02
..:: Bump ::..

I really need some help with this.


Dr Small

---

### Post by LLRNR on 2006-12-02
[http://ubuntuforums.org/showthread.php?t=310229](http://ubuntuforums.org/showthread.php?t=310229) post # 4

---

