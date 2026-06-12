---
title: "DC++ in Wine, how to get it to work.?"
date: 2005-11-02
forum: General Help
---

### Post by jnk on 2005-11-02
How do I get DC++ to work in Wine 0.9.0.?
Just installed wine 0.9.0, copied riched20.dll and comctl32.dll to:
**.wine/drive_c/windows/system32/**

then installed DC++ with wine, runned wincfg, pointed to the two dll's and selected native.
But DC just crashes when I try to download and there is some gui problems to. =(
Please if anyone is running DC++ in Ubuntu 5.10 with wine, tell me how to get it to work.

---

### Post by teaker1s on 2005-11-02
someone on these forums wrote a howto install dc++ linux which is ported to linux and doesn't need wine

---

### Post by Iandefor on 2005-11-02
You don't need WINE to run DC++. From the [wiki]("https://wiki.ubuntu.com/P2PHowTo#head-b02c45d54fdb9c3d41f60e5a6fed0e9975ba9a5a"):

you need to install all the dependencies first:
```
sudo apt-get install libatk1.0-0 libbz2-1.0 libc6 libgcc1 libglade2-0 libglib2.0-0 libgtk2.0-0 libpango1.0-0 libstdc++6 libxml2 zlib1g
``` then you need to get the package file: ```
wget http://newstuff.orcon.net.nz/ubuntu/dcpp/dcpp_0.0.20050809cvs-1~mird_i386.deb
```
After which, you actually need to install it: ```
sudo dpkg -i dcpp_0.0.20050809cvs-1~mird_i386.deb
``` then restart the GNOME panel by using ```
killall gnome-panel
``` When it reappears, then the DC++ icon should be there.

---

### Post by jnk on 2005-11-02
I wasn't asking about how to install LinuxDC++, I was asking about how to get DC++ (win) to work in wine.
Why don't u run LinuxDC++ you say. Because it's way to buggy for me to use.
I need I dcclient that don't shut down 5min after I've gone to bed for example.

---

### Post by pickarooney on 2005-11-03
[QUOTE=Iandefor]You don't need WINE to run DC++. From the [wiki]("https://wiki.ubuntu.com/P2PHowTo#head-b02c45d54fdb9c3d41f60e5a6fed0e9975ba9a5a"):

you need to install all the dependencies first:
```
sudo apt-get install libatk1.0-0 libbz2-1.0 libc6 libgcc1 libglade2-0 libglib2.0-0 libgtk2.0-0 libpango1.0-0 libstdc++6 libxml2 zlib1g
``` then you need to get the package file: ```
wget http://newstuff.orcon.net.nz/ubuntu/dcpp/dcpp_0.0.20050809cvs-1~mird_i386.deb
```
After which, you actually need to install it: ```
sudo dpkg -i dcpp_0.0.20050809cvs-1~mird_i386.deb
``` then restart the GNOME panel by using ```
killall gnome-panel
``` When it reappears, then the DC++ icon should be there.[/QUOTE]

I can't get the dependencies to work. They fail because the following all need one another:
eieio
cedet-common
emacsen
emacs21
speedbar


I think this is where it goes awry:

```

Source file `/usr/share/emacs21/site-lisp/eieio/eieio-opt.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-doc.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-load.elc
Error loading speedbar... ignored.
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-opt.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/eieio/eieio-speedbar.el:
  !! Wrong type argument ((stringp nil))
Done
emacs-install: /usr/lib/emacsen-common/packages/install/eieio emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1

```

---

### Post by Iandefor on 2005-11-03
> I wasn't asking about how to install LinuxDC++, I was asking about how to get DC++ (win) to work in wine.
Why don't u run LinuxDC++ you say. Because it's way to buggy for me to use.
I need I dcclient that don't shut down 5min after I've gone to bed for example.


I'm fully aware that you were asking how to get the DC++ client for Windows to work under WINE. However, I simply made the assumption that you just wanted DC++ and didn't know there  was a Linux port. Sorry bout that. 
 I think one thing it's really valuable to keep in mind about WINE is that it only recently entered Beta. It's still liable to crash for no apparent reason. It may be that the download function as coded in DC++ for Windows just makes it go nuts.

---

### Post by tonysathre on 2005-11-03
i have never heard of a windows program ran in wine to be more stable than the linux port

---

