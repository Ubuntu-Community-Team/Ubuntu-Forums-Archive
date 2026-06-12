---
title: "installing transcode w/o breaking everything"
date: 2005-04-21
forum: General Help
---

### Post by farnsworth on 2005-04-21
go here and get the old version:
[http://sorcerer.mirrors.pair.com/sources/transcode/0.6.12/](http://sorcerer.mirrors.pair.com/sources/transcode/0.6.12/)

before begining, you should have all of the standard dependancies the marillat package asks for, EXCEPT libavcodeccvs and libpostproc0.  just apt-get transcode (doesn't work, but gives a list of dependancies), apt-get the dependancies, rinse, repeat.

1.  because of the avcodec library hoary gives us, we have to do some source editing.  after unzipping the file, go into the [wherever]/transcode-0.6.12/import/decode_dv.c file with gedit and add these lines of code (just the two "static const..." lines):

# this lines already there, right up towards the top
static int verbose=TC_QUIET;
# vvvv .:add these lines:. vvvv
```

static const int frame_size_625_50 = 12 * 150 * 80;
static const int frame_size_525_60 = 10 * 150 * 80;

```
2.  the hoary libavifile gives us problems... configure the package with:
```
./configure --with-avifile-mods=no
```

if anything's missing, like ffmpeg or something, configure will tell you.  just snag the packages with synaptic.

3.  then...
make all
sudo make install

4.  I also had to add a link from usr/local/bin to /usr/bin
ln -s /usr/local/bin/transcode /usr/bin/transcode

---

### Post by coolbreeze on 2005-04-23
Thanks for the instructions;however, I'm getting an error. I followed your instructions and edited decode dv c.  I then typed the following: 

./configure --with-avifile-mods=no 

While checking for a lot of things it returns this error:

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity chec

Any suggestions?

---

### Post by farnsworth on 2005-04-23
do you have gcc and g++ installed?

---

### Post by coolbreeze on 2005-04-25
Yes g++3.4 is installed but g++ wasn't.  I installed it and the error didn't occur again!!  Thanks!  

I was able to get passed configuration and now get a new error after typing "make".  Here is the error:

libtool: link: `import_avi.lo' is not a valid libtool object
make[3]: *** [import_avi.la] Error 1
make[3]: Leaving directory `/root/transcode-0.6.12/import'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/transcode-0.6.12/import'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/transcode-0.6.12'
make: *** [all] Error 2

I see it has a problem with avi. How did you get around this error?

---

### Post by coolbreeze on 2005-04-25
Ok I have transcode installed!!!

I googled and found this:

avifile-0.7-0.7.43.tar.bz2

After untarring and installing it took away the error!  avifile-0.7-0.7.43.tar.bz2 had a few dependancies I had to meet.  I simply googled and found them.  After that transcode went through!!

thanks so much!  

Now on to MythTV.  I know it will install cause I once had it going in Kubuntu. 

thanks again

P.S.  What are consequences of --with-avifile-mods=no ?

---

### Post by farnsworth on 2005-04-25
the --with-avifile-mods=no flag tells transcode not to build a module for the avifile library, which  from what I've heard is necessary for importing old M$ avi formats.  I might be wrong about that, however.

You might also want to compile mplayer for the great set of tools it comes with (mencoder, mplex, etc.) and toolame for encoding audio.

---

### Post by coolbreeze on 2005-04-26
Ok I will install mplayer.

I am now having problems with MythTV but that's another topic. Thanks for your help.

---

