---
title: "SPDBV program"
date: 2005-06-21
forum: General Help
---

### Post by andrewL on 2005-06-21
Hi there,
  I have a program called SPDBV and I am having difficulty running it.  I have downloaded the program and unpacked it with sudo.  It is supposed to execute with the ./spdbv command and this is what I get:

/home/andrew/SPDBV/bin/spdbv.Linux: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

  On the SPDBV website, they have a linux hint posted but I don't think it applies.  The library they are mentioning is different.  Any help to solve this is appreciated.  

thanks,
ciao,
Andrew

:-)

This is the Linux help faq from the SPDBV website:


    * Error in loading shared libraries: libMesaGL.so.3. ...

    Why this
    The simple reason for this is that the newer Mesa now uses different names for the libraries than those with which SPDBV has been linked with. Apparently they are now called libGL.so and libGLU.so instead of libMesaGL.so and libMesaGLU.so.

    How to solve it
    The new Mesa is completely backward compatible and should not harm SPDBV from working properly. So there is no need to install an old Mesa version.
    Just a little hack is needed to get it work: if you can get root access to your linux box, make the following symbolic links from the new libraries to the old names:


ln -s  /usr/X11R6/lib/libGL.so.1.2.0 /usr/X11R6/lib/libMesaGL.so.3
ln -s  /usr/X11R6/lib/libGLU.so.1.2.0 /usr/X11R6/lib/libMesaGLU.so.3

then run  

/sbin/ldconfig

    to make the system remember this changes.

---

### Post by intangible on 2005-06-21
You're missing some stuff the program requires to run.

This will get you what you need, but it may require additional libraries after you install this one.
**sudo apt-get install libmotif3**
You'll have to have the multiverse enabled to get that package tho.
[https://wiki.ubuntu.com//HowToEnableTheMultiverseRepositoryInUbuntu](https://wiki.ubuntu.com//HowToEnableTheMultiverseRepositoryInUbuntu)

You can find which packages have files that you are missing by doing a search at the bottom of this page: [http://packages.ubuntu.com](http://packages.ubuntu.com)

Hope this helps.

---

### Post by andrewL on 2005-06-29
Hi there,

That got the program up and running.  Installing programs into ubunto is fairly easy.  I just don't know how to get them to run.  

That has helped me out tremendously.

thanks!
Andrew

:-)

---

### Post by intangible on 2005-06-29
The person who packaged the program (kindof like creating an installer) is the one who should make it install shortcuts in your menus.  If they didn't, you may have to create your own shortcuts.  You can usually start the program just by typing the program name in a terminal or in the Run Application box (under "Applications").

You need to install a program to manage the menus for you though if you want to add your own entries.  The most popular one for Ubuntu is called "Smeg" [http://ubuntuforums.org/showthread.php?t=38183](http://ubuntuforums.org/showthread.php?t=38183)

Hope this helped.

---

### Post by runlevel6 on 2005-11-23
I am having the exact same problem running [Swiss PDB viewer]("http://www.expasy.org/spdbv/"). Sad thing is, I can't find libmotif anywhere:

 # sudo apt-get install libmotif3
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libmotif3

A search in synaptic didn't get me anything either. Ideas muchly appreciated!

---

### Post by intangible on 2005-11-23
Have you enabled the Multiverse and Universe repositories?  If not, or you are not sure, follow the instructions here and then see if you can find libmotif3 (I see it in my packages list here with those repositories enabled): [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Bionic_Beefpile on 2006-02-13
I tried the fix above (installing libmotif3), and I still get the same error
> /home/#####/SPDBV/bin/spdbv.Linux: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

It seemed like libmotif installed just fine, so I'm not sure what is wrong. :-k

---

### Post by Bionic_Beefpile on 2006-02-21
I'm thinking that this has something to do with the library links that SPDBV mentions in the FAQ.  If I go to the properties of libmotif3 and look under installed files, I see (among others) this:
```
/usr/X11R6/lib/libMrm.so.3
/usr/X11R6/lib/libUil.so.3
/usr/X11R6/lib/libXm.so.3
```
The problem is that I'm not sure which of these should be linked to libMesaGL.so.3 and which should be linked to libMesaGLU.so.3 :confused:

::EDIT:: Tried this and it didn't work:
```
sudo ln -s  /usr/X11R6/lib/libXm.so.3 /usr/X11R6/lib/libMesaGL.so.3
sudo ln -s  /usr/X11R6/lib/libUil.so.3 /usr/X11R6/lib/libMesaGLU.so.3
sudo /sbin/ldconfig
```

---

### Post by irve on 2006-02-25
Found the solution:

```
$ sudo ln -s /usr/X11R6/lib/libXm.so.3 /usr/lib/libXm.so.3
```

(The program looks for the openmotif library in the wrong place.)

---

### Post by IronArjen on 2007-03-14
All of the above doesn t work.

I had installed another version I guess (libXm.so.3.0.2)  tried to link but nothing

I located another libXm.so.3 in my JRE directory tried to link, nothing.

Any idea?

---

### Post by davebridges on 2008-06-17
I get a similar error message

spdbv.Linux: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

has anyone gotten swiss pdb viewer to work in ubuntu?

---

### Post by garg on 2008-06-24
> **davebridges said:**
> I get a similar error message

spdbv.Linux: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

has anyone gotten swiss pdb viewer to work in ubuntu?

I'm getting the exact same error. Did you have any luck installing this?

---

### Post by davebridges on 2008-06-24
nope i ended up just using a windows machine for the modelling.  For other structure stuff I have been learning PyMol (which is in the repos)

---

### Post by garg on 2008-06-24
> **davebridges said:**
> nope i ended up just using a windows machine for the modelling.  For other structure stuff I have been learning PyMol (which is in the repos)

Thanks for the response. 

I even tried Wine. It runs but then it says "Cannot Open _Stuff_\Rotolib.aa

If I find something, I'll post it in this thread.

---

### Post by garg on 2008-06-24
This worked:

[http://forum.tuxx-home.at/viewtopic.php?f=10&p=4040](http://forum.tuxx-home.at/viewtopic.php?f=10&p=4040)

I downloaded: [http://packages.ubuntu.com/gutsy/i386/libx11-6/download](http://packages.ubuntu.com/gutsy/i386/libx11-6/download)

then ran:

dpkg -i libx11-6_1.1.1-1ubuntu4_i386.deb

And it started working. I don't know what else it broke though :)


edit:

Also got the following response from a friendly wine appdb admin:> 

Hi, you need to run it with the full path, then it starts fine e.g.

wine "c:\\spdbv\\spdbv.exe"

(if you extracted it in "c:\\spdbv"
We appreciate your help in making the Application Database better for all users.

---

