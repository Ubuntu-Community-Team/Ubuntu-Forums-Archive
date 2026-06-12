---
title: "F-Spot 0.3.1 Install Gone Wrong...  Help Please?"
date: 2007-01-21
forum: General Help
---

### Post by SendDerek on 2007-01-21
Hello!

I am having some problems installing F-Spot 0.3.1 on 6.06, and I was hoping that some of you might be able to help me a little. 

Basically, the story is this:  I had F-Spot 0.1.1 installed once before, but decided I didn't like it so I uninstalled it through the package manager.  Well, I would like to give it yet another shot since there have been many improvements made.  So, I downloaded the program, made sure I had all the proper dependancies installed, compiled it, and ran the make and make install commands.  It worked perfectly.  But,  I soon realized that it hadn't asked me where to find the photos as it did the first time I installed it.  In fact, it still had some very old photos in directories that don't even exist anymore.  So, in my lack of wisdom, I decided that there was an old config file somewhere that needed to be deleted.  I did a make uninstall for the time and then searched for any files that had the word "f-spot" in them.  I deleted several files (5-7) and figured that would be good.  So, I then went to re-install f-spot with the ./configure, make, and make install commands (all in sudo),  Unfortunatly, I never made it to the make install command and I am stuck with this output from the make command (I have replaced my username with "<user>"):

```

libtool: install: warning: remember to run `libtool --finish /home/<user>/.f-spot/lib/f-spot'
make[2]: Leaving directory `/home/<user>/f-spot-0.3.1/libjpegtran'
make[1]: Leaving directory `/home/<user>/f-spot-0.3.1/libjpegtran'
Making install in libfspot
make[1]: Entering directory `/home/<user>/f-spot-0.3.1/libfspot'
make  install-am
make[2]: Entering directory `/home/<user>/f-spot-0.3.1/libfspot'
make[3]: Entering directory `/home/<user>/f-spot-0.3.1/libfspot'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/f-spot" || mkdir -p -- "/usr/local/lib/f-spot"
 /bin/sh ../libtool --mode=install /usr/bin/install -c  'libfspot.la' '/usr/local/lib/f-spot/libfspot.la'
libtool: install: error: cannot install `libfspot.la' to a directory not ending in /home/<user>/.f-spot/lib/f-spot
make[3]: *** [install-fspotlibLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/<user>/f-spot-0.3.1/libfspot'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/<user>/f-spot-0.3.1/libfspot'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/<user>/f-spot-0.3.1/libfspot'
make: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/<user>/f-spot-0.3.1/libfspot'
make: *** [install-recursive] Error 1

```
(/home/<user>/f-spot-0.3.1 is the directory that I have downloaded and unzipped the original files to.)

I have tried a make clean following a make uninstall and finally I tried to compile it yet again with the same error messages every time.

I know this is a eyefull, but I wanted to be detailed in my steps to getting to this problem.

Thank you for any help in advance!

-SendDerek

---

### Post by SendDerek on 2007-01-21
My second attempt:

I deleted the f-spot-0.3.1 folder that I was working out of and re-unzipped the freshly downloaded folder.

I ran ./configure no problems.  Ran make with no problems (sweet!).  Ran make install with no problems!  Finally, I opened f-spot through the applications menu with the same problem as before!  At least I have dugg myself out of this hole!

My problem is still I have photos that are outdated and the directories are non-existant, but the thumbnails are still viewable.  When I goto "import" my new photos, it freezes and I have to force quit.  Bummer.

I'll have to play around and browse around at any websites and see if I can figure it out...

---

