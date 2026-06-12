---
title: "Install 32 bit architecture ?"
date: 2015-03-08
forum: General Help
---

### Post by michael-piziak on 2015-03-08
12.04 LTS 64 bit system.

Trying to install Kega Fusion following directions on this page:  [http://www.carpeludum.com/kega-fusion/](http://www.carpeludum.com/kega-fusion/)

I guess I need to install the 32 bit architecture, because terminal tells me so after I type in the first sudo.

How do I install this 32 bit architecture - ?    BTW what is this ?

---

### Post by tgalati4 on 2015-03-08
It appears that the Sega emulator is only compiled for 32-bit mode, so you need to install 32-bit libraries on your system.  The link you posted shows these two commands:

```
   sudo dpkg --add-architecture i386
   sudo apt-get update
```

Did they work for you?

Some reading:

[http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package](http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package)

[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)

---

### Post by michael-piziak on 2015-03-08
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo dpkg --add-architecture i386
[sudo] password for michael: 
dpkg: error: unknown option --add-architecture


Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

---

### Post by michael-piziak on 2015-03-08
Update:  I simply double clicked the .deb file and the software center installed it for me.  It runs great.

I guess my system (12.04 LTS) already had the 32 bit architecture installed - ?

How does this 32 bit architecture work?    I want my system to stay 64 bit unless it *needs* 32 bit architecture to run a certain program - like Kega Fusion.

---

### Post by steeldriver on 2015-03-08
What do

```

dpkg --print-architecture

dpkg --print-foreign-architectures

```

say?

---

### Post by michael-piziak on 2015-03-08
> **steeldriver said:**
> What do

```

dpkg --print-architecture

dpkg --print-foreign-architectures

```

say?

michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ dpkg --print-architecture
amd64
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ dpkg --print-foreign-architectures
i386
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

---

### Post by tgalati4 on 2015-03-08
The links I included explain the difference.  64-bit processors (you have one) can run both 64-bit and 32-bit code at the same time.  That is called Multi-Architecture.  Older code, like the Sega Emulator will only run in 32-bit mode.  So as long as it works you don't need to worry about it.

---

