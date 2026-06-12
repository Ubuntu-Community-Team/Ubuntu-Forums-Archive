---
title: "xmms plugin for m4a files doesn't work"
date: 2005-07-27
forum: General Help
---

### Post by GreatestGravity on 2005-07-27
"libmp4v2.so.0: cannot open shared object file: No such file or directory" is the error I get when starting xmms from the terminal window. As far as I can tell, I've gotten the plugin I need, but it doesn't recognize it. There is an "libmp4.so" file in the xmms plugins directory (/usr/lib/xmms/Input/), and there are also the files /usr/lib/libmp4ff.so.0.0.0 and /usr/lib/libmp4ff.so.0 which may be vaguely related to my other attempts to get this to work. 

I've come across other people who have had this problem (google does wonders) but I haven't found a nice concise explanation of what I can try to do to fix it... can someone help me out here?

I'd switch to beep, but it would have the same hassles of needing to find a plugin or something...

[edit] Or, alternatively, if someone could point out how to get mp4 to work in Beep, that would work just as well! I downloaded the plugin suggested at [http://www.sosdg.org/~larne/w/Plugin_list](http://www.sosdg.org/~larne/w/Plugin_list) , but the inetructions don't work - I got automake 1.8, but it still gives me errors.

"root@GreatestGravity:~/bmp-mp4_20041215# ALOCAL=aclocal-1.8 AUTOMAKE=automake-1.8 autoreconf -vifs

autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal --force
configure.ac:59: warning: underquoted definition of MY_CHECK_TYPEDEF_FROM_INCLUDE
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending%20aclocal](http://sources.redhat.com/automake/automake.html#Extending%20aclocal)
/usr/share/aclocal/pkg.m4:5: warning: underquoted definition of PKG_CHECK_MODULES
aclocal: configure.ac: 11: macro `AM_DISABLE_STATIC' not found in library
aclocal: configure.ac: 19: macro `AM_PROG_LIBTOOL' not found in library
autoreconf: aclocal failed with exit status: 1
" 

I'm going to try to figure this out, google knows stuff, but I've been trying to get this to work for a long time now and it's getting *really* frustrating.
[/edit]

[edit #2]
GAH. I've spent all of today trying various things, and every single plugin seems to hate me, every single potential solution seems to die on me... like my attempt at beep... :-x  ](*,)  ](*,)  ](*,)  ](*,)  ](*,) 

Someone, heeeeeeelpppp.... [/edit]

---

### Post by SFN on 2005-07-27
OK. I have no idea if this really works but somebody was just telling me today that you can just change the m4a extension to mp3 and it will play.

Try that. I'm dying to know.

---

### Post by GreatestGravity on 2005-07-27
[QUOTE=SFN]OK. I have no idea if this really works but somebody was just telling me today that you can just change the m4a extension to mp3 and it will play.

Try that. I'm dying to know.[/QUOTE]

Nope.

---

### Post by SFN on 2005-07-27
Damn.

It sounded so good.

---

### Post by GreatestGravity on 2005-07-27
Someone, help... I'm so lost...

---

### Post by RaymondQE on 2005-07-28
The plugin requires the libmp4-0 package but it is neither in ubuntu hoary nor backported from breezy yet.  You can either download it from the marillat site and install it or try to backport it from breezy.

   If you want to try to backport the package from breezy the following steps should help, although the former option is easier.

1) Install build-essentials package (needed to compile the source files from the breezy repo)
```
sudo apt-get install build-essentials
```

2) install the fakeroot package (sets up a fake root for compiling)
```
sudo apt-get install fakeroot
```

3) add an entry into your '/etc/apt/sources.list' pointing to the breezy source files
```

deb-src http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
```

4) install files needed for building the package, commonly referred to build dependencies
```

sudo apt-get build-dep libmp4v2-0
```

5) allow apt-get to download and build a package under a fake root.  You'll probably want to enter a temporary directory since this step downloads the source files into the current directory.
```

fakeroot apt-get -b source libmp4v2-0
```


If all goes well, you should have a file named libmp4v2-0_2.0.0clean-0ubuntu1_i386.deb

Install the package using the following command
```
sudo dpkg -i libmp4v2-0_2.0.0clean-0ubuntu1_i386.deb
```

---

### Post by SFN on 2005-07-28
Oooh. Sweet.

If you don't want to build that from source, you can get an RPM from [here](http://rpm.pbone.net/index.php3?stat=26&dist=0&size=236129&name=libmp4v2_0-devel-0.9.2.8-3.1tex.i586.rpm)

Then just do:

```
sudo alien --to-deb libmp4v2_0-devel-0.9.2.8-3.1tex.i586.rpm
``` 

and

```
sudo dpkg -i libmp4v2-0-devel_0.9.2.8-4.1_i386.deb
```

---

### Post by GreatestGravity on 2005-07-28
[QUOTE=SFN]Oooh. Sweet.

If you don't want to build that from source, you can get an RPM from [here](http://rpm.pbone.net/index.php3?stat=26&dist=0&size=236129&name=libmp4v2_0-devel-0.9.2.8-3.1tex.i586.rpm)

Then just do:

```
sudo alien --to-deb libmp4v2_0-devel-0.9.2.8-3.1tex.i586.rpm
``` 

and

```
sudo dpkg -i libmp4v2-0-devel_0.9.2.8-4.1_i386.deb
```[/QUOTE]

Well, I tried that, it still gives me the same error, libmp4v2.so.0: cannot open shared object file: No such file or directory....

do I need to copy something to the right directory? 

I suppose I'll try the long way, try getting it from the marillat site like RaymondQE suggested

---

### Post by RaymondQE on 2005-07-28
Here's a link to the marillat libmp4 deb

[http://www.las.ic.unicamp.br/pub/debian-marillat/pool/main/libm/libmp4/libmp4-0_2.0.0-0.2_i386.deb](http://www.las.ic.unicamp.br/pub/debian-marillat/pool/main/libm/libmp4/libmp4-0_2.0.0-0.2_i386.deb)

The reason why the rpm didn't work is that it was a development package, not the actual package that contains the library.  If you converted the non-devel package and converted it with alien, it may have worked fine.

---

### Post by GreatestGravity on 2005-07-28
[QUOTE=RaymondQE]Here's a link to the marillat libmp4 deb

[http://www.las.ic.unicamp.br/pub/debian-marillat/pool/main/libm/libmp4/libmp4-0_2.0.0-0.2_i386.deb](http://www.las.ic.unicamp.br/pub/debian-marillat/pool/main/libm/libmp4/libmp4-0_2.0.0-0.2_i386.deb)

The reason why the rpm didn't work is that it was a development package, not the actual package that contains the library.  If you converted the non-devel package and converted it with alien, it may have worked fine.[/QUOTE]

YES!!! IT WORKS NOW!!!! \\:D/ 

Thank you thank you thank you so much!!! 


<3 <3

---

### Post by SFN on 2005-07-29
[QUOTE=RaymondQE]The reason why the rpm didn't work is that it was a development package, not the actual package that contains the library.  If you converted the non-devel package and converted it with alien, it may have worked fine.[/QUOTE]

That's odd. That worked for me. I suppose I may have had what I needed before I did that. I didn't actually test it before hand. I installed the RPM then tested it.

Glad to hear it's working.

---

