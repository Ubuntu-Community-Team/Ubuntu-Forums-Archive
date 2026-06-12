---
title: "Boost-1_33_1"
date: 2007-11-21
forum: General Help
---

### Post by Holonet on 2007-11-21
I'm trying to configure avisynth 3.0, and it can't find boost-1_33_1, and neither can I.  I have installed everything that even comes up when I search for "boost" in adept manager, and still nothing.  I even did find /usr -name boost-1_33_1, and I got nothing, which indicates to me the configure file is right on about me not having it...if someone could render assistance....:confused:

---

### Post by monktbd on 2007-11-21
boost usually install in /usr/local/include for the templated header files and /usr/local/lib for the compiled libraries.
at least that is what the tarballs from boost itself do when building them with boostjam.

the relevant paths on my system are:

> /usr/local/include/boost-1_35/
/usr/local/lib/boost

---

### Post by Holonet on 2007-11-24
Ok nothing in those directories on my machine.  I have a /usr/include/boost directory, which has plenty of stuff in it, nothing I can find that will help though.

Being new to linux, I'd appreciate if someone could help me through the overall installation for boost and its header files.  I've looked at several procedures I've found online, but they all say something different, and none of them seem to do anything for me, or in some cases, even make any sense.  This is surely partly attribute to my ignorance of the operating system, but even following step-by-step, I whatever guide I follow citing things which I did not come with my package.

I downloaded the package off the website ([www.boost.org](www.boost.org)).

Oh another thing to note is I switched from Kubuntu back to Ubuntu, because Kubuntu was buggy and getting on my nerves hehe...so I did the same with synaptic as I did before with adept, still to no avail, and the same exact problem.

Like I said, I've also installed everything that came up when searching for boost in the package manager, yet I still get the aforementioned error.  I've installed a few other programs without much issue, so I don't see what's so elusive and complicated about this one...help...:confused:

---

### Post by monktbd on 2007-11-24
well most of the boost libraries are in fact just header files with a lot of templated classes in them. 
[http://www.boost.org/more/getting_started/unix-variants.html](http://www.boost.org/more/getting_started/unix-variants.html)
is kinda what i did.

if you already have a /usr/include/boost directory then that is where it got installed. i never installed the deb package so i dont know if there is anything precompiled in there. if it is you should find some boost libs under /usr/lib/boost.
if not you can just use the commands given in the above link to compile the libraries within the already installed headers (section 5.1).
if that still does not work then you might need to get bjam to compile the libraries.

---

### Post by Holonet on 2007-11-25
Thanks for the replies, though I'm still having issues.

I followed section 5.1 to the best of my ability, and here is precisely what I did.  I went to the directory which I untarred the download to, and I put in the following:

 sudo ./configure --prefix=/usr/local/

which I'm a little vague on what exactly "setting my configuration options" implies, and I got this:

Building Boost.Jam with toolset gcc... tools/jam/src/bin.linux/bjam
Detecting Python version... 2.5
Detecting Python root... /usr
Unicode/ICU support for Boost.Regex?... /usr
Backing up existing Boost.Build configuration in user-config.jam.1
Generating Boost.Build configuration in user-config.jam...
Generating Makefile...

seemingly just fine.

Then I went ahead and typed "make install" and got this (I used the -j2 argument so it would use my dual core):

./tools/jam/src/bin.linux/bjam -sICU_PATH=/usr --user-config=user-config.jam --prefix=/usr/local/ --exec-prefix=/usr/local/ --libdir=/usr/local//lib --includedir=/usr/local//include  install
Jamfile.v2:341: in load-aux
rule path.glob-tree unknown in module Jamfile</home/q/boost_1_34_1>.
/usr/share/boost-build/build/project.jam:318: in load-jamfile
/usr/share/boost-build/build/project.jam:68: in load
/usr/share/boost-build/build/project.jam:170: in project.find
/usr/share/boost-build/build-system.jam:148: in load
/usr/share/boost-build/kernel/modules.jam:261: in import
/usr/share/boost-build/kernel/bootstrap.jam:132: in boost-build
/home/q/boost_1_34_1/boost-build.jam:9: in module scope
Not all Boost libraries built properly.

Now the extent of my programming knowledge is reading C for dummies 500 pages in a number of years ago, so I have very little clue what that garbage means :cool:.  Anyhoo, it doesn't simply tell me that I'm missing something, so I'm confused as to what's wrong here.

If this means building the jam thingamaboo, that'll be fine, if one could possibly explain that procedure, or link to that specifically as well, because that part is what is making least sense of all to me.  Thanks again for the input thus far.  I like Linux, but it's certainly humbling my intelligence...

EDIT:  Forgot to mention, I have nothing under /usr/lib/boost, in fact, there is no "boost" directory under /usr/lib at all, which I'm guessing (and yes, just guessing) that is odd considering I installed all that boost stuff via synaptic.

Also, if it is relevant, here is the error I get in Avisynth configuring, which is where this whole shebang started:

checking for Boost header files in /usr/include/boost-1_33_1... no
configure: WARNING: Boost header files not in /usr/include/boost-1_33_1
checking for Boost header files in /usr/local/include/boost-1_33_1... no
configure: WARNING: Boost header files not in /usr/local/include/boost-1_33_1
checking for Boost header files in /usr/include/boost-1_33... no
configure: WARNING: Boost header files not in /usr/include/boost-1_33
checking for Boost header files in /usr/local/include/boost-1_33... no
configure: WARNING: Boost header files not in /usr/local/include/boost-1_33
configure: error: "Boost is needed !"

I also tried pointing avisynth to the aforementioned boost directory which I can see with my own eyes has lots of files in it (headers or what-have-you, I don't know) using:

 ./configure  --with-boost-includedir-path=/usr/include/boost/

from the avisynth directory.  It still spits out:

checking for Boost header files in /usr/include/boost/... no
configure: WARNING: Boost header files not in /usr/include/boost/
checking for Boost header files in /usr/include/boost/... no
configure: WARNING: Boost header files not in /usr/include/boost/
checking for Boost header files in /usr/include/boost/... no
configure: WARNING: Boost header files not in /usr/include/boost/
checking for Boost header files in /usr/include/boost/... no
configure: WARNING: Boost header files not in /usr/include/boost/
configure: error: "Boost is needed !"

---

### Post by Holonet on 2007-11-25
Just as an update, I checked the /usr/include/boost directory, and the subdirectories, I can actually see .hpp files, which I understand are boost header files...I point avisynth's configure to there, and to individual subdirectories with said .hpp files, and it still outright says "boost header files not found in..." etc...  I'm thinkin' suicide or homicide here...:guitar:

---

### Post by monktbd on 2007-11-26
about make install: did you sudo that command? because it tries to (write-)access folders owned by root.

about pointing avisynth to the correct dir: try pointing it just to /usr/include
i have a subfolder under my boost-1_35 folder called boost where the actual header files are.
so i guess avisynth searched then for a /usr/include/boost/boost folder in your case.

about having no /usr/lib/boost folder: i dont know if the precompiled libs are coming with the boost package you installed or whether there are totally precompiled ones. 

.... ok i looked at [http://packages.ubuntu.com/dapper/libdevel/](http://packages.ubuntu.com/dapper/libdevel/)
there a lot of boost libs are listed, like filesystem, regex, etc.. those are the ones that actually need to be built and are not just headers. so e.g. [the filesystem lib](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libboost-filesystem-dev&version=dapper&arch=i386)
should copy files to /usr/lib.

for your problem it is now important which boost libs are needed by avisynth, that should be listed within the avisynth documentation for building it. if you just build all libs yourself then you should not have a problem but building boost libs can take some time.

---

