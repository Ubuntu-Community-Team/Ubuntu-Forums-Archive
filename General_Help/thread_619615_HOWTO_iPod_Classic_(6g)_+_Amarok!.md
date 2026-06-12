---
title: "HOWTO: iPod Classic (6g) + Amarok!"
date: 2007-11-21
forum: General Help
---

### Post by Ghostbear121 on 2007-11-21
Okay guys, there's a ton of "how do I get my awesome new iPod to work!" questions.  I spent a few hours on it when I should've been working... :)   So here's how:


1.  I use Amarok because it's pretty similar to iTunes in a lot of ways.  The version you can download from apt-get is perfectly fine.  (v1.4.7).  The trick to getting your "classic" iPod working isn't amarok, it's a library it uses called libgpod.

Just to add here, we all know Apple changed the hashing around on the new ipod itunesdb: basically if it isn't iTunes that's uploading songs, your ipod will display "no songs" and consider itself empty.  That's BS.  So, libgpod fixes this 'problem'.


2.  Go here:  [http://sourceforge.net/project/showfiles.php?group_id=67873&package_id=156254&release_id=553119]("http://sourceforge.net/project/showfiles.php?group_id=67873&package_id=156254&release_id=553119").  Download this file:  libgpod-0.6.0.tar.gz.  Save it to your desktop, your home folder, wherever.  I put it on my desktop.

3. Unzip it.  I use console commands:
```

cd Desktop/
tar -zxvf libgpod-0.6.0.tar.gz
cd libgpod-0.6.0

```
Don't change out of this directory 'till we're done.

4.  Now you've decompressed the source code for libgpod.  Before anything else, make sure you've got the required dependencies installed:
```

sudo apt-get install build-essential libglib2.0-dev libgtk2.0-dev libsgutils1-dev checkinstall

```
OK now: ```
sudo apt-get build-dep libgpod2
```
FYI: Build-dep installs all the required dependencies for a program, but not the program itself.  This is perfect, 'cause we don't WANT the version of libgpod that's on apt right now.  We want the one we're about to compile:

5.  Compile it!
```
./configure 
make
```

6. Now we build a debian install:
```
sudo checkinstall
```
You'll get a prompt that says:  "should I create a default set of package docs?"  Just press Enter to say YES.  On the next screen, type whatever description you'd like.  Maybe something like "Compiled libgpod-0.6.0".  Press enter again.  This is what will show up:

```

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ you@yourcomputer ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ libgpod ]
3 -  Version: [ 0.6.0 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ libgpod-0.6.0 ]
9 -  Alternate source location: [  ]
10 - Requires [ ]

Enter a number to change any of them or press ENTER to continue:

```
Type 2, press Enter.  Enter libgpod2 at the prompt.  It should now look like this:  2 -  Name:    [ libgpod2 ]

Press Enter to commit the changes.  The package will get automatically installed.

Okay one last thing:  we link the libraries:
```

sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.2
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.3

```

There!  Now your system has libgpod v0.6.0 installed. 

I uninstalled Amarok and reinstalled it fresh, just to be 'safe'.  
```
sudo apt-get remove amarok; sudo apt-get install amarok
```


Next, plug in your iPod.  KDE or Gnome (I use Kubuntu.. so KDE) will see your device and mount it.  
```
df
```
Find your ipod in that list.  Mine looked like this:
/dev/sda1  /media/IPOD

There's a slick little script you have to run that came with libgpod:
```

ipod-read-sysinfo-extended /dev/sda1 /media/IPOD

```
**Make sure you swap out /dev/sda1 with whatever your ipod is actually connected to!**
This script will add an XML file called sysinfo-extended onto your ipod's config directory; it's what libgpod uses to 'see' your ipod's firewire device ID, serial number, etc.

Okay, now fire up Amarok.  Under the Devices tab, there will be a dropdown menu (top-left area of the window).  Move down the menu, select Classic ->  (Your Ipod).  Mine's an 80gb Black.  

That should be it!  Try transferring a couple of tracks, then disconnect it properly.  You should see your tracks on your ipod now.



Hope this solves some confusion.  Enjoy your new 6G iPod!

---

### Post by Berryjiveuptown5 on 2007-11-21
Holy crap...if this actually works, I will be soooo grateful!! I've spent at least 36 hours (i'm a noob to ubuntu/linux) trying to get my new ipod to work via will's backdot and paul's packages, with no success.  Gonna go try this now!!

---

### Post by Berryjiveuptown5 on 2007-11-21
unfortunately, it's asking me for the gutsy cd's while i'm downloading libgpod 6.0 (not sure why, though).   i'm going to have to try and re-download gutsy, as both of my disks are broken.  let you know then.

---

### Post by D0minik on 2007-11-22
> **Berryjiveuptown5 said:**
> unfortunately, it's asking me for the gutsy cd's while i'm downloading libgpod 6.0 (not sure why, though).   i'm going to have to try and re-download gutsy, as both of my disks are broken.  let you know then.No, you don't have to. Simply disable the CD-ROM repository: [https://help.ubuntu.com/community/Repositories/Ubuntu#head-1d5d8ce5319742aea968112701e3a2292ac7d187](https://help.ubuntu.com/community/Repositories/Ubuntu#head-1d5d8ce5319742aea968112701e3a2292ac7d187)

---

### Post by runsink on 2007-11-22
Good job GB !

I tried it, but I'm getting a error at "sudo checkinstall"

All seems to go fine, I have no errors at configure or make, but when it is installing libaries from ".libs/" I get an error like this :

> test -z "/usr/local/lib/python2.5/site-packages/gpod" || mkdir -p -- "/usr/local/lib/python2.5/site-packages/gpod"
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  '_gpod.la' '/usr/local/lib/python2.5/site-packages/gpod/_gpod.la'
libtool: install: warning: relinking `_gpod.la'
(cd /home/joost/install/libgpod-0.6.0/bindings/python; /bin/bash ../../libtool  --tag=CC --mode=relink gcc -g -O2 -o _gpod.la -rpath /usr/local/lib/python2.5/site-packages/gpod -module -avoid-version _gpod_la-gpod_wrap.lo -lgobject-2.0 -lglib-2.0 -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 ../../src/libgpod.la )  
gcc -shared  .libs/_gpod_la-gpod_wrap.o  -L/usr/lib -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -L/usr/local/lib -lgpod  -Wl,-soname -Wl,_gpod.so -o .libs/_gpod.so
/usr/bin/install -c .libs/_gpod.soT /usr/local/lib/python2.5/site-packages/gpod/_gpod.so
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.so': No such file or directory
/usr/bin/install -c .libs/_gpod.lai /usr/local/lib/python2.5/site-packages/gpod/_gpod.la
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.la': No such file or directory
/usr/bin/install -c .libs/_gpod.a /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.a': No such file or directory
chmod 644 /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
ranlib /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
ranlib: could not create temporary file whilst writing archive: No more archived files
make[5]: *** [install-gpodLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings/python'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings/python'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings/python'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings/python'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

What does is mean by .libs ? I can not see it with "ls -a"
If I run that line by hand I get :

>  sudo /usr/bin/install -c .libs/_gpod.soT /usr/local/lib/python2.5/site-packages/gpod/_gpod.so
/usr/bin/install: cannot stat `.libs/_gpod.soT': No such file or directory


Any idea what is going wrong ?

Thanks,
Joost

---

### Post by Rustyk1 on 2007-11-22
Hey, great tutorial. However, I've been having some probelms. I just got a new ipod classic 80Gb today (Firmware 1.0.2) and have being trying to set it up with ubuntu. I managed to get it showing up in amarok and even synced all my music with it. However, when i disconnected the ipod it said there was no music on it, just 30gb of 'Other' data. 

I thought this may be because I needed to do my initial setup in windows so I did a restore and initial setup again under xp, however it didn't make any difference. 

Does anyone have any idea where I'm going wrong? Or why it won't work?

Thanks in advance

Rustyk1

---

### Post by tomauty on 2007-11-22
Hopefully people will see this so there is more feedback. Works for me.

---

### Post by citizenkeith on 2007-11-22
> **Rustyk1 said:**
> Hey, great tutorial. However, I've been having some probelms. I just got a new ipod classic 80Gb today (Firmware 1.0.2) and have being trying to set it up with ubuntu. I managed to get it showing up in amarok and even synced all my music with it. However, when i disconnected the ipod it said there was no music on it, just 30gb of 'Other' data. 


Same here. Running Gutsy. Tried Amarok and Rythmbox with similar results.

---

### Post by itmanvn on 2007-11-23
Same here! OMG !!! where's my music

---

### Post by D0minik on 2007-11-23
I have the same problem. Think that's because of the new 1.0.2 firmware :/

At the moment I'm syncing my iPod via iTunes in a VirtualBox. The non-OSE of VirtualBox supports USB devices. Works very well for me, especially in VirtualBox' "seamless mode" :-)

---

### Post by D0minik on 2007-11-23
> **runsink said:**
> Good job GB !

I tried it, but I'm getting a error at "sudo checkinstall"
Try "sudo make install" - worked for me :-)

Important: set your iPod in AmaroK to the correct version ("classic silver 80GB") or the files copied via AmaroK won't show up on your iPod!

---

### Post by Rustyk1 on 2007-11-23
> **D0minik said:**
> Important: set your iPod in AmaroK to the correct version ("classic silver 80GB") or the files copied via AmaroK won't show up on your iPod!

I've tried this and it still does not seem to work. My ipod accepts the files fine but then, when i disconnect it, it just says it's got many GBs of 'Other' data. On reconnection to my XP install (in vmware), iTunes detects that it cannot read from the iPod so I have to do a restore. I'v eonly had my ipod a day and done about 4 restores!

I guess I'll just have to stick to using it in my virtual XP install, rubbish.

---

### Post by D0minik on 2007-11-23
> **Rustyk1 said:**
> I'v eonly had my ipod a day and done about 4 restores!

I guess I'll just have to stick to using it in my virtual XP install, rubbish.Both _exactly_ the same for me.. this really, really sucks. I want to start *using* my iPod :/

---

### Post by citizenkeith on 2007-11-23
> **D0minik said:**
> Both _exactly_ the same for me.. this really, really sucks. I want to start *using* my iPod :/


Yup. Thank you, Apple. :roll:

I may try the Virtual Box solution for now. But in the meantime, I will continue kicking myself for buying this damn thing.

---

### Post by runsink on 2007-11-23
Ghostbear121, what firmware version is in your ipod ? 

(It took me some time, but it is under settings > about -> and then press the center button 2 times).

I have the 80Gb white, I followed the howto and also have the problem that there is no music on the device. I will look in to it tonight.

Thanks

---

### Post by runsink on 2007-11-23
I can sync the music now, I can even see it. Not sure if it is reproducible, so try at your own rysc.
I'm using ipod firmware 1.0.2

First with the ipod mounted see what is in the file SysInfo, like :

```
 cat /media/[ipodname]/iPod_Control/Device/SysInfo
```

there should be something like :

> ModelNumStr: xA448
FirewireGuid: 0x000A27003462572D


If the FirewireGuid is missing something went wrong with the ipod-read-sysinfo-extended command. Try running it with sudo and see if that changes anything, I didn't bother and tried the manual method. The manual method is described in the libgpod source tree, look at the file README.SysInfo.

After that I did an :

```
sudo apt-get remove libgpod2
```

I answered yes if it could remove all the other stuff for now.

the I went back to the source tree and did the following things :

```
make clean
./configure
make
sudo make checkinstall
```

option 2, change to "libgpod2"

```
sudo apt-get install amarok
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.2

After that I sync some new music that wasn't on the ipod before and now I have music !

Again, I'm not sure what the real problem was, before I started the howto I already had amarok and gtkpod for my ipod nano, so the libgpod2 was already on my computer. I think that was also the reason that the first time my "sudo checkinstall" failed at installing the libaries.

Keep posting you problems !

```

---

### Post by bobandiara on 2007-11-23
Hello, guys!

I tried to install libgpod2 with ```
sudo checkinstall
``` and got the same error as runsink. 
Then, I thought "what if I try to build a package with this one?" and it worked for me. The command for this is ```
sudo checkinstall -D
``` with a capital "D".
It automatically builds the .deb package and installs it. Right now, I'm synchronizing my iPod classic 80 GB with Amarok running over Gutsy. Let's see what will happen next...

Oh, and by the way, thank you Ghostbear121 for this awesome HowTo!!!!:)

---

### Post by bobandiara on 2007-11-23
Yeah!!!

It successfully added the songs to my iPod!!!!

Now i'm gonna kick iTunes out of my life!!!

---

### Post by rye_ on 2007-11-24
thanks for this, I'm trying it now.
The only difference will be that I'll be using rhythmbox.

Ryan

---

### Post by Hoppiesbox on 2007-11-24
> **runsink said:**
> Good job GB !

I tried it, but I'm getting a error at "sudo checkinstall"

All seems to go fine, I have no errors at configure or make, but when it is installing libaries from ".libs/" I get an error like this :



What does is mean by .libs ? I can not see it with "ls -a"
If I run that line by hand I get :

> 
test -z "/usr/local/lib/python2.5/site-packages/gpod" || mkdir -p -- "/usr/local/lib/python2.5/site-packages/gpod"
/bin/bash ../../libtool --mode=install /usr/bin/install -c '_gpod.la' '/usr/local/lib/python2.5/site-packages/gpod/_gpod.la'
libtool: install: warning: relinking `_gpod.la'
(cd /home/joost/install/libgpod-0.6.0/bindings/python; /bin/bash ../../libtool --tag=CC --mode=relink gcc -g -O2 -o _gpod.la -rpath /usr/local/lib/python2.5/site-packages/gpod -module -avoid-version _gpod_la-gpod_wrap.lo -lgobject-2.0 -lglib-2.0 -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 ../../src/libgpod.la )
gcc -shared .libs/_gpod_la-gpod_wrap.o -L/usr/lib -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -L/usr/local/lib -lgpod -Wl,-soname -Wl,_gpod.so -o .libs/_gpod.so
/usr/bin/install -c .libs/_gpod.soT /usr/local/lib/python2.5/site-packages/gpod/_gpod.so
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.so': No such file or directory
/usr/bin/install -c .libs/_gpod.lai /usr/local/lib/python2.5/site-packages/gpod/_gpod.la
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.la': No such file or directory
/usr/bin/install -c .libs/_gpod.a /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.a': No such file or directory
chmod 644 /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
ranlib /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
ranlib: could not create temporary file whilst writing archive: No more archived files
make[5]: *** [install-gpodLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings/python'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings/python'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings/python'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings/python'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings'
make: *** [install-recursive] Error 1

**** Installation failed. Aborting package creation.

Cleaning up...OK

Bye. 


Any idea what is going wrong ?

Thanks,
Joost

I solved this problem by doing a 
```

sudo apt-get remove libgpod2

```
then deleted the directory I was compiling in, re-extracted libgpod2 from the .tar.gz - and then again, from the source directory
```

./configure
make
sudo checkinstall

```

I am still having 1 problem - I don't know how to get media that amarok can't read on there...I've got a video and a few images I'd like to add. I'm going to give Thin Liquid Film a try for the conversion of the video - I've got a feeling that will work. UGH - am I going to have to use gtkpod to upload the images? 1 more program at this point seems like a mountain of a pain in the @$$ ;)

oh, GHOSTBEAR - you rock :) Thanks for taking the time out of work for this...you KNOW we'd all do it for you, lol

---

### Post by rabanomen on 2007-11-25
I dont know how i do but ..

```
 Done. The new package has been installed and saved to

/home/username/Escritorio/libgpod-0.6.0/libgpod_0.6.0-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r libgpod

```


:D:D:D:D

sudo apt-get remove libgpod2
 make clean
./configure
make
sudo make checkinstall ( give me an error )
sudo chekinstall ( give me an error )
sudo chekinstall -D
RUN !

---

### Post by mhp888 on 2007-11-25
> **D0minik said:**
> Try "sudo make install" - worked for me :-)

Important: set your iPod in AmaroK to the correct version ("classic silver 80GB") or the files copied via AmaroK won't show up on your iPod!

Bought today the iPod Classic 160Gb but have problems as many others,,,
I installed libgpod2 and followed all tips in this thread which apparently worked ok. But I still can't get music on the iPod. 
1. In Amarok, I can't select any Classic Ipods. Only Videos.
2. The iPod is on Firmware 1.0. Could it be that? How do I change the firmware via Ubuntu?

---

### Post by runsink on 2007-11-25
mhp888, are you on Feisty or on Gutsy ? Did you remove the original libgpod2 from your system ?

---

### Post by runsink on 2007-11-25
Okay, seems like music transfer is working nicely for most now. Is anybody successful at transferring the cover art ? I don't have them embedded in the mp3, just the ones that amarok found, how (if) do I transfer them to the ipod.

I tried to recompile libgpod2 after I installed libsgutils from the repo, but that didn't make a difference.

Thanks,
Joost

---

### Post by mhp888 on 2007-11-25
> **runsink said:**
> mhp888, are you on Feisty or on Gutsy ? Did you remove the original libgpod2 from your system ?

I am on Gutsy. Did not remove the original libgpod2 at the first try, but tried later to remove it before installing everything again (libgpod2 and amarok)... 
Hope it will work soon, my iPod is useless right now :confused:

---

### Post by ratatek on 2007-11-25
Following this procedure I was able to get my 6G working with Rhythmbox (at least with music, that's all i've tried).  Thanks guys.

---

### Post by runsink on 2007-11-26
mhp888, I don't think it would hurt to go over it once more. Go to the folder where lipgpod 0.6.0 is unpacked, do at least the following :

```
sudo apt-get remove libgpod2
```

Check if you have all the dependencies as described in the 1st post.

make clean
./configure
make
sudo checkinstall

after that link the libaries again and run the ipod-read-sysinfo-extended command with the right devices

stop amarok and start it again, look if anything changed. If it doesn't, look in the README.SysInfo and
see what is in the /media/[ipod-name]/iPod_Control/Device/SysInfoExtended

Let us know if it works

---

### Post by mhp888 on 2007-11-26
runsink, 

Thanks very much for your time! I think I got one step further (I forgot to rename to libgpod2, as per Ghostbear121's post) as I now can find the Classic 160Gb Black in Amarok. I also added this post-disconnect command:

rm /media/IPOD/iPod_Control/iTunes/iTunesLock;rm "/media/IPOD/iPod_Control/iTunes/Play Counts";gnome-eject -t -d /dev/sdb1

Found here: [http://ubuntuforums.org/showthread.php?t=497201]("http://ubuntuforums.org/showthread.php?t=497201")

It disconnects correctly but then the iPod freezes. It gives a 'click' like the hard drive parks. The Apple logo appears and after a while it starts again but the right hand display is white and I can't move the cursor...

---

### Post by runsink on 2007-11-26
Hi Mhp888,

I read here :

[http://www.nabble.com/artworkdb-broken-for-nano-3g---ipod-freezes-t4574628.html](http://www.nabble.com/artworkdb-broken-for-nano-3g---ipod-freezes-t4574628.html)

that there right site lockup may happen when something is wrong with the artworkdb.
It seems that you tried quit a bit, is it possible for you to recover it from a windows or apple machine and try again.

After recovery, be sure to re apply ipod-read-sysinfo-extended or do it manually as described in README.SysInfo before launching amarok

Joost

---

### Post by mhp888 on 2007-11-26
Hi runsink,

I actually just booted Ubuntu a couple of times and tried to reset the iPod and suddenly it worked - but one time only ](*,)
It does seem something is messed up with all my experimenting so I will bring it to a friend tomorrow to give it a reset and a firmware upgrade.

Thanks for your help. I will post the result tomorrow.

---

### Post by mhp888 on 2007-11-27
The firmware upgrade did the job. Everything is working now!
Many thanks for all inputs!

---

### Post by runsink on 2007-11-27
Good job !! Did you go from 1.0.0 to 1.0.2 or did you came from 1.0.1 ?

Joost

---

### Post by mhp888 on 2007-11-27
Straight from 1.0.0 to 1.0.2

---

### Post by citizenkeith on 2007-11-27
> **mhp888 said:**
> The firmware upgrade did the job. Everything is working now!
Many thanks for all inputs!

I assume you're talking about Apple's official firmware for the iPod classic, correct?

---

### Post by rkyve on 2007-11-27
This is an addon to the previous instructions.
This is what it took to get the new iPOD nano (3rd gen) working on my system. [Kubuntu 7.10]

EDIT//NOTE:
  After trying the instructions from the original post, the 'ipod-read-sysinfo-extended' command would not work (command not found). 
I would uninstall libgpod ('sudo apt-get remove libgpod2') first before re-trying. Then continue w/ the following steps:

1.  Download libgpod-0.6.0.tar.gz
```

cd ~/Desktop
wget http://superb-east.dl.sourceforge.net/sourceforge/gtkpod/libgpod-0.6.0.tar.gz

```

2.  Uncompress libgpod...
```

tar -zxvf libgpod-0.6.0.tar.gz
cd libgpod-0.6.0

```
* Don't change out of this directory 'till we're done.

4.  Attain dependencies before install:
```

sudo apt-get install build-essential libglib2.0-dev libgtk2.0-dev libsgutils1-dev checkinstall

```

5. Build dependencies for libgpod, but don't install libgpod:
```

sudo apt-get build-dep libgpod2

```

6.  Compile libgpod!
* should still be in ~/Desktop/libgpod-0.6.0/ directory
```

./configure 
make

```

7. Now we build a debian install:
```

sudo checkinstall

```
You'll get a prompt that says:  "should I create a default set of package docs?" 
Just press Enter to say YES.
On the next screen, type "Compiled libgpod-0.6.0".
Press enter again.  This is what will show up:

```

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ you@yourcomputer ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ libgpod ]
3 -  Version: [ 0.6.0 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ libgpod-0.6.0 ]
9 -  Alternate source location: [  ]
10 - Requires [ ]

Enter a number to change any of them or press ENTER to continue:

```

Type 2, (to edit Name) press Enter.  
Enter "libgpod2" at the prompt (w/o Quotes).  It should now look like this:  2 -  Name:    [ libgpod2 ]

Press Enter to commit the changes.  The package will get automatically installed.

8. For some reason this didn't seem to install the package for me.
    ( 'ipod-read-sysinfo-extended' command not found -- wasn't installed w/ libgpod2)
So i had to run the following command to really install it apparently
```

sudo make install

```

9. Okay one last thing:  we link the libraries:
(it is right: .3 -> .2 and .3 -> .3 )
```

sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.2
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.3

```

Now your system has libgpod v0.6.0 installed!!

10. Remove/Install Amarok (to be safe):
```

sudo apt-get remove amarok
sudo apt-get install amarok

```
or
```

sudo aptitude reinstall amarok

```
if you have aptitude installed

11. Plug in your iPod.  Wait for it to be recognized (ie shown on desktop).. 
  (If the icon on the desktop doesn't show a small triangle in the corner, right-click the icon and select 'Mount'.)
```
df
```
Find your ipod in that list.  Mine looked like this:
[INDENT]/dev/sda1  /media/IPOD[/INDENT]

(Mine actually was /media/iKJK from naming it as such when restoring it with iTunes)

12. There's a slick little script you have to run that came with libgpod:
```

ipod-read-sysinfo-extended /dev/sda1 /media/IPOD

```
**Make sure you swap out /dev/sda1 with whatever your ipod is actually connected to!**
This script will add an XML file called sysinfo-extended onto your ipod's config directory; it's what libgpod uses to 'see' your ipod's firewire device ID, serial number, etc.

[INDENT]
 In my case I entered
 ```

 ipod-read-sysinfo-extended /dev/sda1 /media/iKJK
 
```
 and got an error that it couldn't mount Device

 But entering the same with an appended / worked!
 ```

 ipod-read-sysinfo-extended /dev/sda1 /media/iKJK/
 
```
[/INDENT]


13. On my system this worked perfectly.
 On a friends system i had to 'sudo' that last command -- unsure why.

14. Start Amarok.
 i. Devices tab (bottom left usually)
 ii. Near top of Devices Panel, select IPOD (may be hidden w/ >> arrows) & select your iPod model.

15. Transfer songs to iPod.
 Click-Drag-Drop songs to playlist or directly to Devices tab and from playlist to device.
  This will Queue the songs for transfer.
 Click the Transfer button.

16. Disconnect iPod from Amarok
 the disconnect command wouldn't unmount my iPod, so i right-clicked the desktop icon and 'Safely Remove' it.

17. Phyiscally remove iPod from USB.

You should see your tracks on your iPOD now!!

Mainly the largest change from the Ghostbear121's post is that i needed to run the 'make install' command as well to get the 'ipod-read-sysinfo-extended' command to work. This needed to by done on my system as well as a friends' to get it working -- otherwise 'command not found' error.

Hopefully this is helpful for anyone getting stuck at the spots i got stuck at.

---

### Post by mhp888 on 2007-11-27
> **citizenkeith said:**
> I assume you're talking about Apple's official firmware for the iPod classic, correct?

Correct, did it through iTunes at a friends computer.

---

### Post by mhp888 on 2007-11-27
As mentioned above, everything works perfect for me, including cover flow. That is... almost everything, as I have not managed to transfer a video podcast. Anybody who knows how this works in Amarok? Is it actually supported? I can download the podcast, but can not view it in Amarok nor transfer it.

---

### Post by fullbleedboy on 2007-11-28
Hi I've been following this thread since my new 160GB iPod Classic wasn't working.  I followed the OP's instructions to no avail.  I was having the same problems everyone else-- after Amarok transferred the files, they'd "disappear" upon disconnect.

I noticed that there was no "iPod Classic" option in Amarok.  So I suspected a problem with the libgpod install.  Everything looked fine, but since I was using Fiesty, both libgpod1 and the newly compiled libgpod2 were installed.  My Amarok was a Fiesty-backported version of 1.4.7.  *ldd /usr/bin/amarokapp | grep gpod* didn't return anything so I did an strace to figure out which it was using:

```
# strace -f -o broken amarok
# grep 'libgpod' broken
open("/usr/lib/libgpod.so.1", O_RDONLY) = 26
```

So Amarok was obvoiusly still using libgpod1.  I tried re-installing both the stock Fiesty 1.4.5 and the Fiesty-backported 1.4.7 without luck.  I even tried to see if libgpod2 was backward-compatible by linking libgpod.so.1 to libgpod.so.3, but that caused Amarok to segfault (no surprise).  So it seemed all Fiesty builds of Amarok are coded for libgpod1?

Finally, I bit the bullet and decided to upgrade to Gutsy. Now everything works!  So if anyone else is spinning their wheels on Fiesty, you probably should upgrade.  Or try and re-compile Amarok (haha!)  I didn't see anyone else mention this, so HTH.

---

### Post by denisesballs on 2007-11-29
Before I buy one of these, do you have to run that script every time you plug the new iPods in, or just once?

---

### Post by steven_r on 2007-11-30
fallowed your instructions but when i got to name the doc step you reply yes then give description and end it the description with empty line or EOF. well when i did that i named the doc Compiled libgpod-0.6.0 but nothing happend what do i do

---

### Post by runsink on 2007-12-03
What do you mean steven_r ?

Just enter the description like you did, press enter (Now you have the empty line) and press enter again, this tells the program to continue. After that you can follow the howto like normal.

Joost

---

### Post by CaptainSumo on 2007-12-04
I have followed everything to the letter in this post now (twice!), and I'm convinced that everything is running against the correct library. However, there is no 'iPod Classic' option in the Amarok settings, and every time I connect the iPod, it makes my music unplayable. I've tried Gtkpod, with the same results.

I'm wondering whether the fact I'm on AMD64 Gutsy could have any any influence on this. Has anyone else got this to work?

I'm running:
iPod classic 80Gb Silver.
iPod firmware 1.0.2         (restored from Vista several times now)
Kubuntu Gutsy AMD64    (clean Gutsy install with Ubuntu Studio metapackages added later)

Has anyone else struggled with any of the above combinations?

(It doesn't help that you have to actually connect the iPod before you can see the possible models in Amarok. By then, it's already too late to stop a sync taking place!)

---

### Post by fullbleedboy on 2007-12-04
CaptainSumo, if you're running a 64-bit kernel, you might have forgotten to link against your /**usr/lib64** instead of **/usr/lib**.

so...

```
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.2
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.3

```

becomes...

```
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib64/libgpod.so.2
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib64/libgpod.so.3

```

I haven't ever installed x86_64 ubuntu, so I dunno if thats all you'll have to do.  HTH.

P.S. If you still can't verify which library path it should use, do an strace and grep for *libgpod*

```

# strace -f -o amarok.strace.log amarok
```

---

### Post by Berryjiveuptown5 on 2007-12-04
Btw guys, version 1.03 is out.  Anyone seen any results?  Afraid to mess with it.

---

### Post by CaptainSumo on 2007-12-05
Thank you fullbleedboy for taking the time to respond. However, I've discovered the problem. Daft old me had only cut and pasted 15 of the 16 characters from the firewire id. I'm feeling kinda stupid right now! 

So, linking against **/usr/lib/** works fine. Everything else works great on 64 bit, and ignore my previous post.

I also haven't had the nerve to upgrade to the 1.0.3 firmware yet!

---

### Post by ColombianGold on 2007-12-06
> **runsink said:**
> Good job GB !

I tried it, but I'm getting a error at "sudo checkinstall"

All seems to go fine, I have no errors at configure or make, but when it is installing libaries from ".libs/" I get an error like this :

test -z "/usr/local/lib/python2.5/site-packages/gpod" || mkdir -p -- "/usr/local/lib/python2.5/site-packages/gpod"
/bin/bash ../../libtool --mode=install /usr/bin/install -c '_gpod.la' '/usr/local/lib/python2.5/site-packages/gpod/_gpod.la'
libtool: install: warning: relinking `_gpod.la'
(cd /home/joost/install/libgpod-0.6.0/bindings/python; /bin/bash ../../libtool --tag=CC --mode=relink gcc -g -O2 -o _gpod.la -rpath /usr/local/lib/python2.5/site-packages/gpod -module -avoid-version _gpod_la-gpod_wrap.lo -lgobject-2.0 -lglib-2.0 -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 ../../src/libgpod.la )
gcc -shared .libs/_gpod_la-gpod_wrap.o -L/usr/lib -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -L/usr/local/lib -lgpod -Wl,-soname -Wl,_gpod.so -o .libs/_gpod.so
/usr/bin/install -c .libs/_gpod.soT /usr/local/lib/python2.5/site-packages/gpod/_gpod.so
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.so': No such file or directory
/usr/bin/install -c .libs/_gpod.lai /usr/local/lib/python2.5/site-packages/gpod/_gpod.la
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.la': No such file or directory
/usr/bin/install -c .libs/_gpod.a /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.a': No such file or directory
chmod 644 /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
ranlib /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
ranlib: could not create temporary file whilst writing archive: No more archived files
make[5]: *** [install-gpodLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings/python'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings/python'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings/python'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings/python'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/joost/install/libgpod-0.6.0/bindings'
make: *** [install-recursive] Error 1

**** Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


What does is mean by .libs ? I can not see it with "ls -a"
If I run that line by hand I get :



Any idea what is going wrong ?

Thanks,
Joost

Great tutorial, I finally got ot working!!! I was too getting this error, my problem was that my dependencies weren't being built...some URI error was appearing. I was able to solve it by editing my sources.list

copy the repositorie lines that are being used and add -src after deb, to the copy...something like this:

sudo gedit /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse

This did it for me. Hope it helps anybody. After that dependencies were fetched and built correctly.

Just follow the howto its pretty straight forward. 

The other thing is to use:

sudo checkinstall -D

Hope this solves it for someone.
Thanks for the howto!!!

CG
:grin:

---

### Post by Wobblybob on 2007-12-07
I'm using Gutsy 7.10 on an Intel PC and my iPod is an 80GB Classic with firmware 1.0.2, I can now use Amarok to upload music and GTKpod-acc to upload my video and all goes well and goodbye to itunes & windows. I've only been using linux for a few months now, I moved after 30+ years of windows as the thought of a move to Vista was the last straw. ubuntu is great and the forums the best.

Thanks guys for your help, great stuff, it took me a couple of days and a little help from the following [[COLOR="Purple"]**post**[/COLOR]]("http://ohioloco.ubuntuforums.org/showthread.php?t=611404&page=2"). I had all of the problems listed above and finally added the firmware id manually which worked for me. [I may even try to do the same on the laptop now!]

now all we need is a way of uploading images but that's not a major problem.

Thanks again.

---

### Post by zsugiart on 2007-12-07
Guys, did any of you manage to transfer album arts/covers into your iPod? 

I can transfer songs etc OK, but I can't transfer them artworks - I am using amarok. 

Pls let me know if anyone can do this :)

---

### Post by rkyve on 2007-12-08
> **denisesballs said:**
> Before I buy one of these, do you have to run that script every time you plug the new iPods in, or just once?

Short Answer: No,
Once you run these commands and get Amarok working w/ the new libgpod that's all. The selection of iPod models changes from the previous libgpod to a new style. The old style was selecting by generation (about 5 options) and the new style is selecting the iPod by model, then by generation.  

However, for each Nano (for example) you own or if a friend wants to use his on yours, you'll have to run the
```
ipod-read-sysinfo-extended
```
command to get each new nano working w/ Amarok.

---

### Post by Wobblybob on 2007-12-08
> **zsugiart said:**
> Guys, did any of you manage to transfer album arts/covers into your iPod? 

I can transfer songs etc OK, but I can't transfer them artworks - I am using amarok. 

Pls let me know if anyone can do this :)

I added all my album art before upload using EasyTag, then cover art and cover flow worked on my iPod classic 80GB.

---

### Post by bomanizer on 2007-12-09
Hello all!

First of all, let me point out that I managed to make my Ipod to sync with amarok by using this methoid.

Here are my findings:

1. works with firmware version 1.0.3, Ipod Classic, black 80gb (configured using Itunes + Windows XP)

2. There's a thread about editing the Firewire-id in  /media/*something*/iPod_Control/Device/SysInf. This is a no-no, in my opinion. I kept the file as is and would recommend others to do so.

I've got cover art, but video transfer is still untested.

---

### Post by djdjules on 2007-12-11
I understand that Amarok 1.4.8 is necesary along with libgpod 0.6.0 for the transfers to work.
Will there be a release of Amarok 1.4.8 in the Feisty repos?
Is there a way to get the tranfer working with Feisty.

---

### Post by CaptainSumo on 2007-12-14
> **Wobblybob said:**
> I've only been using linux for a few months now, I moved after 30+ years of windows as the thought of a move to Vista was the last straw. 

30 years! I thought Windows 1.0 came out in 1985.

---

### Post by fjgaude on 2007-12-14
> **CaptainSumo said:**
> 30 years! I thought Windows 1.0 came out in 1985.

So it's 22 years... and let's say, that's enough.

---

### Post by Wobblybob on 2007-12-14
20 odd years then, so old timers disease is  setting in, I've spent too many years using Windows and very happy to see the back of it.

---

### Post by iron_maiden89b on 2007-12-15
Thank you!

---

### Post by jdbausch on 2007-12-16
I've been playing with this since I got an 80GB classic on tuesday.  I'm no expert on this stuff, so I'm guessing I've done some part incorrectly.



I've followed the various instructions on this thread, and I think I should be working, but no.

I was unable to get the script:
ipod-read-sysinfo-extended

to ever work, so I populated that file by hand.

other than that things went well, except it does not work:


in amarok when the ipod gets plugged in I get an error:

KLibLoader could not load the plugin:
libamarok_ipod-mediadevice

Error message:
libgpod.so.2 cannot open shared object file: no such file or directory



also, when I plug in the ipod, rythmbox opens with an error:
plugin error
unable to activate plugin portable players - iPod


any guess/assistance  as to what I've done incorrectly?

also, how would one remove the changes made by these various instructions and go back to the version of libgpod that comes in the gutsy repos?

thanks

---

### Post by zygut on 2007-12-19
When I plug in my ipod nano 3rd gen, it gets mounted read-only, so I can't edit that FirmwareID file. dmesg has the following:

hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only
hfs: filesystem is marked journaled, leaving read-only

---

### Post by runsink on 2007-12-19
It is hfs formatted. It would be better (or mandatory ?!) to format it to fat.
Hook it up to iTunes in a windows machine and let it convert the ipod.

Is this ipod out of the box ?

Joost

---

### Post by witkows6 on 2007-12-19
I've got an Ipod nano 3rd gen. and I've also done everything in this thread and still cannot get it to work.  I'm new to Ubuntu and don't understand why there isn't a fix for the most popular music player on the planet.  Any help out there?

---

### Post by zygut on 2007-12-19
> **runsink said:**
> It is hfs formatted. It would be better (or mandatory ?!) to format it to fat.
Hook it up to iTunes in a windows machine and let it convert the ipod.

Is this ipod out of the box ?

Joost

I dont have a windows box, but I have a mac, can  I convert it that way, or some other way? It was hooked up to a mac for a second, but itunes said it needed a newer version so it didn't do anything

---

### Post by runsink on 2007-12-19
Hi,

You can maybe Google for it, but I doubt that it would be easy. I'm not sure how they are delivered these days.
I can not speak for you situation, but the easiest way seems to find a windows machine anywhere, put itunes on it, convert, and remove it again. Where are you located ? maybe somebody here on the forum can offer you to convert it.

Joost

---

### Post by runsink on 2007-12-19
hi Zygut,

I googled around a bit and did not find much. I remember in the earlyer days that you could dd the firmware off the disk, fdisk and format it to fat32 and then dd the firmware back. But I'm not to sure if that is a good idea. Only post I found about that is for 3g 'classic' ipods.

Is it possible that you go back to where you purchased it or go to a apple store to covert it ?

Joost

---

### Post by apd on 2007-12-23
pisken@gizmo:~/libgpod-0.6.0$ ipod-read-sysinfo-extended /dev/sda1 /media/IPOD
Couldn't read xml sysinfo from /dev/sda1

this is what it says when i´m trying to run the sysinfo-extended command.
Clues any1?
this thread will eventually solve it for me but goosh not whitout bruises!!

---

### Post by apd on 2007-12-23
i also tried to change my repositories cos i were told to add some sources to my sources.list, did not change a thing. Right now im kinda wondering if i meeesed up my sources.list by changing and saving the changes... well easy fix. anyhow i´m stuck with a 80G Classic that does´nt work. :(

---

### Post by dummy_load on 2007-12-23
apd:
if it says Couldn't read xml ... it probably means the device isn't mounted where the command is looking.  I had to change mine from /devsda1 to /dev/sdc1.  You can see all of the available drives with
sudo fdisk -l
and mount will show which of those are mounted and where.

as far as your sources are concerned, if you start up the synaptic package manager, you will have the option to add sources from  Settings>Repositories menu.



Note to everyone.  I have tried a million times over the fall to get this to work.  This is the first tutorial that actually worked for me.  I'm totally psyched!  There was a small problem with the sudo checkinstall error mentioned earlier.  This was solved with d0minick's sudo make install suggestion followed by another sudo checkinstall.

SUCCESS AT LAST, YEE HAW!

---

### Post by lukem on 2007-12-23
Does anyone know if this will work with Dapper?  I'm unable do get all the dependancies and I wonder if it is because I am running Dapper.  

Thanks

---

### Post by Folk Theory on 2007-12-23
did you enable all repositories?

i still cant upload artowrk or videos. anyone got those to work?

---

### Post by lukem on 2007-12-23
All are enabled.  It says failed to get "404" from Beerorkid

---

### Post by apd on 2007-12-24
does´nt work with ./configure 
make.
Telling me that no such file or directory found. 

this is what happens when i´m trying sudo checkinstall -D

The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: 

Preparing package documentation...OK

*** No known documentation files were found. The new package 
*** won't include a documentation directory.

Please write a description for the package.
End your description with an empty line or EOF.
>> Compiled libgpod-0.6.0
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@gizmo ]
1 -  Summary: [ Compiled libgpod-0.6.0 ]
2 -  Name:    [ pisken ]
3 -  Version: [ 20071224 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ pisken ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 2
Enter new name: 
>> libgpod2

This package will be built according to these values: 

0 -  Maintainer: [ root@gizmo ]
1 -  Summary: [ Compiled libgpod-0.6.0 ]
2 -  Name:    [ libgpod2 ]
3 -  Version: [ 20071224 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ pisken ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** Ingen regel för att skapa målet "install".  Stannar.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
IDEAS???... :confused:

---

### Post by idoerg on 2007-12-24
> **Ghostbear121 said:**
> Okay guys, there's a ton of "how do I get my awesome new iPod to work!" questions.  I spent a few hours on it when I should've been working... :)   So here's how:



4.  Now you've decompressed the source code for libgpod.  Before anything else, make sure you've got the required dependencies installed:
```

sudo apt-get install build-essential libglib2.0-dev libgtk2.0-dev libsgutils1-dev checkinstall

```
OK now: ```
sudo apt-get build-dep libgpod2
```
FYI: Build-dep installs all the required dependencies for a program, but not the program itself.  This is perfect, 'cause we don't WANT the version of libgpod that's on apt right now.  We want the one we're about to compile:



This is where I get stuck. 
```
sudo apt-get build-dep libgpod2
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to find a source package for libgpod2


```

I pushed through anyway with the rest of the tutorial, and I still get an amarok that transfers to my ipod (classic, silver 80GB) but the songs do not show up on the ipod display.

Help?

Thanks

---

### Post by idoerg on 2007-12-24
OK, I found my problem. I am using feisty, which uses libgpod1, not libgpod2.

I tried compiling and packaging libgpod-0.6.0 as libgpod1, but amarok freezes when I try to transfer song files. 

Any help for a 7.04 user? (Besides upgrading to 7.10?)

---

### Post by elchato on 2007-12-25
Ok, I'm following step by step, I've got an 8g nano

> **Ghostbear121 said:**
> 
There's a slick little script you have to run that came with libgpod:
```

ipod-read-sysinfo-extended /dev/sda1 /media/IPOD

```
**Make sure you swap out /dev/sda1 with whatever your ipod is actually connected to!**
This script will add an XML file called sysinfo-extended onto your ipod's config directory; it's what libgpod uses to 'see' your ipod's firewire device ID, serial number, etc.


this is not working.. gives me

```

ipod-read-sysinfo-extended /dev/sda1 /media/IPOD
Couldn't read xml sysinfo from /dev/sda1

```

then the other thing is

> **Ghostbear121 said:**
> 

Okay, now fire up Amarok.  Under the Devices tab, there will be a dropdown menu (top-left area of the window).  Move down the menu, select Classic ->  (Your Ipod).  Mine's an 80gb Black.  


can't seem to find this in amarok (using the spanish version) all I've got for choices is
-Nomad Jukebox
-Iriver
-Ipod
-a couple others


thanks a lot



EDIT: just read the last post... is the fact, Im using Feisty too... any way around this?

---

### Post by apd on 2007-12-25
hey ho let´s go...


well, i´ve started all over again and right now i´m not able to get by the .configure
                                                                                                        make
command. Says no makefile or directory found.

So this is probably ezy for one of u brightminded ones. any response appreciated.

---

### Post by jtreach on 2007-12-25
Heya I've been trying to get my iPod to work, updated to gutsy just to see if that would help. My iPod will not mount now though I get the following error message in dmesg:

```
[ 3306.764000] SCSI device sda: 19488471 4096-byte hdwr sectors (79825 MB)
[ 3306.768000] sda: Write Protect is off
[ 3306.768000] sda: Mode Sense: 68 00 00 08
[ 3306.768000] sda: assuming drive cache: write through
[ 3306.772000] SCSI device sda: 19488471 4096-byte hdwr sectors (79825 MB)
[ 3306.772000] sda: Write Protect is off
[ 3306.772000] sda: Mode Sense: 68 00 00 08
[ 3306.772000] sda: assuming drive cache: write through
[ 3306.772000]  sda: sda1
[ 3306.784000] sd 2:0:0:0: Attached scsi removable disk sda
[ 3306.804000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[ 3307.600000] FAT: Unrecognized mount option "usefree" or missing value
[ 3589.888000] usb 2-7: USB disconnect, address 2
[ 3609.488000] usb 2-7: new high speed USB device using ehci_hcd and address 3
[ 3609.620000] usb 2-7: configuration #1 chosen from 2 choices
[ 3609.628000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3609.628000] usb-storage: device found at 3
[ 3609.628000] usb-storage: waiting for device to settle before scanning
[ 3614.628000] usb-storage: device scan complete
[ 3614.636000] scsi 3:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 3614.640000] SCSI device sda: 19488471 4096-byte hdwr sectors (79825 MB)
[ 3614.640000] sda: Write Protect is off
[ 3614.640000] sda: Mode Sense: 68 00 00 08
[ 3614.640000] sda: assuming drive cache: write through
[ 3614.648000] SCSI device sda: 19488471 4096-byte hdwr sectors (79825 MB)
[ 3614.648000] sda: Write Protect is off
[ 3614.648000] sda: Mode Sense: 68 00 00 08
[ 3614.648000] sda: assuming drive cache: write through
[ 3614.648000]  sda: sda1
[ 3614.836000] sd 3:0:0:0: Attached scsi removable disk sda
[ 3614.836000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[ 3615.560000] FAT: Unrecognized mount option "usefree" or missing value

```

I don't know if that helps but the error message that comes up is moaning about the file system. Even though I just synced it with a windows computer. Any ideas?
[EDIT]  Found out why it was if anybody is interested [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)

Thanks in advance.

---

### Post by Excalibre on 2007-12-25
> **runsink said:**
> Good job GB !

I tried it, but I'm getting a error at "sudo checkinstall"

All seems to go fine, I have no errors at configure or make, but when it is installing libaries from ".libs/" I get an error like this :



What does is mean by .libs ? I can not see it with "ls -a"
If I run that line by hand I get :



Any idea what is going wrong ?

Thanks,
Joost

Yeah, didn't work for me either.

Uh, good try, I guess.

---

### Post by jtreach on 2007-12-25
Okay new problem i think everything went alright on installation after using 'sudo make install' instead of 'sudo checkinstall' the

```
ipod-read-sysinfo-extended
```

seemed to work so I assume everything went okay. The only thing now is that amarok seems to be using another older version of libgpod that is already on my system and synaptic thinks that i don't have it installed and when ever i try and reinstall amarok it reinstalls the old version of libgpod with it. What should i do?

---

### Post by Excalibre on 2007-12-25
> **Excalibre said:**
> Yeah, didn't work for me either.

Uh, good try, I guess.
And this is what I get for not reading through the whole thread before trying. Worked great. Now just have to figure out about the whole cover art situation.

---

### Post by adam.tropics on 2007-12-25
Worked eventually thank you....took a few goes getting checkinstall to work right though. Still not quite sure why it suddenly did. Initially I had to point amarok in the direction of my ipod as it did not detect it, but after that no problem. Artwork working fine too. 

Also in case anyone still curious, I tried this with my exisiting firmware, all good, then, being, well, bored, went to a windows box and upgraded the firmware. Now I had to remove and replace my tracks, but it does indeed work with current upgraded firmware just fine. No guru tricks required!

---

### Post by adam.tropics on 2007-12-26
Since you guys did the hard yards, I would just share my latest discovery!

Since it was a tad of an ordeal getting this far....simple once up and running, but a pain to get there, I was inclined to not worry about putting other stuff on there, such as contacts...but 

it turns out you can just drag and drop them from nautilus into the contacts folder. Well I didn't know that. But using thunderbird, I needed to install an extension [from here]("http://nic-nac-project.de/%7Ekaosmos/morecols-en.html") to make exporting all your contacts as vcards easy...Then just drag and drop. 

I should just mention, that at the time, whilst obviously mounted, it was not being used by amarok. However, I did then connect with amarok and remove a couple tracks then disconnect, just to see if it all worked without affecting each other, and it's all fine. Thought I'd share. (I don't use/have evolution, so ymmv on that)

edit: same goes for calendars, just drag the .ics (ical) file into calendars folder on ipod, and presto!

---

### Post by awardk on 2007-12-26
Thanks guys - you really saved me a whole lot of time! Much appreciated.

---

### Post by hollowhead on 2007-12-26
I followed the instructions above using checkinstall -D but the libgpod has not apparently compiled correctly libgpod.so.3 is not on my system /libgpod-Artwork.html': No such file or directory

debian install failed here is the output (sorry about the length)

Enter new name: 
>> libgpod2

This package will be built according to these values: 

0 -  Maintainer: [ root@hollowfamily ]
1 -  Summary: [ Compiled libgpod-0.6.0 ]
2 -  Name:    [ libgpod2 ]
3 -  Version: [ 0.6.0 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ libgpod-0.6.0 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/src'
make[2]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/src'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libgpod.la' '/usr/local/lib/libgpod.la'
/usr/bin/install -c .libs/libgpod.so.3.0.0 /usr/local/lib/libgpod.so.3.0.0
/usr/bin/install: setting permissions for `/usr/local/lib/libgpod.so.3.0.0': No such file or directory
(cd /usr/local/lib && { ln -s -f libgpod.so.3.0.0 libgpod.so.3 || { rm -f libgpod.so.3 && ln -s libgpod.so.3.0.0 libgpod.so.3; }; })
(cd /usr/local/lib && { ln -s -f libgpod.so.3.0.0 libgpod.so || { rm -f libgpod.so && ln -s libgpod.so.3.0.0 libgpod.so; }; })
/usr/bin/install -c .libs/libgpod.lai /usr/local/lib/libgpod.la
/usr/bin/install: setting permissions for `/usr/local/lib/libgpod.la': No such file or directory
/usr/bin/install -c .libs/libgpod.a /usr/local/lib/libgpod.a
/usr/bin/install: setting permissions for `/usr/local/lib/libgpod.a': No such file or directory
chmod 644 /usr/local/lib/libgpod.a
ranlib /usr/local/lib/libgpod.a
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
test -z "/usr/local/include/gpod-1.0/gpod" || mkdir -p -- "/usr/local/include/gpod-1.0/gpod"
 /usr/bin/install -c -m 644 'itdb.h' '/usr/local/include/gpod-1.0/gpod/itdb.h'
/usr/bin/install: setting permissions for `/usr/local/include/gpod-1.0/gpod/itdb.h': No such file or directory
make[2]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/src'
make[1]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/src'
Making install in tools
make[1]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/tools'
make[2]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/tools'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'ipod-read-sysinfo-extended' '/usr/local/bin/ipod-read-sysinfo-extended'
/usr/bin/install -c .libs/ipod-read-sysinfo-extended /usr/local/bin/ipod-read-sysinfo-extended
/usr/bin/install: setting permissions for `/usr/local/bin/ipod-read-sysinfo-extended': No such file or directory
test -z "" || mkdir -p -- ""
test -z "" || mkdir -p -- ""
make[2]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/tools'
make[1]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/tools'
Making install in tests
make[1]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/tests'
make[2]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/tests'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/tests'
make[1]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/tests'
Making install in po
make[1]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/po'
/home/nrh1/Desktop/libgpod-0.6.0/install-sh -d /usr/local/share/locale
linguas="de es fr he it ja ro sv "; \
        for lang in $linguas; do \
          dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
          /home/nrh1/Desktop/libgpod-0.6.0/install-sh -d $dir; \
          if test -r $lang.gmo; then \
            /usr/bin/install -c -m 644 $lang.gmo $dir/libgpod.mo; \
            echo "installing $lang.gmo as $dir/libgpod.mo"; \
          else \
            /usr/bin/install -c -m 644 ./$lang.gmo $dir/libgpod.mo; \
            echo "installing ./$lang.gmo as" \
                 "$dir/libgpod.mo"; \
          fi; \
          if test -r $lang.gmo.m; then \
            /usr/bin/install -c -m 644 $lang.gmo.m $dir/libgpod.mo.m; \
            echo "installing $lang.gmo.m as $dir/libgpod.mo.m"; \
          else \
            if test -r ./$lang.gmo.m ; then \
              /usr/bin/install -c -m 644 ./$lang.gmo.m \
                $dir/libgpod.mo.m; \
              echo "installing ./$lang.gmo.m as" \
                   "$dir/libgpod.mo.m"; \
            else \
              true; \
            fi; \
          fi; \
        done
/usr/bin/install: setting permissions for `/usr/local/share/locale/de/LC_MESSAGES/libgpod.mo': No such file or directory
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/libgpod.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/es/LC_MESSAGES/libgpod.mo': No such file or directory
installing es.gmo as /usr/local/share/locale/es/LC_MESSAGES/libgpod.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/fr/LC_MESSAGES/libgpod.mo': No such file or directory
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/libgpod.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/he/LC_MESSAGES/libgpod.mo': No such file or directory
installing he.gmo as /usr/local/share/locale/he/LC_MESSAGES/libgpod.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/it/LC_MESSAGES/libgpod.mo': No such file or directory
installing it.gmo as /usr/local/share/locale/it/LC_MESSAGES/libgpod.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/ja/LC_MESSAGES/libgpod.mo': No such file or directory
installing ja.gmo as /usr/local/share/locale/ja/LC_MESSAGES/libgpod.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/ro/LC_MESSAGES/libgpod.mo': No such file or directory
installing ro.gmo as /usr/local/share/locale/ro/LC_MESSAGES/libgpod.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/sv/LC_MESSAGES/libgpod.mo': No such file or directory
installing sv.gmo as /usr/local/share/locale/sv/LC_MESSAGES/libgpod.mo
make[1]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/po'
Making install in m4
make[1]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/m4'
make[2]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/m4'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/m4'
make[1]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/m4'
Making install in docs
make[1]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/docs'
Making install in reference
make[2]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/docs/reference'
make[3]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/docs/reference'
make[3]: Nothing to be done for `install-exec-am'.
installfiles=`echo ./html/*`; \
        if test "$installfiles" = './html/*'; \
        then echo '-- Nothing to install' ; \
        else \
          /bin/bash ../../mkinstalldirs /usr/local/share/gtk-doc/html/libgpod; \
          for i in $installfiles; do \
            echo '-- Installing '$i ; \
            /usr/bin/install -c -m 644 $i /usr/local/share/gtk-doc/html/libgpod; \
          done; \
          echo '-- Installing ./html/index.sgml' ; \
          /usr/bin/install -c -m 644 ./html/index.sgml /usr/local/share/gtk-doc/html/libgpod || :; \
        fi
mkdir -p -- /usr/local/share/gtk-doc/html/libgpod
-- Installing ./html/ch01.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/ch01.html': No such file or directory
-- Installing ./html/home.png
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/home.png': No such file or directory
-- Installing ./html/index.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/index.html': No such file or directory
-- Installing ./html/index.sgml
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/index.sgml': No such file or directory
-- Installing ./html/itunesdb.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/itunesdb.html': No such file or directory
-- Installing ./html/left.png
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/left.png': No such file or directory
-- Installing ./html/libgpod-Artwork.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/libgpod-Artwork.html': No such file or directory
-- Installing ./html/libgpod.devhelp
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/libgpod.devhelp': No such file or directory
-- Installing ./html/libgpod.devhelp2
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/libgpod.devhelp2': No such file or directory
-- Installing ./html/libgpod-Device.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/libgpod-Device.html': No such file or directory
-- Installing ./html/libgpod-File-handling-functions.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/libgpod-File-handling-functions.html': No such file or directory
-- Installing ./html/libgpod-Low-level-functions.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/libgpod-Low-level-functions.html': No such file or directory
-- Installing ./html/libgpod-Photo-database.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/libgpod-Photo-database.html': No such file or directory
-- Installing ./html/libgpod-Playlists.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/libgpod-Playlists.html': No such file or directory
-- Installing ./html/libgpod-Smart-Playlists.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/libgpod-Smart-Playlists.html': No such file or directory
-- Installing ./html/libgpod-The-Itdb-iTunesDB-structure.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/libgpod-The-Itdb-iTunesDB-structure.html': No such file or directory
-- Installing ./html/libgpod-Time-handling.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/libgpod-Time-handling.html': No such file or directory
-- Installing ./html/libgpod-Tracks.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/libgpod-Tracks.html': No such file or directory
-- Installing ./html/photodb.html
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/photodb.html': No such file or directory
-- Installing ./html/right.png
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/right.png': No such file or directory
-- Installing ./html/style.css
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/style.css': No such file or directory
-- Installing ./html/up.png
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/up.png': No such file or directory
-- Installing ./html/index.sgml
/usr/bin/install: setting permissions for `/usr/local/share/gtk-doc/html/libgpod/index.sgml': No such file or directory
make[3]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/docs/reference'
make[2]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/docs/reference'
make[2]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/docs'
make[3]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/docs'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/docs'
make[2]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/docs'
make[1]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/docs'
Making install in bindings
make[1]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings'
Making install in python
make[2]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python'
make  install-recursive
make[3]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python'
Making install in examples
make[4]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python/examples'
make[5]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python/examples'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python/examples'
make[4]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python/examples'
Making install in tests
make[4]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python/tests'
make[5]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python/tests'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python/tests'
make[4]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python/tests'
make[4]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python'
make[5]: Entering directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/python2.5/site-packages/gpod" || mkdir -p -- "/usr/local/lib/python2.5/site-packages/gpod"
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  '_gpod.la' '/usr/local/lib/python2.5/site-packages/gpod/_gpod.la'
libtool: install: warning: relinking `_gpod.la'
(cd /home/nrh1/Desktop/libgpod-0.6.0/bindings/python; /bin/bash ../../libtool  --tag=CC --mode=relink gcc -g -O2 -o _gpod.la -rpath /usr/local/lib/python2.5/site-packages/gpod -module -avoid-version _gpod_la-gpod_wrap.lo -lgobject-2.0 -lglib-2.0 -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 ../../src/libgpod.la )  
gcc -shared  .libs/_gpod_la-gpod_wrap.o  -L/usr/lib -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -L/usr/local/lib -lgpod  -Wl,-soname -Wl,_gpod.so -o .libs/_gpod.so
/usr/bin/install -c .libs/_gpod.soT /usr/local/lib/python2.5/site-packages/gpod/_gpod.so
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.so': No such file or directory
/usr/bin/install -c .libs/_gpod.lai /usr/local/lib/python2.5/site-packages/gpod/_gpod.la
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.la': No such file or directory
/usr/bin/install -c .libs/_gpod.a /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.a': No such file or directory
chmod 644 /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
ranlib /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
ranlib: could not create temporary file whilst writing archive: No more archived files
make[5]: *** [install-gpodLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings/python'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/nrh1/Desktop/libgpod-0.6.0/bindings'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
I think I know why  the checkinstall does not create the gtkdoc directory or child dirs as shown on the following line
/usr/local/share/gtk-doc/html/libgpod/libgpod-Device.htm

Although as shown below I told it to
nrh1@hollowfamily:~/Desktop/libgpod-0.6.0$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.

I have tried this twice now. 

Anyone got a deb with version 3 of the library in they could post?

---

### Post by siwilson on 2007-12-26
There's a very good write up on how to get the newer iPods (in my case an A980/A1386) going with Ubuntu here: 
[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

I tried to build the libraries myself but ended up in a bit of a mess.

The above instructions worked fine for me.

HTH

/Simon

---

### Post by hollowhead on 2007-12-26
siwilson you've saved my bacon.......  It works!  Please note if you use the link instructions that siwilson posted posted again here [http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

you cannot install the dev deb first install the library first then the dev deb.  One of them requires a couple of libs to be installed (the dev deb) do it.  My daughters Christmas present a 4gb nano (firmwire 1.0.1) A1236  bought a month or so ago now works and I have loaded music onto it from gtkpod.  I no longer have "no music" on it but 29 songs and plays them!  Bizarrely it would always play using  xxms off the computer just not independently.   Now to work out out how to buy music from itunes w/o windos or macintoy.

Thanks everyone.

---

### Post by lukem on 2007-12-26
hollowhead and siwilson:

Thank you very much for your posts.  using ubuntu 6.06 Dapper.  I get an error when trying to install libgpod2_0.5.3+actually0.6.0.1-i386.deb.  It says "Error: Dependancy is not satisfiable: libc6"

I checked and I do have libc6 installed.  So I reinstalled it but still get the same result.  Would really appreciate anyone's help who may recognize this problem.

Thanks

---

### Post by hollowhead on 2007-12-26
I'm just guessing but I think you might need to upgrade to a more recent version of ubuntu.......

---

### Post by apd on 2007-12-26
siwilson: Do u know if  it´s possible for me to try it with my amd64? Or is it only on the i386 machines that it works? And by the way any1, i´m still not being able to get by the .configure
make             thing at the beginning, any1 up for some advices...? Cheers apd :)

---

### Post by mharless on 2007-12-27
Okay, did I just brick my ipod classic?

I was able to transfer a couple of songs, but then I had some failed writes, and now it doesn't 
show any songs anymore.  When I mount the ipod, it's being mounted read-only as well now too.

I also tried to connect it to itunes on a windows xp machine, and I can see the mass storage
drive, but itunes never sees the ipod.

Any suggestions?  Thanks.

--Mike

---

### Post by adam.tropics on 2007-12-27
don't know if these will help,but

[http://www.apple.com/support/ipod/five_rs/classic/#](http://www.apple.com/support/ipod/five_rs/classic/#)

[http://docs.info.apple.com/article.html?artnum=60983](http://docs.info.apple.com/article.html?artnum=60983)

First time I used my iPod (incidentally in windows) I had to restore since it stopped doing anything. All good since though.

---

### Post by jdbausch on 2007-12-27
> **hollowhead said:**
> siwilson you've saved my bacon.......  It works!  Please note if you use the link instructions that siwilson posted posted again here [http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

you cannot install the dev deb first install the library first then the dev deb.  One of them requires a couple of libs to be installed (the dev deb) do it.  My daughters Christmas present a 4gb nano (firmwire 1.0.1) A1236  bought a month or so ago now works and I have loaded music onto it from gtkpod.  I no longer have "no music" on it but 29 songs and plays them!  Bizarrely it would always play using  xxms off the computer just not independently.   Now to work out out how to buy music from itunes w/o windos or macintoy.

Thanks everyone.

I followed the instructions that siwilson's linked, and also had to install the lib first.

BUT

it looks like adding 1 file from Rhythmbox removed about 90% of the album artwork from my 80gb classic ipod? ( I already had 2.5 thousand songs with artwork loaded on it from via itunes)
is this to be expected? 

is there a consensus on the best way to get cover art (and movies) on to this damn thing?

---

### Post by adam.tropics on 2007-12-27
Amarok (1.4.8 in gutsy-backports repo) does a very good job, and deals well with artwork. I had limited success with Rhythmbox, which is a shame, and gtkpod....I don't want to take an HCI course just to use it! Amarok is fine.

---

### Post by chickenwing1 on 2007-12-27
> **apd said:**
> does´nt work with ./configure 
make.
Telling me that no such file or directory found. 

this is what happens when i´m trying sudo checkinstall -D

The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: 

Preparing package documentation...OK

*** No known documentation files were found. The new package 
*** won't include a documentation directory.

Please write a description for the package.
End your description with an empty line or EOF.
>> Compiled libgpod-0.6.0
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@gizmo ]
1 -  Summary: [ Compiled libgpod-0.6.0 ]
2 -  Name:    [ pisken ]
3 -  Version: [ 20071224 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ pisken ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 2
Enter new name: 
>> libgpod2

This package will be built according to these values: 

0 -  Maintainer: [ root@gizmo ]
1 -  Summary: [ Compiled libgpod-0.6.0 ]
2 -  Name:    [ libgpod2 ]
3 -  Version: [ 20071224 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ pisken ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** Ingen regel för att skapa målet "install".  Stannar.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
IDEAS???... :confused:

I have the same problem as this guy. Help would be much appreciated

---

### Post by jdbausch on 2007-12-27
> **jdbausch said:**
> I followed the instructions that siwilson's linked, and also had to install the lib first.

BUT

it looks like adding 1 file from Rhythmbox removed about 90% of the album artwork from my 80gb classic ipod? ( I already had 2.5 thousand songs with artwork loaded on it from via itunes)
is this to be expected? 

is there a consensus on the best way to get cover art (and movies) on to this damn thing?

Update to my previous post - not only is most of the art gone, but the remaining art is in many cases incorrect - meaning that, for example, in the ipod, I now have a metallica covers on a replacements album.

it all appears to play correctly though.

hmmm.

---

### Post by GuySmily on 2007-12-27
> **mharless said:**
> Okay, did I just brick my ipod classic?

I was able to transfer a couple of songs, but then I had some failed writes, and now it doesn't 
show any songs anymore.  When I mount the ipod, it's being mounted read-only as well now too.

I also tried to connect it to itunes on a windows xp machine, and I can see the mass storage
drive, but itunes never sees the ipod.

Any suggestions?  Thanks.

--Mike

This just happened to me.  I could [kinda] browse the iPod filesystem in both WinXP and Ubuntu, but most attempts to add/remove files (and even opening some folders) would result in various error messages about them being corrupt/inaccessible/etc.  iTunes didn't register the iPod at all.

After tons of messing around with different programs on both Windows and Linux, I managed to fix it with fdisk, mkfs, and iTunes.

I know it seems scary to format your iPod, but many topics on other forums recommended it as a last resort.  They all say to use some HP USB formatting tool, but it kept giving me a write-protected error.  Instead, this worked for me!

First I looked for my ipod.  My ipod's name is Nanako.
```
df
```

This outputs
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            234418848  26267832 196243240  12% /
varrun                 1031092       100   1030992   1% /var/run
varlock                1031092         0   1031092   0% /var/lock
udev                   1031092        92   1031000   1% /dev
devshm                 1031092         0   1031092   0% /dev/shm
lrm                    1031092     38324    992768   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1            156017456    529184 155488272   1% /media/NANAKO
```

As you can see, Nanako is /dev/sdb1 on my computer

Then I tried to format the iPod multiple times.  Each time, it seemed to start doing something, then failed.

```
sudo mkfs -t vfat /dev/sdb1

sudo fdisk /deb/sdb1

sudo mkfs -t vfat /dev/sdb1

sudo fdisk /deb/sdb1
```

I know it sounds wierd, but that did the trick!  I booted back into windows, and iTunes was able to restore my iPod.  So I restored it, copied my music over, etc. Problem solved!

Yes, I used iTunes to copy my music over.  I still haven't gotten Amarok, gtkpod, Rhythmbox, or floola to work.  I got Amarok to upload files once, but the iPod didn't show them.

My post count reflects my experience with Linux, so if you think I'm giving dangerous instructions, please say so.  On the other hand.. A chance at fixing your iPod is better than having a $350 paper weight.  I was able to be brave since I was still within the return period.

Good luck~

btw - I had bad luck using VirtualBox w/iTunes to flash the firmware on my iPod, even though it was able to add music.  If you're going to flash the firmware, do it from a real Windows install.

Also, I don't think I read anywhere in this thread that at least with the 160gb iPod Classic, none of the Linux programs can connect to the iPod unless you do the firmware update.  So give that a shot, too.

---

### Post by GuySmily on 2007-12-27
> **chickenwing1 said:**
> I have the same problem as this guy. Help would be much appreciated

To get around this, I replaced ```
sudo checkinstall
``` with ```
sudo make install
```

---

### Post by lukem on 2007-12-28
I finally had some success after upgrading to Gutsy then following the instructions here:

[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

Then I installed Amarok.  Amarok is nice but I'm still just learning the whole music manager program thing.  Anyway, Amarok put songs onto the Ipod and Cover art.  A couple of the covers are wrong, but that is most likely to my mispelling the album name when the MP3s were created.

I did have to tell Amarok where to look for the Ipod.  It did not look in /media by default.

Still need to get the cover art straight and then want to upload some video and photos.  

Thanks to all and if you're still stuck, try the link above.

---

### Post by mattgarm on 2007-12-28
Thanks, lukem :). You've made my day

---

### Post by hipotermia on 2007-12-28
> **lukem said:**
> I finally had some success after upgrading to Gutsy then following the instructions here:

[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

Then I installed Amarok.  Amarok is nice but I'm still just learning the whole music manager program thing.  Anyway, Amarok put songs onto the Ipod and Cover art.  A couple of the covers are wrong, but that is most likely to my mispelling the album name when the MP3s were created.

I did have to tell Amarok where to look for the Ipod.  It did not look in /media by default.

Still need to get the cover art straight and then want to upload some video and photos.  

Thanks to all and if you're still stuck, try the link above.

damn. it gives me this error

> Couldn't read xml sysinfo from [/dev/sda1]


---

### Post by lukem on 2007-12-28
hipotermia

what were you doing when you got the error about /dev/sda1

---

### Post by hipotermia on 2007-12-28
> **lukem said:**
> hipotermia

what were you doing when you got the error about /dev/sda1

so, in the link that you posted [http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

in the step 7, with the location of the ipod and name, it gives me that error.

it's a classic 80gb grey ipod.

---

### Post by apd on 2007-12-28
a friend  come by and removed every change i´d made and followed the Howto making a sudo checkinstall -D. Everything works correctly (as it seems). I now have a 6th generation Ipod that i can use.  Thanks for ur patience in solving this!! 
apd :guitar:

---

### Post by TheOrangePeanut on 2007-12-28
Did anyone figure out how to fix this?  I saw some other people had this problem but no one has posted a solution yet (I think)

```

make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/nelson/Desktop/libgpod-0.6.0/bindings/python'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/nelson/Desktop/libgpod-0.6.0/bindings'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

---

### Post by adam.tropics on 2007-12-28
In repo settings, check the source box....see attachment.

---

### Post by mcgodx on 2007-12-29
I just got the install-failed as well.

```
make[5]: *** [install-gpodLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

I wish I could get this to work

By the way, I have 1.0.3 firmware

---

### Post by mcgodx on 2007-12-30
> **mcgodx said:**
> I just got the install-failed as well.

```
make[5]: *** [install-gpodLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

I wish I could get this to work

By the way, I have 1.0.3 firmware

Nevermind this.  When compiling the package, I did
sudo ./configure
sudo make
sudo checkinstal -D
Other than that, I followed the original tutorial exactly and it works like a charm.

---

### Post by lukem on 2007-12-30
Does anyone know if the "Disconnect" button is also supposed to eject the Ipod?  Mine does not and a message pops up saying that the post disconnect command failed and to make sure it is safe to remove the device before doing so.  I think it should unmount it (eject it) but I'm do not know what to put in the "Post disconnect command" box in the "Configure Media Device" window.  

Thanks

---

### Post by adam.tropics on 2007-12-30
You can configure the eject command. (Click on the  gear icon thing), then for eject, something like (change sda1 as per)

```
 gnome-eject -t -d %d /dev/sda1
```

---

### Post by cinephy on 2007-12-30
Has anyone had any luck with Model A1238 (Classic Black 80G)? According to [[COLOR="DarkRed"]this[/COLOR]]("http://gtkpod.wikispaces.com/Supported+iPods") it is not supported yet by libgpod.

---

### Post by jdbausch on 2007-12-30
> **cinephy said:**
> Has anyone had any luck with Model A1238 (Classic Black 80G)? According to [[COLOR="DarkRed"]this[/COLOR]]("http://gtkpod.wikispaces.com/Supported+iPods") it is not supported yet by libgpod.

not sure how to determine model number, but I have a classic 80gb black, and I can confirm that I was able to add a song without blowing up the DB, after following these instructions:

[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

however, I had a bunch of music on there, and doing this messed up the album artwork - this could be my own issue. not sure.


I have not tried this since I fixed my artwork under windows itunes - I'm afraid to try it again.


but as I said, this may be a unique to me issue...

---

### Post by cinephy on 2007-12-30
The model number should be printed on the back of your iPod in fine print under the serial number.

---

### Post by jdbausch on 2007-12-30
> **cinephy said:**
> The model number should be printed on the back of your iPod in fine print under the serial number.

silly me, assuming that I could find it in software...  of course the case I have didn't help!



it is an:
a1238

and as  I said, I can add songs to the ipod without blowing up the db.

---

### Post by cinephy on 2007-12-30
Thanks for the feedback jdbausch... Okay now one more problem. I have downloaded and built the libgpod library but I cannot seem to find the ipod-read-sysinfo-extended command. I've looked through my /usr/bin and my /usr/local/bin and don't seem to have it. Any ideas?

EDIT: I read README.Sysinfo and I guess I forgot to install libsgutils

---

### Post by pabloisthewolf on 2007-12-30
same result with the libgpod install -- sycing and xfers the ipod but cannot see the music.  Also get an error with the photos db?

---

### Post by chickenwing1 on 2007-12-30
Songs now show up on my iPod but videos still wont show up.  How can I get videos to work?

---

### Post by jdbausch on 2007-12-30
> **cinephy said:**
> Thanks for the feedback jdbausch... Okay now one more problem. I have downloaded and built the libgpod library but I cannot seem to find the ipod-read-sysinfo-extended command. I've looked through my /usr/bin and my /usr/local/bin and don't seem to have it. Any ideas?

EDIT: I read README.Sysinfo and I guess I forgot to install libsgutils


glad to be of any (minor) assistance - BUT

I can not even play a song out of my ipod without it shreading my artwork (it blows most of it away - and most of the remaining artwork is on the wrong album)

as I mentioned, I loaded most of this ipod up under itunes in windows.

I think it probably has to do with what I found here:
[http://amarok.kde.org/wiki/Media_Device:IPod#My_iPod_does_not_show_any_music]("http://amarok.kde.org/wiki/Media_Device:IPod#My_iPod_does_not_show_any_music")

in this section:
>  Artwork not working

    * It is important that Amarok recognizes your iPod model:
          o it is shown in the combo box at the top of the media device browser
          o if not, you have to set it manually (choose 'Set iPod model' below iPod drop-down button) 
    * Version 1.4.5 introduced support for setting the iPod model from within Amarok, however this did not work, making artwork and video transfer impossible. This is fixed starting with Amarok 1.4.6.
    * Make sure, all the optional prerequisites were available when you compiled libgpod! I.e.
          o GdkPixbuf has to be available (including development package)
          o libgpod has to be compiled with gtk support
          o DBus and HAL libraries have to be installed
          o libgobject-2.0 is required 
    * With libgpod 0.4.0 and older, DBus/Hal has to be working for recognizing your iPod model!
    * Your iPod has to be recognized properly (e.g. problems with some HP iPods):
      submit the contents of iPod_Control/Device/SysInfo together with a description of your iPod model to [email]gtkpod-devel@lists.sourceforge.net[/email]
    * A bug within libgpod older than libpgod 0.6 makes artwork fail as soon as iPodControl/Artwork/ArtworkDB grows to more than 16 MB
    * Problems within libgpod make artwork fail on 64-bit systems, because of different alignment within structs (this is fixed in libgpod 0.4.0 and newer)
    * Recent iPod firmware versions (newer than mid 2006, and the firmware on 2nd gen iPod nanos, 5.5 gen iPods and the 2nd gen iPod shuffle) only create an empty iPod_Control/Device/SysInfo file. But this is used by libgpod for determining the kind of iPod you have. And libgpod has to know your iPod model for transferring artwork correctly. A work-around is to use a recent version of gtkpod for setting the iPod model manually (this sets the model version string in the SysInfo file).
    * As of Amarok 1.4.6, I needed no DBUS or HAL stuff running, I've just setup iPod model within Amarok, updated artwork and everything automagically worked (iPod Nano 2GB Silver). Your mileage may vary. 




I do not have a correct option available in amarok for my ipod  (no choice for model a1238 is listed)

Since I  had to manually create the sysinfo file, it does not include the model, just because I was not sure exactly what it should say there...

so if anyone know IF a sysinfo file with the correct model entry will make the amarok artwork problem go away, that would be a big help.  Also if anyone know what that line should say, well that would also be good to know.

  until I figure out more, well I guess I will continue to dual boot...

which sucks of course.

hey apple, thanks again for changing the DB format.:roll:

---

### Post by cinephy on 2007-12-30
Okay this is what I have done so far. I compiled and installed libgpod, linked the libraries, then installed amarok as stated in the first post but I did not use ipod-read-sysinfo-extended. Instead I just edited the SysInfo file manually as described in README.SysInfo. When I opened up amarok I set the iPod setting to the Classic Black 80G iPod setting with the Bxxxx Model Number since the Axxxx Model number was not there. My iPod had been previously loaded from a WinXP computer with album art for everything on it and about 4 videos. I then loaded one album to the device with cover art that amarok had found via the Cover Manager tool. Then I unmounted via amarok and turned on my iPod this is what I have found. The album itself loaded and I still had everything that was loaded on it previously minus the album art. Strangely enough the only album art that showed up was from the one that I loaded from amarok. Now the wierd part... The right side of the menu where the images used to scroll by no longer works for music or the videos but my videos are still intact and viewable. 

I will be experimenting more over the next few days and I'll try to keep everyone updated. Does anyone know if the libgpod devs are actually working on the newer model numbers? I have a feeling this is why a few things are messing up, that or the newer firmware (I'm running 1.0.3 PC)

---

### Post by chickenwing1 on 2007-12-31
When I get to step 5 of the instructions and enter the comand

make

I get the following error



> make[2]: Entering directory `/home/owner/Desktop/libgpod-0.6.0/tools'
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o ipod-read-sysinfo-extended  ipod_read_sysinfo_extended-read-sysinfoextended-sgutils.o ipod_read_sysinfo_extended-ipod-scsi-inquiry.o -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    -lsgutils ../src/libgpod.la 
rm: cannot remove `.libs/ipod-read-sysinfo-extended': Permission denied
gcc -g -O2 -o .libs/ipod-read-sysinfo-extended ipod_read_sysinfo_extended-read-sysinfoextended-sgutils.o ipod_read_sysinfo_extended-ipod-scsi-inquiry.o  /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so //usr/lib/libsgutils.so ../src/.libs/libgpod.so  -Wl,--rpath -Wl,//usr/lib
/usr/bin/ld: cannot open output file .libs/ipod-read-sysinfo-extended: Permission denied
collect2: ld returned 1 exit status
make[2]: *** [ipod-read-sysinfo-extended] Error 1
make[2]: Leaving directory `/home/owner/Desktop/libgpod-0.6.0/tools'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/owner/Desktop/libgpod-0.6.0'
make: *** [all] Error 2
 

---

### Post by Hoppiesbox on 2007-12-31
This may seem out of place, but I'd suggest to anyone having troubles getting amarok to work with their 6g iPod to try Floola - It's not perfect(not open source, doesn't manage a local library) and definitely can't replace amarok - but it does support every feature of the iPod with ease(music, video, podcasts, playlists, artwork, and yes, even has youtube/web video conversion built in). You just unzip the archive and place the resulting folder(floola-linux) into the root folder of your iPod - then run the application right off the iPod( ./floola in a terminal, or make an app launcher for the Desktop ) You'll have to have used iTunes at least 1 time - which is a bit annoying for those of us who pride ourselves on using Linux exclusively - but I bit the bullet and brought the thing to work, installed iToones, copied over some free anti-G.W.Bush song - and then never looked back.

Amarok is a great app to be sure, and I do happen to be one of the lucky ones to have it working with my iPod - but honestly, the 6g iPod is about video, podcasts, artwork, etc - and until amarok can do those things as well as it does music....I'm going to have to keep on going with Floola  :)

---

### Post by lukem on 2007-12-31
Chickenwing1:  You might have better luck installing libgpod this way.   It worked well for me.  Install them in the opposite order thought.

[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

good luck

---

### Post by Windsurfer619 on 2007-12-31
> **chickenwing1 said:**
> When I get to step 5 of the instructions and enter the comand

make

I get the following error

make[2]: Entering directory `/home/owner/Desktop/libgpod-0.6.0/tools'
/bin/bash ../libtool --tag=CC --mode=link gcc -g -O2 -o ipod-read-sysinfo-extended ipod_read_sysinfo_extended-read-sysinfoextended-sgutils.o ipod_read_sysinfo_extended-ipod-scsi-inquiry.o -lgobject-2.0 -lglib-2.0 -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lsgutils ../src/libgpod.la
rm: cannot remove `.libs/ipod-read-sysinfo-extended': Permission denied
gcc -g -O2 -o .libs/ipod-read-sysinfo-extended ipod_read_sysinfo_extended-read-sysinfoextended-sgutils.o ipod_read_sysinfo_extended-ipod-scsi-inquiry.o /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so //usr/lib/libsgutils.so ../src/.libs/libgpod.so -Wl,--rpath -Wl,//usr/lib
/usr/bin/ld: cannot open output file .libs/ipod-read-sysinfo-extended: Permission denied
collect2: ld returned 1 exit status
make[2]: *** [ipod-read-sysinfo-extended] Error 1
make[2]: Leaving directory `/home/owner/Desktop/libgpod-0.6.0/tools'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/owner/Desktop/libgpod-0.6.0'
make: *** [all] Error 2 


I was getting the same error until I "completely removed" libgpod2 using synaptic. After that, everything worked like a charm!

---

### Post by jdbausch on 2007-12-31
> **Hoppiesbox said:**
> This may seem out of place, but I'd suggest to anyone having troubles getting amarok to work with their 6g iPod to try Floola - It's not perfect(not open source, doesn't manage a local library) and definitely can't replace amarok - but it does support every feature of the iPod with ease(music, video, podcasts, playlists, artwork, and yes, even has youtube/web video conversion built in). You just unzip the archive and place the resulting folder(floola-linux) into the root folder of your iPod - then run the application right off the iPod( ./floola in a terminal, or make an app launcher for the Desktop ) You'll have to have used iTunes at least 1 time - which is a bit annoying for those of us who pride ourselves on using Linux exclusively - but I bit the bullet and brought the thing to work, installed iToones, copied over some free anti-G.W.Bush song - and then never looked back.

Amarok is a great app to be sure, and I do happen to be one of the lucky ones to have it working with my iPod - but honestly, the 6g iPod is about video, podcasts, artwork, etc - and until amarok can do those things as well as it does music....I'm going to have to keep on going with Floola  :)

thanks for the suggestion, I will try it.  One of my issues is that I want to use the ipod with itunes at the office.  do you know if running floola in one location under ubuntu, and itunes at another location would produce any issues?

---

### Post by chickenwing1 on 2007-12-31
I think everything was installed properly but there is no option in Amarok for my ipod model ( a1238 )

---

### Post by jdbausch on 2007-12-31
> **Hoppiesbox said:**
> This may seem out of place, but I'd suggest to anyone having troubles getting amarok to work with their 6g iPod to try Floola - It's not perfect(not open source, doesn't manage a local library) and definitely can't replace amarok - but it does support every feature of the iPod with ease(music, video, podcasts, playlists, artwork, and yes, even has youtube/web video conversion built in). You just unzip the archive and place the resulting folder(floola-linux) into the root folder of your iPod - then run the application right off the iPod( ./floola in a terminal, or make an app launcher for the Desktop ) You'll have to have used iTunes at least 1 time - which is a bit annoying for those of us who pride ourselves on using Linux exclusively - but I bit the bullet and brought the thing to work, installed iToones, copied over some free anti-G.W.Bush song - and then never looked back.

Amarok is a great app to be sure, and I do happen to be one of the lucky ones to have it working with my iPod - but honestly, the 6g iPod is about video, podcasts, artwork, etc - and until amarok can do those things as well as it does music....I'm going to have to keep on going with Floola  :)

Hoppiesbox, or should I say my new best friend,

floola is the BOMB

it does exactly what I want my ipod manager to do.

it works for adding songs, artwork, and videos, as well as editing tags. without messing up anything already there.

NICE 

thank you so much for the advice -forum thanks given!

the only thing I need to test is to take the ipod to the office, and make sure a trip through Itunes works out ok  (I'm guessing it will be fine)

In case I forgot to say it, thanks!

:grin:

---

### Post by ions on 2008-01-01
I have been using this iPod with XP for several weeks and have roughly 20gig of music on it. Last night I attempted Floola on my Ubuntu 7.10 box for the first time. Floola sees the music, in fact so does Rhythmbox and Amarok, but now my iPod no longer sees the music.

I've seen post that says 2.3 is to fix this problem. I've also seen a post about 'selecting your iPod model', something Floola has never asked me to do.

The iPod is an 80 gig black Classic with 1.3 software on it. The version of Floola I'm using is 2.3 and Ubuntu 7.10...not sure what else to share. Oh, If I ask Floola to fix my iPod it says the iPod is fine. Lost files says nothing is lost. and that's all I can think of.

Thoughts?

---

### Post by ions on 2008-01-01
Fixed.  When I had first ran Floola it had not asked me about which version I had.  I 'uninstalled' Floola, ran it again and that was the first question it asked me.  That and an fwid.

For the fwid I ran '$ sudo lsusb -v | grep -i Serial' and selected the 16 digit number.  Floola said that looked no good but I told it to try anyway.  Unmounted the iPod and the goodness was back.  Now to see if I can get Floola to put stuff on the bugger.

---

### Post by ions on 2008-01-01
Huh, back to No Music....

Do I need to uninstall and reinstall each time?

It appears to work if I move stuff over the uninstall Floola.  If I don't then no media is shown.  Then of course when I plug it in again I need to select generation and input the fwid each time.  Is this the way it's supposed to be?

---

### Post by jdbausch on 2008-01-01
> **ions said:**
> Huh, back to No Music....

Do I need to uninstall and reinstall each time?

It appears to work if I move stuff over the uninstall Floola.  If I don't then no media is shown.  Then of course when I plug it in again I need to select generation and input the fwid each time.  Is this the way it's supposed to be?

No,  it should not do that.

I only had to put the FWID in Floola one time, and it said that it looked correct (or some such positive affirmation)

this is just a guess, but do you have on your ipod a /iPod_Control/Device/SysInfo file with the firewire id in it?

I have no idea if it is required for floola, but it since this appears to have something to do with your FWID, I would look there first.

---

### Post by ions on 2008-01-01
It's started accepting my fwid on the first try and so far it hasn't had a problem with 'no music' since.  As long as it's properly unmounted.

Getting help from [here](http://www.floola.com/modules/newbb/viewtopic.php?topic_id=403&viewmode=flat&order=ASC&start=0).

---

### Post by Hoppiesbox on 2008-01-01
Hey guys - I see you've been posting on the floola boards Ion, that's probably the best place, so I'll subscribe over there :)

---

### Post by missed her show on 2008-01-03
[QUOTE=mcgodx;4038139]I just got the install-failed as well.

```
make[5]: *** [install-gpodLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```
I'm getting this same problem.....oh woe is me.  

Still having some problems, mainly i can't see any of the music i've "transfered" to the ipod.

---

### Post by missed her show on 2008-01-03
wow


i'm having a problem.   new ipod classic 80 gb, when i plugged it in and transferred mp3s on an XP box, i could see the music on the ipod.  



in Amarok, the files/mp3s are showing on the device, but after i disconnect the ipod shows no music....any ideas are GREATLY appreciated.

---

### Post by missed her show on 2008-01-04
> **ColombianGold said:**
> Great tutorial, I finally got ot working!!! I was too getting this error, my problem was that my dependencies weren't being built...some URI error was appearing. I was able to solve it by editing my sources.list

copy the repositorie lines that are being used and add -src after deb, to the copy...something like this:

sudo gedit /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse

This did it for me. Hope it helps anybody. After that dependencies were fetched and built correctly.

Just follow the howto its pretty straight forward. 

The other thing is to use:

sudo checkinstall -D

Hope this solves it for someone.
Thanks for the howto!!!

CG
:grin:

hi

i'm having the same problem....my sources.list has a lot of commented out lines....maybe you can suggest?


heres my soureces.list
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe multiverse restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by missed her show on 2008-01-04
um. hello?   I really don't want to go back to xp.

---

### Post by Hoppiesbox on 2008-01-04
Don't be rude about it - I've read all of your posts, as have many others who receive an email for each time a reply is posted...

Try to post more info so someone might be able to figure this out for you. Did you try adding the two lines you noted to your sources.list?

---

### Post by missed her show on 2008-01-05
sorry about being the rudy toodie. 

basically, i can get ipod classic to be recognized in Ubuntu, and "transfer" files to ipod in ubuntu, but those  mp3s are not browsable on the ipod.  

Ipod works fine with windows...

---

### Post by jdbausch on 2008-01-05
have you tried using floola?



Hoppiesbox has some post in this thread about it.  it works best for me.

---

### Post by lukem on 2008-01-05
Missed her show
Your problem may be the wrong version of libgpod.  If you have not done so already, try installing it as described here

[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

And then try to reinstall Amarok.  that worked for me.  
btw on this link they say to install the "dev"file first but I had to install it second for it to install properly.  Good Luck

---

### Post by laurentmartin on 2008-01-08
Hi,

I have an ipod nano 3rd gen grey 4Gb xA426   A1236
with above procedure, I can now sync the music, but cover arts does not work.

---

### Post by Hoppiesbox on 2008-01-09
Does anyone have cover art working using amarok? I thought it was one of the functions not yet supported.

---

### Post by tigerplug on 2008-01-09
Any chance of this working with iPod Touch?

---

### Post by bomanizer on 2008-01-12
> **cinephy said:**
> Has anyone had any luck with Model A1238 (Classic Black 80G)? According to [[COLOR="DarkRed"]this[/COLOR]]("http://gtkpod.wikispaces.com/Supported+iPods") it is not supported yet by libgpod.

I got it working, but I don't remember the steps anymore... :(  I have music and artwork transfer working and I'm updating my last.fm stats with lastPod, but video transfer is still lacking, sort of... see, the videos are transfered, but they show up having zero length, as in "0:00". Weird.

---

### Post by bomanizer on 2008-01-13
> **Hoppiesbox said:**
>  I'm going to give Thin Liquid Film a try for the conversion of the video - I've got a feeling that will work. 

It will, sorta... the encoding is ok for ipods, but I tested the upload using WinXP+iTunes. Amarok doesn't upload the mp4.... :mad:

---

### Post by shadowh511 on 2008-01-15
Third try, no luck

help please

---

### Post by Folk Theory on 2008-01-15
[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)
try this.

also is thin liquid film in the repositories?

---

### Post by devehf on 2008-01-21
I feel the need to point out that you really need to uninstall and reinstall Amarok as described in the instructions of original post. I blew that off thinking that since I had recently installed Amarok I would be ok. This is not the case. AFAIK, you need to reinstall Amarok after installing the new libgpod-0.6.0 software so all the magical interoperation between Amarok and libgpod works correctly. I think someone else mentioned this higher up in this thread.

Oh and if anyone from [Apple]("http://discussions.apple.com/category.jspa?categoryID=151") is reading this thread, take note how much [interest]("http://discussions.apple.com/thread.jspa?messageID=6307319&#6307319") there is in your products running on our preferred OS. I wouldn't run iTunes on Linux, but why not make it easier for consumers to use your products as we please? Yes there is an additional support cost to add another OS, sure. But think of the marketing value of a million nerds promoting your products to their friends because they work on one of the most amazing community projects in computing history.

---

### Post by narghile on 2008-01-21
OK!

its definitely possible to get music and covers working with amarok...after lots of tinkering.

now has anyone figured out how to get photos uploaded. ive got tripod installed and working but i only get thumbs to show, full size images show a black screen..

Any post info or google results are from early 2007. is there something out there im missing?

---

### Post by ryrules1 on 2008-01-22
i followed all the steps however when i hit the last one it says this, any ideas???? because i would love to get my 6g finally working.


rysanderson@rysandersonLAP:~/Desktop/libgpod-0.6.0$ ipod-read-sysinfo-extended /dev/sdc1 /media/RY\'S\ IOPOD/
bash: ipod-read-sysinfo-extended: command not found

---

### Post by devehf on 2008-01-23
[QUOTE=ryrules1;4185916
ipod-read-sysinfo-extended /dev/sdc1 /media/RY\'S\ IOPOD//QUOTE]

IOPOD?

do you mean IPOD?

Not sure if a typo would make a difference.

---

### Post by ryrules1 on 2008-01-24
yes I have it correctly i misnamed my ipod when i reformatted it in windows.

---

### Post by frame45 on 2008-01-25
I have a 160GB Silver iPod classic Model # MB145LL with iPod software 1.0.2PC 

Has anyone had any luck with one of these models. Also I know that this thread is for Amarok but has anyone tried using Songbird by mozilla?? Just curious. 

I haven't had time yet to try all the patches at the beginning of the post but I will post info if I get it working. 

Thanks for all the info from everyone.

---

### Post by rshel on 2008-01-25
No luck; same problems as reported above.  Connects, transfers music, on disconnect--no music.  Not worth the hassle.  Nice try though.  Apple sucks!  I'm using my ipod as a paperweight.

---

### Post by Deathknell on 2008-01-25
OP is my saviour and hero for all eternity.

Now I just have to fix my Klauncher problems and Linux will be a usable OS for me.  Wuwu.

---

### Post by Mobiesque on 2008-01-26
Well something is amiss here. I've followed the instructions and can now load songs onto muh nano 4gig in Rhythmbox (amarok still doesn't recognize it) and the songs show up, however, the second you disconnect and come up to the 'music' menu the unit freezes and you gotta reset it. If you can scroll it down to the shuffle option on the menu before the 'music' selection freezes, you can listen to all the tunes.

Is my junk broke? Help would be most appreciated.

---

### Post by Hoppiesbox on 2008-01-27
Floola is still probably the best choice for anyone having troubles with amarok :) It's not a well known app, but it works better than you'd imagine! Works for all iPood gens.

---

### Post by jdbausch on 2008-01-27
> **Hoppiesbox said:**
> Floola is still probably the best choice for anyone having troubles with amarok :) It's not a well known app, but it works better than you'd imagine! Works for all iPood gens.

I'm subscribed to this thread, and everytime I see a message pop up, I'm tempted to come write the same thing...  I struggled with my ipod classic 80giger for waaaayy to long, until I took Hoppiesbox's suggestion, and it just worked.

---

### Post by bomanizer on 2008-01-28
> **jdbausch said:**
> I'm subscribed to this thread, and everytime I see a message pop up, I'm tempted to come write the same thing...  I struggled with my ipod classic 80giger for waaaayy to long, until I took Hoppiesbox's suggestion, and it just worked.

Are you able to use all the main features with Floola? I tried it onche 'baut a month ago and it didn't work. What version of Floola do you have? I'm tempted to ditch amarok, 'cause its pointless to have those kde libs for the sake of one program.

Thanks in advance!

---

### Post by jdbausch on 2008-01-28
with floola I can:
upload music, and videos
delete music and videos
edit the tags on music and videos
play music  (never tried videos) from the ipod
upload artwork

I think the only thing it is supposed to do that it does not is eject the ipod when you exit holding shift.  (I have to unmount it manuall)

I'm using floola 2.5 (the current verstion)  and I have the most recent firmware on my ipod classic as well.

I use itunes at the office occasionally, and there have been no issues stemming from running both apps to access this ipod.

---

### Post by bomanizer on 2008-01-28
Ok, thanks!

I got the recent version and all is ok!

---

### Post by edfromballarat on 2008-01-30
Thanks for the original post.

I have ipod classic 160gb black

I had difficulties after installing a non functioning version of libgpod and not fully uninstalling it before trying all the different methods of fixing the "no music" problem.  The direct copying of the serial number into the SysInfo file did not work.  

However, after deleting the Sysinfo file, completely unistalling libgpod and gtkpod and amarok and deleting the libgpod folder and then redownloading and extracting the libgpod file from sourceforge and doing a fresh compile, after reinstalling amarok it worked fine.  I used the 80gb 6th gen black setting and songs are copying fine and come up when the ipod is unplugged.

Solving this problem was better than drugs.  Uninstalling itunes on Vista computer, copying music file  by file, uploading from ipod to desktop, deleting music from ipod with one click.  IT IS WORTH THE EFFORT!  Those of you who are about to give up, keep reading the threads and trying new settings, you'll get there in the end, I did!

---

### Post by kc600 on 2008-01-30
Thank for starting this great thread. My iPod works now. I have an iPod Classic (80G) Silver, and i run Ubuntu 7.10 (Gutsy).

I ran into a couple of problems whose solutions i'd like to share with you:

First of all, there seems to be an error in libgpod: compiling stopped in the directory "po". The reason turned out to be that the variable $(GMSGFMT) in the Makefile was empty, but this command was still called (with parameter -o). So the shell complained it couldn't find command -o. When configuring, the absence of MSGFMT or GMSGFMT was noticed correctly, so i think it's a configuration error.
Solution: I commented out the relevant line in po/Makefile, because it seemed necessary only to translations. This solved the problem and libgpod compiled just fine.

Second, when following step 6 in the original post, i have not renamed "libgpod" to "libgpod2" in the checkinstall menu. This way, created library files will also be called libgpod instead of libgpod2, and they will work with the indicated symbolic links.

2008/03/03 EDIT:

About that first point: I submitted this to the libgtkpod mailing list and got this reply:
> 
Date: Sun, 03 Feb 2008 13:43:28 +0900
From: Jorg Schuler 
Subject: Re: [Gtkpod-devel] possible error in libgpod po/Makefile?
To: gtkpod-devel <gtkpod-devel@lists.sourceforge.net>

Well, I guess you need to have msgfmt, which is included in gettext.

As far as I can see, we make no effort to support compiling libgpod 
without gettext. If you have installed gettext and configure complains 
about a missing msgfmt, your setup is broken.

Cheers,


JSc.


---

### Post by lanemeyer67ss on 2008-01-30
Regarding Floola, I've downloaded it and double click it, but nothing happens.  I've run it successfully in XP, but I just installed Ubuntu last night and can't get this to work.

I'm a newb to this so instructions would help.  My 6G Classic iPod is detected when I plug it in.

---

### Post by jdbausch on 2008-01-30
> **lanemeyer67ss said:**
> Regarding Floola, I've downloaded it and double click it, but nothing happens.  I've run it successfully in XP, but I just installed Ubuntu last night and can't get this to work.

I'm a newb to this so instructions would help.  My 6G Classic iPod is detected when I plug it in.

where did you extract the file to?

the download for floola is a .tar.gz file.  I extracted it to a folder in my home directory so the path for me is:

/home/jdbausch/Floola-linux/Floola

and I can run it fine from there, or from a folder within the ipod itself.

I know this might appear basic, but you do identify yourself as a newb, so we have to ask the basic questions...


oh yeah, this should probably go in the floola forums found here:

[http://www.floola.com/modules/newbb/](http://www.floola.com/modules/newbb/)

---

### Post by lanemeyer67ss on 2008-01-30
i fixed it and Floola is working for me now.

Apparently I didn't have any Repositories updated.  I followed the instructions here and it works!

[http://ubuntuforums.org/showpost.php?p=3723797&postcount=4](http://ubuntuforums.org/showpost.php?p=3723797&postcount=4)

I'm confused why this wasn't activated from my initial install, but oh well, works now!

---

### Post by Folk Theory on 2008-01-31
i installed floola and it works fine...but it wont recognize my ipod nano 4GB (amarok, rytmbox do)

---

### Post by rshel on 2008-02-01
Floola worked fine most of the time for me with the 80g classic.  Sometimes it would seize up at the very end of copying music and I would have to kill floola, eject the ipod, and reconnect or risk having my ipod report itself empty of all things.   Another big problem with floola for me is that it does not do photos.  Does anyone know of a utility that will transfer photos to ipod with the current crApple encrypted databases?  I use ipod for presentations (using jpeg files, composite video cable connected to projector, etc.) and it is a wonderfully convenient alternative to carrying around a laptop.  But I have to boot into windows and use itunes to transfer presentations to it.  And I really hate dual-booting.

Thanks!

---

### Post by TwoFlightsDown on 2008-02-04
I did the 
"sudo checkinstall -D"
with the capital "D" and that's what got it finally working for me.  Thanks for the help!  Now my IPOD finally can recognize the music I put on it.

Thanks to everybody who worked through this!

---

### Post by adamsjw2 on 2008-02-08
Has anyone been able to get the iphone or itouch to work? I want to be free of Vista/Itunes. If need be, I'll run itunes in a virtual machine. Any suggestions?
TIA

---

### Post by Harry789 on 2008-02-09
I cannot get past this

Here is where it fails, see the last bit:

I did
sudo checkinstall

and got the error below at the bottom

laan97ac@laan97ac-laptop:~/Desktop/libgpod-0.6.0$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 - Maintainer: [ root@laan97ac-laptop ]
1 - Summary: [ compiled_libgpod-0.6.0 ]
2 - Name: [ libgpod ]
3 - Version: [ 0.6.0 ]
4 - Release: [ 1 ]
5 - License: [ GPL ]
6 - Group: [ checkinstall ]
7 - Architecture: [ i386 ]
8 - Source location: [ libgpod-0.6.0 ]
9 - Alternate source location: [ ]
10 - Requires: [ ]

Enter a number to change any of them or press ENTER to continue: 2
Enter new name:
>> libgpod2

This package will be built according to these values:

0 - Maintainer: [ root@laan97ac-laptop ]
1 - Summary: [ compiled_libgpod-0.6.0 ]
2 - Name: [ libgpod2 ]
3 - Version: [ 0.6.0 ]
4 - Release: [ 1 ]
5 - License: [ GPL ]
6 - Group: [ checkinstall ]
7 - Architecture: [ i386 ]
8 - Source location: [ libgpod-0.6.0 ]
9 - Alternate source location: [ ]
10 - Requires: [ ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/laan97ac/Desktop/libgpod-0.6.0/src'
make[2]: Entering directory `/home/laan97ac/Desktop/libgpod-0.6.0/src'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
/bin/bash ../libtool --mode=install /usr/bin/install -c 'libgpod.la' '/usr/local/lib/libgpod.la'
/usr/bin/install -c .libs/libgpod.so.3.0.0 /usr/local/lib/libgpod.so.3.0.0
/usr/bin/install: setting permissions for `/usr/local/lib/libgpod.so.3.0.0': No such file or directory
(cd /usr/local/lib && { ln -s -f libgpod.so.3.0.0 libgpod.so.3 || { rm -f libgpod.so.3 && ln -s libgpod.so.3.0.0 libgpod.so.3; }; })
(cd /usr/local/lib && { ln -s -f libgpod.so.3.0.0 libgpod.so || { rm -f libgpod.so && ln -s libgpod.so.3.0.0 libgpod.so; }; })
/usr/bin/install -c .libs/libgpod.lai /usr/local/lib/libgpod.la
/usr/bin/install: setting permissions for `/usr/local/lib/libgpod.la': No such file or directory
/usr/bin/install -c .libs/libgpod.a /usr/local/lib/libgpod.a
/usr/bin/install: setting permissions for `/usr/local/lib/libgpod.a': No such file or directory
chmod 644 /usr/local/lib/libgpod.a
ranlib /usr/local/lib/libgpod.a
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
test -z "/usr/local/include/gpod-1.0/gpod" || mkdir -p -- "/usr/local/include/gpod-1.0/gpod"
/usr/bin/install -c -m 644 'itdb.h' '/usr/local/include/gpod-1.0/gpod/itdb.h'
/usr/bin/install: setting permissions for `/usr/local/include/gpod-1.0/gpod/itdb.h': No such file or directory
make[2]: Leaving directory `/home/laan97ac/Desktop/libgpod-0.6.0/src'
make[1]: Leaving directory `/home/laan97ac/Desktop/libgpod-0.6.0/src'
Making install in tools
make[1]: Entering directory `/home/laan97ac/Desktop/libgpod-0.6.0/tools'
make[2]: Entering directory `/home/laan97ac/Desktop/libgpod-0.6.0/tools'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
/bin/bash ../libtool --mode=install /usr/bin/install -c 'ipod-read-sysinfo-extended' '/usr/local/bin/ipod-read-sysinfo-extended'
/usr/bin/install -c .libs/ipod-read-sysinfo-extended /usr/local/bin/ipod-read-sysinfo-extended
/usr/bin/install: setting permissions for `/usr/local/bin/ipod-read-sysinfo-extended': No such file or directory
test -z "" || mkdir -p -- ""
test -z "" || mkdir -p -- ""
make[2]: Leaving directory `/home/laan97ac/Desktop/libgpod-0.6.0/tools'
make[1]: Leaving directory `/home/laan97ac/Desktop/libgpod-0.6.0/tools'
Making install in tests
make[1]: Entering directory `/home/laan97ac/Desktop/libgpod-0.6.0/tests'
make[2]: Entering directory `/home/laan97ac/Desktop/libgpod-0.6.0/tests'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/laan97ac/Desktop/libgpod-0.6.0/tests'
make[1]: Leaving directory `/home/laan97ac/Desktop/libgpod-0.6.0/tests'
Making install in po
make[1]: Entering directory `/home/laan97ac/Desktop/libgpod-0.6.0/po'
file=`echo de | sed 's,.*/,,'`.gmo \
&& rm -f $file && -o $file de.po
/bin/sh: -o: not found
make[1]: *** [de.gmo] Error 127
make[1]: Leaving directory `/home/laan97ac/Desktop/libgpod-0.6.0/po'
make: *** [install-recursive] Error 1

**** Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

laan97ac@laan97ac-laptop:~/Desktop/libgpod-0.6.0$


why why why?

Kubuntu 7.10, ipod nano 8gb

---

### Post by Berryjiveuptown5 on 2008-02-15
Not to be rude, but you should really read the forums before posting.  [Here's the solution on page 2. ]("http://ubuntuforums.org/showpost.php?p=3826640&postcount=17") 

Also, try 'sudo make install'

Edit: TwoFlightsdown answered your question TWO POSTS above yours.

---

### Post by k9nacl on 2008-02-15
nevermind! i'm an idiot. just had to read the wiki.

---

### Post by k9nacl on 2008-02-17
well i've still had no luck with this. on ubuntu, have tried rhythm box, amarok, and floola (with all necessary plugins). rhythm and amarok will transfer the songs, but then they appear as "other"  on my ipod. floola will transfer some songs, randomly, but about 35gigs worth of them show up as "other". then, after another restore, floola will just crash.


guess i'll just use my laptop with xp.

---

### Post by Ni85 on 2008-02-17
I don't get any error running all the procedure, but i still can't see my music on the ipod! am i supposed to restore everything before running all this and then upload my music for the "first time", or should it actually let me see the music that was already on it?
i have a 160gb iPod classic, latest generation.
thanks

---

### Post by Pod_Man on 2008-02-19
Okay so i am going a little insane here haha....

I keep getting the same error from both floola and yamipod: I enter the 6th gen and the correct fwid, but they dont accept it as correct. I have found plenty of people asking this question, but no answers. Might it be my ipod firmware? (i only have 1.0.3) or something else?

I dont have a windows comp at school where i live, so i cant get onto itunes to restore my already broken itunes.db file.

---

### Post by DreamerHxC on 2008-02-24
Excellent!
sudo checkinstall didn't work for me so I directly did sudo make install and it worked!
Then I linked the libraries and I executed that script about the extended info and now I can listen to music on my iPod, but unfortunatelly it seems to be that I cannot see all the album covers I had into my iPod, or at least my iPod shows none of them now.
Any help?
Thanks!

EDIT: Alright, this is another kind of problem, I still haven't solved but I know where to look for the solution.
Thanks for all.

---

### Post by casperlingus on 2008-02-28
SOLVED CHECKINSTALL PROBLEM:

I am not quite sure if this worked overall, but I figured out the error from checkinstall.  I don't have the error in front of me anymore, but it had something to do with not being able to find 

```
/usr/local/lib/python2.5/site-packages/gpod/_gpod.a
```

and others like it.  Well if you look for that directory, you find there is no gpod directory in /usr/local/lib/python2.5/site-packages/ and it definitely attempted to make one before it spit out the error.  For whatever reason, even with sudo, it couldn't make the directory.  So I issued the command 

```
sudo mkdir /usr/local/lib/python2.5/site-packages/gpod
```

and then ran "sudo checkinstall" again.  It works!  Well checkinstall works.  I haven't yet determined if I can write to the iPod....

EDIT:  This **did** work for me.  I am now using Rhythmbox to write to the iPod.  Only problem is it's really slow...

---

### Post by lanemeyer67ss on 2008-03-01
^^^^^^^^
This post above worked for me!  Thanks!!  Amarok now works for my Classic 80GB, although I had to do a fresh install of Ubuntu 7.10 to clean up all the mistakes I made. 

Also, I've tried Floola, gtkpod, and Wine+iTunes and all gave me errors of some sort.  This is the only thing that's worked yet.

edit: I will say that I downgraded my iPod firmware from 1.1.1 to 1.0.3, and made sure to plug the USB cable into the back of my laptop, not the side.  Not sure if that was part of the reason this worked, but in all my searching for an answer, those came up.

---

### Post by Mega_Fauna on 2008-03-03
> **ryrules1 said:**
> yes I have it correctly i misnamed my ipod when i reformatted it in windows.

Let me guess, it's colour is silver?

As in IOSILVER?

---

### Post by wubrgamer on 2008-03-04
what firmwares do you know to work with this method ?

I have a feeling that I might need to downgrade, but I don't want to downgrade too far down...

---

### Post by doctorcorn2002 on 2008-03-05
I'm having trouble with this part

ipod-read-sysinfo-extended /dev/sda1 /media/IPOD

after I press enter nothing happens except getting

>
>

Is this supposed to happen? And in Amarok the transfer button won't work.

thanks

---

### Post by cbr954 on 2008-03-05
Im having problems with the last command /dev/sda1 /media/IPOD says i dont have permission. I logged in as myself and as the root and same thing.

---

### Post by lanemeyer67ss on 2008-03-05
have there been any updates on how to transfer videos?  i can transfer them, but i can't get the ipod to recognize them.

---

### Post by cfmunster on 2008-03-12
I got stuck on the checkinstall step like a lot of other users. I used casperlingus mkdir method on page 18 of this thread to create the missing directory and was able to build the libgpod package. I created the links like in the original instructions on the thread, but my iPod was still not visible on my system. My system, BTW, is Gutsy (7.10) and I have a 160 GB iPod Classic. 

dmesg revealed this:

[175009.612000] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[175009.624000] sd 4:0:0:0: [sdc] Spinning up disk....ready
[175011.940000] sd 4:0:0:0: [sdc] 39023511 4096-byte hardware sectors (159840 MB)
[175011.940000] sd 4:0:0:0: [sdc] Write Protect is off
[175011.940000] sd 4:0:0:0: [sdc] Mode Sense: 68 00 00 08
[175011.940000] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[175011.940000] sd 4:0:0:0: [sdc] 39023511 4096-byte hardware sectors (159840 MB)
[175011.940000] sd 4:0:0:0: [sdc] Write Protect is off
[175011.940000] sd 4:0:0:0: [sdc] Mode Sense: 68 00 00 08
[175011.940000] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[175011.940000]  sdc: sdc1
[175012.132000] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[175012.132000] sd 4:0:0:0: Attached scsi generic sg2 type 0

so I did this to connect my iPod:

sudo mkdir /media/ipod
sudo mount /dev/sdc1 /media/ipod
ls /media/ipod

and my iPod appeared. Checking further, I found that /media/ipod/iPod_control/Device/SysInfo had no contents, so I ran:

sudo lsusb -v | grep -i Serial

to get the 16 digit Firewire id and

vi /media/ipod/iPod_control/Device/SysInfo

and I inserted the Firewireid in the file with this format:

FirewireGuid: 0x<16_digit_ID>

Then I installed Amarok:

sudo apt-get install amarok

Next I ran Amarok and configured it to use MySQL, which I already had installed on my system. Follow these directions if you want to use MySQL but don't know how: [http://amarok.kde.org/wiki/MySQL_HowTo]("http://amarok.kde.org/wiki/MySQL_HowTo"). 

It took Amarok awhile to build the initial database, but now I have my iPod playable from inside Ubuntu. 

Thanks to everyone on the thread and elsewhere who contributed to the solution! You guys rock!

:guitar:

---

### Post by csall on 2008-03-13
I have previously had ipod 3g working under ubuntu gutsy 32 bit, however i am having trouble setting up for my x64 laptop.

When I get to this step I am stuck. Please Help!

sudo apt-get build-dep libgpod2


craig@LAPTOP:~/Desktop/libgpod-0.6.0$ sudo apt-get build-dep libgpod2Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for libgpod


not sure what to do. Thanks for help in advance!

---

### Post by csall on 2008-03-13
sorry for asking for help so soon. After realizing my mistake, I went into synaptic and source to my repositories. Hopefully, I won't have any other bumps... Thanks

---

### Post by csall on 2008-03-13
Ahh.. spoke too soon... At the last step I need some advice/help... Here is the output:

craig@LAPTOP:~/Desktop/libgpod-0.6.0$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             56585724   3465740  50245556   7% /
varrun                  191048       196    190852   1% /var/run
varlock                 191048         0    191048   0% /var/lock
udev                    191048        76    190972   1% /dev
devshm                  191048        24    191024   1% /dev/shm
lrm                     191048     38324    152724  21% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              3793036   3608720    184316  96% /media/IPOD

craig@LAPTOP:~/Desktop/libgpod-0.6.0$ ipod-read-sysinfo-extended /dev/sda1 /media/IPOD
bash: ipod-read-sysinfo-extended: command not found


I don't think I did anything wrong? The ipod-read line should have remained the same so i just pasted it...

Thanks for help in advance

---

### Post by csall on 2008-03-13
Okay, so I figured that out by dredging through multiple pages of this post.... However no cigar on transferring music.. always says No Music... but data is transferred to the drive

I am using 1.0.2 firmware.... is what the problem is? I need help I hate iTunes and Windows!!!!

---

### Post by Berryjiveuptown5 on 2008-03-24
I believe your solution is installing and using Floola (mentioned several times in the forum) instead of using Amarok/Rthymbox.  Not only because it is very easy to install and use, but also because you can transfer and watch video as well.  And works with itunes. 

Also, you might want to try reading this install guide found [here]("http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/").

Some people had to switch the order of the files downloaded, but this is one of the more straightforward approaches.  Personally, Floola is the answer to anyone still reading this, at least until Amarok 2 or something else comes out and does all the config for you.

---

### Post by RoadRunner_UK on 2008-03-27
Had amorak installed but could not get it to see my ipod.
When i connect the ipod, ubuntu launches "Music Player" which 'sees' my ipod and all the tunes on it.
Amorak just fails to see it at all.

Tried the above install and just get this error:```
****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
```

Any help much appreciated.

I have 3 ipods and I would like to just be able to copy files from my ipod to my laptop, then from my laptop to any ipod.

---

### Post by DragonJoker on 2008-03-30
hi!!
i'm italian so i'm not sure my english is very well, but i'll try to explain:
i used amarok 1.47 and all worked great (except when syncronyzing LOADS of music). then i saw amarok 1.48 was on the net and I upgraded...
now i can't set the right ipod model (classic 80gb) cause it ends at 6xth gen (80 gb video or smth)
so i cannot view music on my f***** ipod.
i think that's because of the setting of the ipod model because i re-installed libgpod 0.6.0 and have read ipodsysinfoextended...
i don't know how to do
please help... thanks a lot DR J

---

### Post by DragonJoker on 2008-03-30
hum...i tried uninstall and reinstall amarok 1.4.7 and that goes perfectly...that's a little contraddition cause amarok developers say it's "stable" but...that's linux...bye...hope this will help
dr j

---

### Post by Folk Theory on 2008-04-02
cool. i'll try that

---

### Post by Folk Theory on 2008-04-06
btw will Hardy be better in this area? meaning will we have to jump through hoops to get an ipod to work or will it work by default?

---

### Post by fiatguy85 on 2008-04-10
Hardy has libgpod 0.6.0 so it should work with these.  I followed the guide and had the same error a lot of people were getting:

```
make[5]: *** [install-gpodLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings/python'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/bindings'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
```

and fixed it by doing:

```
sudo make install
```
then
```
sudo checkinstall -D
```

All happily working now with amarok and gtkpod

---

### Post by DragonJoker on 2008-04-11
hi...i would like to know if anyone gets the error "failed to write ipod db" while syncing with amarok...i get it when i sync many songs...amarok (1.4.7)  works correctly only if i sync some songs...then i have to disconnect and to reconnect the ipod...(classic, 80gb, black)
any hints?

---

### Post by Moustacha on 2008-04-16
I can confirm this works. Thanks ghostbear :D Thought i'd have to go into windows to use winamp to add songs to my ipod.

---

### Post by Incompetnce on 2008-04-16
Can anyone using the Hardy beta confirm my hope that Hardy + gtkpod = seamless effortless ipod synching?

because with so little time before the actual release, i don't feel like jumping through hoops to get my ipod working...

---

### Post by xaocan on 2008-04-16
> xaoc@xaoc-desktop:~/libgpod-0.6.0$ ipod-read-sysinfo-extended /dev/sdb1 /media/IPOD
bash: ipod-read-sysinfo-extended: command not found

didn't find any answer... any suggestions?

---

### Post by DragonJoker on 2008-04-17
anyone could help me?? please?? -.-

---

### Post by williamson389 on 2008-04-17
I have the same proble of runsink. it stated installation error and failed.

---

### Post by DragonJoker on 2008-04-20
hi... i read about "no support for classic A1238"...damn... i got it...
what should I do? my problems are above

---

### Post by ericxhall on 2008-04-21
Ok, look, I cant read through all those pages, I did everything on the first page. And it all finished well, but it just simply wont work.
I am trying amarok and gtkpod, so please, could someone help me out?

also I just tried again and got this before i linked the directories or what have you.

grep: /var/tmp/JmonhZVlVSjFCAZNjqTZm/newfile: No such file or directory

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package

Do you want to see the log file?  [y]:

---

### Post by adrimaxi on 2008-04-27
Question : what about in Hardy ? Does we have to do the same ?

---

### Post by jtreach on 2008-04-27
No, hardy has the latest version of libgpod installed and the amarok in hardy's repositories uses the latest libgpod....

Good aye?!

---

### Post by adrimaxi on 2008-04-27
Thanks for this fast reply.
Excuse me if it is a it off topic, I had my 1st iPod today... And I don't know really how it is working!
Virtually all my Music is encoded in ogg, so how can I handle it with the ipod. Does Amarok or Rhythmbox synchronise it in the ipod ?
Thank you in advance,
adrimaxi

---

### Post by wubrgamer on 2008-04-27
Nope, you'll have to re-encode, amarok MIGHT do this on-the-fly per song and keep it off your hard disk

and why are you using a lossy format anyway?

hard drives are CHEAP, use FLAC!

---

### Post by Folk Theory on 2008-04-27
i think most people stick to lossy.

---

### Post by Moustacha on 2008-04-27
> **adrimaxi said:**
> Thanks for this fast reply.
Excuse me if it is a it off topic, I had my 1st iPod today... And I don't know really how it is working!
Virtually all my Music is encoded in ogg, so how can I handle it with the ipod. Does Amarok or Rhythmbox synchronise it in the ipod ?
Thank you in advance,
adrimaxi

For amarok you need to download a transcoding script. There's only a couple. I tried dirtyxcoder, it didn't seem to transcode on the fly though. It uses gstreamer so you need all the plugins for that.

---

### Post by wubrgamer on 2008-04-27
Honestly, I think your best move is to just re-encode your entire library into a more compatible format I'd go from ogg --> wav 

then delete the ogg

then wav --> mp3

BUT KEEP THE wav (or flac!)

This is going to be a long process for you, sorry.

---

### Post by ericxhall on 2008-04-27
Word, Whats the best way to recopy music from ipod to my system.

---

### Post by Folk Theory on 2008-04-27
amarok?

ive done it with amarok with no problem

---

### Post by ericxhall on 2008-04-27
oh for real?
i havent even tried haha.

---

### Post by ericxhall on 2008-04-28
Upon trying this I click autodetect in Amarok and given the message "No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them. You can test this by running "dcop kded mediamanager fullList" in a Konsole window."

I ran that code but it didnt work.

---

### Post by wubrgamer on 2008-04-28
you might have to manually add it

search around in the media players tab in the amarok configuration

someone else might be able to help you with that

---

### Post by jedibrand on 2008-05-01
Woot! Got my A1238 to sync AND play music via Amarok+libgpod2. 

Basically, followed instructions on page 1 with some caveats. After running the "ipod-read-sysinfo-extended" script/tool, if a cat of the SysInfo file at "/media/ROXY/iPod_Control/Device/" (yes, I named my iPod "ROXY" :) does not produce a "FirewireGuid" entry, then you will need to manually insert that line into the file. Instructions on how to do so can be found within the file "README.SysInfo". A STRONG word of caution is necessary here--make sure to follow those instructions to the tee, which means, don't forget to append a "0x" to the beginning of the FireWireGuid! This is what got me stuck for a good two hours while I painstakingly plucked nearly everyone of my hairs out! For your reference, the SysInfo file should look something like this:

ModelNumStr: xB147
FirewireGuid: 0x000A2700130EAE61

Ok, so, the only other thing or two to add is, and this may or may not be necessary, but make sure that you are using the latest Ubuntu build of Amarok, which you will likely have to get from one of the gutsy-backports, assuming that you are using gusty (you should be!). To do that, just make your way over to your trusty /etc/apt/sources.list file and uncomment the two lines in corresponding section that mentions the backports. Once that's done, do an "sudo apt-get update" and proceed with the instructions on page 1, incorporating my amendments as necessary.

Finally, make sure that you see entries for the Classic iPod inside Amarok, as the iPod Video ones will simply not do.

Good luck--hope this helps!

---

### Post by prem1er on 2008-05-01
Thanks to everyone for their help on this post.  I got it working after installing Hardy and following the instructions on page one.  I'm still having album art issues, so if someone could link me to somewhere in this post to sort that out it would be much appreciated!

---

### Post by bilal.17 on 2008-05-01
does anyone if the Ipod Touch can be synced with Amarok

---

### Post by bilal.17 on 2008-05-01
I mean does libgpod work with the Ipod Touch

---

### Post by prem1er on 2008-05-01
Haven't tried it personally, but the Amarok forums says that it does.

---

### Post by wubrgamer on 2008-05-01
it should work, just be willing to submit a few bug reports

please do!

but it might "just work"(t)

---

### Post by KevNice on 2008-05-03
I read through this whole thread and so far there doesnt seem to be a solution for this problem:

```
-laptop:~/Desktop/libgpod-0.6.0$ ipod-read-sysinfo-extended /dev/sdb2 /media/IPOD
Couldn't read xml sysinfo from /dev/sdb2

```

Several other posters had the same issue.. any ideas??

---

### Post by ilSignorCarlo on 2008-05-03
On Ubuntu Hardy Heron, with this command:

```
sudo apt-get build-dep libgpod2
```

I get this:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to find a source package for libgpod2 
```

What can I do?
Thanks.

---

### Post by abhiroopb on 2008-05-13
Don't you want libgpod3?

Also, this worked great, music synced, etc. I only transferred a few songs to test it out. Then I took it out. Now what happens is that the iPod mounting is very tempremental. It sometimes does it and it sometimes doesn't. I have to restart it, and it may just work. This time I restarted it and it didn't automatically mount. I have no idea why its doing this! It shows up on lsusb and I can manually mount it as a filesystem. Any thoughts?

---

### Post by abhiroopb on 2008-05-13
SOLVED:

Mount the iPod manually. Navigate to the folder. Delete the iPod_Control folder, and it resets all the data. Then mounting it works like a charm! :)

---

### Post by Folk Theory on 2008-05-13
what folder?

---

### Post by abhiroopb on 2008-05-13
"iPod_Control"

---

### Post by csmicfool on 2008-05-20
> **abhiroopb said:**
> SOLVED:

Mount the iPod manually. Navigate to the folder. Delete the iPod_Control folder, and it resets all the data. Then mounting it works like a charm! :)

How do you mount the ipod manually?  The whole problem I keep having is being unable to mount the ipod at all.  I've tryed a couple ways of mounting it but have had no luck at all.

If I open Computer I can see the ipod as "FireWire Drive", but trying to open/mount it results in an error:

"Unable to mount location: Can't mount file"

---

### Post by abhiroopb on 2008-05-20
so you connect it as firewire? if that is the case I'm sorry but I have no experience with that :(

---

### Post by csmicfool on 2008-05-23
So I thought I had figured this problem out.  No matter what settings I change or commands I used the ipod could not be mounted.

I restarted computer in Windows (hardest, most painful part of this), deleted hidden iPod_Control folder (saved backup to not lose music).

I then went back to Ubuntu, and the ipod mounted automatically- no trouble at all.

I then restored all music files and it was working properly.  I then made the mistake of disconnecting it from the computer and now cannot re-mount it until I delete the whole iPod_Control folder again.

The one thing I did not have a chance to test was if the ipod could be disconnected and remounted if I do not restore those files before disconnecting.  I will post again once I've tested it more.

Using firewire should be no different from USB, the device is just recognized as /dev/sdf

abhiroopb, could you please tell me how you were able to manually mount the drive?

---

### Post by abhiroopb on 2008-05-23
Ok to mount:

Create a folder in the media directory:

```

sudo mkdir /media/iPod2

```

Check where the iPod is mounted:
```

sudo fdisk -l

```

When you find the iPod (it should be FAT) make a note of what it says (e.g. /dev/sdf)

then type in the following:
```

sudo mount /dev/sdf /media/iPod2

```

This should have it mounted.

I had a similar problem where it wouldn't mount. It can be a number of problems.
1. iTunesLock File (if you see my guide below and put in the correct eject command this should be deleted).
2. Issues with your HAL - not sure how to sort this out
3. computers just being a pain - which is what I think happened with mine, as it sometimes would connect and sometimes wouldn't!

Started a new thread: [http://ubuntuforums.org/showthread.php?p=5025712#post5025712](http://ubuntuforums.org/showthread.php?p=5025712#post5025712)

Where I outlined how I got libgpod3 and Amarok working with the iPod

---

### Post by csmicfool on 2008-05-23
totally not working the way it should- this is the problem I've been having along.  I guess I did know how to mount it manually, but the command does not work- I get the error "can't read superblock" unless iPod_Control is deleted.

when I use "sudo fdisk -l" the ipod is not listed even though you can see it in nautilus as a firewire drive. I will try deleting the iPod_Control folder again using windows and see if I can find a working solution through trial/error (mostly error I'm sure).

---

### Post by abhiroopb on 2008-05-23
unfortunately it was trial and error for me as well! But i did get it working so if you do get it connected I suggest following what I did on: [http://ubuntuforums.org/showthread.p...12#post5025712](http://ubuntuforums.org/showthread.p...12#post5025712)

Also take a look at this [http://ubuntuforums.org/showthread.php?t=641802](http://ubuntuforums.org/showthread.php?t=641802)

If you can see it in nautilus does it not mean it is mounted already? What does the command lsusb give you?

---

### Post by csmicfool on 2008-05-23
The first link you sent does not work- it doesn't load a specific post.  I had already seen the second link but that does not apply in my case because I cannot get that far.

The lsusb command may not help either- I think that is specific to usb ports, no?

I can see "Firewire Drive" in nautilus under the computer directory, but it does not actually get mounted.  If I try to open that i get a mounting error.  If I try to mount it manually I get the superblock error.

I was able to get around that once by deleting iPod_Control folder using windows.  However, I have tried this fix again and it no longer works.  I also tried doing an iPod restore using windows to start fresh and that had similarly plagued results even if I was able to remove the iPod_Control dir the ipod could not be mounted.

Anyway- road trip tonight after work for memorial day weekend so I am not going to risk killing the thing any moreso till next week (already lost one use of my DRM songs from itunes after restoring the ipod).  I'll also try playing with the usb cable instead of firewire to see if that makes any difference.

---

### Post by abhiroopb on 2008-05-23
Yes it could be a usb v firewire issue. Sorry couldn't help more...

The link got chopped in the middle: [http://ubuntuforums.org/showthread.php?t=804761](http://ubuntuforums.org/showthread.php?t=804761)

---

### Post by csmicfool on 2008-05-23
thanks for the corrected link.  I can see right away that step 3 may not work for me, but I will hold on to this and play with it next week.

Have a good holiday!

---

### Post by abhiroopb on 2008-05-23
Enjoy you're trip, unfortunately its exam time for me :P

---

### Post by MeanStreak on 2008-06-06
Firstly, thanks very much for this fix. I just have one question - 

I've spent a lot of time updating my song library in Amarok and fear this information will be lost if I re-install Amarok to get this fix working - has anyone been successful getting their iPod Classic to work *without* uninstalling/re-installing Amarok?

---

### Post by abhiroopb on 2008-06-06
It won't work without reinstalling as as amarok has to work AFTER removal of libgpod2. If you remove libgpod2 without installing amarok (through the new repository), amarok will get removed with libgpod2. You can try without that step but I don't think it will work. Also the amarok folder with your settings shouldn't be erased so all your settings will be intact. If you are scared about this go to //home/<amarok>/.kde/share/apps and backup the amarok folder.  Also when you edit music the METADATA of the each song is edited and permanently saved with the songs, something that can't be changed anyway.

---

### Post by Nin10dude on 2008-06-11
Quick question... in Amarok, is there any way to organize videos as being a TV show? As of now, everything goes into the Movies section of my iPod, and I'd just like it to be a bit more organized. In addition, after being set as a TV show, is there any way to set a video as being part of a specific TV show/season? If it's not possible in Amarok, does anyone know of any programs which can do that?

---

### Post by demon68 on 2008-07-03
> **Nin10dude said:**
> Quick question... in Amarok, is there any way to organize videos as being a TV show? As of now, everything goes into the Movies section of my iPod, and I'd just like it to be a bit more organized. In addition, after being set as a TV show, is there any way to set a video as being part of a specific TV show/season? If it's not possible in Amarok, does anyone know of any programs which can do that?

same question here. on win i used 'TVTagger' it's java, it starts on Ubuntu, but it doesnt write any tag in the file. on win i was able to set all the data with it, even the release date. is there a similar program on linux?

---

### Post by Ghostbear121 on 2008-07-16
Holy crap I never thought this thread would grow so big..  I posted and kinda forgot about it. :)


Thanks to everyone who picked up my slack with the follow-up questions!

---

