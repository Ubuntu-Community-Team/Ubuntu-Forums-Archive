---
title: "gphoto2 2.4.1 Release trying to download"
date: 2008-04-11
forum: General Help
---

### Post by tinkietruck on 2008-04-11
I am trying to download the latest version of gphoto2 from the website.  I have downloaded it to my computer, but I do not know where to "extract" the files to in order to  use the latest version.  I have a Canon Powershot A650 that is not supported by the old version.  I need to install the latest version to see if it is supported.  Right now I have the files saved in my home directory.  I want to be able to see them within Synaptic Package Manager to install them.



Any help would be greatly appreciated.

Thanks,
Brandy

---

### Post by TeoBigusGeekus on 2008-04-11
Wait wait wait!!!!
Can you see the application in Synaptic Package Manager? I think it's in the repositories-just do a search for it. Right click it and select mark for installation. Then click apply.
If it's in Synaptic, you don't need anything from the software's site...

---

### Post by tinkietruck on 2008-04-11
The installed and latest version I see in Synaptic Package Manger is 2.2.0-3.  The version available on the website is 2.4.1.  That is the version I want.  So, when I download it from the site, where do I extract the files to for it to work properly?

Thanks,
Brandy

---

### Post by TeoBigusGeekus on 2008-04-12
Ok, I've just downloaded the package and I see what it is about. You need to compile the package yourself.

1) Double click the archive (tar.bz2 or tar.gz). Extract its contents (gphoto2-2.4.1 folder) to your /home folder.
2)Open a terminal and navigate to the folder
```
cd /home/yourusername/gphoto2-2.4.1
```
3)Type 
```
./configure
```
and wait. The compiler will gather information about your system and will check if everything is OK.
4)Type
```
make
```
the package will be compiled.
5)Type
```
make install
```
the package will be installed.

There is also an installation guide inside the archive - consult it if you want...

---

### Post by tinkietruck on 2008-04-12
I tried what you suggested, but it is telling me the folder doesn't exist.  

[IMG]http://i75.photobucket.com/albums/i310/lovemysan/brandys%20folder/Screenshot.png[/IMG]

I am sure your directions will work just fine as long as it will acknowledge that the folder exists.  I did this yesterday trying to make a folder in the terminal.  It created both folders through the terminal, but when I went to put some pictures there, it told me the folder didn't exist.

Thanks for your help.

Brandy

---

### Post by TeoBigusGeekus on 2008-04-12
Leave a space between cd and /home, i.e.
```
cd /home/ etc.
```
and not
```
cd/home/ etc.
```

---

### Post by gionnico on 2008-04-13
Will gphoto be updated to 2.4.1 with hardy heron?

---

### Post by tinkietruck on 2008-04-13
> **TeoBigusGeekus said:**
> Leave a space between cd and /home, i.e.
```
cd /home/ etc.
```
and not
```
cd/home/ etc.
```


Thanks, I did that.  It compiled.  I got to the following: 

checking for LIBGPHOTO2... no
checking libgphoto2 config program... gphoto2-config
checking for gphoto2-config... /usr/bin/gphoto2-config
checking for libgphoto2 version according to gphoto2-config... 2.3.0
checking if libgphoto2 version is matching requirement >= 2.4.0... no
configure: error: Version requirement libgphoto2 >= 2.4.0 not met. Found: 2.3.0
tinkietruck@tinkietruck:~/gphoto2-2.4.1$ make
make: *** No targets specified and no makefile found.  Stop.
tinkietruck@tinkietruck:~/gphoto2-2.4.1$ make install
make: *** No rule to make target `install'.  Stop.
tinkietruck@tinkietruck:~/gphoto2-2.4.1$ 


I do have the libgphoto2-2.4.1 as well.  I tried to install it the same way and it gave me the same message that no makefile found.

Thanks,

Brandy

---

### Post by tinkietruck on 2008-04-14
I was able to download those files finally.  Thanks for all the help.

---

### Post by JemW on 2008-04-23
./configure does not work for me...I get

root@jem-desktop:/home/jem/gphoto2-2.4.1#  ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for POSIX sh $() command substitution... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
root@jem-desktop:/home/jem/gphoto2-2.4.1# su
root@jem-desktop:/home/jem/gphoto2-2.4.1# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for POSIX sh $() command substitution... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by modorf on 2008-07-24
you need to get build-essentials

this will download and install GCC and a bunch of other programs needed to for compiling programs.

It seems like your new to Linux and need to look into building ubuntu packages.

Nathan.

---

