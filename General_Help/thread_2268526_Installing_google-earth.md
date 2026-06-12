---
title: "Installing google-earth"
date: 2015-03-09
forum: General Help
---

### Post by sam_baker2 on 2015-03-09
hi,
I am trying to install google-earth.  I just installed xubuntu 14.04.2 LTS 64 bit on an intel laptop
 I went to this web site and followed the instructions.
[http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html](http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html)

 I ran this command the terminal:
```
sudo apt-get install libfontconfig1:i386 libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386    
```
but got this:
```
    Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.3)
                        Recommends: libgl1-mesa-dri:i386 (>= 7.2)
E: Unable to correct problems, you have held broken packages.            
```


I did this:

```
sudo dpkg -i google-earth-stable_current_i386.deb
sudo apt-get install -f       
```
but when I run google-earth i get this:
```
  ./googleearth-bin: error while loading shared libraries: libfontconfig.so.1: cannot open shared object file: No such file or directory     
```


any help appreciated

---

### Post by slickymaster on 2015-03-09
Try this:```
sudo apt-get -s install libgl1-mesa-glx-lts-utopic:i386
```The **-s** parameter makes it a simulation. If everything go as expected, just remove that parameter from the command to actually install the package.

---

### Post by sam_baker2 on 2015-03-09
thanks for reply slickmaster.
I tried that, but when I try google-earth in terminal I get:
```
./googleearth-bin: error while loading shared libraries: libfontconfig.so.1: cannot open shared object file: No such file or directory
   
```

when I try to cd to ./google-earth-bin, I get:
```
 bash: cd: ./googleearth-bin: No such file or directory
   
```

---

### Post by slickymaster on 2015-03-09
I assume you're on 64-bit system. Please see this: [Google-Earth will not launch]("http://askubuntu.com/questions/130970/google-earth-will-not-launch")

---

### Post by sam_baker2 on 2015-03-09
I have a /opt/google/earth/free/googleearth-bin,
but when I try to run googleearth-bin in the terminal while cd'd to /opt/google/earth/free , I get:
```
 googleearth-bin: command not found 
```

trying ```
 ldd /opt/google/earth/free/googleearth-bin 
```

gives me this:

```

    linux-gate.so.1 =>  (0xf7701000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf76ce000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf7688000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf74d9000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf74d4000)
    libgoogleearth_free.so => not found
    libglobalnew.so => not found
    libQtGui.so.4 => not found
    libQtNetwork.so.4 => not found
    libfontconfig.so.1 => not found
    libfreetype.so.6 => not found
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf739f000)
    libXrender.so.1 => not found
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf738b000)
    libGL.so.1 => /usr/lib/i386-linux-gnu/mesa/libGL.so.1 (0xf72f9000)
    libGLU.so.1 => not found
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf72f0000)
    libQtCore.so.4 => not found
    libQtWebKit.so.4 => not found
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf7206000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf71e9000)
    /lib/ld-lsb.so.3 => /lib/ld-linux.so.2 (0xf7704000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf71c7000)
    libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0xf719e000)
    libglapi.so.0 => /usr/lib/i386-linux-gnu/libglapi.so.0 (0xf7184000)
    libXdamage.so.1 => /usr/lib/i386-linux-gnu/libXdamage.so.1 (0xf7180000)
    libXfixes.so.3 => /usr/lib/i386-linux-gnu/libXfixes.so.3 (0xf717a000)
    libX11-xcb.so.1 => /usr/lib/i386-linux-gnu/libX11-xcb.so.1 (0xf7177000)
    libxcb-glx.so.0 => /usr/lib/i386-linux-gnu/libxcb-glx.so.0 (0xf715f000)
    libxcb-dri2.so.0 => /usr/lib/i386-linux-gnu/libxcb-dri2.so.0 (0xf7158000)
    libxcb-dri3.so.0 => /usr/lib/i386-linux-gnu/libxcb-dri3.so.0 (0xf7154000)
    libxcb-present.so.0 => /usr/lib/i386-linux-gnu/libxcb-present.so.0 (0xf7150000)
    libxcb-sync.so.1 => /usr/lib/i386-linux-gnu/libxcb-sync.so.1 (0xf7149000)
    libxshmfence.so.1 => /usr/lib/i386-linux-gnu/libxshmfence.so.1 (0xf7146000)
    libXxf86vm.so.1 => /usr/lib/i386-linux-gnu/libXxf86vm.so.1 (0xf713f000)
    libdrm.so.2 => /usr/lib/i386-linux-gnu/libdrm.so.2 (0xf7132000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf712e000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf7127000)


```

---

### Post by yancek on 2015-03-09
Try in a terminal:

```
/opt/google/earth/free/googleearth

```

---

### Post by sam_baker2 on 2015-03-09
trying googleearth in terminal yields:

```
bash: /opt/google/earth/googleearth: No such file or directory

```
but there is a googleearth in that directory ( a shell script )

---

### Post by slickymaster on 2015-03-09
Did you get to try the solution I mention on my [previous post]("http://ubuntuforums.org/showthread.php?t=2268526&p=13242320&viewfull=1#post13242320")?

---

### Post by sam_baker2 on 2015-03-09
@slickmaster
I went to this web site and tried some things:
[http://askubuntu.com/questions/130970/google-earth-will-not-launch](http://askubuntu.com/questions/130970/google-earth-will-not-launch)
Although, they are talking about 12.04.
I have just recently installed 14.04 on my laptop.


I had 12.04 on the laptop before and have 12.04 on a desktop now. It worked on the laptop before
as well as works now on the desktop.

---

### Post by mc4man on 2015-03-09
It won't hurt to re run this to make sure you have all - 
```
sudo apt-get install  libfontconfig1:i386 libx11-6:i386 libxrender1:i386 /
libxext6:i386 libgl1-mesa-glx-lts-utopic:i386 libglu1-mesa:i386 libglib2.0-0:i386 /
libsm6:i386 lsb-core
```

Then assuming you installed the 32 bit google-earth packge - 
```
google-earth
```
or find the .desktop launcher & d. click on (I don't use xubuntu, in ubuntu it's right in the Dash

(- google-earth must be run from "google-earth" command as it will pre-load some .so's

Edit:
if you want to test launching via google-earth's .desktop then  - 
```
gtk-launch google-earth
```

---

### Post by gifford on 2015-03-09
This is the link I used to install Google earth in Ubuntu 14.04.
[http://www.noobslab.com/2014/03/install-google-earth-in-ubuntulinux.html](http://www.noobslab.com/2014/03/install-google-earth-in-ubuntulinux.html)

I tried various other methods without success. Good luck.

---

### Post by sam_baker2 on 2015-03-09
I ran 
```
 
sudo apt-get install libfontconfig1:i386  libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386  libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
 
```
and  then a font agreement of some sort came up in the terminal and it just hung there.
I closed out the terminal and running the install again gave me this:
```
   
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```gtk-launch google-earth gives me this 

```

./googleearth-bin:  error while loading shared libraries:  libfontconfig.so.1: cannot open  shared object file: No such file or  directory


```

---

### Post by sam_baker2 on 2015-03-09
I ran
```

sudo apt-get install libfontconfig1:i386  libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386  libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
 
```
and then a font agreement of some sort came up in the terminal and it just hung there.
I closed out the terminal and running the install again gave me this:
```
  
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```gtk-launch google-earth gives me this

```

./googleearth-bin:  error while loading shared libraries:  libfontconfig.so.1: cannot open  shared object file: No such file or  directory


```

---

### Post by slickymaster on 2015-03-09
> **sam_baker2 said:**
> I ran
```

sudo apt-get install libfontconfig1:i386  libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386  libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
 
```
and then a font agreement of some sort came up in the terminal and it just hung there.
That would be the package** ttf-mscorefonts-installer**, which contains the Microsoft freeware web fonts. If it failed to install just run```
sudo apt-get install ttf-mscorefonts-installer
``` and accept the EULA. Use the Tab and Enter keys to accept the EULA in the window that pops up.
> **sam_baker2 said:**
> I closed out the terminal and running the install again gave me this:
[CODE]  
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
<--snip-->
See my post [here]("http://ubuntuforums.org/showthread.php?t=2248189&p=13143213&viewfull=1#post13143213"), to fix that error.

---

### Post by yancek on 2015-03-09
For the installation of the ttf-mscorefonts, the default is set to No or to Not Accept so as stated above, you need to use the Tab key so that Yes or OK is highlighted and then hit the enter key.  The suggestion in my last post was what I use on 12.04, I don't have googleearth on 14.04 so I don't know if it changed.  It is:

/opt/googlearth/free/googleearth.  You left out the 'free' directory, maybe that was just a typo?

---

### Post by sam_baker2 on 2015-03-10
latest horror story:

I did a apt-get install on each one of these individually:
```

libc6-i386 libglib2.0-0:i386 libsm6:i386  libglu1-mesa:i386 libgl1-mesa-glx:i386 libxext6:i386 libxrender1:i386  libx11-6:i386 libfontconfig1:i386 lsb-core

```
to see which ones were not loading , and all loaded except for libgl1-mesa-glx:i386
and I got this:
```

Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:  The following packages have unmet dependencies:  libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.3)                         Recommends: libgl1-mesa-dri:i386 (>= 7.2) E: Unable to correct problems, you have held broken packages.

```

The message says "Recommends: libgl1-mesa-dri:i386 (>= 7.2)", so I installed  libgl1-mesa-dri:i386
I got a bunch of library removals, some adds, and some program removals.
I then downloaded and installed google-earth using this:
```

wget -O google-earth64.deb http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb

```
and also tried: 
```

wget -O google-earth64.deb http://dl.google.com/dl/earth/client/current/google-earth-stable_current_amd64.deb

```

No luck running google-earth and I noticed that opt/google/earth/free folder simply did not exists anymore.
I rebooted the laptop and now I cannot get the desktop at all, I can only get into the command line console using 
ctrl/alt F1 ( can't exit using F7 to get into the desktop also )

---

### Post by egeezer on 2015-03-10
Use
```
startx
```
in the F1 console to get your GUI back.

Slightly later: Just saw you're using Xubuntu.  The command might have to be
[CODE]startxfwm4[CODE]

---

### Post by sam_baker2 on 2015-03-10
I get this trying startx:

```

/etc/X11/xinit/xserver: 3: exec:  /usr/bin/x: not found
xnit: giving up
xnit: unable to connect to X server: connection refused
xnit: server error

```

Have to leave for a few hours, will be back latter

---

### Post by sam_baker2 on 2015-03-11
I finally got google-earth to work somewhat.
For the record, I completely re-installed the xubuntu .iso, then I installed the libraries
and now google-earth will run. I think part of the problem was that I am
getting wifi disconnects, causing some of the stuff to not fully download.
 
The only problem in google-earth is that the pictures will not display. When a little picture icon
on google-earth is selected, a square, white box comes up but no picture.
A few years ago, on either 10 or maybe 12 xubuntu, I had the same problem.
I was thinking it had something to do with the libcurl.so.x library, don't remember

Also, I notice that there is some pixelation in google-earth.
See attached photos.

For the record, I installed xubuntu 14.04.2 64 bit, and this is on a Lenovo 
laptop, intel processor with Intel graphics controller.

---

### Post by slickymaster on 2015-03-11
> **sam_baker2 said:**
> <---snip--->
 
The only problem in google-earth is that the pictures will not display. When a little picture icon
on google-earth is selected, a square, white box comes up but no picture.
<---snip--->
[How to solve blank Panoramio photo problem in google earth on ubuntu]("https://bkjaya.wordpress.com/2014/04/27/how-to-solve-blank-panoramio-photo-problem-in-google-earth-on-ubuntu-2/")

---

### Post by sam_baker2 on 2015-03-11
the website says that this solution is for 64bit google-earth.

this is the google-earth I think I installed. Is it 64 bit, or how can I tell for sure?
```

google-earth-stable_current_i386.deb

```

---

### Post by slickymaster on 2015-03-11
That's the 32-bit version. The 64-bit is```
google-earth-stable_current_amd64
```

---

### Post by sam_baker2 on 2015-03-11
uh-oh. Do you think if I download and install the 64 bit version, [google-earth_amd64.deb]("http://drive.noobslab.com/data/apps/google-earth/google-earth_amd64.deb") as sugested from that website,
that it will mess something up?
( my laptop & xubuntu is 64 bit version )

---

### Post by slickymaster on 2015-03-11
> **sam_baker2 said:**
> uh-oh. Do you think if I download and install the 64 bit version, [google-earth_amd64.deb]("http://drive.noobslab.com/data/apps/google-earth/google-earth_amd64.deb") as sugested from that website,
that it will mess something up?
( my laptop & xubuntu is 64 bit version )
It's your call, but I think it's worth the shot. Worst case scenario you can always purge it from your system and reinstall from scratch once again. ;)

---

### Post by sam_baker2 on 2015-03-11
the website shows the 64 bit google-earth comes from that website 
```

wget -O google-earth64.deb [http://drive.noobslab.com/data/apps/google-earth/google-earth_amd64.deb](http://drive.noobslab.com/data/apps/google-earth/google-earth_amd64.deb)
   --->  google-earth64.deb

```
would it be better to get it from googles download wesite instead?
```

http://www.google.com/earth/download/ge/agree.html
    --->   google-earth-stable_current_amd64.deb

```

---

### Post by slickymaster on 2015-03-11
> **sam_baker2 said:**
> the website shows the 64 bit google-earth comes from that website 
```

wget -O google-earth64.deb [http://drive.noobslab.com/data/apps/google-earth/google-earth_amd64.deb](http://drive.noobslab.com/data/apps/google-earth/google-earth_amd64.deb)
   --->  google-earth64.deb

```
would it be better to get it from googles download wesite instead?
```

http://www.google.com/earth/download/ge/agree.html
    --->   google-earth-stable_current_amd64.deb

```
Yes, I'd go with Google website instead as you're not sure of how up-to-date the noobslab version is.

---

### Post by sam_baker2 on 2015-03-11
I am going to install google website google-earth-stable_current_amd64.deb 
It is in my /tmp folder, I am cd'd there. What command do I call up to install it?

---

### Post by The Cog on 2015-03-11
The command would be:
```
sudo dpkg -i /tmp/google-earth-stable_current_amd64.deb
```

---

### Post by slickymaster on 2015-03-11
Run, in the terminal```
sudo dpkg -i name_of_google-earth-stable_current_amd64_package.deb
```

EDIT: lol, The Cog beat me.

---

### Post by sam_baker2 on 2015-03-11
I  don't need to remove the google-earth I have now before installing the 64 bit?

---

### Post by slickymaster on 2015-03-11
I'm not 100% sure, but I'd remove the 32-bit version. I think you cannot install both of the -dev packages on the same system at the same time as they contain some of the same files. Multi-arch doesn't enable cross-compilation support, which is what you'd be trying to do.

---

### Post by sam_baker2 on 2015-03-11
opps, I remove the version of google-earth I had and then installed the 64bit earth that came from google website.
got this:
```

Selecting previously unselected package google-earth-stable.
(Reading database ... 184258 files and directories currently installed.)
Preparing to unpack google-earth-stable_current_amd64.deb ...
Unpacking google-earth-stable (7.1.2.2041-r0) ...
dpkg: dependency problems prevent configuration of google-earth-stable:
 google-earth-stable depends on ia32-libs; however:
  Package ia32-libs is not installed.

dpkg: error processing package google-earth-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Errors were encountered while processing:
 google-earth-stable


```

---

### Post by slickymaster on 2015-03-11
That's the old issue about Google Earth 32bit package not supporting multiarch so it doesn't install all the 32bit dependencies it needs to run on Ubuntu 64bit.

But if you're willing to try something, you could see if we manage to fool him. Try, in a terminal window:```
sudo apt-get install ia32-libs
```and please post back the full output you get.

---

### Post by sam_baker2 on 2015-03-11
I got this doing  sudo apt-get install ia32-libs

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0

E: Package 'ia32-libs' has no installation candidate

```

---

### Post by slickymaster on 2015-03-11
Sorry, that's my bad, ia32-libs was indeed removed since 11.10 when multiarch has been added. So what I had in mind will not have any chances in succeeding. Maybe you really have to deal with the fact of running the 32-bit version.

---

### Post by sam_baker2 on 2015-03-11
ok, I took 64bit google-earth out and re-installed google-earth-stable_current_i386.deb 
Hope they get a fix.

---

### Post by sam_baker2 on 2015-03-11
it is odd, I have google-earth 6.2.2.6613 running right now on a AMD 64 bit desktop
using xubuntu 12.04, and it works fine.

---

