---
title: "scim: 100% CPU and RAM use, and won't start"
date: 2007-02-12
forum: General Help
---

### Post by precinto on 2007-02-12
I had a .xsession file in my home folder to start SCIM (since starting it from Startup Programs as 'scim -d' would not work). But today I was going to write some Chinese and noticed the tray icon wasn't there. I tried starting scim manually from terminal. Everything seems normal, it gets up to 'Creating SCIM backend...' or something similar and starts eating all the CPU and RAM, turning my system unstable and forcing me to reset the PC. No errors appear at all.

I think I can't use SCIM since yesterday. Yesterday I upgraded my system with the following packages:
```

language-pack-en (1:6.10+20061130) to 1:6.10+20070115
language-pack-es (1:6.10+20061130) to 1:6.10+20070115
language-pack-gnome-en (1:6.10+20061201) to 1:6.10+20070115
language-pack-gnome-es (1:6.10+20061201) to 1:6.10+20070115
language-pack-kde-es (1:6.10+20061130) to 1:6.10+20070115
libgnomevfs2-0 (2.16.1-0ubuntu4) to 2.16.1-0ubuntu7
libgnomevfs2-bin (2.16.1-0ubuntu4) to 2.16.1-0ubuntu7
libgnomevfs2-common (2.16.1-0ubuntu4) to 2.16.1-0ubuntu7
libgnomevfs2-extra (2.16.1-0ubuntu4) to 2.16.1-0ubuntu7
linux-headers-generic (2.6.17.10) to 2.6.17.11
linux-image-generic (2.6.17.10) to 2.6.17.11
linux-libc-dev (2.6.17.1-10.34) to 2.6.17.1-11.35

linux-headers-2.6.17-11 (2.6.17.1-11.35)
linux-headers-2.6.17-11-generic (2.6.17.1-11.35)
linux-image-2.6.17-11-generic (2.6.17.1-11.35)
```

But I could be wrong and this could come from some days before.

I'm using Edgy. It was working perfectly until recently. My X language is Spanish but the keymap is a custom one (enabling pinyin accents and so on). I installed (and reinstalled) these scim packages:

```
libscim8c2a (1.4.4-4ubuntu6)
libuim-data (1:1.2.1-3ubuntu2)
libuim3 (1:1.2.1-3ubuntu2)
scim (1.4.4-4ubuntu6)
scim-gtk2-immodule (1.4.4-4ubuntu6)
scim-modules-socket (1.4.4-4ubuntu6)
scim-modules-table (0.5.6-1build1)
scim-pinyin (0.5.91-0ubuntu6)
scim-tables-zh (0.5.6-1build1)
scim-uim (0.1.4-1build1)
```

I opened a bug [https://bugs.launchpad.net/ubuntu/+source/scim/+bug/84605](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/84605)

But maybe someone knows what to do here.

Thanks.

---

### Post by precinto on 2007-03-03
I just deleted every scim package, as well as the ~/.scim directory  (I think that was the problem). Then followed the instructions in the scim wiki for Ubuntu.

[http://www.scim-im.org/wiki/documentation/installation_and_configuration/ubuntu_kubuntu](http://www.scim-im.org/wiki/documentation/installation_and_configuration/ubuntu_kubuntu)

For it to work properly I had to had an ~/.xsession file with te following content:

```

scim -d
export XMODIFIERS=@im=SCIM
export GTK_IM_MODULE=scim
export QT_IM_MODULE=scim
gnome-session

```

Now it works again! &#25105;&#29616;&#22312;&#33021;&#20889;&#27721;&#23383;&#12290;

---

