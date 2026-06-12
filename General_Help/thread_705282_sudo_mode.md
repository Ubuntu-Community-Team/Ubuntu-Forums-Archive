---
title: "sudo mode"
date: 2008-02-23
forum: General Help
---

### Post by abc7887 on 2008-02-23
yesterday i installd ubuntu....

today i tried to enter sudo mode by typing su and pressed enter...then it asked for password..i put the password but it said authentication failed....

i tried it again and again and i checked the caps lock.....

---

### Post by dje on 2008-02-23
su asks for the root password, you need to use:
```
sudo su
```
this opens a root terminal ANY COMMAND WILL HAVE ROOT PRIVILEGES, so be careful ;)

or for just one command:
```
sudo *command*
```

hope that helps you

dje

---

### Post by seventhc on 2008-02-23
in ubuntu sudo is all you should need, what is it your trying to do?
You don't really need to su, but if you want, try this.
```
sudo su
```

---

### Post by luisromangz on 2008-02-23
The password that su asks for is not your user password but root's password. Since you don't know root's passwords because nobody asked you since root's account is disabled by default in Ubuntu, you can not use su (without prefixing it with sudo, of course).

---

### Post by abc7887 on 2008-02-23
this is really quick help.....thanx a lot ..
its working...i tried sudo su....

nw i want to install ktorrent 2.2.5

can some one please tell me the comand....

---

### Post by seventhc on 2008-02-23
Im not sure what version number this is, but this will install ktorrent.```

sudo apt-get install ktorrent
```
See? you don't need su. ;)

---

### Post by abc7887 on 2008-02-23
this is really quick help.....thanx a lot ..
its working...i tried sudo su....

---

### Post by abc7887 on 2008-02-23
sory...by mistake pasted the same post....

---

### Post by abc7887 on 2008-02-23
i am registered in a private tracker and there i need ktorrent 2.2.5 to download torrents ...the previous versions of ktorrents have been banned....

i ahve the set up on my desktop but i dont knw ho to install it...

---

### Post by seventhc on 2008-02-23
well, if you unpacked it, then it should be a folder on your desktop. There should be a readme in it but normally this should work.
Open a terminal
```
cd Desktop/foldername
./configure
make
sudo make install

```

---

### Post by abc7887 on 2008-02-23
i did wat u told me to do but it gave me the following output:::::

root@amit-desktop:/home/amit# cd Desktop/foldername
bash: cd: Desktop/foldername: No such file or directory
root@amit-desktop:/home/amit# cd Desktop/ktorrent-2.2.5
root@amit-desktop:/home/amit/Desktop/ktorrent-2.2.5# ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
root@amit-desktop:/home/amit/Desktop/ktorrent-2.2.5# make
make: *** No targets specified and no makefile found.  Stop.
root@amit-desktop:/home/amit/Desktop/ktorrent-2.2.5# sudo make install
make: *** No rule to make target `install'.  Stop.
root@amit-desktop:/home/amit/Desktop/ktorrent-2.2.5#

---

### Post by seventhc on 2008-02-23
I've been messing aroung with it, but it keeps giving me errors too, different than yours though.I was hoping to get the same error so the same fix would work for you. I have to find more info.

---

