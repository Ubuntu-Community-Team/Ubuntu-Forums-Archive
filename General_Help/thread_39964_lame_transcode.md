---
title: "lame /transcode"
date: 2005-06-07
forum: General Help
---

### Post by [pl]ice on 2005-06-07
hi, trying to compile transcode. what can i do about that:
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
lame compiles ok, but then transcode gives me:

checking for lame/lame.h... yes
checking lame version... configure: error: lame requested, but cannot compile and run a test program
:/usr/src/transcode-0.6.14 # sudo apt-get -t testing install transcode

i can install lame, but my source.list can't find transcode. 
thanks

---

### Post by oritpro on 2005-06-07
There is a Transcode Deb package available via Synaptic if you configure your sources to include the unstable branches.  

But I have to warn you, after heavy usage, I ended up with a corrupt hard drive and had to re-install Ubuntu. The manufacturers drive utility reported no problems with the drive so I have to assume it was transcode that caused the problem.

With that said, add these sources to /etc/apt/sources.list

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

Run Synaptic and hit the reload button.

The transcode package is in the unstable branch but there are related packages in the other two.  As far as compiling from source, I ran into a lot of dependency problems myself and decided to hold off until the project matures.

This is probably not the answer your looking for but I wanted to bring it up as more of an informative post, hopefully somebody will do a how-to on compiling from stable sources.

---

### Post by [pl]ice on 2005-06-07
thanks.
    i'll hold off then. But any ideas what program can i use for movie transformation? avi>mpeg etc ?  i was counting on transcode.


  and would you know where is a list for source.list ;  a safe one? i think i have messed up my a bit.

thanks.

---

### Post by oritpro on 2005-06-08
[QUOTE='[pl]ice']thanks.
    i'll hold off then. But any ideas what program can i use for movie transformation? avi>mpeg etc ?  i was counting on transcode.


  and would you know where is a list for source.list ;  a safe one? i think i have messed up my a bit.

thanks.[/QUOTE]

I've spent quite a bit of time searching through sourceforge and the web for an alternative myself and haven't found anything that even comes close.  When it worked, it worked great but I've got too much time setting up my Ubuntu system to risk corrupting the drive again.

Here's my sources list, they haven't caused me any problems yet.
-----

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

# deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
# deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
# deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

---

### Post by [pl]ice on 2005-06-09
thanks, will let u know if i'll find some progs.

---

### Post by word_virus on 2005-06-09
[QUOTE='[pl]ice']thanks.
    i'll hold off then. But any ideas what program can i use for movie transformation? avi>mpeg etc ?  i was counting on transcode.


  and would you know where is a list for source.list ;  a safe one? i think i have messed up my a bit.

thanks.[/QUOTE]

If you have the marilliat repositories enabled (I assume you have decss installed from there if you're trying to to get transcode working) just apt-get liblame-dev (I THINK that's right, could be "liblame0-dev" or similar) and transcode should compile cleanly. 

I was equally frusterated by transcode the first time I tried compiling it.  Had lame installed, enabled the shared libraries, etc. and everything looked okay but still wouldn't compile.  Installing the lame development package fixed it, though.

---

### Post by [pl]ice on 2005-06-09
yep, configured, but i had to add one libdvd-dev or something, added all lame & dev
but now i got that @ make:
: undefined reference to `vorbis_info_clear'
/usr/lib/libavcodec.a(oggvorbis.o)(.text+0x6d7): In function `oggvorbis_decode_close':
: undefined reference to `vorbis_comment_clear'
collect2: ld returned 1 exit status
make[3]: *** [tcdecode] B&#322;&#261;d 1
make[3]: Opuszczenie katalogu `/usr/src/transcode-0.6.14/import'
make[2]: *** [all-recursive] B&#322;&#261;d 1
make[2]: Opuszczenie katalogu `/usr/src/transcode-0.6.14/import'
make[1]: *** [all-recursive] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/usr/src/transcode-0.6.14'
make: *** [all] B&#322;&#261;d 2
:/usr/src/transcode-0.6.14 #  

i.e. error, 
i assume it's something to do with tcdecode ?

thanks for help.

---

### Post by [pl]ice on 2005-06-09
got it working :)  turns out that i've had my resps. on unstable versions, and it kept asking about new libc6; searched ubuntu forum, got that: 

 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

 
 If you see any of these, delete them. Add these lines instead:
 
 

 deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
 deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 


and got the dep. for transcode + transcode off mirrormax :)

thanks.

---

### Post by oritpro on 2005-06-22
> **'[pl]ice']got it working :)  turns out that i've had my resps. on unstable versions, and it kept asking about new libc6 said:**
> ftp://ftp.nerim.net/debian-marillat/[/url] stable main
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

 
 If you see any of these, delete them. Add these lines instead:
 
 

 deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
 deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 


and got the dep. for transcode + transcode off mirrormax :)

thanks.

That definately did the trick, thanks for the info.  \\:D/

---

