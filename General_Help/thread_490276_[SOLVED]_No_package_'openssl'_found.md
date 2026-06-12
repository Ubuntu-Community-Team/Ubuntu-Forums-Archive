---
title: "[SOLVED] No package 'openssl' found"
date: 2007-07-02
forum: General Help
---

### Post by ataiger on 2007-07-02
Hi. This is one of my very first days on linux, so please understand if I don't know too much.
plus, sorry for my poor English

I use utorrent for file sharing on Windows. I didn't 100% abandon Windows, I made a dual boot configuration. but I think to spend much time on Feisty, so I looked up for a nice bittorrent client and found rTorrent.

I learned how to install the program, I downloaded libtorrent and rtorrent. libtorrent is required for rtorrent AFAIK. I unzipped the tar.gz files, and entered the folder, typed "./autogen.sh" as the README said. that returned "aclocal not found" i just skipped, and entered "./configure.sh"

Before that, I installed g++ and required packaged thru synaptic.

the point is when I type "./configure.sh", an error is returned.
```
checking for OPENSSL... configure: error: Package requirements (openssl) were not met:

No package 'openssl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables OPENSSL_CFLAGS
and OPENSSL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

when I check out synaptic to find out, I DO have openssl. I really don't understand what's happening. why no package 'openssl' found?
(and what's "aclocal not found?")

also, when I looked up this forum, there was some other asking a similar problem about the openssl.
[http://ubuntuforums.org/showthread.php?t=478297&highlight=openssl](http://ubuntuforums.org/showthread.php?t=478297&highlight=openssl)

---

### Post by milton1 on 2007-07-02
rTorrent should be installable through synaptic. save yourself the trouble. If you don't find it in synaptic, you may need to enable the universe repositories. Do this with the following command in the terminal:

```
gksudo gedit /etc/apt/sources.list
```

delete the # characters in front of every line that starts with deb http:// or deb-src http://

save, and update synaptic.

---

### Post by ataiger on 2007-07-02
Thank u milton1 for the quick reply.
I could find rTorrent on synaptic, but I tried a manual install to learn and the version on the internet/svn is a way higher than the version in the synaptic.

how can I fix this problem with openssl?

---

### Post by milton1 on 2007-07-02
Sorry, can't be of much more help.

---

### Post by ataiger on 2007-07-02
solved:
[http://ubuntuforums.org/showthread.php?t=371275&highlight=openssl+rtorrent](http://ubuntuforums.org/showthread.php?t=371275&highlight=openssl+rtorrent)

I think
> ```
sudo apt-get install build-essential libsigc++-2.0-dev pkg-config comerr-dev libcurl3-openssl-dev libidn11-dev libkadm55 libkrb5-dev libssl-dev zlib1g-dev libncurses5 libncurses5-dev
```
worked.

---

### Post by bmorency on 2007-07-02
> **ataiger said:**
> solved:
[http://ubuntuforums.org/showthread.php?t=371275&highlight=openssl+rtorrent](http://ubuntuforums.org/showthread.php?t=371275&highlight=openssl+rtorrent)

I think

worked.

just a tip for next time. when you run the configure script and it asks for a specific package to be install it is usually talking about  the development package.(ie: libcurl3-openssl-dev ) It needs to end with -dev.  you need them because you are actually building the program yourself.

---

### Post by ataiger on 2007-07-02
Thank u for the info bmorency!!

---

### Post by Sudo Sumo on 2008-05-15
> **ataiger said:**
> solved:
[http://ubuntuforums.org/showthread.php?t=371275&highlight=openssl+rtorrent](http://ubuntuforums.org/showthread.php?t=371275&highlight=openssl+rtorrent)

I think

worked.

Worked for a different problem!!!

I googled "No package 'openssl' found" and got this forum, copy and pasted the command, and fixed my configure problem.

Thanks!!!  (the program, btw, was "Barry" for the BlackBerry)

---

