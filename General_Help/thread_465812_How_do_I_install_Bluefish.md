---
title: "How do I install Bluefish?"
date: 2007-06-06
forum: General Help
---

### Post by tomislav on 2007-06-06
Hi, I need help on installing Bluefish. It's an IDE.

I've downloaded it in .deb format. When I run it it says I don't have a prerequisite -> libpcre 3.0 or higher.

So I download libpcre 7.1 in tar.gz format. I extract all contents to a folder in my home directory. I've read the INSTALL file and it says I should 'cd' to the folder with all the content and type ./configure.

So I did that but it says I don't have a valid C compiler in that directory.

Could you please help me out? Are Linux installation always this messy? 

Oh, and I know I can download all these with Add/Remove programs but I don't have an internet connection on that computer (I downloaded everything with my windows comp and transport everything on a USD stick) and I'd like to learn how to install linux applications through normal means.

---

### Post by viciouslime on 2007-06-06
Bluefish is in the repos, that will have all its dependencies met :)

---

### Post by tomislav on 2007-06-06
I don't have internet on that comp.

---

### Post by zvacet on 2007-06-06
From comp with internet download this files(all marked with red ball are dependencies,but you maybe want and blue ones)and after that choose architecture wich you use and download bluefish.Burn that to disc and install it on your comp.Install dependencies first.

[http://packages.ubuntu.com/feisty/web/bluefish]("http://packages.ubuntu.com/feisty/web/bluefish")

---

### Post by tomislav on 2007-06-07
I have no idea how to install anything, that's what I said in my first post. I tried installing dependancies but I got some errors, please read my post.

P.S. I'm supposed to install 31 dependancy?!?!

---

### Post by zvacet on 2007-06-07
Put your Dapper CD in the drive and type in terminal

```
sudo apt-cdrom add
```
```
sudo aptitude install build-essential
```

When you have this package install try to install bluefish again.If any problem come up,just post it here.

---

### Post by tomislav on 2007-06-07
So I did as you said. I entered ./configure and didn't get that compiler error. After that I entered make. And after make I entered make install but that's where another problem occured... Here's the error msg I received:

```

make[1]: Entering directory `/home/zagreb/sjeta'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/sh ./libtool --mode=install /usr/bin/install -c  'libpcre.la' '/usr/local/lib/libpcre.la'
/usr/bin/install -c .libs/libpcre.so.0.0.1 /usr/local/lib/libpcre.so.0.0.1
/usr/bin/install: cannot create regular file `/usr/local/lib/libpcre.so.0.0.1': Permission denied
 /bin/sh ./libtool --mode=install /usr/bin/install -c  'libpcreposix.la' '/usr/local/lib/libpcreposix.la'
libtool: install: warning: relinking `libpcreposix.la'
(cd /home/zagreb/sjeta; /bin/sh ./libtool  --tag=CC --mode=relink gcc -g -O2 -version-info 0:0:0 -o libpcreposix.la -rpath /usr/local/lib pcreposix.lo libpcre.la )
gcc -shared  .libs/pcreposix.o  -Wl,--rpath -Wl,/usr/local/lib -L/usr/local/lib -lpcre  -Wl,-soname -Wl,libpcreposix.so.0 -o .libs/libpcreposix.so.0.0.0
/usr/bin/ld: cannot find -lpcre
collect2: ld returned 1 exit status
libtool: install: error: relink `libpcreposix.la' with the above command before installing it
 /bin/sh ./libtool --mode=install /usr/bin/install -c  'libpcrecpp.la' '/usr/local/lib/libpcrecpp.la'
libtool: install: warning: relinking `libpcrecpp.la'
(cd /home/zagreb/sjeta; /bin/sh ./libtool  --tag=CXX --mode=relink g++ -g -O2 -version-info 0:0:0 -o libpcrecpp.la -rpath /usr/local/lib pcrecpp.lo pcre_scanner.lo pcre_stringpiece.lo libpcre.la )
g++ -shared -nostdlib /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.0.3/crtbeginS.o  .libs/pcrecpp.o .libs/pcre_scanner.o .libs/pcre_stringpiece.o  -Wl,--rpath -Wl,/usr/local/lib -L/usr/local/lib -lpcre -L/usr/lib/gcc/i486-linux-gnu/4.0.3 -L/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib -L/usr/lib/gcc/i486-linux-gnu/4.0.3/../../.. -L/lib/../lib -L/usr/lib/../lib -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i486-linux-gnu/4.0.3/crtendS.o /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crtn.o  -Wl,-soname -Wl,libpcrecpp.so.0 -o .libs/libpcrecpp.so.0.0.0
/usr/bin/ld: cannot find -lpcre
collect2: ld returned 1 exit status
libtool: install: error: relink `libpcrecpp.la' with the above command before installing it
make[1]: *** [install-libLTLIBRARIES] Error 1
make[1]: Leaving directory `/home/zagreb/sjeta'
make: *** [install-am] Error 2

```

I also tried installing Anjuta IDE but instead of that cpp compiler error I received yesterday I had a problem with an XML parses or something... Will Linux ever get normal installers?

---

### Post by zvacet on 2007-06-07
Instead of make install you should type** sudo make install**.

---

### Post by tomislav on 2007-06-08
This is really starting to get apsurd... Thanks to your tip I managed to install libpcre 7.1 (latest version) or so I thought. I mean, I've encountered no error. But when I tried installing the .deb package for bluefish it said my dependancies were missing (libpcre 3.0 at least).

So I've downloaded the source and tried compiling it... this time it said I'm missing libgtk 2.0 or something. 

Why doesn't Ubuntu come with this packages? And what's going on? Why can't I install anything?

---

### Post by tomislav on 2007-06-08
I got 3 packages (anjuta, bluefish, vlc) and only anjuta installed properly (all dependancies met) but when I tried running it an error popped up saying something about child directory error. I'll paste it here in a sec.

There:

```

Could not launch menu item
Details: Failed to execute child process
"anjuta" (No such file or directory)

```

---

### Post by zvacet on 2007-06-09
Sorry for my overlook.Uninstall** libpcre 7.1** firsr with synaptic and after that install this

[http://packages.ubuntu.com/dapper/web/bluefish]("http://packages.ubuntu.com/dapper/web/bluefish")


[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=anjuta&searchon=names&subword=1&version=dapper&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=anjuta&searchon=names&subword=1&version=dapper&release=all")

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=vlc&searchon=names&subword=1&version=dapper&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=vlc&searchon=names&subword=1&version=dapper&release=all")


Allways install dependencies first.I hope this time install will go without problems.If you have any just post here.Once again,sorry for my overlook of version you are runing.

---

### Post by ThinkBuntu on 2007-06-09
$ sudo aptitude install bluefish

---

### Post by tomislav on 2007-06-10
I'm supposed to install 20+ programs manually? Isn't there some package to install most of them at the same time?

P.S. How do I run synaptic? Is that add/remove programs?

---

### Post by zvacet on 2007-06-10
You can not use synaptic or add/remove without internet.Most of packages are libraries wich are not too big,but I don´t think you have choice without internet.

---

### Post by tomislav on 2007-06-10
Still have a couple of questions:

**1.** If I had internet, would all the dependancies be automatically installed if I were to instally Bluefish for example?

**2.** Almost forgot... What about anjuta? Why is that program not running?

> **tomislav said:**
> I got 3 packages (anjuta, bluefish, vlc) and only anjuta installed properly (all dependancies met) but when I tried running it an error popped up saying something about child directory error. I'll paste it here in a sec.

There:

```

Could not launch menu item
Details: Failed to execute child process
"anjuta" (No such file or directory)

```

**3.** I've downloaded the deb package for libpcre and now that dependacy is met but when I try to install Bluefish it now says I don't have libatk1.0-0. However, when I run Synaptic and search for libatk it prints that I already have libatk1.0-0 installed... How is this possible?

---

### Post by tomislav on 2007-06-13
Does anybody know the answers to my questions?

---

### Post by andrew.46 on 2007-07-06
Hi,

> **tomislav said:**
> Does anybody know the answers to my questions?

 The easiest way is to get an Internet connectiond and then run:

```
sudo apt-get install bluefish
```

 There really is no way around that, the program will be installed and fully running in about 3 minutes with no input required from you. Well worth the 3 minutes, I have used Bluefish for 6 months and it is a great program!

                              Andrew

---

