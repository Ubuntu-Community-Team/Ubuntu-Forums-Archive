---
title: "install and run firefox 2.0.0.20 on ubuntu 16.1"
date: 2016-11-11
forum: General Help
---

### Post by krisbadsg on 2016-11-11
i am working in a public sector organisation in india. we use our own web based software to perform our regular work. the problem is we work on firefox 2.0.0.20 version which i am unable to install and run on ubuntu 16.10 version. i surfed the net for installation guides and videos and followed all the steps specified but no use. i removed the bundled 49th version of firefox and downloaded the 2.0.0.20 version and installed in /usr/lib. connected a java plugin to this firefox and tried to run through a launcher. it is trying to launch the browser after few seconds it exits. so please help me.

---

### Post by &amp;KyT$0P# on 2016-11-11
What Firefox 2.0.0.20 did you download?

Please post the output of running this in a Terminal -
```
uname -a
```

Do you get any output if you run Firefox from a Terminal?

---

### Post by bearlake on 2016-11-11
That version of FireFox was Dec 18 2008.

---

### Post by krisbadsg on 2016-11-12
i downloaded the firefox version from official webpage : 2.0.0.20.tar.gz and extracted to /usr/lib

and from java folder i copied a plugin to the plugins folder

with a launcher i tried to start the firefox, but it is trying and exiting.

---

### Post by wildmanne39 on 2016-11-12
I seriously doubt that old of a version of firefox will ever install.

---

### Post by SeijiSensei on 2016-11-12
> **Wild Man said:**
> I seriously doubt that old of a version of firefox will ever install.
It might work on a 32-bit version of Ubuntu.  There is only an i686 version of the binary on the Mozilla site.  I tried using that on my 14.04 machine after extracting the tar file to /usr/local/bin.  The first error I got was that it couldn't find libgtk-x11-2.0.so.0.  On my 14.04 machine that library now resides in /usr/lib/x86_64-linux-gnu.  I tried fixing the problem by creating a symlink to that file in /usr/lib itself.  Now firefox finds the file, but it returns
```
./firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: wrong ELF class: ELFCLASS64
```
That means it wants a x86 (32-bit) library.

You could try to see whether it would run on a [32-bit version of Ubuntu]("http://cdimage.ubuntu.com/ubuntu/releases/12.04/release/ubuntu-12.04.5-dvd-i386.iso").  The simplest method would be to install Virtualbox and create a 32-bit Ubuntu VM. Otherwise you could try compiling your own copy from the source [https://ftp.mozilla.org/pub/firefox/releases/2.0.0.20/source/firefox-2.0.0.20-source.tar.bz2](https://ftp.mozilla.org/pub/firefox/releases/2.0.0.20/source/firefox-2.0.0.20-source.tar.bz2).

More importantly, why is your organization using a version of Firefox that is eight years old and likely riddled with bugs and security issues?  Have you tried using an up-to-date version? Is is somehow incompatible with your organization's needs?

---

### Post by krisbadsg on 2016-11-14
thank you for your reply. actually i tried to install other versions of firefox in both linux and windows. it never worked. besides as far as my knowledge is concerned the software we are using is very low level and very much vulnerable. but we are very safe, coz outsiders cannot access the servers via internet. i will follow your advise of installing 32bit os in virtual box.

---

