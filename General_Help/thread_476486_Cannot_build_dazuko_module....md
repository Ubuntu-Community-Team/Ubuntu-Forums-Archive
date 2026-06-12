---
title: "Cannot build dazuko module..."
date: 2007-06-17
forum: General Help
---

### Post by rmd on 2007-06-17
Hello all,

i am using ubuntu feisty and i want to install dazuko module.
i've dazuko module-assistant packages installed.
i run this command to compile dazuko:
```
sudo module-assistant prepare
sudo m-a a-i dazuko
```the first command run without error. the when i run the second command 
```
sudo m-a a-i dazuko
```it won't finished the process, and it show some error.
these what i got from the log file:

```
dh_clean
dh_clean
/usr/bin/make clean
make[1]: Entering directory `/usr/src/modules/dazuko'
make[1]: Leaving directory `/usr/src/modules/dazuko'
rm -rf .tmp_versions Makefile debian/control.backup
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/dazuko'
dh_clean
dh_clean
/usr/bin/make clean
make[2]: Entering directory `/usr/src/modules/dazuko'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/usr/src/modules/dazuko'
make[1]: [kdist_clean] Error 2 (ignored)
rm -rf .tmp_versions Makefile debian/control.backup
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.20-15-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.20-15-generic/g ;s/#KVERS#/2.6.20-15-generic/g ; s/_KVERS_/2.6.20-15-generic/g ; s/##KDREV##/2.6.20-15.27/g ; s/#KDREV#/2.6.20-15.27/g ; s/_KDREV_/2.6.20-15.27/g  ' < $templ > ${templ%.modules.in}; \
  done
./configure --without-library --without-example-c
checking host system type... Linux
checking for make utility... ok (make)
checking for C compiler... ok (gcc-4.1)
kernel source in /lib/modules/2.6.20-15-generic/build... yes
acquiring Linux kernel code configuration... ok
.: 1565: linux.config: not found
make[1]: *** [kdist_config] Error 2
```
i don't know what those mean, can any body help me?

thanx...

---

### Post by rbmorse on 2007-06-22
Can't help, but I just got the same error. Kubuntu 7.04

---

### Post by rmd on 2007-06-23
i have dazuko installed on my feisty. 
i used the source package dazuko-2.3.3.tar.gz file from **dazuko.org**. and it works for me.
i don't what was happened with package from ubuntu repos??

---

### Post by oscarand on 2007-10-03
I tried to install Dazuko on Kubuntu 7.10 and I received the "linux.config" missing error too.
So, I tried a newer version on Dazuko (....) with the commands bottom (I found this on Ubuntu web site):


[COLOR="Blue"][FONT="Courier New"]wget [http://dazuko.org/files/dazuko-source_2.3.3-1_all.deb](http://dazuko.org/files/dazuko-source_2.3.3-1_all.deb)
[sudo apt-get install module-assistant debhelper j2re1.4] I didn't execute this command because "module-assistant" was yet installed in my Kubuntu
sudo dpkg -i dazuko-source_2.3.3-1_all.deb
sudo module-assistant prepare
sudo m-a a-i dazuko[/FONT][/COLOR]


This is an automated procedure. With these commands I didn't received the "linux.config" error anymore, Dazuko compiles but after some seconds I received this new error:

So, What can I do now to install Dazuko on Kubuntu? Can anyone hel me/us? Thanx

---

