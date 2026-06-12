---
title: "winex without package"
date: 2006-09-10
forum: General Help
---

### Post by feest on 2006-09-10
hi, i want to download and insall winex but the only way to do this seems to be getting it through the cvs way. that results in a error here so is it possible to get it as a .deb or an other package?

---

### Post by tuxinvader on 2006-09-10
WineX is commercial application (now called Cedega). I think Transgaming got upset when Debian tried to package it a while ago. Which is why you can't get it from a repo. You have three choices.

1. Pay for it. Go to [http://www.transgaming.org](http://www.transgaming.org)
2. Use the CVS version and build it on your own.
3. Use [linuX Gamers]("http://www.linux-gamers.net") CVS script -- [WineCVS]("http://winecvs.linux-gamers.net")

I would recommend you try [wine]("http://www.winehq.com") itself first though. They have been doing a lot of DirectX work recently and the free wine plays many games as well or better than Cedega.

Also the CVS version doesn't include all the copy protection stuff which is needed for many games. I'm a transgaming subscriber so I've never used the CVS version, but I would be suprised if it worked better than [Wine]("http://www.winehq.com").

---

### Post by ~LoKe on 2006-09-10
> **tuxinvader said:**
> WineX is commercial application (now called Cedega). I think Transgaming got upset when Debian tried to package it a while ago. Which is why you can't get it from a repo. You have three choices.

1. Pay for it. Go to [http://www.transgaming.org](http://www.transgaming.org)
2. Use the CVS version and build it on your own.
3. Use [linuX Gamers]("http://www.linux-gamers.net") CVS script -- [WineCVS]("http://winecvs.linux-gamers.net")

I would recommend you try [wine]("http://www.winehq.com") itself first though. They have been doing a lot of DirectX work recently and the free wine plays many games as well or better than Cedega.

Also the CVS version doesn't include all the copy protection stuff which is needed for many games. I'm a transgaming subscriber so I've never used the CVS version, but I would be suprised if it worked better than [Wine]("http://www.winehq.com").

I seem to have screwed up DirectX under wine when I installed WineTools (oops), how would one reinstall it?

---

### Post by feest on 2006-09-11
ok i run that script but when i enter the cvs password (it says it cvs... FINE!) it waits a long time and i then it goes to try to configure but it shows this message:

Configuring ...




--------- Error log - file /home/sven/.WineCVS/sources/cvscedega/ErrorLog : ---------
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

so what now?

---

### Post by monktbd on 2006-09-11
you need to install the build environment.

please read [this howto](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS&amp;amp;amp;amp;back=HOWTO+INDEX+Wine) for how to install cvscedega and the packages you need to install before building it.

the most important you miss right now is called "build-essential".

---

### Post by feest on 2006-09-11
okay i installed the packages but now it seems to do als whole bunch of nothing in the 'make' area...

---

### Post by feest on 2006-09-11
ah it is installed and i installed simcity but now i dont know where -_- so where is de default c drive...

---

### Post by monktbd on 2006-09-11
> **feest said:**
> okay i installed the packages but now it seems to do als whole bunch of nothing in the 'make' area...

i cannot remember the output the make section gave me but compiling wine can take quite a bit of time depending on your comp specs.

ah too late ;). good it got installed.

---

### Post by monktbd on 2006-09-11
> **feest said:**
> ah it is installed and i installed simcity but now i dont know where -_- so where is de default c drive...

just do as the how to says in step 4.
you can choose in which path you would like to put your drive c.
if you used the standard then it should be somewhere like

> cd ~/.cvscedega/c_drive

the ~ always stands for your home folder, e.g. /home/joedoe.

---

