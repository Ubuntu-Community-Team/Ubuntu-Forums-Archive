---
title: "Howto: Gyachi - Yahoo! messenger, Webcam, room voice chat, photo sharing"
date: 2008-04-29
forum: General Help
---

### Post by loell on 2008-04-29
for lucid and maverick
try installing from this repo.

[https://launchpad.net/~adilson/+archive/experimental](https://launchpad.net/~adilson/+archive/experimental)

---

### Post by halln on 2008-05-02
cool but how cool -0 degs b themable b ni do I'm using kopete right now. The only problem is I can't voice chat dyn s pinas. Daghan n b ang ubunteros dha s dvo?

---

### Post by loell on 2008-05-02
use gizmo if you must call a yahoo messenger user,  [http://gizmo5.com/pc/download/]("http://gizmo5.com/pc/download/")

for webcam, room voice chat, and photosharing then gyachi.

---

### Post by chilliepierre on 2008-05-02
I am having issues with my webcam when it comes to GYACHI.  Please assist.  It works in Ekiga.

Thanks!

---

### Post by Sef on 2008-05-02
Thank you for providing that Gyachi deb link.

---

### Post by loell on 2008-05-03
glad to be of service :)

---

### Post by loell on 2008-05-03
> **chilliepierre said:**
> I am having issues with my webcam when it comes to GYACHI.  Please assist.  It works in Ekiga.

Thanks!

hi, your webcam is a v4l2 webcam only which is great, but gyachi is a v4l application only, like the state of Adobe flash.

a workaround is to use [http://www.swift-tools.net/Flashcam/]("http://www.swift-tools.net/Flashcam/")

---

### Post by halln on 2008-05-03
Sir loell I've downloaded the file and install it. I'm having a problem with my webcam, (not broadcasting) downloaded the flashcam-1.1 and this is what happened:
cc -O -shared -fPIC -o flashcamhook.so flashcamhook.c
flashcamhook.c:8:19: error: stdio.h: No such file or directory
flashcamhook.c:9:20: error: stdlib.h: No such file or directory
flashcamhook.c:10:20: error: string.h: No such file or directory
flashcamhook.c:11:25: error: sys/syscall.h: No such file or directory
flashcamhook.c:12:23: error: sys/ioctl.h: No such file or directory
flashcamhook.c:13:28: error: linux/videodev.h: No such file or directory
flashcamhook.c:14:19: error: errno.h: No such file or directory
flashcamhook.c:20: error: &#8216;NULL&#8217; undeclared here (not in a function)
flashcamhook.c: In function &#8216;scanVloopDevices&#8217;:
flashcamhook.c:27: error: storage size of &#8216;cap&#8217; isn&#8217;t known
flashcamhook.c:29: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
flashcamhook.c:31: warning: incompatible implicit declaration of built-in function &#8216;sprintf&#8217;
flashcamhook.c:33: error: &#8216;SYS_open&#8217; undeclared (first use in this function)
flashcamhook.c:33: error: (Each undeclared identifier is reported only once
flashcamhook.c:33: error: for each function it appears in.)
flashcamhook.c:35: error: &#8216;errno&#8217; undeclared (first use in this function)
flashcamhook.c:35: error: &#8216;ENOENT&#8217; undeclared (first use in this function)
flashcamhook.c:38: error: &#8216;VIDIOCGCAP&#8217; undeclared (first use in this function)
flashcamhook.c:40: error: &#8216;VID_TYPE_CAPTURE&#8217; undeclared (first use in this function)
flashcamhook.c:45: warning: incompatible implicit declaration of built-in function &#8216;strdup&#8217;
flashcamhook.c: In function &#8216;readConfig&#8217;:
flashcamhook.c:56: error: &#8216;FILE&#8217; undeclared (first use in this function)
flashcamhook.c:56: error: &#8216;map&#8217; undeclared (first use in this function)
flashcamhook.c:62: warning: assignment makes pointer from integer without a cast
flashcamhook.c:63: warning: incompatible implicit declaration of built-in function &#8216;alloca&#8217;
flashcamhook.c:63: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
flashcamhook.c:64: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
flashcamhook.c:65: warning: incompatible implicit declaration of built-in function &#8216;strcat&#8217;
flashcamhook.c:67: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
flashcamhook.c:75: warning: incompatible implicit declaration of built-in function &#8216;strdup&#8217;
flashcamhook.c: In function &#8216;open&#8217;:
flashcamhook.c:104: warning: incompatible implicit declaration of built-in function &#8216;sprintf&#8217;
flashcamhook.c:107: error: &#8216;SYS_open&#8217; undeclared (first use in this function)
flashcamhook.c:111: error: &#8216;errno&#8217; undeclared (first use in this function)
flashcamhook.c:111: error: &#8216;ENOENT&#8217; undeclared (first use in this function)
make: *** [flashcamhook.so] Error 1

and if I open the voice chat, I'm having these:

Cannot run gyvoice due to the following missing files:

      tsd32.dll
      tssoft.acm

Not in the following directories:
      /usr/lib/win32/
      /usr/local/lib/win32/

need help pls. salamat po

---

### Post by loell on 2008-05-03
for voice chat you need to have the codecs either from medibuntu or download

[http://downloads.sourceforge.net/gyachi/gyachi-codecs.deb]("http://downloads.sourceforge.net/gyachi/gyachi-codecs.deb")

you need to install the kernel headers before compiling flashcam

```
apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r`
```

yeah, i know, this is an inconvenience for v4l2 webcam users, be sure that yours is really a v4l2 webcam though before trying this one.

---

### Post by chilliepierre on 2008-05-03
I tried the flashcam and I still can't get it to work.  I tried to do the apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r`

but it told me that permission was denied.


Any follow-up?

---

### Post by loell on 2008-05-03
add it with a **sudo** at the beginning of the command ;)

---

### Post by halln on 2008-05-03
Sir Loell, my webcam is still dead it wont work anymore even in kopete and ekiga since I installed hardy. This webcam is working happy with gutsy before and I already did your tutorial. The only thing is I cannot install the flashcam till now, same error (the one I posted earlier). Voice chat seems working now, thanks 4 ur how to. MANY THANKS and need more help here.

---

### Post by halln on 2008-05-03
I already manage to make my webcam to work on kopete and ekiga but not on gyachi. Still need help pls. (stuck on flashcam) I'm now using 2.6.24-17 kernel, does it make sense?

---

### Post by chilliepierre on 2008-05-03
Me too...still stuck on Flashcam...!!!!

---

### Post by halln on 2008-05-05
bump

---

### Post by loell on 2008-05-06
howdy, i was too busy this couple of days.

@halln, same error despite installing the kernel headers?

---

### Post by halln on 2008-05-08
This what happened after installing flashcam:
-desktop:~/flashcam-1.1$ make
cc -O -shared -fPIC -o flashcamhook.so flashcamhook.c
flashcamhook.c:8:19: error: stdio.h: No such file or directory
flashcamhook.c:9:20: error: stdlib.h: No such file or directory
flashcamhook.c:10:20: error: string.h: No such file or directory
flashcamhook.c:11:25: error: sys/syscall.h: No such file or directory
flashcamhook.c:12:23: error: sys/ioctl.h: No such file or directory
flashcamhook.c:13:28: error: linux/videodev.h: No such file or directory
flashcamhook.c:14:19: error: errno.h: No such file or directory
flashcamhook.c:20: error: ‘NULL’ undeclared here (not in a function)
flashcamhook.c: In function ‘scanVloopDevices’:
flashcamhook.c:27: error: storage size of ‘cap’ isn’t known
flashcamhook.c:29: warning: incompatible implicit declaration of built-in function ‘printf’
flashcamhook.c:31: warning: incompatible implicit declaration of built-in function ‘sprintf’
flashcamhook.c:33: error: ‘SYS_open’ undeclared (first use in this function)
flashcamhook.c:33: error: (Each undeclared identifier is reported only once
flashcamhook.c:33: error: for each function it appears in.)
flashcamhook.c:35: error: ‘errno’ undeclared (first use in this function)
flashcamhook.c:35: error: ‘ENOENT’ undeclared (first use in this function)
flashcamhook.c:38: error: ‘VIDIOCGCAP’ undeclared (first use in this function)
flashcamhook.c:40: error: ‘VID_TYPE_CAPTURE’ undeclared (first use in this function)
flashcamhook.c:45: warning: incompatible implicit declaration of built-in function ‘strdup’
flashcamhook.c: In function ‘readConfig’:
flashcamhook.c:56: error: ‘FILE’ undeclared (first use in this function)
flashcamhook.c:56: error: ‘map’ undeclared (first use in this function)
flashcamhook.c:62: warning: assignment makes pointer from integer without a cast
flashcamhook.c:63: warning: incompatible implicit declaration of built-in function ‘alloca’
flashcamhook.c:63: warning: incompatible implicit declaration of built-in function ‘strlen’
flashcamhook.c:64: warning: incompatible implicit declaration of built-in function ‘strcpy’
flashcamhook.c:65: warning: incompatible implicit declaration of built-in function ‘strcat’
flashcamhook.c:67: warning: incompatible implicit declaration of built-in function ‘printf’
flashcamhook.c:75: warning: incompatible implicit declaration of built-in function ‘strdup’
flashcamhook.c: In function ‘open’:
flashcamhook.c:104: warning: incompatible implicit declaration of built-in function ‘sprintf’
flashcamhook.c:107: error: ‘SYS_open’ undeclared (first use in this function)
flashcamhook.c:111: error: ‘errno’ undeclared (first use in this function)
flashcamhook.c:111: error: ‘ENOENT’ undeclared (first use in this function)
make: *** [flashcamhook.so] Error 1
What do you think? You're the expert!!! he he he:)\\:D/

---

### Post by Desterie on 2008-05-08
Hmm is there a Gyachi client for 64 bit architectures?  I downloaded your link, but when I tried to install it said Error: wrong architecture.  Umm I am a pretty fresh newbie around here, so I kinda need things spelled out step by step right now.  Thanx

---

### Post by loell on 2008-05-08
@halln,  i might have to explore if flashcam can be packaged as deb for easier installation, let's see if its possible.


@Desterie, theres no 64bit package at this time, you could install the package using getlibs [http://ubuntuforums.org/showthread.php?t=769590]("http://ubuntuforums.org/showthread.php?t=769590")

---

### Post by halln on 2008-05-10
Actually, That's the one I want to ask from you a deb package for easy install. YOU'RE THE MAN!!!!!!:guitar:

---

### Post by halln on 2008-05-16
bump

---

### Post by loell on 2008-05-16
hi halln, **pasensya na ;)** deb package for flashcam is not possible at the moment or its just beyond my limited knowledge in packaging and autotools.

i'd like to share this response from flashcam developer

> autotools instead of hand coded makefile? (New)
By: loell (loell) - 2008-05-13 00:19
hi, could you make a more conventional makefiles via autotools? i think its easier to package.


      RE: autotools instead of hand coded makefile? (New)
      By: Swift (swift-toolsProject Admin) - 2008-05-13 22:59
      I like custom Makefiles to be honest, I see nothing conventional with autotools, maybe easier to use. 
      Remember the audience is **developers**, I've never got any feedback on how worth the project is. 
       
      You're welcome to create auto stuff. The package contains a kernel module, which implies compile at 
      install time, for the rest I agree the frame forwarder can be autotools driven. It will create more files 
      than simple Makefile, but why not. 
       
      I still consider the whole thing unfinished and really temporary. 
       
      -Swift



but, if you like we could go back on trying to figure out your error in compiling flashcam.

i just did a closer look at the error you previously posted, i think you haven't installed **build-essential**

---

### Post by halln on 2008-05-17
where can i get this build-essential thing, is it in synaptics?

---

### Post by ShodanjoDM on 2008-05-17
No source code for 1.1.31? The latest source version in Sourceforge tops at 1.1.26 and it was from March 1st.

I would like to compile myself though.

---

### Post by loell on 2008-05-17
> **halln said:**
> where can i get this build-essential thing, is it in synaptics?

yeah in synaptic, or

```
sudo apt-get install build-essential
```

or

[Click This APT-URL to install build essential]("apt:build-essential")

:)

---

### Post by loell on 2008-05-17
> **ShodanjoDM said:**
> No source code for 1.1.31? The latest source version in Sourceforge tops at 1.1.26 and it was from March 1st.

I would like to compile myself though.

despite 1.1.31's huge change over 1.1.0  its still considered a minor release hence no tar source package, you can get the source code in the CVS

---

### Post by halln on 2008-05-18
Boss Loell, Flashcam already installed after installing build essentials but my webcam is still not working just a black screen. Do I have to change this webcam?

---

### Post by ShodanjoDM on 2008-05-19
> **loell said:**
> despite 1.1.31's huge change over 1.1.0  its still considered a minor release hence no tar source package, you can get the source code in the CVS

Thanks. Compiling now :)

---

### Post by loell on 2008-05-19
> **halln said:**
> Boss Loell, Flashcam already installed after installing build essentials but my webcam is still not working just a black screen. Do I have to change this webcam?

in the webcam window, theres **connection** menu --> **properties**

try to adjust the brightness & contrasr see if there any change.

---

### Post by halln on 2008-05-20
I tried it already, change the settings for brightness,contrast, etc but nothing, still black screen.

---

### Post by loell on 2008-05-20
i haven't ask you this, can you do a **lsusb** 

copy and paste it here , so we'll know what webcam you have.

---

### Post by halln on 2008-05-20
Here it goes:
-desktop:~$ lsusb 
Bus 002 Device 006: ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 15d9:0a41  
Bus 001 Device 005: ID 03f0:b202 Hewlett-Packard 
Bus 001 Device 004: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 001 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 002: ID 07b2:5100 Motorola BCS, Inc. SurfBoard SB5100 Cable Modem
Bus 001 Device 001: ID 0000:0000

---

### Post by fiftydollarsocks on 2008-05-20
im running Hardy 64 bit.  i went through the steps regarding getlibs and have gotten gyachi 1.1.0 installed and running just fine.

The problem is when i install the 1.1.31 version.  it installs no problem, but when i run it i get a libgyachi.so not found.

Any quick way to work around this, or is a 64 bit compile of gyachi going to be available?

thanks, matt

---

### Post by dimas869 on 2008-05-20
hello...i am getting this message:
cannot run gyvoice due to the following missing file:
tsd32.dll
tssoft.acm
not in the following directories:
/usr/lib/win32/
/usr/local/lib/win32/

and when i go to this page
[http://sourceforge.net/project/downloading.php?groupname=gyachi&filename=gyachi-codecs.deb&use_mirror=ufpr](http://sourceforge.net/project/downloading.php?groupname=gyachi&filename=gyachi-codecs.deb&use_mirror=ufpr)

the installer get an error message:
Error: conflicts with the installed package "w32codecs"

and is there anyway to better the webcam configuration?
the picture comes cut in half...i am using Creative webcam im vista and ov51x as a driver wich work perfect in others applications.

thanks for the help

---

### Post by tomeriker on 2008-05-20
Hello, I am getting the same error.

conflict with w32codecs

hope there is a fix. I don't care about web cam just the voice chat.

Thanks in advance for your help.

---

### Post by loell on 2008-05-20
gyachi codecs will conflict w32codecs as they are just duplicate files, if you have w32codecs, normally you wouldn't need gyachi codecs.

do you have medibuntu enabled?

---

### Post by loell on 2008-05-20
> **halln said:**
> Here it goes:
-desktop:~$ lsusb 
Bus 002 Device 006: ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 15d9:0a41  
Bus 001 Device 005: ID 03f0:b202 Hewlett-Packard 
Bus 001 Device 004: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 001 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 002: ID 07b2:5100 Motorola BCS, Inc. SurfBoard SB5100 Cable Modem
Bus 001 Device 001: ID 0000:0000

halln, can you test this script, from this thread see if your webcam works with that,

[http://ubuntuforums.org/showthread.php?p=5006350](http://ubuntuforums.org/showthread.php?p=5006350)

---

### Post by dimas869 on 2008-05-20
yes i do have medibuntu enabled but still gyvoice wont start

---

### Post by loell on 2008-05-21
can you find these file for me?

[B]tsd32.dll
tssoft.acm[/B]

in your system?

---

### Post by dimas869 on 2008-05-21
the location is:
/usr/lib/codecs

---

### Post by halln on 2008-05-22
> **loell said:**
> halln, can you test this script, from this thread see if your webcam works with that,

[http://ubuntuforums.org/showthread.php?p=5006350](http://ubuntuforums.org/showthread.php?p=5006350)

still doesn't work 4 me, I may just try 2 replace my webcam and 4 the meantime back 2 kopete while we r sorting this out. :)

---

### Post by loell on 2008-05-22
yeah, good move :)

---

### Post by halln on 2008-05-22
bought a new webcam cheap one, I,m testing it right and it won't work either on gyachi and kopete but it works on ekiga by changing it to v4l2. I tried it with skype no luck as well.kaubo n t ani pre.](*,)

---

### Post by loell on 2008-05-22
heheh, webcams are still  hit or miss choice for linux users.




send ko og PM sa imoha :)

---

### Post by balagosa on 2008-05-22
pareng loell. naa sad ko error. when i start my cam in Gyachi, "ioctl VIDOSPICT" "could not set camera properties"

i already got flashcam, but i didnt run it. i just pointed out, 
```
If you want to support a new application, as root, change to the directory and type:
[root]% ln -s /usr/local/bin/flashcamwrap myApp
```

that is what i did.

am i supposed to run Gyachi and Flashcam simultaneously??

---

### Post by dimas869 on 2008-05-22
> **loell said:**
> can you find these file for me?

[B]tsd32.dll
tssoft.acm[/B]

in your system?


the location in my computer is in
/usr/lib/codecs

---

### Post by loell on 2008-05-22
you can copy those two files and put it in /usr/lib/win32, apparently they are the codecs path now.

---

### Post by loell on 2008-05-22
> **balagosa said:**
> pareng loell. naa sad ko error. when i start my cam in Gyachi, "ioctl VIDOSPICT" "could not set camera properties"

i already got flashcam, but i didnt run it. i just pointed out, 
```
If you want to support a new application, as root, change to the directory and type:
[root]% ln -s /usr/local/bin/flashcamwrap myApp
```

that is what i did.

am i supposed to run Gyachi and Flashcam simultaneously??

yeah, your doing it right. may i know your webcam?

```
lsusb
```

---

### Post by dimas869 on 2008-05-23
> **loell said:**
> you can copy those two files and put it in /usr/lib/win32, apparently they are the codecs path now.

how do i copy them?

---

### Post by balagosa on 2008-05-23
> **loell said:**
> yeah, your doing it right. may i know your webcam?

```
lsusb
```

pre, naa ra oh.

```
daniel@daniel-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 174f:5a11 Syntek 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

**My Cam: Bus 006 Device 002: ID 174f:5a11 Syntek **

my cam works on ekiga and cheese.

---

### Post by balagosa on 2008-05-25
*bump*

---

### Post by loell on 2008-05-25
this is most probably a v4l2 webcam.

---

### Post by balagosa on 2008-05-25
> **loell said:**
> this is most probably a v4l2 webcam.


pare...i have no idead what a v4l2 webcam is.

care to educate me XD

---

### Post by loell on 2008-05-25
in gyachi's context, you'll be needing flashcam to work it out.  you can download it from the first post of the thread, you'll gonna have to compile it first.

---

### Post by balagosa on 2008-05-26
i already did flashcam, as i said it wont work.

---

### Post by balagosa on 2008-05-26
scratch that...already got it working.

(dali raman diay pre, naskip lang nako isa ka instruction)

---

### Post by loell on 2008-05-26
great :)

---

### Post by phalbert on 2008-05-26
Thanks for the deb file.  Gyachi installed okay and it runs but I cannot login.  I get the error "Could not login: Connection timed out." when I try almost all of the available servers.

When I run gyachi from the terminal I get *** DEBUG: UNKNOWN PACKET
TYPE:  [0x7d1/2001]
DATA:  66&#65533;&#65533;1003&#65533;&#65533;

Do you know how I can log in to a chat server?
I'm running on Hardy Heron (Ubuntu 8.04)

Also, I verified that my login username and password work on the Yahoo website, so that's not the problem.

Any help would be appreciated.
Thanks.

---

### Post by Joffa65 on 2008-05-28
Please please is there any chance of a deb for Feisty 7.04?

i tried installing the gutsy deb and I got an error " dependency is not satisfiable: libasound2".
I checked in Synaptic and it tells me I have libasound2 already. Maybe its incompatible.

I have compiled stuff before but have no idea about CVS. Please help!

---

### Post by loell on 2008-05-28
sorry as much as i'd like to build a package for fiesty, i couldn't :(

as i only have two partitions with gutsy and hardy on it..

---

### Post by Joffa65 on 2008-05-29
Tarball source perhaps?

---

### Post by loell on 2008-05-29
you can get the source at , [gyachi.sourceforge.net]("http://gyachi.sourceforge.net")

---

### Post by Joffa65 on 2008-05-29
Thanks loell.

Today I tried both 1.1.0 and 1.1.26 from sourceforge and have hit a dead end.
To compile first requires running the autogen.sh script which throws up fatal errors.

--------------------------------------------------------------

me@me:~/gyachi-1.1.26$ sudo ./autogen.sh
searching for GNU gettext intl directory...
 -> /usr/share/gettext/intl ... found it
copying gettext intl files ...
running aclocal ...
aclocal: configure.ac: 12: macro `AM_DISABLE_STATIC' not found in library
aclocal: configure.ac: 13: macro `AM_PROG_LIBTOOL' not found in library
aclocal: macro `AM_PROG_MKDIR_P' required but not defined
aclocal: macro `AM_PROG_MKDIR_P' required but not defined
aclocal failed, stopping.
---------------------------------------------------------------

Apparently automake v1.5 or later is required. I tried v1.9 and then 1.7 which gave less errors, but 1.5 is not avialable from the repo.

---

### Post by johnthelemon on 2008-05-30
Hi, I love Gyachi for being the only program that handles file transfers exactly like the original messenger. I was using 1.1.0, then I saw this post.
Tried to install Gutsy deb package. It has some dependencies that I have, but an older version although  my Ubuntu is up-to-date. Here they are:
```

The following packages have unmet dependencies:
  gyachi: Depends: libcairo2 (>= 1.6.0) but 1.4.10-1ubuntu4.4 is installed
          Depends: libglib2.0-0 (>= 2.16.0) but 2.14.1-1ubuntu1 is installed
          Depends: libpango1.0-0 (>= 1.20.1) but 1.18.3-0ubuntu1 is installed
          Depends: libssl0.9.8 (>= 0.9.8f-1) but 0.9.8e-5ubuntu3.2 is installed

```
I've installed using --force-depends-version, but that broke my software index and it would only fix it by removing Gyachi.
Thx in advance.

---

### Post by loell on 2008-05-30
try again. then post your gdebi screen shot,   i suspect that you installed the hardy one, but if ever its true that this gyachi for gutsy package will yield an unmet dependency, you'd be the first case to have this issue. ;)

[http://www.mediafire.com/?izgy1gktmxf]("http://www.mediafire.com/?izgy1gktmxf")

---

### Post by johnthelemon on 2008-05-30
Yep, you're right. I quickly downloaded the first package, without reading. And because there's no "hardy" part in it's name, like the gutsy package, i thought it's for all distros.
I've installed the Gutsy package now, works great, thx ;)

---

### Post by Joffa65 on 2008-05-30
Re build on Feisty:

 automake 1.9 worked after installing autotools and libtools (1.7 failed me) and enabled me to finish the autogen script and do:

sudo ./configure --enable-v4l2 --enable-soundevents --enable-statuspixmaps --enable-wine --disable-rpath --enable-plugin_photosharing --disable-plugin_xmms

The configure script is a lot more verbose in indicating whats actually missing!
Ok satisfied all that and it compiled..

sudo make
sudo make install

now when I try to run gyachi i get:
gyachi: error while loading shared libraries: libgyachi.so: cannot open shared object file: No such file or directory

NOW im stuck :( Please help!

EDIT: v1.1.0 compiled successfully but 1.1.26 wont work for me (error quoted above)
EDIT2: No smilies :( . Looks like its back to 1.0.5 if i cant get this going :(

EDIT3: Gave up and upgraded ubuntu 8.04

---

### Post by jarelkamar on 2008-06-07
Thank you 

This worked just perfectly

---

### Post by RJQ on 2008-06-09
It is a way to use GYachI with a 1394 device?, that is how i can get my camera to work in ubuntu, i was wondering if I can use the /dev/raw1394 for this task.

Thanks.

Never mind found it [here]("http://ubuntuforums.org/showthread.php?t=664596&highlight=1394+webcam")

---

### Post by johnthelemon on 2008-06-13
Hi everybody. I've noticed that a URL sent in a PM gets formatted accordingly, and the cursor changes into a hand, but I can't click it. Is this a setting, a bug or Gyachi doesn't have such a feature?
It's annoying when I have to copy-paste a long URL :tongue:

---

### Post by loell on 2008-06-13
by default, you need an opened firefox for the link to be opened, you can change these option in **setup** --> **options** --> **default browser command**

---

### Post by johnlvs2run on 2008-06-13
Gyachi works for chat but not for my aiptek dv5100m webcam.

Do you have a procedure for how the webcam can work with Gyachi.

---

### Post by loell on 2008-06-14
does it work with other webcam applications?

---

### Post by johnlvs2run on 2008-06-14
Yes, it worked well previously with xp.

---

### Post by loell on 2008-06-14
webcam drivers in XP and webcam drivers in linux are not the same, you need to find out if your webcam could work in linux.

---

### Post by johnlvs2run on 2008-06-14
I just got ubuntu and have only tried the webcam in linux in gyachi.

Is there another program to try it?

---

### Post by loell on 2008-06-14
> **johnlvs2run said:**
> I just got ubuntu and have only tried the webcam in linux in gyachi.

Is there another program to try it?

yes, you can try **camorama** , **xawtv** and **cheese** .

---

### Post by manfer on 2008-06-15
Since I made a fresh installation of hardy heron I had installed this program in three ways:

[LIST]
[*]Converting 1.1.26 rpm package to deb package with alien.
[*]Building 1.1.26 version from source.
[*]With this 1.1.31 deb package.
[/LIST]

I get the same error message all times when running the program as normal user: "segmentation fault". I can only run the program as root.

Do you know any way to solve this problem?

---

### Post by loell on 2008-06-15
> **manfer said:**
> Since I made a fresh installation of hardy heron I had installed this program in three ways:

[LIST]
[*]Converting 1.1.26 rpm package to deb package with alien.
[*]Building 1.1.26 version from source.
[*]With this 1.1.31 deb package.
[/LIST]

I get the same error message all times when running the program as normal user: "segmentation fault". I can only run the program as root.

Do you know any way to solve this problem?

i'm not sure whats happening over your setup, could be a component that's been hosed or could be an entirely different thing, in any case

can you delete **.yahoorc** and try to execute it again.

---

### Post by johnlvs2run on 2008-06-15
> **loell said:**
> yes, you can try **camorama** , **xawtv** and **cheese** .

I didn't get any image with those, but not sure if I was doing it right.

---

### Post by loell on 2008-06-15
> **johnlvs2run said:**
> I didn't get any image with those, but not sure if I was doing it right.

ok, so lets find out what your webcam is

copy and paste the output of this command

```
lsusb
```

---

### Post by johnlvs2run on 2008-06-15
> **loell said:**
> ok, so lets find out what your webcam is

copy and paste the output of this command

```
lsusb
```

john@john-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 08ca:2043 Aiptek International, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
john@john-desktop:~$

---

### Post by manfer on 2008-06-16
Manfer
   "segmentation fault" error when running the program as normal user. The program was only working as root.

Loell
   Delete .yahoorc/ on user home directory.


And that solved it. Loell you are a PRO. :guitar:

Thanks.

What could be happening? Garbage from a previous failed installation?

---

### Post by ShelJ on 2008-06-21
I can't get the webcam to work.  I'm using a Logitec orbit.

---

### Post by t.alex on 2008-06-26
Hi,

i have a strange issue concerning the avatar. None of my buddies, that are using the regular Windows messenger can see my avatar icon. All they can see instead is a black box. 
By the way Pidgin has the same issue regarding the buddy icon.

Anyone having this problem?

---

### Post by loell on 2008-06-26
probably windows messenger could not render PNG files accurately..

---

### Post by t.alex on 2008-06-26
Hi,

thanks for the quick reply :)
but no, i'm mot using png's, although i've tried them too. I'm using 96x96 px (i've also tried larger), ~5 KB jpg's.

it's quite simple for me to check if it works, as i have a working Windows in VirtualBox running an Yahoo account and another account running within Gyachi. No matter what i do (in Gyachi), i can't seem to get a picture on the windows side.

---

### Post by johnthelemon on 2008-06-28
Hi there! I got my Microdia webcam working with the SN9C1xx driver at [www.linux-projects.org;](www.linux-projects.org;) works in ekiga, for example. 
Now, I installed flashcam, compiles fine, installs, but I get this:
```

johnthelemon@johnthelemon-desktop:~$ flashcam
Scanning devices
------
Found V4L2 Capture device: /dev/video0 (sn9c102/SN9C1xx PC Camera)
Found V4L Video loopback input: /dev/video2
------
Forwarding frames from /dev/video0 to /dev/video2
Input device: /dev/video0
Size = 160 x 120
Pixel format = JPEG
Bpl = 0
Unsupported format.

```

Had anybody encountered this before?

---

### Post by johnlvs2run on 2008-06-28
> **johnlvs2run said:**
> john@john-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 08ca:2043 Aiptek International, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
john@john-desktop:~$

Any updates on how to get this to work?

Also, Gyahci keeps putting everyone in the flood box and blocking them.

These are people I have chatted with for awhile, so I know they are not flooding me.  
Any way to stop Gyachi from blocking everyone?

---

### Post by loell on 2008-06-28
aiptek webcams mostly use **gspca driver**

to be able to know if indeed the driver is loaded when the webcam is plugged,

type

```
lsmod | grep videodev
```

paste the output here. 

could this be a new webcam?


to stop the flood flagging mechanism

uncheck the basic and advance boot prevention at **setup --> protection tab**.

---

### Post by johnlvs2run on 2008-07-01
> **loell said:**
> to be able to know if indeed the driver is loaded when the webcam is plugged,

```
lsmod | grep videodev
```

The webcam model is from a couple of years ago.

> xxx@xxx-desktop:~$ lsmod | grep videodev
xxx@xxx-desktop:~$

There is no output from typing this.

---

### Post by loell on 2008-07-01
i see, so the driver isn't used :( , 

strange if this isn't new, the device ID  **08ca:2043** should have several reference, but google could only find this post and some other link.

i guess this webcam isn't compatible with linux.

---

### Post by dark-_-blades on 2008-07-01
hi, i've installed flashcam, but how to make it work in gyachi??

the error message is :

> 
An error occured at 'ioctl VIDIOCSPICT'.
Could not set camera properties.


can anybody tell me how to make it work??

---

### Post by johnlvs2run on 2008-07-02
> **loell said:**
> i see, so the driver isn't used :( , 

strange if this isn't new, the device ID  **08ca:2043** should have several reference, but google could only find this post and some other link.

Should the driver work automatically or does it need to be downloaded to work.

---

### Post by loell on 2008-07-02
> **johnlvs2run said:**
> Should the driver work automatically or does it need to be downloaded to work.

yes, the gspca driver works automatically for a compatible webcam as the gspca driver is installed in ubuntu by default, in this case the webcam in question isn't compatible.

---

### Post by acp_ on 2008-07-04
Hi loell,

I have installed gyachi successfully, but seem that my webcom is not working I get "Gyachi (WebCam Broadcaster) An error occured at 'ioctl VIDIOCSPICT'. Could not set camera properties." and "Gyachi (WebCam Broadcaster):Error while querying mmap-buffers." when I click the 'Start my webcam' here is the output of my lswh and lsusb [http://paste.ubuntu.com/24890/](http://paste.ubuntu.com/24890/). can you direct me to a howto to fix this thanks.


Additional info:

 lsmod | grep videodev
videodev               29440  2 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev

So this mean I need to compile flashcam?


-AC

---

### Post by loell on 2008-07-04
it seemsyour webcam is using a uvc driver

can you confirm if the driver is loaded?

**lsmod | grep video**

---

### Post by acp_ on 2008-07-04
here is the output:

uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
video                  19856  0 
output                  4736  1 video
usbcore               146028  6 uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd

---

### Post by loell on 2008-07-04
i see, in this case you need to compile flashcam as this webcam is a v4l2 device, please refer to the first post of the thread.

---

### Post by acp_ on 2008-07-04
Thanks! its now working. hats up to sir loell!

---

### Post by johnlvs2run on 2008-07-08
Loell,
I've found some Aiptek drivers for Linux on the net, but don't know enough about Ubuntu to see if they will work with this DV 5100M.

If I have to get another digital camera/webcam, what reasonably priced brand and models would you recommend?

---

### Post by loell on 2008-07-08
if i have to recommend a webcam brand, that would be **logitech**. ;)

---

### Post by johnlvs2run on 2008-07-09
Loell, thanks.  :)  Should any logitech cam work?

Is it better to get the digital camera separate from the cam?

---

### Post by albasheers on 2008-07-12
i have installed Gyanchi , all its codecs and flashcam 

i am unable to have voice chat and when i start my webcam it show me a error saying errror occured at 'videocspict'could not set the camera property

can any body me?

---

### Post by dynastywarrior on 2008-07-12
Dear Master Loell,

sir your link to download gyachi for hardy heron is not working...it seems "mediafire" has server problems ("No servers are currently available with the requested data on them.Pls. [COLOR="Red"][I]retry[COLOR="Black"][I]in a moment")...but i've retried the whole day & still get the same notification....do you happen to know another link where i can get the package for hardy heron?

thanks in advance.....

---

### Post by loell on 2008-07-12
hi, thanks for the heads up :) , i've added another link from filedropper host.

---

### Post by dynastywarrior on 2008-07-14
Sir loell,

Thanks a lot! your other link is perfect. i had successfully installed gayachi on my system......by the way i'm planning to set-up an internet cafe using ubuntu as OS both for the workstation(about 20 units) and server....

Pls. i need your highly valuable opinion on this...is it better or easier to set-up than a windows, is it more versatile?...do you have any recommendations for a cafe timer and management software for an ubuntu network?

"this world is a better place to live because of people like you"
:):):)

---

### Post by dynastywarrior on 2008-07-14
P.S.
do you have a deb package for gayachi 1.35 for hardy?

thanks again sir loell........

---

### Post by loell on 2008-07-14
i have another thread for a cafe timer ;)

[cyber cafe management / timer for ubuntu]("http://ubuntuforums.org/showthread.php?t=777093") just follow the tips of the entire thread.

version 1.35 didn't had much visible improvement, so 1.33 will  do just fine. :)

hope you'll be successful with your cafe ventures using ubuntu, I know others have. :D

---

### Post by dynastywarrior on 2008-07-15
thanks again sir loell for the link....you really are a GURU of this trade.......
):P):P):P):P):P

---

### Post by jimmy the saint on 2008-07-17
I appreciate the deb packages, but I run amd64.  I am also trying to force myself to complie everything that I install.  how else am I to learn!!  anyway, I went to the sourceforge site and I cannot find the source for any version past 1.1.26.  Am I missing something?

---

### Post by loell on 2008-07-17
have you already tried installing the 32bit package by using getlibs in 64?

---

### Post by peter_babeone on 2008-07-19
> **loell said:**
> i have another thread for a cafe timer ;)

[cyber cafe management / timer for ubuntu]("http://ubuntuforums.org/showthread.php?t=777093") just follow the tips of the entire thread.

version 1.35 didn't had much visible improvement, so 1.33 will  do just fine. :)

hope you'll be successful with your cafe ventures using ubuntu, I know others have. :D

where can I get those versions for ubuntu hardy?

thanks

---

### Post by loell on 2008-07-19
> **peter_babeone said:**
> where can I get those versions for ubuntu hardy?

thanks
are you asking for the cafe timer? or gyachi's latest version?

---

### Post by peter_babeone on 2008-07-20
> **loell said:**
> are you asking for the cafe timer? or gyachi's latest version?

I meant gyachi's latest version :)

---

### Post by U-ZONE on 2008-07-20
Hello Ubuntu World!

Can anybody point me to the right chat room and server for Gyache voice chat please. Any server I enter seems to have no voice chat enabled.

Thanks, m

---

### Post by loell on 2008-07-20
> **peter_babeone said:**
> I meant gyachi's latest version :)

you could compile code from the CVS for the really latest version, but as for the deb package for 1.1.35 and beyond, i'll have to see if it really warrants packaging. until then 1.1.33 deb package is available.

are you looking for some particular fix?

---

### Post by loell on 2008-07-20
> **U-ZONE said:**
> Hello Ubuntu World!

Can anybody point me to the right chat room and server for Gyache voice chat please. Any server I enter seems to have no voice chat enabled.

Thanks, m

just keep on trying, there are times that you really can't get in, it usually works when theres medium users on a chat room.

---

### Post by peter_babeone on 2008-07-20
> **loell said:**
> you could compile code from the CVS for the really latest version, but as for the deb package for 1.1.35 and beyond, i'll have to see if it really warrants packaging. until then 1.1.33 deb package is available.

are you looking for some particular fix?

I'm using the version 1.1.31, and I've just thought, I could get the next versions somewhere.

Anyway thanks for your support :lolflag:

---

### Post by loell on 2008-07-23
hi all, if you have contacts using Yahoo Messenger 9 beta, can you confirm  if you **can not recieve** webcam streams from these contacts?


thanks..

---

### Post by student21 on 2008-07-27
Hi Loell

I've posted my instant messaging problems in the below post:

[http://ubuntuforums.org/showthread.php?p=5389781#post5389781](http://ubuntuforums.org/showthread.php?p=5389781#post5389781)

Yet my instant messaging is not smooth.  Can you guide me if I can use this Gyachi for me and if yes how to?  I 'm a ubuntu newbie and use hardy heron 64 bit in wubi on laptop.

---

### Post by loell on 2008-07-27
hello, gyachi won't give you that exact features. :(

also. doesn't that defeats the purpose when you're using wubi? since you can use yahoo messenger in your windows where your wubi is running?

---

### Post by student21 on 2008-07-27
Hi Loell

My intention is not to keep wubi forever and in recent future I might move it to dedicated partition.  But even hopping between OSes(in wubi) is overwhelming for me.  When I'm browsing from firefox on ubuntu I'd like to access YM buddies and be in contact via voice and video chat.  For this sole purpose, I can't restart and boot into vista immediately.  So I want voice and video chat facility from ubuntu itself.  If Gyachi is not for me, then what can I use?  Did I misunderstand this quote on the first post of this thread? 

> About gyachi: Yahoo! client for Linux operating system supports almost all of the features you would expect to find on the official Windows Yahoo! client: Voice chat, webcams, faders, 'nicknames', audibles, avatars, display images, and more

most notable newest feature: Full implementation of Yahoo! Photosharing with drag n drop and pointer


BTW I hope you've read my post regd. instant messaging problems, so what is wrong with my kopete??  and aMSN??

Thanks in advance.

---

### Post by loell on 2008-07-27
> **student21 said:**
>  If Gyachi is not for me, then what can I use?  Did I misunderstand this quote on the first post of this thread? 

when you say voice you most likely mean pc to pc call, which gyachi can't do yet, as title suggest it means room voice chat only. i use gizmo project to call yahoo messenger user. while streaming the user's webcam through gyachi.

> **student21 said:**
> 
BTW I hope you've read my post regd. instant messaging problems, so what is wrong with my kopete??  and aMSN??

Thanks in advance.

i haven't use kopete and amsn for a long time, so i really have no idea.

---

### Post by student21 on 2008-07-27
Hi Loello

Thanks for the reply!

I didn't get the technical point you want to convey.  I didn't understand what gizmo project is.  Also I did't understand what room voice chat is in this specific context?  May be these technical details fly past my head.  All I know is yahoo have different rooms and one can enter any room(based on topics like culture, religion, language etc) for chat after I log in.  But still if something like 'gyachi' helps me to communicate with my Yahoo messenger buddy with text, voice and video, it'd be helpful for me, but I'm not sure when you say "gyachi can't do yet".   Well, I think I'll have to hunt for some other tool that can help me do these things :(.  Isn't there any other tool in ubuntu that comes near to YM's functionality??

---

### Post by Abnormal123 on 2008-08-06
I am having problems getting my webcam working.

I was able to install gyachi with get libs on hardy 64-bit, but when I try to start my webcam nothing happens.  I've installed flashcam, and made a symbolic link to gyachi (not sure if this is correct).
```
ln -s /usr/local/bin/flashcamwrap gyachi
```
I also tried running flashcam from a terminal and then tried the webcam in gyachi, but no luck.  
```
flashcam -qD
```
My webcam does work using a flash application.
Any help would be appreciated.

I am using an HP webcam built in to an HP dv6000 laptop.
```
lsusb 
Bus 002 Device 002: ID 04f2:b015 Chicony Electronics Co., Ltd 

```

---

### Post by dart1007 on 2008-08-06
Hey Loell!

Thank you for this link!  Kanina pa ako naghahanap ng deb package for gyachi coz' I just upgraded
to Hardy.... Maraming Salamat!!! ;-)

---

### Post by loell on 2008-08-06
> **dart1007 said:**
>  Maraming Salamat!!! ;-)

Welcome po! :)

---

### Post by ShelJ on 2008-08-17
Terminal hangs when I try getlibs t retrieve the libs.

---

### Post by loell on 2008-08-22
update: version 1.1.48 :)

64 bit package is also available

please refer to the first post. :)

---

### Post by Sef on 2008-08-22
> installing gyachi in 64 bit system

Download the 64 bit package Ver. 1.1.48
note: this package has no room voice chat feature

in your 64 bit system with 32 deb package, install getlibs

then in the terminal,

force to install,
Code:

sudo dpkg -i --force-all gyachi_1.1.31-1_i386.deb

get the 32 bit dependencies
Code:

sudo getlibs /usr/bin/gyachi



For the 64-bit version, one needs to use the terminal or just click on the package?  

If it is the terminal, then shouldn't the package me gyachi_1.1.48_i386.deb instead of gyachi_1.1.31-1_i386.deb.

---

### Post by loell on 2008-08-22
ooops..  thanks for the heads up sef :) 

 i had it fixed. :)

---

### Post by Abnormal123 on 2008-08-22
I uninstalled the 32-bit .deb and installed the 64-bit .deb.  The installation went fine, but I still can't get my web cam to work.  I got the following error message:
 [I]An error occurred at 'ioctl VIDIOCSPICT
Could not set camera properties[/I]

With the 64-bit version do you still have to install flashcam?  If so, I still don't have that working.

---

### Post by forstfed on 2008-08-23
Hi, I just installed 1.1.48 and gettin the followin after i got the codecs sorted out:

GYachI Voiceclient
Version 1.1.48


No sound plugin has been configured, or the configured sound plugin was not found, or did not load.

Ed

THIS IS SOLVED

---

### Post by Joffa65 on 2008-08-23
I just updated from 1.1.31 to 1.1.48 and now the voice chat wont work.

From a terminal window..
-desktop:~$ gyachi
 Plugin Loaded [#8F4CB1m:  'GyachI-sound-plugin-PulseAudio' 

Looks fine, but a popup window gives...
--------------------------
GYachI Voiceclient
Version 1.1.48


No sound plugin has been configured, or the configured sound plugin was not found, or did not load.
-------------------------------------

Any tips please?

---

### Post by forstfed on 2008-08-23
Joffa, i figured it out.  Go to Setup, click on Options. Look for Sound_Device and click the drop-down.  Select Pulse Audio.

Ed

---

### Post by Joffa65 on 2008-08-24
> **forstfed said:**
> Joffa, i figured it out.  Go to Setup, click on Options. Look for Sound_Device and click the drop-down.  Select Pulse Audio.

Ed

Works it does, thanks Ed :D

The sound is also nice and clear in this version. Previously it had a certain 'modulated by helicopter blades' quality to it.

---

### Post by loell on 2008-08-24
> **Joffa65 said:**
>  Previously it had a certain 'modulated by helicopter blades' quality to it.

heheh, that was the alsa plugin. :D

---

### Post by sujay0000 on 2008-08-29
Hello All...

Am totally new to Ubuntu and Linux

While trying installing gyachi this is the error that I got

Error: Dependency is not satisfiable: libpango1.0-0

Plz guide me what to do

Regards;
Sujay

---

### Post by loell on 2008-08-29
hi, please make sure you downloaded the correct package for your ubuntu version.. may you state the ubuntu version you're using?

---

### Post by Abnormal123 on 2008-09-01
I need some help.

I installed flashcam and tested it with a flash app in Firefox.  How do I make a link to flashcam for gyachi?

Also, I don't understand how to add the start up script to your ~/.bashrc file for flashcam.

---

### Post by loell on 2008-09-01
hi can you test this specifically v4l2 compiled package?
i know you're asking for flashcam, but if this can work, then it won't be needing flashcam.

[http://www.mediafire.com/?mjhpsgheqad]("http://www.mediafire.com/?mjhpsgheqad")

feedback appreciated :)

---

### Post by Abnormal123 on 2008-09-02
I have the 64-bit package installed.  Should I uninstall it, then install this 32-bit package with get-libs?

---

### Post by loell on 2008-09-03
64 bit?

oh, ok.. ;)

hang in there, i'll try to build one later with v4l2 specific tweaks.. :)

---

### Post by ramks on 2008-09-04
Hi Leoll. I too got the flashcam working but couldnt get my v4l2 cam working with gyachi. I couldnt try this [http://www.mediafire.com/?mjhpsgheqad](http://www.mediafire.com/?mjhpsgheqad) as I use gutsy. Do you have a similar v4l2 enabled package for gutsy.

---

### Post by Chang An on 2008-09-14
I cant seem to get a voice chat going.  Also If I have a land line number I bought through yahoo will this client support it?  Can I make calls to land lines and can they call me?

---

### Post by loell on 2008-09-14
> **Chang An said:**
> I cant seem to get a voice chat going.  Also If I have a land line number I bought through yahoo will this client support it?

its **room voice chat** only, not yahoo's **pc to pc call**

you can't use your yahoo phone credits and number with this client.

you most probably have to use a sip softphone( there are tons to choose from) and buy som credits with some provider to call landline. there is also skype for linux.

---

### Post by Chang An on 2008-09-14
> **loell said:**
> its **room voice chat** only, not yahoo's **pc to pc call**

you can't use your yahoo phone credits and number with this client.

you most probably have to use a sip softphone( there are tons to choose from) and buy som credits with some provider to call landline. there is also skype for linux.

Im trying to switch my friend over from XP to Ubuntu and she wants you use her yahoo phone credit.  So there is no way to do that in Ubuntu?

I recommended Gizmo phone but she does not want a new number.

---

### Post by loell on 2008-09-14
> **Chang An said:**
>   So there is no way to do that in Ubuntu?


none :( , but another option is virtualize xp inside ubuntu, so she can use windows yahoo messenger.

---

### Post by vt8235 on 2008-09-19
hello,

i use ubuntu hardy and want to get my webcam to work  which has microdia chipset 0045:627b. i installed driver from google.group.microdia. tested to see if it works with mplayer and it works indeed flawlessly. Now i face the ultimate challenge in trying to get it work under gyachi.

 I downloaded **gyachi_1.1.48-1~v4l2_i386.deb** for hardy , installed and started my webcam preview but i get same image: something of a split screen--- the one in the left side being mostly green-coloured and the one in the right side working but covered with stripes. i noticed the same thing when previewing in ekiga, kopete, skype and wengophone. 

If anyone could give me some advice it would be the nicest thing that could happen to my ubuntu experience. thank you very much.](*,)

---

### Post by peter_babeone on 2008-09-19
hi everybody,

I'm using now the last verion of gyarchi 1.1.48. And I have some problems when I try to save the settings.

For example, I just want to use the stealth settings and everytime I use it, the settings window crashes, gyachi is quitted and nothing happens. That's exactly when I make some configurations of the setup panel (above right from the main window)

I can't figure it out. Maybe someone can help me.

Thanks lots. :lolflag:

---

### Post by loell on 2008-09-19
hi, what part of the setup window are you referring to?

---

### Post by peter_babeone on 2008-09-20
> **loell said:**
> hi, what part of the setup window are you referring to?

hi loell,

I meant the setup window, which you can see, when you run gyachi. They are Connections, Actions, Tools, Rooms, Status, **Setup**.

For all parts of the Setup window I can't make any Configurations. For any changes gyachi crashes :(

It's for me very important to use the feature Stealth Settings.

---

### Post by loell on 2008-09-20
> **peter_babeone said:**
> hi loell,

I meant the setup window, which you can see, when you run gyachi. They are Connections, Actions, Tools, Rooms, Status, **Setup**.

yep, so what part of it? the specific tabs  and fields  that made it crash?

also can you reset your settings? see if it can fix it.

exit gyachi and type this in command line

```
rm -rf .yahoorc
```

now execute gyachi..

---

### Post by peter_babeone on 2008-09-20
Oh sorry for missundertanding you,

I have tried it before "rm -rf .yahoorc" and made a new installation again.

But it seems to be crashed everytime when I make some configurations in all parts of the Setup window.

**PS: It's a bug "Seqmentation fault". But I maybe configure it out to modify the "gyachrc" in .yahoorc/gyach.**

---

### Post by a3qp on 2008-09-22
Hi loell,
I have a Sony vaio (VGN-SR129E/B) with built in camera.I'm running the amd64 version.

I installed the drivers, and I can use Skype with cam and mic.
However, when I run gyachi, it says: 

An error ocurred at 'ioctl VIDIOCSPICT'. Could not set camera properties.

and another window with a message: Gyachi (Webcam Broadcaster): Error while querying mmap-buffers.

Is there anything that I'm missing to install?

Thanks,
a3qp

---

### Post by loell on 2008-09-22
hello, you're not missing anything ;)

its gyachi who's missing it, the developer promises to address this by the end of this year.

---

### Post by spiderbatdad on 2008-09-22
Hey. loell. Always wanted to thankyou for all your work on gyachi. I use it daily. It has been running great in Intrepid on the 2.6.25 kernel, however the latest is 2.6.27.-3 When I try to launch my cam on this kernel, I get...The device does not support video capture.
Maybe this is a kernel issue.

---

### Post by loell on 2008-09-22
> **spiderbatdad said:**
> Hey. loell. Always wanted to thankyou for all your work on gyachi. I use it daily. It has been running great in Intrepid on the 2.6.25 kernel, however the latest is 2.6.27.-3 When I try to launch my cam on this kernel, I get...The device does not support video capture.
Maybe this is a kernel issue.

hello **spiderbatdad** :)

I'm well aware of your patronization of the project, and I as a simple supporter  of the project is grateful for that, thanks :)

hmm, about intrepid webcam support, it is supposed to be natively supported by the new kernel, yes this is most likely a kernel issue.

anyhow, i'll also test intrepid when beta comes out.


oh, you might want to join the occasional testing / feedback / suggestion in [gyachi's forum]("http://gyachi.sourceforge.net/forums.shtml"). ;)

---

### Post by Nicole on 2008-09-24
> **a3qp said:**
> 
However, when I run gyachi, it says: 

An error ocurred at 'ioctl VIDIOCSPICT'. Could not set camera properties.

and another window with a message: Gyachi (Webcam Broadcaster): Error while querying mmap-buffers.


I get the same error messages - everything installed fine, flashcam installed fine, it works when I do the test it suggested using firefox; it just won't start in gyachi. Is there something simple I ought to be doing to make this work, or will it just not work with my computer? I'm trying to use the built-in cam on a Dell XPS M1330 - which has never worked with gyachi, but works with Ekiga. So it's not inherently a problem with the cam (which uses v4l2). Should I be doing something other than launching gyachi by typing gyachi in a terminal?

Many thanks for any help you can give me! This is the only thing that's not working well for me in gyachi, which is otherwise a fabulous product!

N

---

### Post by loell on 2008-09-24
> **Nicole said:**
> I get the same error messages - everything installed fine, flashcam installed fine, it works when I do the test it suggested using firefox; it just won't start in gyachi. Is there something simple I ought to be doing to make this work, or will it just not work with my computer? I'm trying to use the built-in cam on a Dell XPS M1330 - which has never worked with gyachi, but works with Ekiga. So it's not inherently a problem with the cam (which uses v4l2). Should I be doing something other than launching gyachi by typing gyachi in a terminal?

Many thanks for any help you can give me! This is the only thing that's not working well for me in gyachi, which is otherwise a fabulous product!

N

if you are using flashcam, try executing ```
flashcamwrap gyachi
```

also try this custom v4l2 build [http://launchpadlibrarian.net/17263051/gyachiv4l2_1.1.48-1%7Eubuntu1_i386.deb]("http://launchpadlibrarian.net/17263051/gyachiv4l2_1.1.48-1%7Eubuntu1_i386.deb") - no flashcam required.

---

### Post by xeddog on 2008-09-25
Not sure if I should start a new thread, or if it is ok to ask here, but . . .

I am running Hardy and installed Gyachi 1.1.48.  For the most part, all has been fine for a couple of weeks.  The two main features of Gyachi that I use are the send to multiple, and photo sharing with my kids.

BUT!.  My problem is a matter of size.  I have noticed that each time I shutdown my Hardy system and restart it, the main Chat window for Gyachi keeps getting larger and larger.  That wouldn't be so bad if I could shrink it back down to a useable size, but I can't.  I can shrink it a little, but not much.  Yesterday morning when I launched Gyachi, the first chat window was aaaaaaalmost fullscreen and the most I could resize the window was . . .well . . .not much.  Yesterday afternoon I added dual monitor support (twinview), and now the gyachi window has grown so that it extends onto the second monitor.  The most I can shrink it to is fullscreen on the first monitor.

I tried removing the gyachi package and re-installing but this did not help.  I am hoping that there is a config file somewhere that I can't find, and if found I could make a few simple changes to.  

Any ideas??


Thanks,

xeddog

---

### Post by loell on 2008-09-25
ooh strange.. :)

this would be the first report involving twinview , i've never tried it.

it should not keep getting larger and larger as the window size is always saved on the settings / rc file whenever the user resizes it.

try erasing the settings file by deleting the directory

```
/.yahoorc
```

---

### Post by xeddog on 2008-09-25
OK.  Two things.

One.  Deleting the .yahoorc directory has "fixed" the problem for now.

Two.  Sorry about the confusion regarding twinview, but his was going on before I added twinview so is not connected with it.  I just mentioned twinview to show how bad it was getting.  I just came back from running some errands and before I left I had shut down my computer.  I rebooted it when I got back and the initial Chat window for Gyachi spanned all of my primary display, and went (literally) half way across the secondary display.  I was not able to resize that window at all. 

But again, deleting the .yahoorc file has got me going again.  Do you know the particular setting in the .yahoorc file that I could edit next time?  It would be a pita if I had done a lot of customization (fortunately I had not) and had to do it all over again.

Yoo da man.

xeddog

---

### Post by loell on 2008-09-25
yes there is a particular entry, i commonly suggest deleting the entire /.yahoorc directory which is actually not that good of an advice but just not to create more confusion in explaining for new users.


anyway, the particular file is **/.yahoorc/gyach/gyachrc**

the entries are explanatory, just try to find

**chat_window_width =**

and

**chat_window_height =**

---

### Post by xeddog on 2008-09-27
Thanks Loell,  I really appreciate the assistance.  After deleting the .yahoorc file the problem of expanding windows seems to be resolved and not just worked around.  It doesn't seem to be happening again.  Now if I can just ask you about a couple of other things.

I have an intermittant problem that has happened twice now (over a period of about a month).  When launching Gyachi, It has gone into a email notification/disconnect loop.  Looks like it will do that about 10 times and then will not reconnect again for the rest of the day.  I have even shutdown and powered off the computer for a time, and when I bring the machine back up it still just doesn't seem to connect again until the next day.  

I'm not sure if the disconnect problem is a Gyachi problem or not because when it happens, no other IM clients ON THIS MACHINE will connect either.  Not even Pidgin.  But yet all other applications that use the internet seem to be unaffected.  Firefox, Azureus, Adept, etc. all still work fine.  I know it isn't a Yahoo problem because I can turn around to my Windows XP machine and connect to Yahoo right away.  The only thing I can say is that since Gyachi is my client of choice, it happens to Gyachi and then the other IM clients cannot connect either. I do not even try to use the others until something happens so I don't know if it would happen to them too.

And lastly, Gyachi seems to just disappear too often.  I have gone to Setup and enabled both basic and advanced boot protection, but Gyachi still seems to quit on it own sometimes.  I have gone to send a message to my son and his daughter (we babysit the grand daughter), and Gyachi is just nowhere to be found.  I have to relaunch.

Any ideers??

Thanks again for your help.

xeddog

---

### Post by tire38 on 2008-09-27
Can you give me an idea on using the gyachiv4l2 package. I have tried to install it doesn't seem to really install anything but the docs.

---

### Post by da.tiger on 2008-09-28
installed gyachi and logged in, but it connects and disconnects every second. dunno whats wrong..........

---

### Post by loell on 2008-09-28
> **da.tiger said:**
> installed gyachi and logged in, but it connects and disconnects every second. dunno whats wrong..........

can you go to **setup**--> **options** tab

uncheck  auto-reconnect if enabled.

---

### Post by da.tiger on 2008-09-29
> **loell said:**
> can you go to **setup**--> **options** tab

uncheck  auto-reconnect if enabled.

that doesnt solve the problem, only stops reconnecting..

---

### Post by banda on 2008-10-19
> **loell said:**
> if you are using flashcam, try executing ```
flashcamwrap gyachi
```

also try this custom v4l2 build [http://launchpadlibrarian.net/17263051/gyachiv4l2_1.1.48-1%7Eubuntu1_i386.deb]("http://launchpadlibrarian.net/17263051/gyachiv4l2_1.1.48-1%7Eubuntu1_i386.deb") - no flashcam required.

that link is boken.. it dnlds a 17kb deb package!

> **loell said:**
> hi can you test this specifically v4l2 compiled package?
i know you're asking for flashcam, but if this can work, then it won't be needing flashcam.

[http://www.mediafire.com/?mjhpsgheqad]("http://www.mediafire.com/?mjhpsgheqad")

feedback appreciated :)

i have installed this package on my laptop which has a built in v4l2 cam. now when i try to start my webcam in gyachi it gives the following error mssg 

```
gyachi (webcam broadcaster):
fatal: video format not supported by grab device
```

this error messageis different from the ones i was getting with previous, non v4l2 enabled builds.

the terminal shows the following messages when i enable the webcam in gyachi ---

```
$ gyachi
ctrl 9963779:Hue min:-40 max:40 def:6
ctrl 9963777:Contrast min:0 max:95 def:20
ctrl 9963776:Brightness min:-64 max:64 def:-10
ctrl 9963778:Saturation min:0 max:128 def:80
ctrl 9963792:Gamma min:72 max:500 def:120

(gyachi-upload:6448): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed

```

ps:thanks to everyone who is involved in developing gyachi.. :) .. i m loving this s/w which runs perfectly on my  desktop with voice and webcam:)).. keep up the gud work!!

<out>

---

### Post by Sef on 2008-10-19
I had been running Gyachi well in Intrepid Ibex 64-bit.  However now there is a problem.  It just crashed and when I went to reinstall it, it said that libltld3 is not there.

Here is the message from the terminal:

> Package libltdl3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libltdl3 has no installation candidate


---

### Post by loell on 2008-10-19
a user PM'd me a few days ago about gyachi hardy 64 , which has exactly the same error, which I completely forgot about.

I've just built a fresh intrepid package in my ppa, i'll statically link the deb from launchpad librarian shortly. :)

-updated the first page for the intrepid debs..

---

### Post by Sef on 2008-10-20
Thank you very much for the intrepid package.

---

### Post by tqft on 2008-10-21
Loell,

You may have seen this (assuming you are the same loell)
[http://sourceforge.net/forum/forum.php?thread_id=2402880&forum_id=533966](http://sourceforge.net/forum/forum.php?thread_id=2402880&forum_id=533966)

Same tqft.

Gyachi was building fine until Sunday when I ran previously working update and build script after updating to 8.10 Intrepid (x86_32).

Could you please post here the config option you used for the intrepid build and any tweaks to the make setup you did to get a build working on intrepid 
ghosler has identfied my problem as
"for whatever reason, the build under your distro is trying to make an executable (which will REQUIRE the "main", from a forced inclusion of crtl.o) when in fact the target of the make is a shared library. "


Other stuff builds fine - built firefox & friends with previously working scripts since the update to Intrepid.

I used your intrepid deb and it worked mostly.

Thanks.

---

### Post by rfrayer on 2008-10-27
> **loell said:**
> just my regular support  thread for gyachi :)

**About gyachi**: *Yahoo! client for Linux operating system supports almost all of the features you would expect to find on the official Windows Yahoo! client: Voice chat, webcams, faders, 'nicknames', audibles, avatars, display images, and more  *

***[COLOR=Red]most notable newest feature: Full implementation of Yahoo! Photosharing with drag n drop and pointer[/COLOR]***

[COLOR=Blue]Intrepid packages[/COLOR]
___________________________________________________________________
**[gyachi 1.1.48 i386.deb]("https://launchpad.net/%7Eloell/+archive/+files/gyachi_1.1.48-1%7Eintrepid1_i386.deb")**

**[gyachi 1.1.48 amd64.deb]("https://launchpad.net/%7Eloell/+archive/+files/gyachi_1.1.48-1%7Eintrepid1_amd64.deb")**
___________________________________________________________________

**[Download: Gyachi 1.1.48 Deb package for hardy heron]("http://launchpadlibrarian.net/16992554/gyachi_1.1.48-1%7Eubuntu2_i386.deb")**


**[COLOR=Blue][Download: Gyachi 1.1.31 Deb package for gutsy]("http://www.mediafire.com/?izgy1gktmxf")[/COLOR]**



for v4l2 webcams: you'll have to compile and use [http://www.swift-tools.net/Flashcam/](http://www.swift-tools.net/Flashcam/) 
thanks and credit goes to **kung fu buntu** for the patch.


**64 bit package**

[Download the 64 bit package Ver. 1.1.48]("http://launchpadlibrarian.net/16993016/gyachi_1.1.48-1%7Eubuntu2_amd64.deb")
note: this package has [COLOR=Red]no room voice chat [/COLOR] feature


**installing gyachi in 64 bit system with 32 bit package if you want room voice chat**
in your 64 bit system with 32 deb package, install [getlibs]("http://ubuntuforums.org/showthread.php?t=474790")

then in the terminal,

force  to install,
```
sudo dpkg -i --force-all gyachi_1.1.48-1_i386.deb
```get the 32 bit dependencies
```
sudo getlibs /usr/bin/gyachi
```


I tried the intrepid package but voice doesnt seem to work. I can hear everyone in chat but they do not even see me key up on the mic. So i tried to compile it myself and here is the error i got at the end
```

/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
make[2]: *** [libgyachi.so] Error 1
make[2]: Leaving directory `/home/george/Desktop/gyachi-1.1.48/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/george/Desktop/gyachi-1.1.48'
make: *** [all] Error 2
george@george-desktop:~/Desktop/gyachi-1.1.48$ 
```

its calling for some kind of function to main but honestly I have no idea what main is . Im asuming intrepid uses a different version of gcc. I was wondering if anyone had the intrepid gcc ./configure or make comands?

---

### Post by tqft on 2008-10-28
> **rfrayer said:**
> I tried the intrepid package but voice doesnt seem to work. I can hear everyone in chat but they do not even see me key up on the mic. So i tried to compile it myself and here is the error i got at the end
```

/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
make[2]: *** [libgyachi.so] Error 1
make[2]: Leaving directory `/home/george/Desktop/gyachi-1.1.48/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/george/Desktop/gyachi-1.1.48'
make: *** [all] Error 2
george@george-desktop:~/Desktop/gyachi-1.1.48$ 
```

its calling for some kind of function to main but honestly I have no idea what main is . Im asuming intrepid uses a different version of gcc. I was wondering if anyone had the intrepid gcc ./configure or make comands?

rfrayer - see the link above of mine - I had exactly the same compile problem - unfortunately gyacghi dev(s) can't reproduce the error and so theyc an't fix it.

Quoting ghosler - main gyachi dev
"for whatever reason, the build under your distro is trying to make an executable (which will REQUIRE the "main", from a forced inclusion of crtl.o) when in fact the target of the make is a shared library. 
 
I cannot begin to guess as to why this is happening, except to say that it looks to me to be a problem with your distribution. It MIGHT be a problem with your setup."

---

### Post by rfrayer on 2008-10-28
hmmm. yeah i ended up just stuffing hardy back on here which kinda blows because intrepid runs great all except for compiling which im sure will be worked out before they do an official release hopefully. 

I mean because gyachi has compiled on every other ubuntu distro just fine....

all in all there doing a great job on intrepid i just like to be able to chat in yahoo and hear what people are saying on the mic lol.

---

### Post by venerix on 2008-10-31
Hello...I have a problem with gyachi in intrepid...In hardy everything was just fine...I cannot receive any files...it simply crashes...The error is:

*** buffer overflow detected ***: gyachi terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb72a8558]
/lib/tls/i686/cmov/libc.so.6[0xb72a6680]
/lib/tls/i686/cmov/libc.so.6[0xb72a5f87]
/lib/tls/i686/cmov/libc.so.6(__snprintf_chk+0x34)[0xb72a5e74]
gyachi(yahoo_fxfer_getfile_thread+0xea)[0x811c13a]
/usr/lib/libglib-2.0.so.0[0xb765102f]
/lib/tls/i686/cmov/libpthread.so.0[0xb731250f]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb728f7ee]

....

---

### Post by loell on 2008-10-31
> **venerix said:**
> Hello...I have a problem with gyachi in intrepid...In hardy everything was just fine...I cannot receive any files...it simply crashes...The error is:

*** buffer overflow detected ***: gyachi terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb72a8558]
/lib/tls/i686/cmov/libc.so.6[0xb72a6680]
/lib/tls/i686/cmov/libc.so.6[0xb72a5f87]
/lib/tls/i686/cmov/libc.so.6(__snprintf_chk+0x34)[0xb72a5e74]
gyachi(yahoo_fxfer_getfile_thread+0xea)[0x811c13a]
/usr/lib/libglib-2.0.so.0[0xb765102f]
/lib/tls/i686/cmov/libpthread.so.0[0xb731250f]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb728f7ee]

....

hi, is this the full backtrace of the crash?

---

### Post by venerix on 2008-10-31
This is the full backtrace....


*** buffer overflow detected ***: gyachi terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb73da558]
/lib/tls/i686/cmov/libc.so.6[0xb73d8680]
/lib/tls/i686/cmov/libc.so.6[0xb73d7f87]
/lib/tls/i686/cmov/libc.so.6(__snprintf_chk+0x34)[0xb73d7e74]
gyachi(yahoo_fxfer_getfile_thread+0xea)[0x811c13a]
/usr/lib/libglib-2.0.so.0[0xb778302f]
/lib/tls/i686/cmov/libpthread.so.0[0xb744450f]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb73c17ee]
======= Memory map: ========
08048000-08143000 r-xp 00000000 08:05 467476     /usr/bin/gyachi
08143000-08144000 r--p 000fb000 08:05 467476     /usr/bin/gyachi
08144000-08153000 rw-p 000fc000 08:05 467476     /usr/bin/gyachi
08153000-0815e000 rw-p 08153000 00:00 0 
08e5d000-09336000 rw-p 08e5d000 00:00 0          [heap]
b43fe000-b43ff000 ---p b43fe000 00:00 0 
b43ff000-b4bff000 rw-p b43ff000 00:00 0 
b4bff000-b4c00000 ---p b4bff000 00:00 0 
b4c00000-b5400000 rw-p b4c00000 00:00 0 
b5400000-b5421000 rw-p b5400000 00:00 0 
b5421000-b5500000 ---p b5421000 00:00 0 
b5578000-b5585000 r-xp 00000000 08:05 603528     /lib/libgcc_s.so.1
b5585000-b5586000 r--p 0000c000 08:05 603528     /lib/libgcc_s.so.1
b5586000-b5587000 rw-p 0000d000 08:05 603528     /lib/libgcc_s.so.1
b559b000-b559c000 ---p b559b000 00:00 0 
b559c000-b5d9c000 rw-p b559c000 00:00 0 
b5d9c000-b5da4000 r-xp 00000000 08:05 469766     /usr/lib/libtrackerclient.so.0.0.0
b5da4000-b5da5000 r--p 00007000 08:05 469766     /usr/lib/libtrackerclient.so.0.0.0
b5da5000-b5da6000 rw-p 00008000 08:05 469766     /usr/lib/libtrackerclient.so.0.0.0
b5da9000-b5dba000 r--p 00000000 08:05 495473     /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf
b5dba000-b5e3c000 rw-p b5dba000 00:00 0 
b5e3c000-b5e88000 r--p 00000000 08:05 495426     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b5e88000-b6136000 r--p 00000000 08:05 41201      /usr/share/fonts/truetype/unfonts/UnDotumBold.ttf
b6136000-b6145000 r-xp 00000000 08:05 600418     /lib/libbz2.so.1.0.4
b6145000-b6146000 r--p 0000f000 08:05 600418     /lib/libbz2.so.1.0.4
b6146000-b6147000 rw-p 00010000 08:05 600418     /lib/libbz2.so.1.0.4
b6147000-b6178000 r-xp 00000000 08:05 466859     /usr/lib/libcroco-0.6.so.3.0.1
b6178000-b617b000 rw-p 00030000 08:05 466859     /usr/lib/libcroco-0.6.so.3.0.1
b617b000-b61ab000 r-xp 00000000 08:05 466862     /usr/lib/libgsf-1.so.114.0.8
b61ab000-b61ad000 r--p 0002f000 08:05 466862     /usr/lib/libgsf-1.so.114.0.8
b61ad000-b61ae000 rw-p 00031000 08:05 466862     /usr/lib/libgsf-1.so.114.0.8
b61ae000-b61af000 rw-p b61ae000 00:00 0 
b61af000-b61e0000 r-xp 00000000 08:05 466864     /usr/lib/librsvg-2.so.2.22.3
b61e0000-b61e1000 r--p 00030000 08:05 466864     /usr/lib/librsvg-2.so.2.22.3
b61e1000-b61e2000 rw-p 00031000 08:05 466864     /usr/lib/librsvg-2.so.2.22.3
b61e9000-b61f4000 r-xp 00000000 08:05 642077     /usr/lib/gio/modules/libgioremote-volume-monitor.so
b61f4000-b61f5000 r--p 0000a000 08:05 642077     /usr/lib/gio/modules/libgioremote-volume-monitor.so
b61f5000-b61f6000 rw-p 0000b000 08:05 642077     /usr/lib/gio/modules/libgioremote-volume-monitor.so
b61f6000-b620f000 r--p 00000000 08:05 505422     /usr/share/fonts/type1/gsfonts/n021003l.pfb
b620f000-b622a000 r-xp 00000000 08:05 466207     /usr/lib/libdbus-glib-1.so.2.1.0
b622a000-b622b000 r--p 0001a000 08:05 466207     /usr/lib/libdbus-glib-1.so.2.1.0
b622b000-b622c000 rw-p 0001b000 08:05 466207     /usr/lib/libdbus-glib-1.so.2.1.0
b622c000-b6232000 r-xp 00000000 08:05 466647     /usr/lib/libnotify.so.1.1.2
b6232000-b6233000 rw-p 00006000 08:05 466647     /usr/lib/libnotify.so.1.1.2
b6233000-b62f6000 r-xp 00000000 08:05 466315     /usr/lib/libasound.so.2.0.0
b62f6000-b62f8000 r--p 000c2000 08:05 466315     /usr/lib/libasound.so.2.0.0
b62f8000-b62fb000 rw-p 000c4000 08:05 466315     /usr/lib/libasound.so.2.0.0
b62fb000-b6320000 r-xp 00000000 08:05 467377     /usr/lib/libmcrypt.so.4.4.7
b6320000-b6321000 r--p 00025000 08:05 467377     /usr/lib/libmcrypt.so.4.4.7
b6321000-b6323000 rw-p 00026000 08:05 467377     /usr/lib/libmcrypt.so.4.4.7
b6323000-b6328000 rw-p b6323000 00:00 0 
b6328000-b634f000 r-xp 00000000 08:05 469606     /usr/lib/libgpgme.so.11.6.4
b634f000-b6351000 rw-p 00026000 08:05 469606     /usr/lib/libgpgme.so.11.6.4
b6351000-b6352000 rw-p b6351000 00:00 0 
b6356000-b6357000 r-xp 00000000 08:05 497278     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b6357000-b6358000 r--p 00000000 08:05 497278     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b6358000-b6359000 rw-p 00001000 08:05 497278     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b6359000-b635d000 r-xp 00000000 08:05 495894     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b635d000-b635e000 r--p 00003000 08:05 495894     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b635e000-b635f000 rw-p 00004000 08:05 495894     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b635f000-b6362000 r-xp 00000000 08:05 537715     /usr/lib/gyachi/plugins/gyachiblowfish.so
b6362000-b6363000 r--p 00002000 08:05 537715     /usr/lib/gyachi/plugins/gyachiblowfish.so
b6363000-b6364000 rw-p 00003000 08:05 537715     /usr/lib/gyachi/plugins/gyachiblowfish.so
b6364000-b6366000 rw-p b6364000 00:00 0 
b6366000-b6369000 r-xp 00000000 08:05 600523     /lib/libcap.so.1.10
b6369000-b636a000 rw-p 00002000 08:05 600523     /lib/libcap.so.1.10
b636a000-b637f000 r-xp 00000000 08:05 466382     /usr/lib/libICE.so.6.3.0
b637f000-b6380000 rw-p 00014000 08:05 466382     /usr/lib/libICE.so.6.3.0
b6380000-b6382000 rw-p b6380000 00:00 0 
b6382000-b6389000 r-xp 00000000 08:05 466384     /usr/lib/libSM.so.6.0.0
b6389000-b638a000 r--p 00006000 08:05 466384     /usr/lib/libSM.so.6.0.0
b638a000-b638b000 rw-p 00007000 08:05 466384     /usr/lib/libSM.so.6.0.0
b638b000-b63d9000 r-xp 00000000 08:05 467022     /usr/lib/libpulse.so.0.4.1
b63d9000-b63da000 r--p 0004d000 08:05 467022     /usr/lib/libpulse.so.0.4.1
b63da000-b63db000 rw-p 0004e000 08:05 467022     /usr/lib/libpulse.so.0.4.1
b63dc000-b63dd000 r-xp 00000000 08:05 537713     /usr/lib/gyachi/plugins/gyachilibnotify.so
b63dd000-b63de000 r--p 00000000 08:05 537713     /usr/lib/gyachi/plugins/gyachilibnotify.so
b63de000-b63df000 rw-p 00001000 08:05 537713     /usr/lib/gyachi/plugins/gyachilibnotify.so
b63df000-b63e1000 r-xp 00000000 08:05 537714     /usr/lib/gyachi/plugins/gyachialsa.so
b63e1000-b63e2000 r--p 00001000 08:05 537714     /usr/lib/gyachi/plugins/gyachialsa.so
b63e2000-b63e3000 rw-p 00002000 08:05 537714     /usr/lib/gyachi/plugins/gyachialsa.so
b63e3000-b63e5000 r-xp 00000000 08:05 537712     /usr/lib/gyachi/plugins/gyachimcrypt.so
b63e5000-b63e6000 r--p 00001000 08:05 537712     /usr/lib/gyachi/plugins/gyachimcrypt.so
b63e6000-b63e7000 rw-p 00002000 08:05 537712     /usr/lib/gyachi/plugins/gyachimcrypt.so
b63e7000-b63ea000 r-xp 00000000 08:05 600528     /lib/libgpg-error.so.0.3.0
b63ea000-b63eb000 rw-p 00002000 08:05 600528     /lib/libgpg-error.so.0.3.0
b63eb000-b63ed000 r-xp 00000000 08:05 537711     /usr/lib/gyachi/plugins/gyachigpgme.so
b63ed000-b63ee000 r--p 00002000 08:05 537711     /usr/lib/gyachi/plugins/gyachigpgme.so
b63ee000-b63ef000 rw-p 00003000 08:05 537711     /usr/lib/gyachi/plugins/gyachigpgme.so
b63ef000-b63ff000 r-xp 00000000 08:05 600454     /lib/tls/i686/cmov/libresolv-2.8.90.so
b63ff000-b6400000 r--p 0000f000 08:05 600454     /lib/tls/i686/cmov/libresolv-2.8.90.so
b6400000-b6401000 rw-p 00010000 08:05 600454     /lib/tls/i686/cmov/libresolv-2.8.90.so
b6401000-b6403000 rw-p b6401000 00:00 0 
b6403000-b6405000 r-xp 00000000 08:05 602924     /lib/libnss_mdns4_minimal.so.2
b6405000-b6406000 rw-p 00001000 08:05 602924     /lib/libnss_mdns4_minimal.so.2
b6408000-b6414000 r-xp 00000000 08:05 467023     /usr/lib/libpulse-simple.so.0.0.1
b6414000-b6415000 r--p 0000b000 08:05 467023     /usr/lib/libpulse-simple.so.0.0.1
b6415000-b6416000 rw-p 0000c000 08:05 467023     /usr/lib/libpulse-simple.so.0.0.1
b6416000-b6418000 r-xp 00000000 08:05 537716     /usr/lib/gyachi/plugins/gyachipulseaudio.so
b6418000-b6419000 r--p 00001000 08:05 537716     /usr/lib/gyachi/plugins/gyachipulseaudio.so
b6419000-b641a000 rw-p 00002000 08:05 537716     /usr/lib/gyachi/plugins/gyachipulseaudio.so
b641a000-b647a000 rw-s 00000000 00:09 31653941   /SYSV00000000 (deleted)
b647a000-b64da000 rw-s 00000000 00:09 31621143   /SYSV00000000 (deleted)
b64da000-b64f2000 r--p 00000000 08:05 505426     /usr/share/fonts/type1/gsfonts/n022003l.pfb
b64f2000-b64f8000 r-xp 00000000 08:05 495903     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b64f8000-b64f9000 r--p 00005000 08:05 495903     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.sAborted


Forgot to say...i can send any files...but when i receive crash occures..

---

### Post by loell on 2008-10-31
thanks, i'll notify the developer when he gets home.

---

### Post by venerix on 2008-11-01
Thanks for your help...

---

### Post by tqft on 2008-11-02
Loell,

Re my previous post(s)

I flicked some configure switches to see if I could get a different (and more informative) error - when I tried --disable-shared I got a libtool error.  Digging - got this:

[http://packages.ubuntu.com/hu/intrepid/libtool](http://packages.ubuntu.com/hu/intrepid/libtool)
"Package: libtool (2.2.4-0ubuntu4"

[http://packages.ubuntu.com/hardy/libtool](http://packages.ubuntu.com/hardy/libtool)
"Package: libtool (1.5.26-1ubuntu1)"


Redhat and Mandriva appear to be at 1.5.26 as well
so explaining why people on other distros are building gyachi are OK.

This may be the cause of my problem but doesn't explain why your build is OK - unless you have an old (pinned?) libtool installed.  Can you please tell me what version of libtool your system has?  

Thanks

---

### Post by loell on 2008-11-03
yeah, i just use whatever libtool ubuntu has on its respective version, so that would be 1.5.26-1 for hardy and 2.2.4-0ubuntu4 for intrepid.

---

### Post by arethz on 2008-11-03
Hello, I need some help. I have gyachi installed without any problem but I cant login to the server. I'm getting this message whenever I run the program.
[I]
** Could not connect to Yahoo! [ CONNECT ERROR: Could not connect to server: scs-dcnc.msg.yahoo.com, errno: 4 ] **[/I]

FYI, I'm running hardy heron(32bit) and the Gyachi version is 1.1.48 . How can I fix it?

---

### Post by ShelJ on 2008-11-05
Hi, I'm glad that you have an Intrepid version, thanks for doing this.  I'm having problems w/ my cam, I should've looked here first, so I'll try the new pkg and let you know if it works.

---

### Post by ShelJ on 2008-11-06
Ok, now I'm getting the following message when I try voice chat:

```
Cannot run gyvoice due to the following missing files:

      tsd32.dll
      tssoft.acm

Not in the following directories:
      /
      /usr/lib/win32/
      /usr/local/lib/win32/
      /usr/lib/codecs/
```

And my webcam is no longer running, I'm not getting any message, but the people I try to connect with get a "not connected" msg.

Any ideas?  Thanks in advance.

btw: I'm using Logitech Quickcam Sphere.

---

### Post by loell on 2008-11-06
try using version [1.1.49]("https://launchpad.net/%7Eloell/+archive/+files/gyachi_1.1.49-1~intrepid_i386.deb")

this is suppose to detect webcams as it has newer webcam API dependency.

---

### Post by ShelJ on 2008-11-06
> **loell said:**
> try using version [1.1.49]("https://launchpad.net/%7Eloell/+archive/+files/gyachi_1.1.49-1~intrepid_i386.deb")

this is suppose to detect webcams as it has newer webcam API dependency.

Thanks, I'll give this a shot.  Do you have this for a 64 archetecture yet?  If so, let me know.

---

### Post by ShelJ on 2008-11-06
Sorry, That didn't work.  It won't load from my appliccations menu, and this is what I get from cmd line:
```
:~$ gyachi
gyachi: error while loading shared libraries: libgyachi.so: cannot open shared object file: No such file or directory

:~$ sudo getlibs gyachi
The file "gyachi" does not exist

:~$ sudo getlibs -p gyachi
The following i386 packages will be installed: gyachi
Continue [Y/n]? 
W: Unable to locate package gyachi
E: No packages found
gyachi was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

```

Revertinting to 1.1.48 for now.  Please let me know if you have the amd64 package, and what I can do to resolve this issue.

I should mention that i can receive webcams, just cannot send.

Shel

---

### Post by loell on 2008-11-06
I have it ;)

[https://launchpad.net/%7Eloell/+archive/+files/gyachi_1.1.49-1~intrepid_amd64.deb](https://launchpad.net/%7Eloell/+archive/+files/gyachi_1.1.49-1~intrepid_amd64.deb)

I regularly update the package in my ppa.

---

### Post by ShelJ on 2008-11-06
Is there a way to test it w/o being connected to another person?

---

### Post by venerix on 2008-11-07
Thanks loell!With gyachi 1.1.50 file transfer problem solved...But my webcam doesn`t work any more...In gyachi 1.1.49 everything was just fine...

Bus 001 Device 003: ID 046d:0929 Logitech, Inc. Labtec WebCam Pro

This is my webcam...I installed it`s drivers using easycam2...In cheese i receive images from it!...

---

### Post by loell on 2008-11-07
> **venerix said:**
> Thanks loell!With gyachi 1.1.50 file transfer problem solved...But my webcam doesn`t work any more...In gyachi 1.1.49 everything was just fine...

Bus 001 Device 003: ID 046d:0929 Logitech, Inc. Labtec WebCam Pro

This is my webcam...I installed it`s drivers using easycam2...In cheese i receive images from it!...

just do an update, it should be fix now :)

thanks, for the buffer overflow trace btw :D

---

### Post by venerix on 2008-11-07
Thank you again...now everithing works magic...You`re the best...

---

### Post by loell on 2008-11-07
> **venerix said:**
> Thank you again...now everithing works magic...You`re the best...

heheh, the kudos should go to the developer. :)

---

### Post by error121 on 2008-11-08
I managed to get the 1.1.49 x64 package to install and run, but now when I try to log in it just keeps connecting and then immediately disconnecting. Does anyone know what could be causing this?

---

### Post by ShelJ on 2008-11-08
> **error121 said:**
> I managed to get the 1.1.49 x64 package to install and run, but now when I try to log in it just keeps connecting and then immediately disconnecting. Does anyone know what could be causing this?
I had this happen a few weeks ago and found that I had another instance of Gyachi already running in the background for some reason.  Take a look at your system monitor to see if that is what is happening.

---

### Post by ebug on 2008-11-09
I added your PPA from [https://launchpad.net/~loell/+archive](https://launchpad.net/~loell/+archive), installed 1.1.50 thru synaptics. Connected to another YM friend (who is in Vista) and got everything working with 1.1.50 except the voice chat. 

Please show us the way man to make voice chat work. 
My Vista friend is killing me with "...can't hear you, just boot xp for goodness sake!!!"   

Boot xp? can't do that man. Just kill me.

---

### Post by loell on 2008-11-09
> **ebug said:**
> I added your PPA from [https://launchpad.net/~loell/+archive](https://launchpad.net/~loell/+archive), installed 1.1.50 thru synaptics. Connected to another YM friend (who is in Vista) and got everything working with 1.1.50 except the voice chat. 

Please show us the way man to make voice chat work. 
My Vista friend is killing me with "...can't hear you, just boot xp for goodness sake!!!"   

Boot xp? can't do that man. Just kill me.

:D

you want **voice** and not the**voice chat** thingy which is only for rooms.

you can call your vista friend through gizmo project or

you can even use ekiga and call him by typing..

**sip:[COLOR="Red"]user[/COLOR]_at_yahoo.com@yahoo.gtalk2voip.com **

---

### Post by oldHat on 2008-11-10
Hi Loell,

Thanks for your work.  I've been using Gyachi for a few months.

Ever since I went to 1.1.48, the program crashes every time I click "Save" from the setup menu.  I just installed 1.1.52, and I'm still having the same problem.

Any suggestions?

thanks

btw, just for fun, I just tried renaming .yahoorc/.gyachi, then starting the program.  I still can't save my updated status.  The same thing happens if I rename .yahoorc.  That should rule out problems with my .gyachirc, at least.

If I run it from a console I get,  "(gyachi:22634): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated", however, this doesn't kill the program.

---

### Post by spiderbatdad on 2008-11-10
> **oldHat said:**
> Hi Loell,

Thanks for your work.  I've been using Gyachi for a few months.

Ever since I went to 1.1.48, the program crashes every time I click "Save" from the setup menu.  I just installed 1.1.52, and I'm still having the same problem.

Any suggestions?

thanks

Hi. and are you using Intrepid on the 2.6.27-7 kernel? I thought these newer versions were for the newer kernels of Ubuntu. I am using 1.1.50. I do not have this problem. You might launch gyachi from the terminal and see what message appears when the program crashes...also look at dmesg | tail.

---

### Post by oldHat on 2008-11-11
> **spiderbatdad said:**
> Hi. and are you using Intrepid on the 2.6.27-7 kernel? I thought these newer versions were for the newer kernels of Ubuntu. I am using 1.1.50. I do not have this problem. You might launch gyachi from the terminal and see what message appears when the program crashes...also look at dmesg | tail.

Thanks for the reply.  Interesting call...I thought I was on the latest kernel, but it turns out that grub was still loading 2.6.24.  Fixed that problem, so now I'm on 2.6.27-7, but still no improvement.

dmesg reported these 3 errors after three abends.

[  166.952251] gyachi[7122]: segfault at 0 ip b71d62c3 sp bfa22b4c error 4 in libc-2.8.90.so[b715f000+158000]
[  224.752227] gyachi[7291]: segfault at 0 ip b72b52c3 sp bfd01a4c error 4 in libc-2.8.90.so[b723e000+158000]
[  263.542862] gyachi[7297]: segfault at 0 ip b721f2c3 sp bfb6a0ac error 4 in libc-2.8.90.so[b71a8000+158000]

Now I wonder if this is a libgtk problem, and not a gyachi problem.

---

### Post by kcallis on 2008-11-13
Any issues with logging in? Everytime I attempt to log in, I get an invalid password/login... But I am able to login using pidgin... Is it just me?

SOLUTION: After I upgraded, I switched the protocol from 8 to 7.5 beta and login worked perfectly...

---

### Post by venerix on 2008-11-15
Where i can find an xmms plugin for gyachi 1.1.52 in intrepid?...

---

### Post by S-99 on 2008-11-16
Came to report here. So i was working on my exgirlfriends computer moving her over to linux (she only used firefox and openoffice in the first place in windows). I asked if i could have her logitech quickcam communicate stx to shave off some money for what she owed me depending on how much the camera was worth.

I found gyachi 1.1.52, and it works just great with my new v4l2 quickcam communicate stx. I just installed gyachi and started up the cam, and it goes. Not to mention works great out of the box in ubuntu overall. Now i don't need crap kopete for kde3 anymore to ruin my gtk onlyness.

Good job. The last time i had cam working in gyachi was back when edgy eft was out with my quickcam messenger. I was expecting to and looking forward to need to use and mess around with flashcam with the latest version of gyachi with this v4l2 cam, but it turns out all the upgrades into the cam system worked out (especially for v4l2 devices).

:KS:KS:KS 3 gold stars and a :confused: me for wondering why i got lucky.

For those looking for the latest version of gyachi...go [here](http://ppa.launchpad.net/loell/ubuntu/pool/main/g/gyachi/). It's actually a repository, but it has the latest versions. Brought to you buy the gyachi devs.

---

### Post by loell on 2008-11-16
> **venerix said:**
> Where i can find an xmms plugin for gyachi 1.1.52 in intrepid?...

xmmms has been deprecated by most distributions, and for this reason, the plugin too is sort of deprecated. well, not entirely but it is disabled by default.

---

### Post by loell on 2008-11-16
> **S-99 said:**
> 
:KS:KS:KS 3 gold stars and a :confused: me for wondering why i got lucky.


heheh, you did not get lucky :lolflag: 

its a feature introduced in 1.1.5x :)

and.. as  gyachi dev said, we couldn't have greater webcam compatibility layer had it not for the work of [Hans De Goede]("http://hansdegoede.livejournal.com/3636.html") :KS

---

### Post by S-99 on 2008-11-16
Is the plans for moving over to gstreamer still going to happen? I know once that does happen, cams will be a lot less chancy. I was looking forward to using flashcam though. Oh well, less trouble for me and future users.

Lastly, the photoshare feature doesn't really work all the way. It works great for sharing any of my pictures, but i am unable to see pictures shared from the person i was chatting with. Happens all the time ever since photoshare was integrated. Still happened in 1.1.48. Idk about 1.1.52.

Very glad xmms got deprecated and disabled. It was easy enough to force install gyachi back in the day and just not have xmms installed also. As far as xmms goes, it's an old and outdated program based on gtk 1. Those looking for an updated xmms for music playing abilities aside from using xmms with gyachi should use audacious.

---

### Post by loell on 2008-11-16
> **S-99 said:**
> Is the plans for moving over to gstreamer still going to happen? I know once that does happen, cams will be a lot less chancy. I was looking forward to using flashcam though. Oh well, less trouble for me and future users.


the initial plan was to use gstreamer, but then pulseadio came in, so he used it for audio i/o and lately libv4l came too, so he used it for webcam i/o. the chances of using gstreamer is dwindling, but there's a plan in using empathy for voice calls, now empathy uses gstreamer, so i guess in the long run gyachi will be using gstreamer indirectly.

> **S-99 said:**
> 
Lastly, the photoshare feature doesn't really work all the way. It works great for sharing any of my pictures, but i am unable to see pictures shared from the person i was chatting with. Happens all the time ever since photoshare was integrated. Still happened in 1.1.48. Idk about 1.1.52. 

really? I haven't use photosharing for quite sometime now, yahoo may have change some implementation lately (you know them, they constanly change). could you take the time to report this in gyachi forum? thanks :)

---

### Post by hamzaad on 2008-11-18
Hello Sir!

I m a new user of Linux Ubuntu. unfortunately i m not a computer literate so i dont understand the technical things of Linux. Can u please help me how can i use Yahoo Messenger here on Linux Ubuntu? i m using Pidgin but that doesnt support voice chat. i tried from this thread the following

downloaded

gyachi_1.1.52-1~intrepid1_i386
gyachi_1.1.52-1~intrepid1_amd64.deb
gyachi_1.1.48-1~ubuntu2_amd64.deb

there is no executable file ...How can i use Gyachi? It will be a great help if i m able to use it, Thanx!!!

---

### Post by hamzaad on 2008-11-18
I m using the following version

Ubuntu 8.04 - the Hardy Heron - released in April 2008.

---

### Post by loell on 2008-11-18
there's a 1.1.48 deb package for hardy heron in the first post, after downloading, you can double click it, the installer will then ask you if you want to install it.

once installed, the program can be found at **main menu --> Internet --> gyachi**.

---

### Post by hamzaad on 2008-11-19
Thanx a lot Sir, it proved quite easy to install, but i m not having room voice chat. please guide me how can i get room voice chat, thanx!

---

### Post by acp_ on 2008-11-20
Hi, 

I had my laptop(fujitsu Esprimo U9200) reformatted and re-install 8.04.1 then I install gyachi 1.1.48 and flashcam everything went will since I have done this before in this same laptop although a different version of gyachi but this time its not working it work on the browser the testing part via flash but when I start the web cam in gyachi I got 'ioctl VIDIOCSPICT' could not set the property. error while querying mmap-buffer. Is there a way to debug this more I could not find any problem from the logs.

Thanks,
AC
[COLOR="Red"]
Please disregard this I already fix it I have change Setup -->General -->Webcam Device:/dev/video0 to video1.[/COLOR]

---

### Post by loell on 2008-11-20
> **hamzaad said:**
> Thanx a lot Sir, it proved quite easy to install, but i m not having room voice chat. please guide me how can i get room voice chat, thanx!

you either install [medibuntu]("https://help.ubuntu.com/community/Medibuntu") 

or install [gyachi-codecs]("http://downloads.sourceforge.net/gyachi/gyachi-codecs.deb?modtime=1194233368&big_mirror=0")

---

### Post by hamzaad on 2008-11-20
After installing the Gyachi codecs i m getting the following error:
Gyachi Voice Client
version 1.1.48
"No sound plugin has been configured, or the configured sound plugin was not found, or did not load"

please help!

---

### Post by dipaish on 2008-11-20
> **loell said:**
> use gizmo if you must call a yahoo messenger user,  [http://gizmo5.com/pc/download/]("http://gizmo5.com/pc/download/")

for webcam, room voice chat, and photosharing then gyachi.

I dont think gizmo supports voice chat for yahoo ...i couldnt make it possible after almost 3 hrs of trial .. It calls as if its really going to call and then after few seconds it cuts off itself ..even i did not manage to send instant message through gizmo..so i wonder it it really supports then how ? could you please mention ?

---

### Post by sabitha on 2008-11-22
i try to build gyachi my self then i got this error 

> 
~/gyachi-1.1.57$ sudo checkinstall
......
........
...........
Libraries have been installed in:
   /usr/local/lib/gyachi/plugins

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
make[3]: Leaving directory `/home/client/gyachi-1.1.57/plugins/mcrypt'
make[2]: Leaving directory `/home/client/gyachi-1.1.57/plugins/mcrypt'
Making install in xmms
make[2]: Entering directory `/home/client/gyachi-1.1.57/plugins/xmms'
make[3]: Entering directory `/home/client/gyachi-1.1.57/plugins/xmms'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gyachi/plugins" || /bin/mkdir -p "/usr/local/lib/gyachi/plugins"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'libgyachixmms.la' '/usr/local/lib/gyachi/plugins/libgyachixmms.la'
/usr/bin/install -c .libs/libgyachixmms.so /usr/local/lib/gyachi/plugins/libgyachixmms.so
/usr/bin/install -c .libs/libgyachixmms.lai /usr/local/lib/gyachi/plugins/libgyachixmms.la
/usr/bin/install: cannot stat `.libs/libgyachixmms.lai': No such file or directory
make[3]: *** [install-pluginLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/client/gyachi-1.1.57/plugins/xmms'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/client/gyachi-1.1.57/plugins/xmms'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/client/gyachi-1.1.57/plugins'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


i need to build gyachi with xmms plugins.
this what i write when configure :
> ./configure --enable-v4l2 --enable-soundevents --enable-statuspixmaps --enable-wine --enable-plugin_photosharing --enable-plugin_xmms

Please any suggestion

---

### Post by loell on 2008-11-23
> **sabitha said:**
> i try to build gyachi my self then i got this error 



i need to build gyachi with xmms plugins.
this what i write when configure :


Please any suggestion

make sure you're in a system that has xmms development files on a gyachi version that supports it (1.1.49 or earlier), every major distro has dropped xmms from their repositories, and that includes ubuntu since hardy heron. even gyachi's current release, xmms plugin code has also been obsoleted.

---

### Post by sabitha on 2008-11-23
> **loell said:**
> make sure you're in a system that has xmms development files on a gyachi version that supports it (1.1.49 or earlier), every major distro has dropped xmms from their repositories, and that includes ubuntu since hardy heron. even gyachi's current release, xmms plugin code has also been obsoleted.

Thanks loell. for your quick replay :)
i had xmms on my ubuntu compiled by myself.
now i already install xmms2-dev files like you say
but i got another error :
> gcc -shared  .libs/gyachi-pulseaudio.o  /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so -lpulse-simple -lpulse -lX11 -lpthread  -Wl,-soname -Wl,libgyachipulseaudio.so -o .libs/libgyachipulseaudio.so
creating libgyachipulseaudio.la
(cd .libs && rm -f libgyachipulseaudio.la && ln -s ../libgyachipulseaudio.la libgyachipulseaudio.la)
make[3]: Leaving directory `/home/client/gyachi-1.1.58/plugins/pulseaudio'
make[3]: Entering directory `/home/client/gyachi-1.1.58/plugins'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/client/gyachi-1.1.58/plugins'
make[2]: Leaving directory `/home/client/gyachi-1.1.58/plugins'
make[2]: Entering directory `/home/client/gyachi-1.1.58'
make[2]: Leaving directory `/home/client/gyachi-1.1.58'
make[1]: Leaving directory `/home/client/gyachi-1.1.58'


---

### Post by loell on 2008-11-23
> gcc -shared .libs/gyachi-pulseaudio.o /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so -lpulse-simple -lpulse -lX11 -lpthread -Wl,-soname -Wl,libgyachipulseaudio.so -o .libs/libgyachipulseaudio.so
creating libgyachipulseaudio.la
(cd .libs && rm -f libgyachipulseaudio.la && ln -s ../libgyachipulseaudio.la libgyachipulseaudio.la)
make[3]: Leaving directory `/home/client/gyachi-1.1.58/plugins/pulseaudio'
make[3]: Entering directory `/home/client/gyachi-1.1.58/plugins'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/client/gyachi-1.1.58/plugins'
make[2]: Leaving directory `/home/client/gyachi-1.1.58/plugins'
make[2]: Entering directory `/home/client/gyachi-1.1.58'
make[2]: Leaving directory `/home/client/gyachi-1.1.58'
make[1]: Leaving directory `/home/client/gyachi-1.1.58' 

there seems to be no error here. reading back at your previous post, I think the error is **checkinstall** specific, I don't know much about checkinstall though.

but a ```
sudo make install
``` could do the job. ;)

---

### Post by sabitha on 2008-11-23
sorry Wrong copy paste (when i try without xmms plugins)
but with xmms plugins enable still got error :
> gcc -shared  .libs/gyachi-xmms.o  /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so /usr/lib/libxmms.so -lX11 -lpthread  -Wl,-Bdynamic -Wl,--export-dynamic -Wl,-soname -Wl,libgyachixmms.so -o .libs/libgyachixmms.so
creating libgyachixmms.la
/bin/sed: can't read /usr/lib/libgtk.la: No such file or directory
libtool: link: `/usr/lib/libgtk.la' is not a valid libtool archive
make[3]: *** [libgyachixmms.la] Error 1
make[3]: Leaving directory `/home/client/gyachi-1.1.58/plugins/xmms'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/client/gyachi-1.1.58/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/client/gyachi-1.1.58'
make: *** [all] Error 2


thank for your attention loell
im just try to make gyachi with xmms plugins
but its ok. i know gyachi's current release, xmms plugin code has also been obsoleted.
maybe on other release it will include another player plugins to show my status online :)

---

### Post by loell on 2008-11-23
1.1.58 package is now available on the first post. :)

---

### Post by hamzaad on 2008-11-24
After installing the Gyachi codecs i m getting the following error:
Gyachi Voice Client
version 1.1.48
"No sound plugin has been configured, or the configured sound plugin was not found, or did not load"

please help!

---

### Post by loell on 2008-11-24
> **hamzaad said:**
> After installing the Gyachi codecs i m getting the following error:
Gyachi Voice Client
version 1.1.48
"No sound plugin has been configured, or the configured sound plugin was not found, or did not load"

please help!

choose any plugin in setup ---> options --> Sound device.

---

### Post by tonyuk123 on 2008-11-30
I have downloaded and extracted GYACHI
but how do i install it?

Tony

---

### Post by loell on 2008-12-01
> **tonyuk123 said:**
> I have downloaded and extracted GYACHI
but how do i install it?

Tony

double click it. :)

---

### Post by tonyuk123 on 2008-12-01
Double click what?
lots of files, if i double click some the try to open in terminal, very briefly, creating some other kind of text file, but no install?
I am new to Linus/Ubuntu.
Only had it few days.....

---

### Post by loell on 2008-12-01
> **tonyuk123 said:**
> Double click what?

what version of ubuntu are you using? 

you only need to download one package that is compatible for the ubuntu version that you installed, after downloading , the file will appear on your desktop, and then you can double click the file, it will prompt you to install it.

---

### Post by tonyuk123 on 2008-12-01
hi,
i have installed ubuntu 8.04
i went to this site
[http://gyachi.sourceforge.net/download.shtml](http://gyachi.sourceforge.net/download.shtml)
and downloaded the latest version of GYACHI 1.1.0
but it is a .tar.gz file?
it doesn't try to install if i double click it, just opens as if it is a folder?

Tony

---

### Post by loell on 2008-12-01
> **tonyuk123 said:**
> hi,
i have installed ubuntu 8.04
i went to this site
[http://gyachi.sourceforge.net/download.shtml](http://gyachi.sourceforge.net/download.shtml)
and downloaded the latest version of GYACHI 1.1.0
but it is a .tar.gz file?
it doesn't try to install if i double click it, just opens as if it is a folder?

Tony

download **Gyachi 1.1.48 Deb package for hardy heron** at the first post of the first page of this thread.

---

### Post by venerix on 2008-12-03
Hi everybody! I wanna compile gyachi from source-code!I have installed all dependencies but i dont know what parameters to use when i configure it!

I have used 

./configure --enable-maintainer-mode --enable-wine --enable-status-pixmaps 

I know there are many more options...If somnebody know them please post here...:-P

---

### Post by danscali on 2008-12-06
Does it work for gusty 8.04? I got an error " dependency is not satisfiable: libasound2" during installation (gyachi_1.1.58-1~intrepid_i386.deb)

---

### Post by tonyuk123 on 2008-12-07
hi,
Ok i gyachi installed and working
but not webcam!
it works in cheese and on a few other bits but not in gyachi
Any ideas?
i have ubuntu 8.04
and an aiptek pencam
Tony

---

### Post by loell on 2008-12-07
> **tonyuk123 said:**
> hi,
Ok i gyachi installed and working
but not webcam!
it works in cheese and on a few other bits but not in gyachi
Any ideas?
i have ubuntu 8.04
and an aiptek pencam
Tony

well, you will need to upgrade to intrepid( ubuntu 8.10) with later versions of gyachi, currently you're on 8.04 with gyachi v 1.1.48 , but the later versions (1.1.50-59 ) addressed some webcam detection not available for Ubuntu 8.04.

---

### Post by tonyuk123 on 2008-12-07
how do i do that easily?
I already have the full install disk for 8.10 
will it ask if i want to upgrade if i try it?
Tony

---

### Post by tonyuk123 on 2008-12-07
Aha, ok i upgraded to 8.10
all seemed to go well, still working and all seems to be as it was basically.
But still no webcam in Gyachi
i get the error
An error occured at 'ioct VIDIOCSPICT'
could not set camera properties

and under it, presumably the first error

could not open Video4linux device
The device may already be in use

even from fresh boot

Tony

---

### Post by loell on 2008-12-07
> **tonyuk123 said:**
> Aha, ok i upgraded to 8.10
all seemed to go well, still working and all seems to be as it was basically.
But still no webcam in Gyachi
i get the error
An error occured at 'ioct VIDIOCSPICT'
could not set camera properties

and under it, presumably the first error

could not open Video4linux device
The device may already be in use

even from fresh boot

Tony

have you already installed gyachi version [COLOR="Red"]1.1.58[/COLOR] in intrepid?

---

### Post by raja_rangaswamy on 2008-12-07
Thanks it worked.
Found this thread after a lot of searching.

---

### Post by raker4058 on 2008-12-08
I have installed gyachi 1.1.59 from your repository on an updated intrepid box in 32bit land.  When setting to the v8 login, i connect, and get disconnected immediately... over and over..

When choosing v7.5 i get a different error.

Pidgin works fine.

Any ideas of where to start?

---

### Post by loell on 2008-12-08
> **raker4058 said:**
> I have installed gyachi 1.1.59 from your repository on an updated intrepid box in 32bit land.  When setting to the v8 login, i connect, and get disconnected immediately... over and over..

When choosing v7.5 i get a different error.

Pidgin works fine.

Any ideas of where to start?

make sure you don't two instances of the program running. as the other will reconnect / disconnect over and over again by default.

---

### Post by tonyuk123 on 2008-12-08
I have installed gyachi 1.1.48 as instructed earlier in this thread on 8.04.
but after that i have upgraded to Ubuntu 8.10
where do i get the version Gyachi 1.1.58 from?
Tony

---

### Post by loell on 2008-12-08
> **tonyuk123 said:**
> 
where do i get the version Gyachi 1.1.58 from?
Tony

still at the first post of the first page of this thread, be sure to remove first the older version, **sudo apt-get remove gyachi**

---

### Post by tusherr on 2008-12-11
its a great thing buddy. gyache is really great.8-)8-)8-)8-)8-)8-) awesome............

---

### Post by tonyuk123 on 2008-12-11
> **loell said:**
> still at the first post of the first page of this thread, be sure to remove first the older version, **sudo apt-get remove gyachi**

Hi leoll,
Thanks for your help here, 

only thing is, i am now on 8.10 because it has better webcam support.(with all updates installed)
I now have installed Gyachi 1.1.58 (1 deb?) after first uninstalling the other version as you suggested.
But still the webcam doesn't function in Gyachi!
any ideas?
Tony

---

### Post by loell on 2008-12-11
> **tonyuk123 said:**
> 
any ideas?
Tony

I really thought it could detect your webcam :(

can you post your webcam ID? I might not able to give any solution about this, but at least we could acquire more info about your case.

```
lsusb
```

---

### Post by tonyuk123 on 2008-12-12
> **loell said:**
> I really thought it could detect your webcam :(

can you post your webcam ID? I might not able to give any solution about this, but at least we could acquire more info about your case.

```
lsusb
```

Hi, tried the command got this

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 03f0:b802 Hewlett-Packard Photosmart 7400 Series
Bus 003 Device 005: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0553:0202 STMicroelectronics Imaging Division (VLSI Vision) Aiptek PenCam 1
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

seems the cam exists, but now since upgrade it doesn't seem to work in cheese either, which it did under 8.04

Regards
Tony

---

### Post by x58 on 2008-12-12
Hi everybody. I have Linux Ubuntu 8.10 and I am new too. Cannot figure out.Witch Gyachi I need to install.
1. gyachi_1.1.48-1~ubuntu11_i386.deb
2. gyachi_1.1.59-1~intrepid1_i386.deb
3. gyachi_1.1.48.orig.tar.gz
4. gyachi_1.1.59-1~intrepid1.tar.gz
All I know, I have 32 not 64
Please help anybody?

---

### Post by loell on 2008-12-12
> **x58 said:**
> Hi everybody. I have Linux Ubuntu 8.10 and I am new too. Cannot figure out.Witch Gyachi I need to install.
1. gyachi_1.1.48-1~ubuntu11_i386.deb
2. gyachi_1.1.59-1~intrepid1_i386.deb
3. gyachi_1.1.48.orig.tar.gz
4. gyachi_1.1.59-1~intrepid1.tar.gz
All I know, I have 32 not 64
Please help anybody?

**gyachi_1.1.59-1~intrepid1_i386.deb**

---

### Post by x58 on 2008-12-12
Thank you

---

### Post by x58 on 2008-12-12
Cannot connect.Port 5050, Protocol YMSG-15/Messenger 8.I try different servers, but was receiving next messages:
1.Connection time out
2.Incorrect Password
4.Connected and then disconnected - I turn auto login off and Auto Reconnected if Disconnected I turn off too.
So, how I can connect?

---

### Post by loell on 2008-12-12
can you login thru pidgin with the same password?

---

### Post by x58 on 2008-12-13
Yes, I can. I disable Pidgin.

---

### Post by x58 on 2008-12-13
My mistake, Cannot connect, no to MSN,no to Yahoo.Sorry, my mistake

---

### Post by x58 on 2008-12-13
Now I am finally in Gyachi, but when I try to put work voice. then I receive next message:Cannot run gyvoice due to the following missing files:

      tsd32.dll
      tssoft.acm

Not in the following directories:
      /
      /usr/lib/win32/
      /usr/lib/win32/
      /usr/local/lib/win32/
      /usr/lib/codecs/

Can you help me, what I need do too exactly now?

---

### Post by loell on 2008-12-13
> **x58 said:**
> 
Can you help me, what I need do too exactly now?

you need to install [gyachi codecs]("http://downloads.sourceforge.net/gyachi/gyachi-codecs.deb?modtime=1194233368&big_mirror=0")

please remember that this is only "room voice chat" not pc to pc call.

---

### Post by x58 on 2008-12-13
Thanks again.I have some kind problem again with sign in.GYachi don't sign in and Pidgin don't sign in. I thinking there supposed be some kind problem.Can you give any advice.

---

### Post by x58 on 2008-12-14
Hi Mr.Loell,
I find out problems with connection and problem was, because Yahoo don't like anybody to use 3-rd party messenger. I changer scs.msg.yahoo.com to 66.163.181.173 and no any problems with sign in. Same I did with Pidgin messenger.
I have internal HP Pavilion web camera and it was working, but picture was double and very little. Had some kind problems. I install old USB Port Logitech and web picture is very clear and beautiful.
When I install Gyatchi Codecs, then Skype. aMSN was messed up. I was able fix everything, only cannot fix aMSN Microphone. It still not work.
So, I try everything to put work Voice Conference, but it never worked.I read and was not able find noting.At Gyatchi anything about VOICE don't just work.
Any advice??? I want thank you Mr. Loell at your Forum I find much help already and I hope maybe somebody can help me with Voice Conference.....

---

### Post by tonyuk123 on 2008-12-16
Hi leoll, 
Well after much trying, with little success i have now re-installed Ubuntu 8.04.
Seems it made no difference to webcam support other than not working in even more programs!.
Also firefox was very very unstable.
So now i am back on 8.04, with the version of Gyachi 1.1.48 deb
it works but no webcam.(works on chesse and in java within firefox)
Any ideas what i should try first?
Bearing in mind this is a fresh install of 8.04 with all updates applied, and a fresh install of Gyachi 1.1.48.
Thanks for any ideas
Tony

---

### Post by spiderbatdad on 2008-12-18
@loell thanks so much for pointing me here: [http://groups.google.com/group/microdia](http://groups.google.com/group/microdia) 
It took only minutes to compile and install the driver, after a reboot, webcam is working great with gyachi.

```
$ lsusb
Bus 002 Device 002: ID 0c45:62e0 Microdia 

```

---

### Post by trendyabinash on 2008-12-18
use "sudo" infront of apt-get and you will get the required permission

sudo is a command used to give root previledges

---

### Post by loell on 2008-12-18
> **spiderbatdad said:**
> @loell thanks so much for pointing me here: [http://groups.google.com/group/microdia](http://groups.google.com/group/microdia) 
It took only minutes to compile and install the driver, after a reboot, webcam is working great with gyachi.

```
$ lsusb
Bus 002 Device 002: ID 0c45:62e0 Microdia 

```

great :), is this also working with intrepid?

---

### Post by DexterLB on 2008-12-19
Hello.
I've used gyachi for 2 years by now under gutsy, then hardy, and it worked perfectly. And now, when I upgraded to intrepid, The voice chat in rooms is screwed up - I can hear the others, but they can't hear me. I tried to upgrade t the newest version, but the problem isn't fixed. Any suggestions?

---

### Post by ruffwuk on 2008-12-19
Hi everyone,
I was reading the thread, and I cant find that 1.48 version of gyachi... Can some one tell me where to get it?

---

### Post by DexterLB on 2008-12-19
I don't know where you can get 1.48 from, but the newest one - e.g. 1.1.58 is available for download at the first post of this thread.

P. S. Still struggling to get the voice chat working, but no luck :cry:

---

### Post by tqft on 2008-12-19
> **DexterLB said:**
> Hello.
I've used gyachi for 2 years by now under gutsy, then hardy, and it worked perfectly. And now, when I upgraded to intrepid, The voice chat in rooms is screwed up - I can hear the others, but they can't hear me. I tried to upgrade t the newest version, but the problem isn't fixed. Any suggestions?

Have you looked at the PulseAudio controls?  PulseAudio is installed in Intrepid by default and you mic may be muted in the Pulse controls.

There is a good howto somewhere in the forums (search recommended).

---

### Post by ruffwuk on 2008-12-19
Thanks DexterLB
My error, and I got 1.1.59 installed.  but I am missing some plugins for Blowfish, ALSA and Pulse (I think I can fix on my own), but I noticed my webcam is not working.  I will update on my progress.

---

### Post by DexterLB on 2008-12-20
> **tqft said:**
> Have you looked at the PulseAudio controls?  PulseAudio is installed in Intrepid by default and you mic may be muted in the Pulse controls.

There is a good howto somewhere in the forums (search recommended).
I noticed that the audio driver is set to ALSA in the gyachi settings. I'll try to change it to pulseaudio and un-mute the mic. Thanks for your replay.

---

### Post by tonyuk123 on 2008-12-22
Hmm, ok
I give up, seems webcam support in 8.10 is worse than 8.04, and seems that Gyachi doesn't do webcams either!
Thanks
Tony

---

### Post by inchkape on 2008-12-26
Hi all, hi Loell,

my first time here, I use linux Mint 6, based on Intrepid and am a user of amsn, kopete and gyachi.

Gyachi is what brings me here. I installed intrepid based mint rc1 so that I could try gyachi 1.1.5x specifically so that i could use the webcam. It worked perfectly.
When I installed the final version of mint 6.0 however and wanted to reinstall gyachi, the .deb packages had been changed to 1.1.58 (the first install was 1.1.52). The webcam (sending) which worked perfectly until then, now showed a double image rather than a normal one.
Switching to a usb webcam (Logitech quickcam for notebooks pro) the webcam again worked fine. The problem seems to be with the integrated webcam in my laptop.
The laptop is a hp dv6658 with integral hp webcam. I noticed that the user "X58" who posted a week ago on this forum has exactly the same problem.
Is it possible for us to reinstall the 1.1.52 package? I could no longer find it to download and unfortunately didn't have the package saved to disk, but installed with GDebi.
Any help will be appreciated, because I don't want to carry a usb cam around when i have one in my comp.
It works fine with amsn and skype, just having this issue with yahoo and gyachi. Ironically the version of kopete delivered with mint 6 (and ubuntu) is also having webcam issues :P

---

### Post by loell on 2008-12-26
> **inchkape said:**
> 
Is it possible for us to reinstall the 1.1.52 package?

hello, unfortunately i am unable to track the PPA url for 1.1.52 , could you try [1.1.59]("https://launchpad.net/%7Eloell/+archive/+files/gyachi_1.1.59-1~intrepid1_i386.deb") instead? maybe then your integrated webcam will work properly.

---

### Post by spiderbatdad on 2008-12-26
> **loell said:**
> great :), is this also working with intrepid?
>  @loell thanks so much for pointing me here: [http://groups.google.com/group/microdia](http://groups.google.com/group/microdia)
It took only minutes to compile and install the driver, after a reboot, webcam is working great with gyachi. 
Sorry to get back so slowly. Yes, working on intrepid.

---

### Post by Tosa on 2009-01-01
Hi all,

I've installed GYachE 1.1.58.
On the first try my MSI StarCam didn't work, but when I changed Webcam Device from video0 to video1 the picture showed up. The problem is that it is a small double picture.
I've tried Kopete and there I have the normal picture...

The other issue is the lack of any sound in GYachE. The only Sound Device I have listed in the Options is ALSA plugin 1.0.17a

Any help will be appreciated.

---

### Post by andyshedd on 2009-01-18
hello, at long last I have found the source! From reading the posts it seems like gyachi does not support voice chat in the 64 bit version. does that mean permamently? and no more new versions for hardy? i've also had some bad luck with intrepid..

---

### Post by loell on 2009-01-18
> **andyshedd said:**
> hello, at long last I have found the source! From reading the posts it seems like gyachi does not support voice chat in the 64 bit version. does that mean permamently? and no more new versions for hardy? i've also had some bad luck with intrepid..

yep, its a wine code that could not be compiled in 64 bit, from the looks of it, its permanent, unless theoretically  the voice decoding is done in ffmpeg .

---

### Post by zouriel on 2009-01-22
I cant figure it out...

With gyachi my cam works peachy but when i request to view someone i get maybe 2 secs. of video then it locks on my side and the cam module poofs away.  If they send it to me same issue, however typically if i request 2 times wait till it dyes both times and they send it to me it works fine after that per user....
any ideas

---

### Post by zouriel on 2009-01-23
i forgot to mention ... im running ubuntu ibex with version 1.1.59 gyache

---

### Post by BordorFox on 2009-01-25
Just thought i would mention this here in case someone has this issue

i am on 8.10 intrepid using a intel quad core

installed 1.1.59 intrepid amd64 package and the codecs

GYachi itself works fine but when i click the voice button, nothing happens

---

### Post by noumaan on 2009-01-27
I have the same problem on my interpid 64bit ubuntu Gyachi works just fine but no voice chat when I pressed voice chat button it gave me some errors. then I found out I need to install gyachi codecs after installing codecs nothing happens when i press voice chat button not even errors come up. 

I tried to install 32bit version with getlibs but get getlibs give me this error

No match for libgyachi.so
No packages to install

I am totally clueless please help me resolve the issue.

---

### Post by loell on 2009-01-27
as stated in the first page, there is no room voice chat for 64 bit.

---

### Post by noumaan on 2009-01-27
loell, 

Can you please tell me is this possible for me to install 32bit Ubuntu on my computer? I installed 64bit just because someone suggested that core2 duo needs 64bit ubuntu os to perform better. If i install 32bit ubuntu so gyachi will work on my computer?

---

### Post by loell on 2009-01-27
install the 32 bit package by using getlibs, it's also in the first page, that, if you want the voice chat for rooms only feature.

---

### Post by fieldstone on 2009-01-29
None of these files for Intrepid seem to work. The Hardy ones are working fine, though. What's going on?

---

### Post by loell on 2009-01-29
> **fieldstone said:**
> None of these files for Intrepid seem to work. The Hardy ones are working fine, though. What's going on?

no one will have a clue, unless you state the error.

---

### Post by bjorkiii on 2009-01-31
I think he means when you try and download the intrepid versions the newer ones it gives a page error

---

### Post by finaldata on 2009-01-31
here are the new links...

[http://ppa.launchpad.net/loell/ppa/ubuntu/pool/main/g/gyachi/gyachi_1.1.59-1~intrepid1_i386.deb](http://ppa.launchpad.net/loell/ppa/ubuntu/pool/main/g/gyachi/gyachi_1.1.59-1~intrepid1_i386.deb)

---

### Post by loell on 2009-01-31
aah! the new url! i didn't notice until i read launchpad's notification, thanks for pointing that out. :)

---

### Post by dhonnoll on 2009-02-02
My in laws at the other end use winblows XP 32 bit with yahoo, am I going to be able to voice chat with them?

---

### Post by loell on 2009-02-03
> **dhonnoll said:**
> My in laws at the other end use winblows XP 32 bit with yahoo, am I going to be able to voice chat with them?

I think you meant voice calls ( voice chat is only for yahoo rooms) , and for that I'd  recommend using gizmo5 to call their yahoo messenger. :)

---

### Post by DougieFresh4U on 2009-02-03
> **dhonnoll said:**
> My in laws at the other end use winblows XP 32 bit with yahoo, am I going to be able to voice chat with them?

No.

---

### Post by draxz on 2009-02-03
Hello,

I was told this also works for MSN, I wanna be able to voice and video chat on MSN and yahoo


is it possible using this software?

---

### Post by loell on 2009-02-03
no you can't, gyachi is exclusively for yahoo protocol, you can however use amsn or kopete to be able to video chat with msn contacts and separately voice call them through gizmo.

---

### Post by t.alex on 2009-02-07
Hi loell,

thanks for sharing this nice piece of Software :p

is it possible to modify the appearance of gyachi? there are a few themes, but they aren't really appealing...

btw  what type of file are the "raw" sounds? I've only managed to open them with audacity and the raw files audacity saves are not rendered correctly by gyachi 

Thanks!

---

### Post by loell on 2009-02-07
> **t.alex said:**
> 
is it possible to modify the appearance of gyachi? there are a few themes, but they aren't really appealing... 

the user interface is hard coded and has become difficult to rewrite it, the current developer can only add features and fix bugs, but couldn't change the appearance drastically.


> **t.alex said:**
> 
btw  what type of file are the "raw" sounds? I've only managed to open them with audacity and the raw files audacity saves are not rendered correctly by gyachi 

Thanks!

its the same raw sound format,but the length of the sound file should more or less the same as the older ones, though i havent tried longer raw sound with pulse audio settings.

---

### Post by gretchch on 2009-02-11
I installed the gyachi_1.1.59-1~intrepid1_i386.deb package on my AMD64 intrepid installation, using the force-all and getlibs method (because I want the sound support).  I can get gyachi to come up, but I get the following messages in the Chat window:

GyachE Improved 1.1.59 
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)
** Plugin '/usr/lib/gyachi/plugins/libgyachilibnotify.so' could not be loaded because of an error:
file not found
** Location: /usr/lib/gyachi/plugins/libgyachilibnotify.so
 Plugin Loaded:  'Blowfish-Internal' 
** Plugin '/usr/lib/gyachi/plugins/libgyachigpgme.so' could not be loaded because of an error:
file not found
** Location: /usr/lib/gyachi/plugins/libgyachigpgme.so
** Plugin '/usr/lib/gyachi/plugins/libgyachigtkspell.so' could not be loaded because of an error:
file not found
** Location: /usr/lib/gyachi/plugins/libgyachigtkspell.so
 Plugin Loaded:  'GyachI-sound-plugin-ALSA' 
 Plugin Loaded:  'GyachI-sound-plugin-PulseAudio' 
** Plugin '/usr/lib/gyachi/plugins/libgyachimcrypt.so' could not be loaded because of an error:
file not found
** Location: /usr/lib/gyachi/plugins/libgyachimcrypt.so
 Loaded 3 plugins from '/usr/lib/gyachi/plugins'.

The /usr/lib/gyachi/plugins directory exists, and all of the libraries that it's complaining about are in there, and oddly it is able to load three of them without complaint, which leads me to believe it's a dependency that's not being found, and not the actual plugin file itself.

I hope that I haven't shot myself in the foot...I went through the whole process of building and installing the 1.1.61 version at 64 bit (downloaded the tar from sourceforge) and disabled wine.  It wasn't until I'd done the make install and started running the application that I realized that wine was needed for sound support.  That's when I found this thread.  I did a make uninstall of the 1.1.61 version and installed the 32-bit 1.1.59 package, but I'm wondering if I installed some 64-bit pre-req when I was doing the 64-bit build which is now interfering with the 32-bit package.

---

### Post by ov1d1u on 2009-02-15
I have a problem:

Gyachi crash everytime when I press the "Save" Button in settings dialog (Segmentation Fault).

Any way to solve that? I'm tired of editing the configuration file :lolflag:

---

### Post by Openrulers on 2009-02-15
Thank you. Something a miss in Ubuntu. Let me see how this works.

---

### Post by crjackson on 2009-02-22
I just installed Gyachi in Intrepid and it went well.  How do I enable my webcam? It's a Philips SPC 900NC

It works in Skype, aMSN, Ekiga, cheese, wxcam, and everything else I've tried.

Any help would be appreciated.

Downloaded and installed GyachE Improved 1.1.59

Nevermind, my bad.  I found it.

---

### Post by crjackson on 2009-02-23
Is it possible to install GyachE Improved **1.1.59** on Hardy?

---

### Post by loell on 2009-02-23
> **crjackson said:**
> Is it possible to install GyachE Improved **1.1.59** on Hardy?

unfortunately it isn't :(

it has a package dependency that's not on hardy, the (**libv4l**) package which also depends of newer kernels.

---

### Post by crjackson on 2009-02-24
> **loell said:**
> unfortunately it isn't :(

it has a package dependency that's not on hardy, the (**libv4l**) package which also depends of newer kernels.

Okay, thanks.

---

### Post by ov1d1u on 2009-03-03
> **ov1d1u said:**
> I have a problem:

Gyachi crash everytime when I press the "Save" Button in settings dialog (Segmentation Fault).

Any way to solve that? I'm tired of editing the configuration file :lolflag:

I started Gyachi from the LiveCD and it runs perfectly... I reinstalled my distro and it crashes again... Somebody knows any workaround?

---

### Post by loell on 2009-03-03
> **ov1d1u said:**
> I started Gyachi from the LiveCD and it runs perfectly... I reinstalled my distro and it crashes again... Somebody knows any workaround?

.gyachrc isn't really hard to edit, if the save setting button is giving you crashes, then might as well just edit the file. once you have a working rc file then back it up for future use.

---

### Post by stanz on 2009-03-08
> **loell said:**
> yes there is a particular entry, i commonly suggest deleting the entire /.yahoorc directory which is actually not that good of an advice but just not to create more confusion in explaining for new users.
anyway, the particular file is **/.yahoorc/gyach/gyachrc** the entries are explanatory, just try to find
**chat_window_width =**
and
**chat_window_height =**

Hi loell, this may be an old issue - but it may help someone...(?)
I'm refering to xeddog's post, #162 -- which is/was my issue also.
The width got so wide - I started opening and using as root, which this did not occur. 
I'm using Ubuntu 8.10, with GyachE Improved 1.1.58 and this post is also mirrored on the [Sourceforge]("https://sourceforge.net/forum/forum.php?thread_id=2286413&forum_id=533967") site.
I didn't install Compiz, which I hear messes with windows in different ways.
Checking into the .yahoorc folder, ".yahoorc/gyach/gyachrc"
For me - line 98, of the gyachrc file - showed:
**chat_text_width** = 2856
**chat_user_height** = 328

I Changed that to:
**chat_text_width** = 856
**chat_user_height** = 328    [COLOR=DarkRed]:: "[/COLOR][COLOR=DarkRed]which was better![/COLOR]

I Changed again:
**chat_text_width** =300
**chat_user_height** = 100   [COLOR=DarkRed]=== BUT == it reverted to[/COLOR]:

**chat_text_width** = 932
**chat_user_height** = 277

[COLOR=DarkRed]*_it also it adjusted the:_*[/COLOR] **emotes_window_height** [COLOR=DarkRed]*from*[/COLOR] 197 [COLOR=DarkRed]*to*[/COLOR] 239

Weird, but much better screen viewing...I'll update this if the changes don't stick.

---

### Post by stanz on 2009-03-08
nope ~ it didn't stick...but grew again slowly.
changes didn't stick--next startup--the file shows:
**emotes_window_height** = 239
**chat_text_width** = [COLOR=DarkRed]1196[/COLOR]
**chat_user_height** = 277

and the next startup:
**emotes_window_height** = 239
**chat_text_width** = [COLOR=DarkRed]1460[/COLOR]
**chat_user_height** = 277

and another:
**emotes_window_height** = 239
**chat_text_width** = [COLOR=DarkRed]1724[/COLOR]
**chat_user_height** = 277

increments of 264...hummm?

---

### Post by loell on 2009-03-08
wierd behavior, could this be the doing of your current DE or wm?

---

### Post by stanz on 2009-03-08
hi,
ya got me there -- i wouldn't have a clue or an idea how to check on that.
this install is a few months fresh, i'm using gnome and believe its metacity {?}.

since this didn't occur using root, i checked roots gyachrc file, and found your mention of:** chat_window_width =** and **chat_window_height =**
its like this:
**chat_window_x** = 170
**chat_window_y** = 104
**chat_window_width** = 800
**chat_window_height** = 600

perhaps a copy & paste into my user file is in order?

and the other pref's:
**emotes_window_height** = 90
**chat_text_width** = 792
**chat_user_height** = 336
which are good and don't change.

anyway - thanks for your reply...i haven't found any other posts about this [except xeddog's] so i didn't figure it worth taking up your time.
:)

---

### Post by stanz on 2009-03-09
huh - so far, that copy & paste is working and the window size hasn't grown!
i did that as root - if it helps anyone.

i can't say if me changing an option - threw it off.
its all setup/standard options - i didn't mess with any others.

i did notice in the "backups" folder - gyachrc.0 had the stuff i just pasted in...
whereas gyachrc.9 had the over-size info...?

ok - guess i'm done....thanks again for the reply loell !!

---

### Post by binskipy2u on 2009-03-10
anyone have gyach 1.1.61 for 64bit?
i seen it on forums, but cant find a 64bit version and if so, what are the changes from 1.1.59.x86_64?

thanks for any information

---

### Post by SleeplessCDN on 2009-03-11
I just installed Gyache 1.1.48 because I am running Ubuntu 8.04 and I am having a very strange problem.

After I supposedly login to Yahoo because the Yahoo login window disappears but that is all that happens, the menu buttons doesn't work and when the information window comes up while I hover over a button or the menu bar the image is highly distorted.

I have no idea how to fix this problem, does anybody have any ideas whatsoever, right now I am open to anything at all.

Here goes:

[IMG]http://i16.photobucket.com/albums/b10/sleeplessincanada/Screenshot.png[/IMG]

[IMG]http://i16.photobucket.com/albums/b10/sleeplessincanada/Screenshot1.png[/IMG]

---

### Post by _sluimers_ on 2009-03-14
For some reason I can no longer start gyachi.
This is my error.

```

rogier@rogier-desktop ~ $ gyachi
Xlib:  extension "RANDR" missing on display ":0.0".
Segmentation fault

```

---

### Post by stalkingwolf on 2009-03-20
here is my situation.  I have 2 desk tops both now running 8.10 with logitech quick cam chat,s .  gyachi works with the cams great, weird but great.

Now my problem My laptop an HP nc8000. same cam.  the cam works everywhere
but gyachi.  Camorama, cheese, ekiga, and gyachi when i click start web cam.
It just wont broadcast.

at this point 8.10 is not an option.  i have no wireless in 8.10. all fo my wireless options that work in 8.04 OOTB refuse to function at all in 8.10.
laptop w/o wireless kind of defeats the purpose.

Any ideas?

also when i try to install gyachi 1.1.59 i get a defencie error libcrypt 4 not satisfiable.  first time that has happened.  but then this install of 8.10 is the first time i have installed and been told that
" no updates were available"  system up to date.  ever

---

### Post by loell on 2009-03-20
the last compatible version for 8.04 was gyachi V 1.1.48 , as 1.1.5**x**
introduces a couple more dependencies not available in 8.04 or earlier. this decision was a move for better webcam compatibility layer,  as you may have noticed, your webcam is functioning in gyachi in your other desktop that could mostly be running 8.10?

so if your laptop is running 8.04 , you may be out of luck for now since version V 1.1.48 and below isn't that good  at detecting some webcams.

I guess, Jaunty is next bet. :)

---

### Post by stalkingwolf on 2009-03-21
It seems to be detected.  It shows just fine when i click start web cam.
It just doesnt broadcast.  Comes up as not on line.


OK i tried 9.04 last night.  same problem . no wifi on the HP laptop.

I am wondering why you would not want to get this product fully functional for the LTS version.

---

### Post by stalkingwolf on 2009-03-24
Last night my wife and I were on Yahoo with her SiL. all of a sudden both cams just stopped working.    We could see them on our respective computers,
it said they were broadcasting but never could see them again on the other computers.

I am going to try to reinstall Gyachi today.  see if that works.

---

### Post by loell on 2009-03-24
it's probably yahoo's.

---

### Post by stalkingwolf on 2009-03-25
I reinstalled Gyachi last evening on both our computers and the cams are working again.  havent tried with the SiL yet.  later today.

Maybe ot was just one of those ozone things, my cell phone has been acting weird the last few days also.

---

### Post by Baby_Allgood on 2009-03-26
I'm having problems logging into my yahoo account on gyache v.1.1.59 
I click on the smiley face in the launch toolbar at the top of the screen...
The interface where I view the friends list and other thing comes up...
With the login interface in front of it...
And then when I click the login button...
it takes a little bit... as if it is connecting..
but, then nothing shows up in the friends list interface...
and I cant do anything but close it and try it again...
but it does the same thing each time..
and I tryed re-installing it...
that has not worked...
it seems like it work for me just the first time, and then.... nothing
I was wondering if anybody else has had this problem, and if there is something that I can do to make it work again....

---

### Post by stalkingwolf on 2009-03-27
try changing the server.  it did that to me with a couple of the servers.

---

### Post by a3qp on 2009-04-04
Hi Loell,
Is it possible to install Gyachi in Ubuntu Jaunty amd64 ?
If so, where can I find tha packages?

Thanks.

---

### Post by loell on 2009-04-05
> **a3qp said:**
> Hi Loell,
Is it possible to install Gyachi in Ubuntu Jaunty amd64 ?
If so, where can I find tha packages?

Thanks.

the intrepid amd64 deb package is still most probably compatible with jaunty, try it, let me know how it goes. :)

---

### Post by loell on 2009-04-06
new version is out **1.1.63** for intrepid and for jaunty, available at my PPA. :)

old new feaure: buddy revocation, you now have the ability again to remove your name in others' buddy list. ;)

---

### Post by crjackson on 2009-04-11
How do you setup the video recording option. Everytime I try to record an incomming video, it only captuers a series of still frame jpg's.

Can someone walk me through this?  I'm setting up a system for a friend of mine who is addicted to Yahoo stuff. He's 2K miles away and I won't be around to help him figure that out so I need to do that now if possible.

I'm currently using 1.1.63 on Intrepid, but he will be using Jaunty.

---

### Post by loell on 2009-04-12
with mencoder, make it as an avi.

```
mencoder -ovc lavc -mf fps=3:type=jpg 'mf://*.jpg' -o movie.avi
```

---

### Post by crjackson on 2009-04-12
> **loell said:**
> with mencoder, make it as an avi.

```
mencoder -ovc lavc -mf fps=3:type=jpg 'mf://*.jpg' -o movie.avi
```

I put the commands into the recorder settings and it won't execute automatically. Is there anyway to make it encode when I tell it to encode?

Also the avi produced by using this command from a terminal screen produces a file that won't open in ms windows. However I can use WinFF to convert the file to an MS avi and it produces a much smaller file that works with windows.

Is there a way to make this happen by just plugging in some information into the Gyachi?

Also, **_the new version does not have the icons showing_** for send file and share photos any more. Is this just a bug on my system or is anyone else seeing this too.

EDIT: I just did an install on Jaunty and it's missing the action icons too...

Thanks for any help.

P.S. - If the task can't be accomplished in Gyachi, I imagine a bash script could automate the process but I don't know how to write bash...

Some hand holding please...

---

### Post by loell on 2009-04-13
updated, the buttons should show up now.

---

### Post by crjackson on 2009-04-13
> **loell said:**
> updated, the buttons should show up now.

Thank you. Yes now the buttons show.

How about some more instruction on how to get the recorder function to work as stated above?

---

### Post by loell on 2009-04-13
I'm thinkng to whip up a pygtk script, to have your friend encode it on a simple UI, but i'm not so free at the momment. if this isn't that urgent, i could do it on the weekend.

in any case you could just copy paste that on a .sh file,  then set it to executable by say chmod +x **encoder.sh** , put it in a directory where you put the webcam still images, then execute the script.

also advise him/her to not open the directory with nautilus, because nautilus loves to preview, nautilus hangs when too many images are in one directory, that's just my observation.

---

### Post by crjackson on 2009-04-13
> **loell said:**
> I'm thinkng to whip up a pygtk script, to have your friend encode it on a simple UI, but i'm not so free at the momment. if this isn't that urgent, i could do it on the weekend.

in any case you could just copy paste that on a .sh file,  then set it to executable by say chmod +x **encoder.sh** , put it in a directory where you put the webcam still images, then execute the script.

also advise him/her to not open the directory with nautilus, because nautilus loves to preview, nautilus hangs when too many images are in one directory, that's just my observation.

Okay. a GUI would be awesome. He won't get his system shipped until after Jaunty is officially released and the machine tested for a few days. It can wait if you really want to do that.

I wonder why the function for Gyachi doesn't work. Is that a bug that could be reported somewhere, or am I misunderstanding the intention of that setting.

Also, is there a way for the encoder to produce an MS Compatible avi file? Otherwise it has to be converted for windows users (other family members) to view the resulting movie.

---

### Post by loell on 2009-04-14
> **crjackson said:**
>  Is that a bug that could be reported somewhere, or am I misunderstanding the intention of that setting.


yes, it's a feature not a bug, but my sentiments is with you, i too wish that it's more autotmated.  the developer conforms to the linux philosophy, which one tool to only do one thing and do it well.

---

### Post by crjackson on 2009-04-14
> **loell said:**
> yes, it's a feature not a bug, but my sentiments is with you, i too wish that it's more autotmated.  the developer conforms to the linux philosophy, which one tool to only do one thing and do it well.

I don't understand what the purpose of having a settings entry field for encoder > encoder command is for then. If they serve no purpose he should have left them out. That's what made me think it should actually do something.

---

### Post by loell on 2009-04-14
> **crjackson said:**
> I don't understand what the purpose of having a settings entry field for encoder > encoder command is for then. If they serve no purpose he should have left them out. That's what made me think it should actually do something.

ahh, yeah, let me lay the timeline on when it had that entry,

It was hoshy(Stefan Sikora) who made that, he's already inactive on the project, he was also responsible with the whole webcam recording thing,

i'll try to ask the current developer if he intends to remove that or not, since it just confuses users, as it doesn't do video encoding at all.

---

### Post by crjackson on 2009-04-14
> **loell said:**
> ahh, yeah, let me lay the timeline on when it had that entry,

It was hoshy(Stefan Sikora) who made that, he's already inactive on the project, he was also responsible with the whole webcam recording thing,

i'll try to ask the current developer if he intends to remove that or not, since it just confuses users, as it doesn't do video encoding at all.

I would like to see the recorder option stay. It's just the encoding dialogue that is confusing. I'm sure it would take much to complete. It only needs to invoke the mencoder and the custom commands. I think just making the launch (encode) button a working function would be easier than chopping out settings from the GUI.

---

### Post by lutosdemayo on 2009-04-16
Hi loell I've always followed your packages but my webcam stopped functioning with version 1.1.61 using Intrepid, now I have upgraded to Juanty hoping that my webcam would once again work but its still the same thing. I can use it with Cheeze Webcam Booth and i have been using it since version 1.1.0 up until now. I'm using a vmicro 305 webcam. Thanks.:(

---

### Post by loell on 2009-04-16
> **lutosdemayo said:**
> Hi loell I've always followed your packages but my webcam stopped functioning with version 1.1.61 using Intrepid, now I have upgraded to Juanty hoping that my webcam would once again work but its still the same thing. I can use it with Cheeze Webcam Booth and i have been using it since version 1.1.0 up until now. I'm using a vmicro 305 webcam. Thanks.:(

didn't it detect or work even if you switch v4l1 and v4l2 back and forth in the webcam settings?

---

### Post by c4pt on 2009-04-17
hello i have a strange problem...when i use the amd64 package for 1.1.59
i have a local webcam window to view my webcam but no voice in the rooms of course.

but when i use the i386 package i have voice in the rooms but i have no local view of my webcam??

is there a way to have the i386 package with voice in the rooms and also display my local video as in the amd64 package?

please let me know thank you

:(

---

### Post by loell on 2009-04-17
> **c4pt said:**
> hello i have a strange problem...when i use the amd64 package for 1.1.59
i have a local webcam window to view my webcam but no voice in the rooms of course.

but when i use the i386 package i have voice in the rooms but i have no local view of my webcam??

is there a way to have the i386 package with voice in the rooms and also display my local video as in the amd64 package?

please let me know thank you

:(


search for how to chroot a 32 bit application to a 64 bit machine if you want room voice for 64 bit.

could you explain more about local window webcam? is this the webcam preview?

---

### Post by c4pt on 2009-04-17
hey wow you got back to me fast...here is an image of the webcam preview local window


[http://img114.imageshack.us/img114/670/screenshotp.png](http://img114.imageshack.us/img114/670/screenshotp.png)

:D


--on the amd64 copy of gyachi i get a webcam preview on the i386 i dont get it so tell me what you think.

i mean it sucks to have voice in rooms but no webcam support even though the webcam works in amd64 so i know its not the cam

---

### Post by loell on 2009-04-18
this is in two machines, right?

a 64 and 32?  if so, does this have the same webcam?

---

### Post by c4pt on 2009-04-18
no one machine. i installed the amd64 package saw that voice in rooms doesnt work but webcam works so then installed the i386 package saw that webcam doesnt work but voice in rooms works

right now i am using the amd64 package until the i386 package is fixed with local webcam preview

:)

---

### Post by loell on 2009-04-18
really? thats strange. ;)

what's your machines architecture? is it i386 or x86_64?

these two packages could not be interchanged. it would yield an error for an incompatible architecture alone.

---

### Post by loell on 2009-04-18
> **crjackson said:**
> Okay. a GUI would be awesome. He won't get his system shipped until after Jaunty is officially released and the machine tested for a few days. It can wait if you really want to do that.

as promised.. :)

just a very simple & crude UI encoder.

requires:* mencoder* package.

---

### Post by c4pt on 2009-04-18
its amd64.

i did a dpkg -i --force-all for the i386 package.

the i386 package works fine for voice in rooms. but when i activate the webcam there is no local viewer


the amd64 package works except no voice in rooms. and the webcam local viewer works fine with it.

so.
:(

---

### Post by c4pt on 2009-04-18
loell btw this isnt related but what is the ram limit on ubuntu i386 server kernel?

---

### Post by crjackson on 2009-04-18
> **loell said:**
> as promised.. :)

just a very simple & crude UI encoder.

requires:* mencoder* package.

sweet! Downloading now... =D>

---

### Post by loell on 2009-04-19
> **c4pt said:**
> its amd64.

i did a dpkg -i --force-all for the i386 package.

the i386 package works fine for voice in rooms. but when i activate the webcam there is no local viewer


the amd64 package works except no voice in rooms. and the webcam local viewer works fine with it.

so.
:(


ah i see, you forced install it, yeah what you're seeing now could be the normal outcome.

if you really want both webcam and voice chat in your 64 bit machine then, you either have to chroot, or use getlibs to install the 32 bit package.

> ```
loell btw this isnt related but what is the ram limit on ubuntu i386 server kernel?
```

if i'm not mistaken, it's only 3 or 3.5 gig of ram.

---

### Post by c4pt on 2009-04-19
loell i am just going to reinstall to i386 i want adobe flash support also so thats pretty much why

iirc i386 server kernel support upto 64GB of ram with PAE support.

---

### Post by c4pt on 2009-04-19
loell what is the gyachi encoder for?

---

### Post by crjackson on 2009-04-19
loell - **_What's the proper way to use the encoder?_**

Do I place it in the same directory as the jpg's and just activate the script?

Running the script seems to start a cross-hair window select. When the script on on the deskto and I click it, it shows the cross-hair and from there if I click a window I get a py file on the desktop with a thumbnail of the window I selected.

---

### Post by loell on 2009-04-19
> **c4pt said:**
> loell what is the gyachi encoder for?

gyachi has a webcam recorder, but it only records in still images, so a specific is what it needs for those not so keen on entering commands in the command line.

---

### Post by loell on 2009-04-19
> **crjackson said:**
> loell - **_What's the proper way to use the encoder?_**

Do I place it in the same directory as the jpg's and just activate the script?

Running the script seems to start a cross-hair window select. When the script on on the deskto and I click it, it shows the cross-hair and from there if I click a window I get a py file on the desktop with a thumbnail of the window I selected.

oh my god, yeah, after downloading the script, it does the cross hair too, and worst! it takes screenshots too! a very wierd behaviour (still finding out how to make a proper installer)

anyway, you can relocate the script away from the Desktop, make a launcher, say a .desktop file (simply right click the desktop to make one) then point it to the script **ie** :  **python /home/..path_of_the_script/gyachi-encoder.py**

that should do it. it should now show a small window, see attached.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=110318&d=1240161570[/IMG]

---

### Post by crjackson on 2009-04-19
Progress is being made. I now get the GUI but when I tell it to actually encode I get the error in screen shot below. Navigating to the folder and running the mencoder command from the cli works however.

Edit: Okay, that was my error. I thought the GUI was asking where I wanted the AVI, it wanted to know where the folder with the jpg's are at.

EDIT: Okay, I got it working. It's picky about the name of the folder where the jpg's are placed. Yahoo Capture won't work, but Yahoo_Capture will.

loell - I know it's a lot to ask, but is there a way it could be modified to allow selection of a default flolder, then on encoding move the avi to the desktop and delete the jpg's?

I had a look at the code and couldn't figure it out.

---

### Post by loell on 2009-04-19
> **crjackson said:**
> 
loell - I know it's a lot to ask, but is there a way it could be modified to allow selection of a default flolder, then on encoding move the avi to the desktop and delete the jpg's?

I had a look at the code and couldn't figure it out.

yea, i'll try looking at it tonight.

---

### Post by crjackson on 2009-04-19
> **loell said:**
> yea, i'll try looking at it tonight.

Thanks loell - I wish I had your talent.

---

### Post by crjackson on 2009-04-20
Latest Gyachi updates broke webcam broadcasting here.

---

### Post by loell on 2009-04-20
> **crjackson said:**
> Latest Gyachi updates broke webcam broadcasting here.

does it hang? or it doesn't detect?

---

### Post by crjackson on 2009-04-20
> **loell said:**
> does it hang? or it doesn't detect?

It hangs. The webcam light comes on and then Gyachi freezes. Sometimes with a picture showing from the webcam display, sometimes no video at all.

---

### Post by loell on 2009-04-20
> **crjackson said:**
> It hangs. The webcam light comes on and then Gyachi freezes. Sometimes with a picture showing from the webcam display, sometimes no video at all.

i see, similar issues was also reported.

[https://sourceforge.net/forum/forum.php?thread_id=3225292&forum_id=533966]("https://sourceforge.net/forum/forum.php?thread_id=3225292&forum_id=533966")

---

### Post by crjackson on 2009-04-20
> **loell said:**
> i see, similar issues was also reported.

[https://sourceforge.net/forum/forum.php?thread_id=3225292&forum_id=533966]("https://sourceforge.net/forum/forum.php?thread_id=3225292&forum_id=533966")

Well I hope it gets fixed soon. That's the main reason for using Gyachi over pidgin for me.

---

### Post by loell on 2009-04-21
1.1.63 is still in the archive, so you can still downgrade to the previous one.

---

### Post by crjackson on 2009-04-21
> **loell said:**
> 1.1.63 is still in the archive, so you can still downgrade to the previous one.

I don't see the .63 build available for download. Can you point me to it?

---

### Post by loell on 2009-04-21
> **crjackson said:**
> I don't see the .63 build available for download. Can you point me to it?

yeah, you're right, i thought the repo won't auto-delete it, strange.. :(

anyway, I know Greg is swift in acting on reported bugs, it would likely be fix this weekend.



on other news, the script is done i think..

try the newly attached, 

notbale changes are

1. saved last chosen folder
2. custom frames per second ( 3 as the default) 
2. delete frames button 

still aiming to make a deb installer for general consumption. ;)


[ATTACH]110474[/ATTACH]

---

### Post by crjackson on 2009-04-21
> **loell said:**
> yeah, you're right, i thought the repo won't auto-delete it, strange.. :(

anyway, I know Greg is swift in acting on reported bugs, it would likely be fix this weekend.



on other news, the script is done i think..

try the newly attached, 

notbale changes are

1. saved last chosen folder
2. custom frames per second ( 3 as the default) 
2. delete frames button 

still aiming to make a deb installer for general consumption. ;)


[ATTACH]110474[/ATTACH]

Wouldn't launch from launcher or terminal. Produced the following output.
```
charles@emachines-m6809:~$ cd Yahoo_Capture
charles@emachines-m6809:~/Yahoo_Capture$ python gyachi-encoder.py 
gyachi-encoder.py:98: GtkWarning: Attempting to read the recently used resources file at `/home/charles/.recently-used.xbel', but the parser failed: Error reading file '/home/charles/.recently-used.xbel': Is a directory.
  self.dialog = gtk.FileChooserDialog(action=gtk.FILE_CHOOSER_ACTION_SELECT_FOLDER,buttons = (gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL, gtk.STOCK_OPEN, gtk.RESPONSE_ACCEPT))
---- file:///home/charles/Yahoo_Capture
Traceback (most recent call last):
  File "gyachi-encoder.py", line 176, in <module>
    enc = gyachi_encoder()
  File "gyachi-encoder.py", line 112, in __init__
    if  len( self.default_folder) == 0: 
TypeError: object of type 'NoneType' has no len()
charles@emachines-m6809:~/Yahoo_Capture$ 

```

---

### Post by loell on 2009-04-21
> **crjackson said:**
> Wouldn't launch from launcher or terminal. Produced the following output.
```
charles@emachines-m6809:~$ cd Yahoo_Capture
charles@emachines-m6809:~/Yahoo_Capture$ python gyachi-encoder.py 
gyachi-encoder.py:98: GtkWarning: Attempting to read the recently used resources file at `/home/charles/.recently-used.xbel', but the parser failed: Error reading file '/home/charles/.recently-used.xbel': Is a directory.
  self.dialog = gtk.FileChooserDialog(action=gtk.FILE_CHOOSER_ACTION_SELECT_FOLDER,buttons = (gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL, gtk.STOCK_OPEN, gtk.RESPONSE_ACCEPT))
---- file:///home/charles/Yahoo_Capture
Traceback (most recent call last):
  File "gyachi-encoder.py", line 176, in <module>
    enc = gyachi_encoder()
  File "gyachi-encoder.py", line 112, in __init__
    if  len( self.default_folder) == 0: 
TypeError: object of type 'NoneType' has no len()
charles@emachines-m6809:~/Yahoo_Capture$ 

```

ouch :(

anyhow do a 

```
gconftool-2 --set "/apps/gyachi-encoder/default-path" --type string ""
```
then reexecute the srcipt, i'll be fixing it, together with a deb package this weekend

---

### Post by crjackson on 2009-04-21
> **loell said:**
> ouch :(

anyhow do a 

```
gconftool-2 --set "/apps/gyachi-encoder/default-path" --type string ""
```
then reexecute the srcipt, i'll be fixing it, together with a deb package this weekend

Okay, I'll try that when I get off from work tonight.

---

### Post by DougieFresh4U on 2009-04-24
Running Jaunty mand latest Gyachi, I can't hear 'audibles like I have before. They worked a week ago and I had to re-install and now no hear. Any suggestions?
Thanks and thanks for the work you put into all.
Dougie :P

---

### Post by loell on 2009-04-24
> **DougieFresh4U said:**
> Running Jaunty mand latest Gyachi, I can't hear 'audibles like I have before. They worked a week ago and I had to re-install and now no hear. Any suggestions?
Thanks and thanks for the work you put into all.
Dougie :P

not sure yet, but the audible player is an external command, if i'm not mistaken, it might have been affected by pulsedaudio or something.

---

### Post by crjackson on 2009-04-25
> **loell said:**
> ouch :(

anyhow do a 

```
gconftool-2 --set "/apps/gyachi-encoder/default-path" --type string ""
```
then reexecute the srcipt, i'll be fixing it, together with a deb package this weekend

Using the command here, I was able to launch the encoder, but as you can see from the screen shot, something isn't just right.

---

### Post by crjackson on 2009-04-25
> **loell said:**
> not sure yet, but the audible player is an external command, if i'm not mistaken, it might have been affected by pulsedaudio or something.

It's working for me in Jaunty, as is the webcam now. The pulseaudio does need some tweaking ans the audibles cut off about the last 2 seconds of playback. This happened for me in Intrepid as well, but started working after some pulseaudio tweaking.

---

### Post by crjackson on 2009-04-25
A fresh install of Jaunty and Gyachi *.65 and web cams are working again.

Problem though - It no longer lets you access the setup menu for the webcam and clicking on the menu option crashes the applet. Clicking on the record button also crashes the video window. Both action close the window instantly.

If you have a quick line to the developer, please ring his bell...

Thanks.

---

### Post by loell on 2009-04-26
I couldn't seem to reproduce it.

you might want to reset the previous settings by removing capturerc and webcamrc.

---

### Post by enigmatic28 on 2009-04-26
Hi,

i have just recentky installed gyachi 1.1.59 (i was unable to locate the latest one)..

my question is how do you turn-off the automatic logging of the chat?
i don't want to stoce conversation on my laptop and can't seem to find how to dis able it.


thanks...

---

### Post by mihaicj on 2009-04-26
How did you manage to install Gyachi on Jaunty? Did you compile from source?

---

### Post by crjackson on 2009-04-26
> **loell said:**
> I couldn't seem to reproduce it.

you might want to reset the previous settings by removing capturerc and webcamrc.

I can't find anything called capturerc or webcamerc. How do I go about removing them for a reset?

---

### Post by crjackson on 2009-04-26
> **mihaicj said:**
> How did you manage to install Gyachi on Jaunty? Did you compile from source?

Look at loell's signature line and install his ppa repository. You will be upgraded.

---

### Post by crjackson on 2009-04-26
loell - I got the encoder to encode. It seems that when you browse for the directory, you can't just highlight it and and assume it's selected. You have to double-click and actually go inside of the folder before clicking open.

I can't get it to delete the completed frames though. I looked at the code but I'm afraid to make modifications to test with. I think it's having trouble finding the frames because of their names. 
since I cant record with GYachiE at this time, I was using some random jpgs. I think that because the GYachiE naming convention isn't being used it's having trouble deleting.

I noticed your rm statement in the py file is along the lines of
```
*-*-*-*-*-*.jpg
```

What would happen if that were just *.jpg ?

Also, how could this code ```
mf://*.jpg -o gyachi-webcam.avi'
``` be modified to place the avi file on the desktop instead of the capture folder?

---

### Post by crjackson on 2009-04-26
> **loell said:**
> I couldn't seem to reproduce it.

you might want to reset the previous settings by removing capturerc and webcamrc.

loell - those files aren't located on my system anywhere...

---

### Post by crjackson on 2009-04-26
> **loell said:**
> I couldn't seem to reproduce it.

you might want to reset the previous settings by removing capturerc and webcamrc.

I purged gyachi and searched my drive for any leftovers. I deleted and reinstalled everything.

Still, as soon as I click the record button the applet closes. I still cant find any trace of capturerc or webcamrc on my system.

Any suggestions?

---

### Post by tqft on 2009-04-26
"I still cant find any trace of capturerc or webcamrc on my system."


[email]XXX@XXXX:~/.yahoor[/email]c/gyach$ ls
backups  capturc   emoticons  history  ignore.regex  webcamrc
bimages  commands  gyachrc    ignore   log           yavatars

Notice the .  in front of .yahoorc

If using Nautilus you need to tick View Show Hidden Files

---

### Post by crjackson on 2009-04-26
> **tqft said:**
> "I still cant find any trace of capturerc or webcamrc on my system."


[email]XXX@XXXX:~/.yahoor[/email]c/gyach$ ls
backups  capturc   emoticons  history  ignore.regex  webcamrc
bimages  commands  gyachrc    ignore   log           yavatars

Notice the .  in front of .yahoorc

If using Nautilus you need to tick View Show Hidden Files

Looked there already. They just aren't there... :confused:

---

### Post by loell on 2009-04-26
strange, 

how about recreating the files?

---

### Post by crjackson on 2009-04-26
> **loell said:**
> strange, 

how about recreating the files?
Just an empty text file with those names?

---

### Post by loell on 2009-04-26
yep.

---

### Post by crjackson on 2009-04-26
> **loell said:**
> yep.

Okay, did that. No difference.

---

### Post by loell on 2009-04-26
> **crjackson said:**
> Okay, did that. No difference.

what other rc files have you got in there?

```
ls .yahoorc/gyach/
```

---

### Post by crjackson on 2009-04-26
That's it...

---

### Post by x58 on 2009-04-27
I have Linux 8.10 and 2 month ago with your help. Loell I install everything and it works or let say it's satisfied me fully.So, anywhere I have little question: Situation is next: I sleeping on night time , but I leaving computer and Gyachi on, because I have many friends living in different time zone, so my problem is: If somebody coming to Gyachi, then there pop up try Icon and if I sleep, I cannot to know if there is somebody. Question: Is there any ways to turn on voice signal like beep or something to listing if there coming somebody to Gyachi? Thanks

---

### Post by loell on 2009-04-27
> **x58 said:**
> I have Linux 8.10 and 2 month ago with your help. Loell I install everything and it works or let say it's satisfied me fully.So, anywhere I have little question: Situation is next: I sleeping on night time , but I leaving computer and Gyachi on, because I have many friends living in different time zone, so my problem is: If somebody coming to Gyachi, then there pop up try Icon and if I sleep, I cannot to know if there is somebody. Question: Is there any ways to turn on voice signal like beep or something to listing if there coming somebody to Gyachi? Thanks

In setup -> message and personal -> enable PM sound events.

then adjust your sound volume.

---

### Post by x58 on 2009-04-27
I have enabled it, but not any sound. Maybe I need to to install Gyachi-codec deb? Right now I don't have any sound in Gyachi. Thanks

---

### Post by ashmew2 on 2009-04-27
loell , Thanks for the great pointers on getting Gyachi up and running!
Great job man! Keep up the good work :guitar:

---

### Post by xx58 on 2009-04-27
:) I don't have codecks too. Do I need? I don't have in Gyachi any sound too. I able sound at Gyachi setup, but no any sond. I have Gyachi gyachi_1.1.59-1~intrepid1_i386.deb. Maybe I need different one? I have Linux 8.10. Anybody knows and can help me?

---

### Post by loell on 2009-04-27
you won't be needing the codec, its only for room voice chat.

try to set your sound device in **setup --> Options --> sound device** choose pulse audio.

see if there is sound, when your recieve an IM.

---

### Post by xx58 on 2009-04-27
Yes now I have very very small volume sound. Thanks, but how I can turn sound volume up?

---

### Post by crjackson on 2009-04-27
> **loell said:**
> strange, 

how about recreating the files?

I placed the files in both the main folder and the sub folder but it make no difference.

I installed on 2 different machines with Jaunty and got the same result even with no webcam attached. Just clicking on the record button causes GYachi to close the viewer window and then become unresponsive. This happens on all three machines I've tested.

Where does one go to file a bug report on this application?

---

### Post by xx58 on 2009-04-27
Everything works now OK.Thanks

---

### Post by loell on 2009-04-27
> **crjackson said:**
> 
Where does one go to file a bug report on this application?

in [http://gyachi.sourceforge.net]("http://gyachi.sourceforge.net")


at the forums open discussion.

---

### Post by crjackson on 2009-04-27
> **loell said:**
> in [http://gyachi.sourceforge.net]("http://gyachi.sourceforge.net")


at the forums open discussion.

Thanks, I posted to that forum.

---

### Post by stalkingwolf on 2009-04-28
What do i need to do to be able to send an SMS message?  to send an Im from Gyachi to a cell phone.

---

### Post by utakbiya on 2009-04-28
Hi loell thank you for this useful and informative post...I was looking for this kind of application...at last I've found it. Salamat kabayan!

---

### Post by crjackson on 2009-04-28
> **loell said:**
> in [http://gyachi.sourceforge.net]("http://gyachi.sourceforge.net")


at the forums open discussion.

Thanks again loell - Greg has identified the bug and will squish it in the .66 release very soon.

---

### Post by loell on 2009-04-28
@utakbiya : glad you find it useful. :)



@crjackson : oh, so it's really a bug. I'm glad it's not just something to do with the deb package I built.

I commend you for describing it so well, maybe this is a start of regular or occasional bug reporting? the project needs more first hand feedback. :D

---

### Post by crjackson on 2009-04-28
> **loell said:**
> @utakbiya : glad you find it useful. :)



@crjackson : oh, so it's really a bug. I'm glad it's not just something to do with the deb package I built.

I commend you for describing it so well, maybe this is a start of regular or occasional bug reporting? the project needs more first hand feedback. :D

Yeah, seems it was a bug. I'm happy to help out with the bug reporting when I find one. I'm not personally big on instant messengers but I have an elderly friend who is. And now that I have built him a computer powered by ubuntu I have become his tech. support guy (qualified or not). That said, since he is big into Yahoo chat / Webcam... Well you can see where this is going.

I'm always glad to fiddle around and report bugs... :)

---

### Post by crjackson on 2009-04-29
.66 version is out.

I tried to compile form source but I really don't know what I'm doing. I'll have to wait until you get a chance to put a deb in the repository before I can test it out.

---

### Post by loell on 2009-04-29
currently building..

---

### Post by crjackson on 2009-04-30
New build works perfectly. Camera works perfectly. Record works perfectly. Gyachi-encoder works perfectly.

New bug regarding smiley's but it's been fixed already. I suspect you'll be building again soon...

EDIT: I see you have .67 queued for building. I'll be testing it tomorrow.

---

### Post by mocha on 2009-05-02
I just found this app by mistake.  It's very nice!  I was just wondering though what folks use Yahoo chat for.  It's still just all spam bots in the channels I tried.  It's always been like this for many years.  Also I was wondering how do you do the voice chat?  When I open the voice chat box the rooms are always empty.

---

### Post by loell on 2009-05-02
> **mocha said:**
>  I was just wondering though what folks use Yahoo chat for.  It's still just all spam bots in the channels I tried.  It's always been like this for many years.  

True , I guess this is just for those who still prefers Yahoo IM services. Actually, many users are not really fond of yahoo public rooms. they just want to communicate with friends and family.



> **mocha said:**
> 
Also I was wondering how do you do the voice chat?  When I open the voice chat box the rooms are always empty. 

you have to enter a room before you can talk or listen.

---

### Post by crjackson on 2009-05-02
GyachI - V1.1.68 (New)
By: Greg Hosler (ghoslerProject Admin) - 2009-05-01 09:13
2009-05-01 (V1-1-68) Move list of voice-server IP's to external file. 
* - Moved hard coded list of voice servers to 
* GYACH_CFG_DIR (~/.yahoorc/gyach/voice_servers 
* and if not found, then the master list in 
* PACKAGE_DATA_DIR ({prefix}/share/gyachi/voice_servers 
* - Additionally, the last selected voice server is 
* saved across runs in a gyvoicerc file.

---

### Post by loell on 2009-05-02
uploading..

---

### Post by mafaldaspeaks on 2009-05-03
How about sending sms from within yahoo? Would you know how i can activate that? I'm using jaunty jackalope.

---

### Post by loell on 2009-05-03
someone ask the same question yesterday through PM

so i'll quote myself

> none so far, as well as login to mobile, both aren't implemented yet. but you could make a request to the developer if you really like a feature like that.

meanwhile you can use yahoo's sms feature by using yahoo mail ajaxified version? not the yahoo mail classic, you can easily switch back and forth with that interface. from there login to yahoo web messenger again from that yahoo mail ajaxified version, then you can use yahoo sms service.

still you can file a request for this feature via the open discussion at [http://gyachi.sourceforge.net](http://gyachi.sourceforge.net)

---

### Post by m_2009 on 2009-05-06
Just wondering if anyone else has been experiencing the issues I am having with gyachi...

1. If i get notification saying i have an email, clicking the email button on the toolbar doesn't do anything, doesnt load my web browser or anything (I have set firefox in the options to be the browser), and the same happens when right clicking the system tray icon and clicking "Email messages"

2. I dont get any sound notifications when someone signs on, or sends me a message etc. My sound works everywhere else in ubuntu and i get sounds in aMSN when i receive a message, but not in gyachi. Anyone know how to fix this?

1 other question I have, what does changing the "theme" actually do? i have changed it to YMlike, gyachi-default, and pidgin etc.. but nothing seems to change anywhere? not even the buddy icons..

Hope someone can possibly help me with the 2 main issues mentioned avbove, thank you.

By the way I am rnning gyachi 1.1.70 jaunty

---

### Post by loell on 2009-05-06
1. gyachi needs embeded browser capability to browse to yahoo web mail, it used to work before by sending the email links to firefox but yahoo webmail URI  has changed 2 years ago. this feature is now disfunctional and needs changing.

2. you have to select the sound device in Setup --> Options --> sound device


Other question: you needed to restart gyachi to see the theme change.

---

### Post by m_2009 on 2009-05-06
THank you for the reply loell.
So Im guessing the only way to view my emails is actually to load up my firefox manually and log into the yahoo website?
 
In regards to the sound, i tried changing the sound device from ALSA to Pulse, and I get no sound output frmo either. I did look around the files and noticed the gyachi sound files have the file extension "RAW". Could it be that a codec is needed for these?
 
I already have the ubuntu-restricted-extras package installed, but just dont seem to be able to get any sound outpu when a buddy signs in or messages me. Would there be anything else I could check or try to make this work?
 
 
I tried changing the theme and then restarting gyachi, and it still doesnt seem to change anything? Which things shoul change if i select a different theme? From looking at the files in the themes folder it seems as though it changes the icons on the buddy list? Mine are always the yellow faces just like in the windows version of yahoo, is this what the theme changes, or does it change the smilies within a chat?

---

### Post by m_2009 on 2009-05-06
UPDATE:

I have now managed to get the sounds working, it seems that by default the "Enable sound events" box is unchecked by default, an I only just noticed there was even this option, checked the box, and sounds now working perfectly. Also themes seem to be working now after a restart.
Is there lso a way to make the interface smaller, so that it only shows my budy list, and not the other tabs, kind of like how yahoo messenger in windows looks?

Also for using gyachi in ubuntu, what do i need to have as the "flashplayer" command and "MP3 player command"

---

### Post by loell on 2009-05-06
2. I'll check if the sound is the latest bug of the latest version.

3. themes are just icon themes not gtk themes, you may see different icons whe you switch and restart.

---

### Post by loell on 2009-05-06
> **m_2009 said:**
> UPDATE:

Is there lso a way to make the interface smaller, so that it only shows my budy list, and not the other tabs, kind of like how yahoo messenger in windows looks? 


not really, but you can resize it though, also drag the buddy tab to the first tab if you like. and in setup-->options--> remember UI tab settings

> **m_2009 said:**
> 
Also for using gyachi in ubuntu, what do i need to have as the "flashplayer" command and "MP3 player command"

the flash player is of no use actually it's a legacy code , the mp3 player is only use for playing audible sounds, in which mplayer is the default setting. install mplayer if you like hearing it.

if you have UI features requests, let the developer know at gyachi.sourceforge.net

---

### Post by m_2009 on 2009-05-06
Thank you.

I dont think the sound is a bug, it was just I never noticed there is a checkbox to turn the sound events on/off, and by default it is deselected.

When you say audiables for the MP3, what kind of audiables would they be?

And if so, could i set anything that comes with ubuntu standard to do this. for example Totem?

---

### Post by m_2009 on 2009-05-07
Another thing Im not sure of.

How can i create/delete groups in the Buddy list.

I know in the windows one you can simply click Create New group, and then type the name for it, and drag friends etc.. But i dont seem to be able to find an option to create a new group in gyachi, can anyone point me as to if this can be done, and if so, how?

---

### Post by adroitster on 2009-05-07
Hello
I have installed gyachi using the deb provided on the first page on my jaunty 64 bit and its up and running !!

But there is very weird problem of logging in using my account . It says the password is incorrect while I login using the same password on pidgin and my account on browser:confused:

Also this problem is only with my account !! that is the other accounts can be logged in without any problem:confused::(

---

### Post by loell on 2009-05-09
> **m_2009 said:**
> 
How can i create/delete groups in the Buddy list.

when you add a new buddy you will have the option to create a new group.

---

### Post by loell on 2009-05-09
> **adroitster said:**
> 
But there is very weird problem of logging in using my account . It says the password is incorrect while I login using the same password on pidgin and my account on browser:confused:
(

try to delete .yahoorc/ then log in with the same account.

---

### Post by adroitster on 2009-05-09
Thank you loell for your quick reply but the thing is its still not working the way it should. It lets me login from other accounts but not the one which I want!! while the same account I cn login from the web browser without any prolems. My account @yahoo.co.in and not @yahoo.com , can that be a problem? because my other account (which i can login is @yahoo.com):confused:

---

### Post by DougieFresh4U on 2009-05-09
Using the latest .deb, my audibles play 1/2 to 3/4  of the way and quit.  And that is only for the first audible I play as it won't play a second audible at all. Have to restart 'gyachi' to only the same result again.
I do have mplayer installed. Should I maybe install that latest 'smplayer' from tutorial in Jaunty?

---

### Post by loell on 2009-05-09
> **adroitster said:**
> Thank you loell for your quick reply but the thing is its still not working the way it should. It lets me login from other accounts but not the one which I want!! while the same account I cn login from the web browser without any prolems. My account @yahoo.co.in and not @yahoo.com , can that be a problem? because my other account (which i can login is @yahoo.com):confused:

probably, have you tried logging in with @yahoo.co.in?

---

### Post by loell on 2009-05-09
> **DougieFresh4U said:**
> Using the latest .deb, my audibles play 1/2 to 3/4  of the way and quit.  And that is only for the first audible I play as it won't play a second audible at all. Have to restart 'gyachi' to only the same result again.
I do have mplayer installed. Should I maybe install that latest 'smplayer' from tutorial in Jaunty?

indeed, it's weird.

---

### Post by adroitster on 2009-05-09
> **loell said:**
> probably, have you tried logging in with @yahoo.co.in?
But how do I login by using @yahoo.co.in since the gyache Improved login window asks only for the user name and not the whole email ID. I have my account setup on pidgin is it possible that some king of security detects the use of the same password on my computer and blocks gyache while it allows me to login the account which is not setup on pidgin (I know it might sound lame but now have no option other thinking of all weird reasons for that weird phenomenon !! )

---

### Post by loell on 2009-05-09
> **adroitster said:**
> But how do I login by using @yahoo.co.in since the gyache Improved login window asks only for the user name and not the whole email ID. I have my account setup on pidgin is it possible that some king of security detects the use of the same password on my computer and blocks gyache while it allows me to login the account which is not setup on pidgin (I know it might sound lame but now have no option other thinking of all weird reasons for that weird phenomenon !! )

simply put @yahoo.co.in? that's how ymail and rocketmail account works.

---

### Post by adroitster on 2009-05-09
> **loell said:**
> simply put @yahoo.co.in? that's how ymail and rocketmail account works.
Loell I have already tried that and again the same error of password or user id incorrect . This time I really pressed each key reading out loudly !!! (I am sure that my password and ID are correct since I have tried them on all different messengers)

---

### Post by loell on 2009-05-09
then it's a bug most probably.

---

### Post by adroitster on 2009-05-09
It is sad that the bug is only for my primary account .....this is the last piece of software I am trying to configure after a clean install of jaunty on my computer(earlier is used pidgin on my intrepid). :(
I just now upgraded to gyachi_1.1.70 from your ppa but all in vain 

somebody who has a workaround please tell me!! I am using @yahoo.co.in as my ID which doesn't works while my @yahoo.com works flawlessly!!! Other having working gyachi please tell me if there is a solution!!

---

### Post by loell on 2009-05-09
do you by any chance using  indian characters? maybe it's the root of the bug?

---

### Post by adroitster on 2009-05-09
> **loell said:**
> do you by any chance using  indian characters? maybe it's the root of the bug?
Ahh I don't know what do you exactly mean by indian characters ? But I use a US(EN) keyboard ! (But after logging in I do use indian audible and stuff but that is after logging in)

Loell you seem to be pretty helping in this matter , If you have any contacts gyachi developers or you are among those please help me with the workaround or tell me what has to be done (It is a great piece of software that will help to keep me from booting my virtual machine just for ymssngr)

---

### Post by loell on 2009-05-09
it's much faster and more reliable if  you could file a bug report yourself at gyachi.sourceforge.net at the open discussion forum.

---

### Post by m_2009 on 2009-05-09
Just in case anyone finds this useful, I have created a package with the latest sound events taken from Yahoo Messenger 9, these include the sounds for buddy online, budy offline, received message, buzz and email alert.

Just copy the RAW files from this archive into the /usr/share/gyachi/sounds folder (You will need t do this as root)

---

### Post by adroitster on 2009-05-09
> **loell said:**
> it's much faster and more reliable if  you could file a bug report yourself at gyachi.sourceforge.net at the open discussion forum.

Ok loell I will do that .

---

### Post by gatoguts on 2009-05-10
I downloaded Gyache using the link below.  How do i completely remove it?

[https://launchpad.net/%7Eloell/+arch...ntu11_i386.deb](https://launchpad.net/%7Eloell/+arch...ntu11_i386.deb)

---

### Post by m_2009 on 2009-05-10
Goto SYSTEM > ADMINISTRATION > SYNAPTICS PACKAGE MANAGER
 
It should be listed under Installed (Local or obselete), you can remove it from there.

---

### Post by loell on 2009-05-10
> **m_2009 said:**
> Just in case anyone finds this useful, I have created a package with the latest sound events taken from Yahoo Messenger 9, these include the sounds for buddy online, budy offline, received message, buzz and email alert.

Just copy the RAW files from this archive into the /usr/share/gyachi/sounds folder (You will need t do this as root)

ah nice, I haven't tried this. :)

---

### Post by gatoguts on 2009-05-10
> **m_2009 said:**
> Goto SYSTEM > ADMINISTRATION > SYNAPTICS PACKAGE MANAGER
 
It should be listed under Installed (Local or obselete), you can remove it from there.

unfortunately, it is not under there...anyway what i really want to do is reinstall Gyachi by first adding the necessary repositories and PPA keys.  That link from Loell uses GDebi.  Even after importing the PPA key i am still getting can not be authenticated messages in synaptic when trying to install Gyachi.

---

### Post by crjackson on 2009-05-10
> **gatoguts said:**
> unfortunately, it is not under there...anyway what i really want to do is reinstall Gyachi by first adding the necessary repositories and PPA keys.  That link from Loell uses GDebi.  Even after importing the PPA key i am still getting can not be authenticated messages in synaptic when trying to install Gyachi.

Add this software source:
```


deb http://ppa.launchpad.net/loell/ppa/ubuntu jaunty main

```

import the attached text file to your authentication tab settings.

---

### Post by gatoguts on 2009-05-11
> **crjackson said:**
> Add this software source:
```


deb http://ppa.launchpad.net/loell/ppa/ubuntu jaunty main

```

import the attached text file to your authentication tab settings.

thanks do i need to add 
deb-src [http://ppa.launchpad.net/loell/ppa/ubuntu](http://ppa.launchpad.net/loell/ppa/ubuntu) jaunty main   ?

---

### Post by crjackson on 2009-05-11
> **gatoguts said:**
> thanks do i need to add 
deb-src [http://ppa.launchpad.net/loell/ppa/ubuntu](http://ppa.launchpad.net/loell/ppa/ubuntu) jaunty main   ?

It's the repository for the source files. I don't use any of them.

---

### Post by m_2009 on 2009-05-11
I have gyachi set to use seperate windwos for each PM chat.

Is it possible to hide/remove the tab that shows at teh top of each other these PM windows, as all the tab actually says is the name of the contact I am talking to, and being as I have the options set to open new window for each PM chat then the tab displaying isnt really needed. Can it be disabled?

---

### Post by loell on 2009-05-11
> **m_2009 said:**
> I have gyachi set to use seperate windwos for each PM chat.

Is it possible to hide/remove the tab that shows at teh top of each other these PM windows, as all the tab actually says is the name of the contact I am talking to, and being as I have the options set to open new window for each PM chat then the tab displaying isnt really needed. Can it be disabled?

yeah, i was wondering about that too, but i think you can't disable it, unless someone request it to the developer.

personally though i have always use tabbed conversations.

---

### Post by m_2009 on 2009-05-11
So who actualyl builds gyachi, or makes changes?

Do you make changes for ubuntu for it, or just add new versions to your PPA?

By the way did you say that the "flashplayer" command actualyl does anything? If so then what does it need to be set to in ubuntu.

---

### Post by loell on 2009-05-11
> **m_2009 said:**
> So who actualyl builds gyachi,

there are quite a few who build specific packages for their distributions, i for one builds ubuntu deb packages

> **m_2009 said:**
> 
 or makes changes? 

[the developer]("https://sourceforge.net/users/ghosler/")

 > **m_2009 said:**
>  or just add new versions to your PPA?

yes

> **m_2009 said:**
> 
By the way did you say that the "flashplayer" command actualyl does anything? If so then what does it need to be set to in ubuntu.

it's an old code from the gyach enhance days, i doubt the current developer nor the developer before him is familiar with that function, but i think it used to view avatars but that's it, which was useless other than that it needs to be removed.

---

### Post by m_2009 on 2009-05-11
SO if i did want to view the flash avatars which some people use.. what woudl the correct flashplayer command need to be for ubuntu?

---

### Post by ani_drexel on 2009-05-12
Im a new Kubuntu user and can i get STEP BY STEP details on how to run yahoo messenger with VC please..ive been using piding..but dont get Voice chat on conferences and rooms...anyone can please guide me STEP BY STEP procedure to get yahoo with voice somehow on kubuntu? I would reallly appreciate it...thanks again

---

### Post by loell on 2009-05-12
if you're in kubuntu just install gyachi 32 bit, and install the codecs from medibuntu repository, and you're good to go :)

---

### Post by ani_drexel on 2009-05-12
where do i get the installation file for gyachi 32bit? sorry im being too much of a spoon feeding thing lol but yeah..any links for that? thanks for ur quick reply!

---

### Post by loell on 2009-05-12
the deb packages are mostly found in the first post. :)

if you're in jaunty youjust install this deb package

[https://launchpad.net/~loell/+archive/ppa/+files/gyachi_1.1.70-1~jaunty_i386.deb](https://launchpad.net/~loell/+archive/ppa/+files/gyachi_1.1.70-1~jaunty_i386.deb)

---

### Post by loell on 2009-05-12
feature teaser for the next release.. buddy images :)

[ATTACH]113564[/ATTACH]

---

### Post by m_2009 on 2009-05-16
Hi loell.

I hav ejust installed the latest version of gyachi from your repositories (1.1.71~jaunty), however when i run gyachi the title bar still shows it as being version 1.1.70, and this is also the same in help, about....

Is this what it should be displaying?

---

### Post by loell on 2009-05-16
> **m_2009 said:**
> Hi loell.

I hav ejust installed the latest version of gyachi from your repositories (1.1.71~jaunty), however when i run gyachi the title bar still shows it as being version 1.1.70, and this is also the same in help, about....

Is this what it should be displaying?

Yes.. my mistake, it's a patched 1.1.70, the changes is set for 1.1.71 :D

this is actually the first time i did it like this, the developer will crucify me, if he knows this.. ;)

---

### Post by m_2009 on 2009-05-16
Ive also noticed in this version that whenever i sign in, all groups on the contact list arent expanded, in the previous version they were.

If i manually expand all groups, or even set the "expand all groups" option, if i sign out and then back in again, they arent expanded... Is this a bug?

Will the email button in the toolbar ever be fixed to allow it to open up the default web browser and sign into yahoo mail?
Also when will a version be released that actually displays as version 1.1.71??

---

### Post by Sef on 2009-05-16
> Add this software source:
 	Code:
 	deb [http://ppa.launchpad.net/loell/ppa/ubuntu](http://ppa.launchpad.net/loell/ppa/ubuntu) jaunty main 
import the attached text file to your authentication tab settings. 		                   		 		 			  			  			  			  			 				 					Attached Files 					 					 	[IMG]http://ubuntuforums.org/images/attach/txt.gif[/IMG] 	[gyachi-Key.txt]("http://ubuntuforums.org/attachment.php?attachmentid=113256&d=1242002442") (598 Bytes, 5 views)

For the gyachi-Key.text, click download to save it to your desktop.  If you click save as, it will not work.

---

### Post by loell on 2009-05-17
> **m_2009 said:**
> Ive also noticed in this version that whenever i sign in, all groups on the contact list arent expanded, in the previous version they were.

If i manually expand all groups, or even set the "expand all groups" option, if i sign out and then back in again, they arent expanded... Is this a bug?


yep, i've had this behavior too, the thing is, it seems inconsistent and we couldn't nail the reall issue yet.

what i did was delete my previous settings ie **rm -rf .yahoorc** or better yet if you havent deleted your settings, post your output with this command

**grep -A 4 show_offline_buddies ~/.yahoorc/gyach/gyachrc**
> **m_2009 said:**
> 
Will the email button in the toolbar ever be fixed to allow it to open up the default web browser and sign into yahoo mail? 

I still don't know, personally, I'm having a different agenda on that feature, in any case you can revive that feature by requesting at gyachi forum. 

> **m_2009 said:**
> 
Also when will a version be released that actually displays as version 1.1.71??

most probably in a little later, 1.1.71 was just officially released.

---

### Post by m_2009 on 2009-05-17
Here is the output of running the grep command.

```
show_offline_buddies = 0
show_offline_in_online = 0
dont_show_offline_buddies = 1
show_empty_groups = 0
expand_all_groups = 1
expand_only_online_groups = 0
expand_no_groups = 0
```

Does this show why this could be happening?

---

### Post by m_2009 on 2009-05-17
also just deleted the ~/.yahoorc folder, and problem still exists.

---

### Post by loell on 2009-05-17
I've forwarded the output to the developer.

---

### Post by m_2009 on 2009-05-18
Another feature that would be nice is pressing the esc kep closing the current PM window, is that possible?

---

### Post by Fire768 on 2009-05-19
hi,
Except yahoo messenger .,what other messenger that can be use.,?





_________________
[IP PBX](http://www.inin.com/ProductSolutions/Pages/Enterprise-Interaction-Center.aspx)

---

### Post by _sluimers_ on 2009-05-19
> **Fire768 said:**
> hi,
Except yahoo messenger .,what other messenger that can be use.,?


None, just yahoo messenger.

---

### Post by I_ated_it on 2009-05-20
I apologize if this has already been answered but I have installed Gyachi using the deb package posted on the first page and it appears as if everything installed properly but when I click to launch Gyachi it just kind of locks up and doesnt load.  Any idea what is happening here?

---

### Post by Sef on 2009-05-23
What version of Ubuntu are you using?

---

### Post by I_ated_it on 2009-05-23
Kubuntu 9.04

---

### Post by loell on 2009-05-24
can you possibly execute it in the terminal? see if there's any output in there?

also, try removing/reinstalling gyachi and delete your settings **./yahoorc**

---

### Post by codewalkz on 2009-05-24
Is there someone over here who ever used skype?

---

### Post by I_ated_it on 2009-05-24
> **loell said:**
> can you possibly execute it in the terminal? see if there's any output in there?

also, try removing/reinstalling gyachi and delete your settings **./yahoorc**

Ok, I ran in terminal and got this:

gyachi: error while loading shared libraries: libgailutil.so.18: cannot open shared object file: No such file or directory

---

### Post by loell on 2009-05-24
that is just strange, **libgail** should be auto - downloaded during installation. anyhow,  install libgail18 **sudo apt-get install libgail18** then try to run it again.

---

### Post by I_ated_it on 2009-05-24
awesome that worked...thanks a lot

---

### Post by colau on 2009-05-24
Thanks loell for gyachi.
How to make the offline buddies not appeared in the buddies tab?

---

### Post by loell on 2009-05-24
> **colau said:**
> thanks loell for gyachi.
How to make the offline buddies not appeared in the buddies tab?

[attach]115025[/attach]

---

### Post by colau on 2009-05-24
> **loell said:**
> [attach]115025[/attach]
Thanks.
I don't see two hotmail buddies in pidgin as visible but here in gyachi they are online to me.
That's interesting.

---

### Post by crjackson on 2009-05-24
Do rooms work? Have a look at the attached picture. I get this error from every machine in the house when I try to join a room from the list.

What's the cure?

Thanks

---

### Post by tqft on 2009-05-24
> **crjackson said:**
> Do rooms work? Have a look at the attached picture. I get this error from every machine in the house when I try to join a room from the list.

What's the cure?

Thanks

Rooms work

Just try again

Check to make sure nothing else is pigging your bandwidth

---

### Post by SEdward on 2009-05-25
Good day
I installed gyachi on my 32bit X86 - ubuntu hardy linux
I have all the features enabled except the voice chat ((neither for room nor for buddies))
I have the voice window open with the 3 buttons on/off/mute
BUT I HAVE THE TALK KEY DIMMED AND DISABLED
Can anyone help me here?
I am stuck in this dilemma
Thanks

---

### Post by Sef on 2009-05-27
Under Setup > Options > check that Sound_Device is listed.  Mine is listed as Alsa_plugin

---

### Post by xeddog on 2009-05-29
If anyone is interested, I just upgraded my test system which was running Jaunty to Karmic Alpha 1 and Gyachi 1.1.65 seemed to be working ok.  I then upgraded to 1.1.71 and it still works.  This was using the jaunty link from the first page.

xeddog

---

### Post by Short__Error on 2009-05-29
](*,)Well i am not sure if this has been tlked about but i have not found any thing on it. 
I am using Ubuntu 9.04 i installed the gyachi_1.1.71-1~jaunty1_i386.deb, ok so now that you know what i am running this is the problem. I can logon get all the way to the captcha code type it in and hit ok and then Gyachi just goes poof truns off. What would cause this and how can i fix it.](*,)

---

### Post by crjackson on 2009-05-29
> **xeddog said:**
> If anyone is interested, I just upgraded my test system which was running Jaunty to Karmic Alpha 1 and Gyachi 1.1.65 seemed to be working ok.  I then upgraded to 1.1.71 and it still works.  This was using the jaunty link from the first page.

xeddog

Thanks for the information...

---

### Post by loell on 2009-05-29
> **Short__Error said:**
> ](*,)Well i am not sure if this has been tlked about but i have not found any thing on it. 
I am using Ubuntu 9.04 i installed the gyachi_1.1.71-1~jaunty1_i386.deb, ok so now that you know what i am running this is the problem. I can logon get all the way to the captcha code type it in and hit ok and then Gyachi just goes poof truns off. What would cause this and how can i fix it.](*,)

check the **no chatroom** checkbox during log on, on the login window , if it quits unexpectedly, try running it on terminal and give us the output or error.

---

### Post by Short__Error on 2009-06-01
Well i think you, but i found out what the problem was it will just not let me in one of the rooms i always go in. This room country:4 idk why it is doing this at all. the next problem i am havein is with my mic it is not reading the mic for some reason. :(

---

### Post by sagesparrow on 2009-06-03
I think I have a similar problem as Short_Error.  I'm running Jaunty and recently upgraded to Gyachi 1.1.71.1.  Gyachi was working up to a few days ago, even after upgrading.  But now it won't start up.  There is a flash of a start up window, then gone.  

Here's the error message when starting from terminal:

The program 'gyachi' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 943 error_code 160 request_code 149 minor_code 8 )
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

When compiling manually I get the following error message from ./configure:

configure: error: cannot run /bin/sh ./config.sub

What's the next move?

---

### Post by Gnomester on 2009-06-09
Just how big is the package to install Gyachi? I am running short of bandwith use in my Midday to Midnight allocation but I just might have enough after Midnight bandwidth to try the install. 

My 2gig by 2gig a month usage has gone to trying a couple of Linux packages. The addition of Jaunty with a few essentials has pushed the limit of my account:(

---

### Post by NT4usB on 2009-06-09
> **Gnomester said:**
> Just how big is the package to install Gyachi? I am running short of bandwith use in my Midday to Midnight allocation but I just might have enough after Midnight bandwidth to try the install. 

My 2gig by 2gig a month usage has gone to trying a couple of Linux packages. The addition of Jaunty with a few essentials has pushed the limit of my account:(

[https://launchpad.net/~loell/+archive/ppa/+sourcepub/632604/+listing-archive-extra](https://launchpad.net/~loell/+archive/ppa/+sourcepub/632604/+listing-archive-extra)

---

### Post by JDorfler on 2009-06-09
Thanks for the how to.  I just added it to my repository list.  So far so good.

---

### Post by Short__Error on 2009-06-10
A good idea would be to add a ymsg16 login with an http option because this would make this chat client completely immune to the boot packets.Just an idea thogh.

---

### Post by kcallis on 2009-06-12
I am running into the same issue... I attempt to log in and it immediately kicks me off. I have reloaded the version that is listed a couple of pages ago, and still nothing...

---

### Post by loell on 2009-06-13
> **Short__Error said:**
> A good idea would be to add a ymsg16 login with an http option because this would make this chat client completely immune to the boot packets.Just an idea thogh.

good one, but this isn't usually the venue to be heard of, by the developer. ;)

you can request this at gyachi forum. :)

---

### Post by Creative1412 on 2009-06-16
> **kcallis said:**
> I am running into the same issue... I attempt to log in and it immediately kicks me off. I have reloaded the version that is listed a couple of pages ago, and still nothing...
I have the same problem

---

### Post by nakama85 on 2009-06-18
I cna log in fine, do cam fine, I can hear others talk in chat rooms but nobody can here me. Any Ideas??

---

### Post by tqft on 2009-06-18
> **nakama85 said:**
> I cna log in fine, do cam fine, I can hear others talk in chat rooms but nobody can here me. Any Ideas??

Are you running pulse-audio as your sound system?  If you are it has a volume meter which lets you see if the sound is getting through

Start pulse-audio device chooser if it hasn't already
Select volume control
Click on the recording tab
Talk in gyachi - you should see the volume move as you speak

"Obvious" stuff that has burned me before (feel free to ignore)
If not - make sure you have clicked on the talk button, make sure everything is plugged in, check if mic has a separate on/off switch and/or volume control on it.

BTW - have noticed an increase in new and particularly nasty booters so this may explain some of the login problems - if you get booted and have trouble getting back in it could be the boot packets are still coming.  Never had a problem with booters befor ethe last week no matter what happened - gyachi just handled it.  Something new doing the rounds I think

---

### Post by Tank Jr on 2009-06-18
> **kcallis said:**
> I am running into the same issue... I attempt to log in and it immediately kicks me off. I have reloaded the version that is listed a couple of pages ago, and still nothing...

I have been having this problem for a couple of days now. Before that the client worked pretty well and I had my webcam up and running.
An interesting point is that the Yahoo messenger for Unix also refuses to connect now, citing something about a very old and out of date client.
This leads me to suspect that Yahoo has done something that is locking out these two clients.
However, I can connect to Yahoo messenger service using Kopete.
Can anyone shed some light on this?
Thank you in advance.

---

### Post by beatlefan on 2009-06-18
I've had a connection problem for about a week and a half, I'll post in the gyachi forum too but I'm at work right now.

If I try to log in using the Yahoo7.5 protocal, it will pause for awhile and then not connect. If I try the 8.0 protocal, it connects and shows me users but I've had a friend message me and they couldn't see my reply messages.

I'm just using regular old Jaunty, with gyachi 1.71.
I tried installing the previous version and same result.

---

### Post by nakama85 on 2009-06-18
> **tqft said:**
> Are you running pulse-audio as your sound system?  If you are it has a volume meter which lets you see if the sound is getting through

Start pulse-audio device chooser if it hasn't already
Select volume control
Click on the recording tab
Talk in gyachi - you should see the volume move as you speak

"Obvious" stuff that has burned me before (feel free to ignore)
If not - make sure you have clicked on the talk button, make sure everything is plugged in, check if mic has a separate on/off switch and/or volume control on it.

BTW - have noticed an increase in new and particularly nasty booters so this may explain some of the login problems - if you get booted and have trouble getting back in it could be the boot packets are still coming.  Never had a problem with booters befor ethe last week no matter what happened - gyachi just handled it.  Something new doing the rounds I think
I dont think I am using pulse. This may be a dumb question but if I do have it how do I start device chooser. However I am pretty sure I am using alsa.

I did check all the "obvious' stuff

Sound recorder works fine as well

---

### Post by tqft on 2009-06-18
"how do I start device chooser. "
Applications Sound PulseAudio Device Chooser

---

### Post by nakama85 on 2009-06-18
> **tqft said:**
> "how do I start device chooser. "
Applications Sound PulseAudio Device Chooser

well apparently I don't use Pulse then. Should I for voice to work with gyachi??

---

### Post by tqft on 2009-06-18
> **nakama85 said:**
> well apparently I don't use Pulse than. Should I for voice to work with gyachi??

You can hear others talk so the sound subsystems have connected.
Hopefully someone else will chime in.
You can check the setup - Setup then select the Options tab.  It will tell you what sound system gyachi is using.

---

### Post by nakama85 on 2009-06-18
> **tqft said:**
> You can hear others talk so the sound subsystems have connected.
Hopefully someone else will chime in.
You can check the setup - Setup then select the Options tab.  It will tell you what sound system gyachi is using.

I tried to see if I could hear myself through my laptop. No dice!

I checked the settings and it is set to alsa. 

It worked last time I had Ubuntu (same version) on this same computer. No changes have been made to this pc at all!

There must be something I am missing!?!?

---

### Post by mocha on 2009-06-18
How do you get to the chat rooms with voice?  Which ones are they?

---

### Post by nakama85 on 2009-06-18
> **mocha said:**
> How do you get to the chat rooms with voice?  Which ones are they?

I just go to a chat room and click on the symbol for voice chat at the top right hand corner (3 gears) and for the most part I use server 68.142.226.73, every now and then I have to switch servers. I do find however that all the servers that start with 66. crash voice chat.
Hope this helps

---

### Post by Sef on 2009-06-18
I can see when friends write me, but they can't see what I write.   they can see me typing, but nothing shows up.   What could be the problem?

---

### Post by tqft on 2009-06-18
> **Sef said:**
> I can see when friends write me, but they can't see what I write.   they can see me typing, but nothing shows up.   What could be the problem?

Change the font and colour and see if that makes a difference.
It might be a font they don't have or the text colour disappearing into the background.  Not sure if either of these are the problem, but it seems like the connection exists, so maybe the message is there and can't be seen.

---

### Post by Sef on 2009-06-18
I think it is a connection problem as I just tried pidgin and does not connect to yahoo, but it has before.

I did change the font color before and no go.

---

### Post by loell on 2009-06-18
> **Sef said:**
> I can see when friends write me, but they can't see what I write.   they can see me typing, but nothing shows up.   What could be the problem?

same symptoms was reported just a couple  weeks ago at gyachi forum, the reported work around seem to be, is to try other servers on the list.

---

### Post by Sef on 2009-06-18
> same symptoms was reported just a couple weeks ago at gyachi forum, the reported work around seem to be, is to try other servers on the list.

That don't seem to work.  A lot of them don't work for me.   Will have to take time and go through them one by one it seems.

---

### Post by nishantgarg25 on 2009-06-19
Even i face the same problem....my friends can not see my messages, they can just see me typing, but do not receive my messages. I can receive their messages.

Plz do post the solution if anybody finds it.

---

### Post by Sef on 2009-06-19
I can't connect to Yahoo with pidgin, so I am wondering if the problem is with Yahoo itself.

There is a [thread]("http://ubuntuforums.org/showthread.php?t=1191664") on not being able to connect with Yahoo.

---

### Post by nishantgarg25 on 2009-06-19
> **Sef said:**
> I can't connect to Yahoo with pidgin, so I am wondering if the problem is with Yahoo itself.

There is a [thread]("http://ubuntuforums.org/showthread.php?t=1191664") on not being able to connect with Yahoo.

Thanks..but i tried login to yahoo web messenger and it connects perfectly and i can communicate with yahoo web messenger. Also yesterday, connecting to gyachi after connecting with yahoo web messenger my msgs in gyachi were delivered. This does not work today

Is this a problem with linux based yahoo clients only??

---

### Post by nishantgarg25 on 2009-06-19
> **Sef said:**
> I can't connect to Yahoo with pidgin, so I am wondering if the problem is with Yahoo itself.

There is a [thread]("http://ubuntuforums.org/showthread.php?t=1191664") on not being able to connect with Yahoo.

Thanks Sef, i got my problem resolved from the link you provided. I just changed the server from scs.msg.yahoo.com to 
cn.scs.msg.yahoo.com

---

### Post by Sef on 2009-06-19
> Thanks Sef, i got my problem resolved from the link you provided. I just changed the server from scs.msg.yahoo.com to 
cn.scs.msg.yahoo.com

You're welcome and ty.  Tried that one and it works. :)

---

### Post by atoztoa on 2009-06-21
> **adroitster said:**
> It is sad that the bug is only for my primary account .....this is the last piece of software I am trying to configure after a clean install of jaunty on my computer(earlier is used pidgin on my intrepid). :(
I just now upgraded to gyachi_1.1.70 from your ppa but all in vain 

somebody who has a workaround please tell me!! I am using @yahoo.co.in as my ID which doesn't works while my @yahoo.com works flawlessly!!! Other having working gyachi please tell me if there is a solution!!


I found it... it is due to special characters in your password :)

_ATOzTOA
[www.atoztoa.com](www.atoztoa.com)

---

### Post by mocha on 2009-06-22
> **nakama85 said:**
> I just go to a chat room and click on the symbol for voice chat at the top right hand corner (3 gears) and for the most part I use server 68.142.226.73, every now and then I have to switch servers. I do find however that all the servers that start with 66. crash voice chat.
Hope this helps

Thanks.  That appears to work but I can't actually find anyone chatting.  I found one room with some guy playing country music and that was all.  Is there any specific room you suggest?

---

### Post by LordKthulhu on 2009-06-22
Interesting... I am having the same sort of issues with Gyachi: I can see my friends' messages, they can see me type, but they can not see what I actually type. Ubuntu 9.04 with appropriate Gyachi version on a dual-boot Dell PC. Any ideas? :confused:

Thanks, y'all!

Kthulhu

---

### Post by Sef on 2009-06-22
> Interesting... I am having the same sort of issues with Gyachi: I can see my friends' messages, they can see me type, but they can not see what I actually type. Ubuntu 9.04 with appropriate Gyachi version on a dual-boot Dell PC. Any ideas?Did you change the server from scs.msg.yahoo.com to cn.scs.msg.yahoo.com?

---

### Post by LordKthulhu on 2009-06-22
> **Sef said:**
> Did you change the server from scs.msg.yahoo.com to cn.scs.msg.yahoo.com?

[s]No. Setup->Options does not allow that. Or am I missing something?[/s] OK, it's an option on the login screen, if somebody else is looking for it. Log off, and then log back on to see it.

[s]Wouldn't let me on. If I log in with my user name only - "XXXXX is not an ID" If I log in as [EMAIL="XXXXX@yahoo.com"]XXXXX@yahoo.com[/EMAIL] I get booted the moment I try to send a message[/s]

OK, so it gives me "not an ID", but it still lets me on. Weird. Thanks a lot!

Kthulhu

---

### Post by loell on 2009-06-23
it's imperative that you not put **@yahoo.com** in your username when logging in.

---

### Post by ragadanga63 on 2009-06-23
Here's why you're having problems with Gyachi lately (like me):  [http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml](http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml)

Any workaround for Gyachi, Kabayang loell?

---

### Post by loell on 2009-06-23
gyachi isn't affected as far as i can tell with login problems, apart from from messages not going through, which is a yahoo server issue and is fixable by changing the server. it still is able to login with the default login method.

unless, are you having problem? loging in with gyachi?

---

### Post by naifnezar on 2009-06-27
hi,

I cant seems to get my new installed gyache improved to work properly. It seems that i can only receive msg but cannot reply. 

Are there anybody out there having the same problem or have the solutions?

:(

help needed....

---

### Post by loell on 2009-06-27
change your server to **cn.scs.msg.yahoo.com** during login.

---

### Post by naifnezar on 2009-06-27
ive tried... but this time could not connect at all. It says error no 4.

---

### Post by naifnezar on 2009-06-27
owh ok.... ive got it...
maybe its becoz of typo error.... anyway... thanks loell.....

---

### Post by bpence310 on 2009-07-01
I'm currently running Intrepid and Gyachi seems to run fine, but when i go to login, i still get disconnected immediately with the "[]" message and Login Failed.  I changed the server to **cn.scs.msg.yahoo.com **and still no luck.  Is it due to Gyachi using the 13 protocol instead of 15 (messenger 6 vs. messenger 7)?  I've never used gyachi before but i am very interested in getting it working for the webcam and voice chat and photoshare etc..   Any help would be appreciated.  Thanks.

BTW:  Pidgin seems to work fine, and when i boot into windows, my yahoo messenger client works properly as well, so it is definately something either I or Gyachi is doing wrong.  

Thanks again...

DISREGARD.  I Had the new gyachi installed, but was still running the old one. All is well.

---

### Post by tgpraveen on 2009-07-01
why isnt this wonderful program in the repos?

it should be added to karmic repos.
someone pls do it.

---

### Post by tqft on 2009-07-01
> **tgpraveen said:**
> why isnt this wonderful program in the repos?

it should be added to karmic repos.
someone pls do it.

Licensing issue with some of the (sound) files

---

### Post by loell on 2009-07-01
> **tgpraveen said:**
> why isnt this wonderful program in the repos?


still attempting.. ;)

[http://mentors.debian.net/cgi-bin/maintainer-packages?action=details;package=gyachi]("http://mentors.debian.net/cgi-bin/maintainer-packages?action=details;package=gyachi")

debian sponsorship is just hard to come these days it seems.

---

### Post by drpjkurian on 2009-07-01
Great you have done something marvel:popcorn:lous

---

### Post by Digitallysick on 2009-07-09
Kumusta loell!  How can I change the Gyachi sounds? I go to setup, options, and theme but the sounds seem to remain the same , they are just too loud is the problem. 

Philippines rocks, keep up the good work


Edit, i just found the sound package and changed it, ahhhh much better

---

### Post by loell on 2009-07-09
heheh, tell me about it, i normally turned off sound on usuall install. because well, it's too loud and horrible. :D 

good that you've changed it. :)

---

### Post by Paradoxfox93 on 2009-07-12
My device:

```

user@comp:~$lususb
Bus 003 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

```

I get this when running xawtv but i get a good picture and the webcam works:
```

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.28-13-generic)
xinerama 0: 1280x1024+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l]: no overlay support
v4l-conf had some trouble, trying to continue anyway
libv4l2: error getting capabilities: Invalid argument
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOCMCAPTURE(frame=0;height=120;width=160;format=7): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=120;width=160;format=15): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=120;width=160;format=9): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=120;width=160;format=5): Invalid argument

```

but when i try to run it in gyachi from the .deb file for jaunty (which I am currently on) i get no output in the terminal but the camera window is just black.  I tried adjusting settings in gyachi (brightness/gamma) to no avail.

What are my options?  This is obviously not a v4l2 cam so i think the script you suggested for halln will not apply.

Thanks, this is more than I was able to do a year ago with gyachi.  I couldn't even get it compiled back then.  I like gyachi even just as an IM prog b/c the interface is A+ imho.  Voice chat, webcam and chat rooms are all a + if I can get them working.  Thanks a lot and I hope you can help me!

---

### Post by loell on 2009-07-12
hmm, i see no reason why it wouldn't work in gyachi, since xawtv can output images even with its libv4l errors above.

try selecting v4l1 or v4l2 in gyachi webcam settings ( still on the webcam window).

---

### Post by Paradoxfox93 on 2009-07-12
v4l1 is already selected but v4l2 puts out:
```
libv4l2: error getting capabilities: Invalid argument

```

---

### Post by tqft on 2009-07-12
Do you have a tv card or anything else like that?

If you go 
ls /dev/video*  
what is the output?

I have a tv card and if I reboot with the webcam in, sometimes the order is changed and I need to set gyachi to look at /dev/video0 rather than /dev/video1

---

### Post by Paradoxfox93 on 2009-07-12
But then it would make no sense that xawtv would work.  Anyway, i don't have a tv tuner card but this is the list in case it might be somethign else:

```
user@comp:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
user@comp:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:07.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

Do i need an encoder?  Under setup (for webcam) it is blank.

It's definately dev0  it freaks out if i try to start the cam with any other assignment.  it's like it works....it's just super frikin dark and brightness/gamma don't change anything.  There no speckle. It's solid black but apparently it make a connection because i don't get any errors.

---

### Post by loell on 2009-07-12
i see,

the only thing i could recommend is, try asking the [libv4l guys]("http://freshmeat.net/projects/libv4l") about this issue. it's probably a decoding problem with libv4l.

---

### Post by Short__Error on 2009-07-14
you should post the Gyachi 1.2.1 on here loell it works great, i have been useing it for about 4 days now and i am very happy with it.
i myself am about to start editing the source for the simple fact of i am tired of the ignored pm message that pops up on my screen. i would rather just not know about it cause it was ignored for a reason. ;)

---

### Post by Sef on 2009-07-14
> you should post the Gyachi 1.2.1 on here loell it works great, i have been useing it for about 4 days now and i am very happy with it.

If you have installed Loell's PPA for Gyachi, it will upgrade to 1.2.1.

---

### Post by Short__Error on 2009-07-15
I know this but i was just saying that he sould post it for those who are new to gyachi...and i dont i compiled it myself and changed some things with the help of some friends..

---

### Post by loell on 2009-07-15
edited! O:) for your satisfaction. ;)

---

### Post by androliviu on 2009-07-22
it has some bugs....
everithimg that someone it writes to me, apears 2 times.
has a big time betwen wrighting and recieving .

---

### Post by loell on 2009-07-22
has been fixed with 1.2.1 , what version are you running?

---

### Post by fballem on 2009-07-22
I'm wondering how you got the webcam to work - I think you're using V4L1, which is what is needed in Flash Player. I would love to be able to figure out how to make that work as well as Gyachi works.

Thanks,

---

### Post by loell on 2009-07-22
we've been using libv4l for quite some time now, which means v4l1 or v4l2 compatible webcams will just work, if it doesn't, it's a libv4l bug.

---

### Post by xeddog on 2009-07-25
Hey Lowell,

There is a whole lot of us (at least 2) that are having problems logging in to Yahoo.  I posted this on the Gyachi help forum over at SourceForge but did not get any reply.  Actually, it was a post by tommygunner88 that I added on to.  But I am hoping that since this forum seems to get more attention I may get some help here.

When Gyachi attempts to login to Yahoo I get a repeated error:

> Could not connect to server:
f5.yahoofs.com 

This happens several times (7?) very quickly and I see in the Gyachi chat window: 

>  ** WARNING: TOO MANY DIALOG MESSAGES HAVE BEEN OPENED TOO QUICKLY (Possible Flood or Boot Attack from a malicious Yahoo user?) -  Dialog Messages will be temporarily disabled for 2.5 minutes to help protect your system, and default actions will be taken for all 'confirmation' dialogs.
** Info Message: Could not connect to server:
f5.yahoofs.com **
** Info Message: Could not connect to server:
f5.yahoofs.com **
** Info Message: Could not connect to server:
f5.yahoofs.com **
  Disconnected from Yahoo!    See Ya!  Online for  0 : 00 : 04

    ** You have been disconnected from Yahoo! [ Error receiving from socket: 9 ] **
  Disconnected from Yahoo!    See Ya!  Online for  346821 : 08 : 38

** Info Message: You have been disconnected from Yahoo!
Error receiving from socket: 9 **

If I try to connect again, It isn't only Gyachi that gets disabled for 2.5 minutes but my entire Jaunty system.  The only thing that works is I can move the mouse pointer but that is all.

Any ideas what may be causing this??  I have the same version of Gyachi installed on an older system that is also running Jaunty, and it works just fine except gor getting disconnected from Yahoo a couple of times a day.

The one that works is on an Intel P-4 2.4Ghz machine.  The one that fails is on my new Intel I7-920 machine if that makes any diff.  But I have not had any issues with other IM programs like Pidgin or SIM-IM, or any other applications for that matter.  Both systems are running Gyachi 1.2.1 from the repos.

Anything I can try to fix this??

TIA,

xeddog

---

### Post by androliviu on 2009-07-27
> **loell said:**
> has been fixed with 1.2.1 , what version are you running?


i am running 1.2.1 and another thing, it does not log with my mail on yahoo.com.
how can i do this?? thanks

---

### Post by xeddog on 2009-08-01
FWIW, I just installed the update to 1.2.2-1 via the update manager and I still have the same problem.

> Could not connect to server:
f5.yahoofs.com 

xeddog

---

### Post by currahee30577 on 2009-08-03
> **loell said:**
> edited! O:) for your satisfaction. ;)

loell thanks for all your hard work

---

### Post by inchkape on 2009-08-14
Hi all,
I'm having exactly the same problem as Xeddog. I have Gyachi 1.2.1 running on linux mint 7.0 64bi (jaunty-based).
Now to make things more fun, I have two yahoo accounts; when I log in with one, I have the problem Xeddog experiences and when I log in with the other, I have no problems at all. Weird

---

### Post by colau on 2009-08-14
Hi,
How can i set up a nickname for my yahoo account in Gyachi?

---

### Post by Couto on 2009-08-14
Would be nice to have a fully featured AIM & MSN client, I don't use Yahoo! but they seem to care more, if this Gyachi is made by Yahoo!

Thanks for this though!

---

### Post by inchkape on 2009-08-15
> **colau said:**
> Hi,
How can i set up a nickname for my yahoo account in Gyachi?

If you mean you don't have a nickname, go to the yahoo web site and make one there, then use it to sign in to yahoo in Gyachi.

---

### Post by colau on 2009-08-15
> **inchkape said:**
> If you mean you don't have a nickname, go to the yahoo web site and make one there, then use it to sign in to yahoo in Gyachi.
If I chat with someone using any yahoo id , the yahoo id is appeared in that window (not my name).
It's ok in pidgin as there is an option in pidgin as Local Alias.

---

### Post by inchkape on 2009-08-15
> **Couto said:**
> Would be nice to have a fully featured AIM & MSN client, I don't use Yahoo! but they seem to care more, if this Gyachi is made by Yahoo!

Thanks for this though!

I know nothing about AIM, but for MSN you can use aMSN which is an excellent alternative to the microsoft MSN client.
As far as Yahoo is concerned, apart from a half-hearted attempt to port their messenger to Linux back in about 2002, they have done nothing at all to contribute to making anything other than their own Microsoft client work on their chat network.
The Chat client that you so rightly praise which is called Gyachi used to be called GyachEand before that simply Gyach.
I do know that Gyachi means Gyach improved. GyachE was Gyach enhanced and gyach...I don't know..GreatYahooChat?
Whatever, yahoo had nothing to do with it and in fact these days it's very much down to a man often on this forum whose name is Loell (thanks Loell!)

---

### Post by loell on 2009-08-15
> **inchkape said:**
> 
The Chat client that you so rightly praise which is called Gyachi used to be called GyachEand before that simply Gyach.
I do know that Gyachi means Gyach improved. GyachE was Gyach enhanced and gyach...I don't know..GreatYahooChat?

yes, your sequence is right. :)   I'm almost certain that it's **"Gtk Yahoo chat"**. I  wish, way way back, they could have just chosen a more simpler name.

> **inchkape said:**
>  
Whatever, yahoo had nothing to do with it and in fact these days it's very much down to a man often on this forum whose name is Loell (thanks Loell!)

heheh, I'm just a user on the front line. ;)

the one really pulling the strings these days is **Greg Hosler**. :)

---

### Post by inchkape on 2009-08-16
> **loell said:**
> yes, your sequence is right. :)   I'm almost certain that it's **"Gtk Yahoo chat"**. I  wish, way way back, they could have just chosen a more simpler name.



heheh, I'm just a user on the front line. ;)

the one really pulling the strings these days is **Greg Hosler**. :)

- Thanks Greg! :lolflag:

- and thanks Loell - you sure keep gyachi working for me in my linux mint world

---

### Post by colau on 2009-08-16
> **loell said:**
> yes, your sequence is right. :)   I'm almost certain that it's **"Gtk Yahoo chat"**.
Gyachi=***Gtk Yahoo chat***!:)

---

### Post by inchkape on 2009-08-17
> **xeddog said:**
> FWIW, I just installed the update to 1.2.2-1 via the update manager and I still have the same problem.



xeddog


OK, here's how I fixed mine: Go to your home folder, do  <ctrl-h> to see hidden folders, open .yahoorc, gyach - then find the file "gyachrc" and rename it "gyachrcOLD"

When you re-start gyachi, it will open a new .gyachrc (which is the config file) and if you then do your usual yahoo login it should connect. You will have to re-do any personalizations such as fonts, but at least your chat client should work again.

---

### Post by xeddog on 2009-08-17
I just tried inchkape's resolution and it did not work for me.  After trying his resolution I even uninstalled Gyachi using Synaptic, then deleted the .yahoorc directory completely, and re-installed Gyahci and it still crashes with the same error.  One more thing now.  After I close all 7 error message boxes, Gyachi stops responding and the window darkens.

Any other suggestions??  I really don't want to use Pidgin anymore.


xeddog

---

### Post by newagelink on 2009-08-17
Why can't I find it in the repository or via Synaptic Package Manager? Are we testing it before an official release?

---

### Post by inchkape on 2009-08-17
> **xeddog said:**
> I just tried inchkape's resolution and it did not work for me.  After trying his resolution I even uninstalled Gyachi using Synaptic, then deleted the .yahoorc directory completely, and re-installed Gyahci and it still crashes with the same error.  One more thing now.  After I close all 7 error message boxes, Gyachi stops responding and the window darkens.

Any other suggestions??  I really don't want to use Pidgin anymore.


xeddog

I read your post, went back to try on my desktop computer...back to the same problem. When I fire up the laptop and use gyachi in there i have no problem. when I use gyachi on the desktop comp but with a different account, I again have no problem. This is weird.

Can anyone else help us?

---

### Post by johnlvs2run on 2009-08-17
> **Couto said:**
> Would be nice to have a fully featured AIM & MSN client, I don't use Yahoo! but they seem to care more, if this Gyachi is made by Yahoo!

AIM still works?  I used to use it all the time, but it got overrun with spam bots quite a few years ago.  Are they still there or has it cleaned up in the meantime?

---

### Post by johnlvs2run on 2009-08-17
Does gyachi work with linux sabayon?

---

### Post by loell on 2009-08-17
> **johnlvs2run said:**
> Does gyachi work with linux sabayon?

it should, if sabayon has  all the necessary dependencies needed to run it.

---

### Post by xeddog on 2009-08-18
> **inchkape said:**
> I read your post, went back to try on my desktop computer...back to the same problem. When I fire up the laptop and use gyachi in there i have no problem. when I use gyachi on the desktop comp but with a different account, I again have no problem. This is weird.

Can anyone else help us?

I just tried Gyachi again using my wife's id this time, and it logs in and runs with no problem.  I did notice that when it starts the main chat window shows her current buddy list three times.  Why is that??

Anyway, I disconnected without shutting gyachi down and then logged back in with my own ID and it works too.  This time it just showed my current buddy list twice though instead of three times.  It seems to be only when I try to login with my own ID at the start that Gyachi goes ape[bleep].

I think I mentioned this once before, but I can use Gyachi on another computer and it works just fine with my own id.  Same release of Gyachi and Ubuntu too.  The difference is that the other computer is an older 3.0Ghz P-4 machine, and the one I am having problems with is my new I7-920 machine.  Maybe it's just too fast???   :)

xeddog

---

### Post by xeddog on 2009-08-18
OK.  Here is an interesting little tidbit.  While I was typing my last message I was also installing some updates.  The updates were mostly the 2.6.28-15 kernel (I was still on the 2.6.28-13 kernel at the time).  Anyway, after the updates were installed and I rebooted, I was able to start Gyachi and log in with my own ID.  So the questions are:
1.  Did the kernel update have anything to do with this?
2.  Did finally getting logged in with my own ID before the reboot have anything to do with it?
3.  Will it last?

xeddog

---

### Post by xeddog on 2009-08-18
I guess I got my answer as to how long it would last.  Excrement!!!  Gyachi did let me login the first time, but it would time out, disconnect, and reconnect every few minutes.  Even when I have the Ping keep alive set to 1 minute, it still timed out about every 5 min. and then it would not let me login again.  Back to the same error again.  I really need some help with this.

xeddog

---

### Post by loell on 2009-08-18
I for one, doesn't have any idea why that is.. :(

as a rule of thumb, when everything gets weird too much in a box, i always do a clean install.

---

### Post by buckeyered80 on 2009-08-18
I am having the same issue. This f5.yahoofs.com error message pops up when I log in, and then it disables the pop-ups and freezes it.  Very strange...if anyone finds this one post it without delay!

---

### Post by xeddog on 2009-08-19
> I for one, doesn't have any idea why that is..

as a rule of thumb, when everything gets weird too much in a box, i always do a clean install. 

I have tried a clean install unless you are talking about a clean install of Ubuntu itself.  If so, then let me just add this.  When I got this new machine and installed Jaunty, the very first application I installed was Gyachi.  I don't remember for certain which version it was but I think it was 1.2.1, and I have had this problem from the very start.  But ONLY on this new I7-920 machine.  I have never had any problems with Gyachi on my older P-4 machines.

The other thing that gets me is why does Gyachi work ok on this machine when I use a different userid?!?!?

Anyway, I (we) would appreciate anything you can do for me (us).

xeddog

---

### Post by DougieFresh4U on 2009-08-19
> **buckeyered80 said:**
> I am having the same issue. This f5.yahoofs.com error message pops up when I log in, and then it disables the pop-ups and freezes it.  Very strange...if anyone finds this one post it without delay!

When I open 'gyachi' all is good for about 5 seconds and then little messege box telling me it can't connect and an address. Then it freezes and have difficult time and either it closes eventually or force quit. This is happening on both my Karmic partitions (32 & 64 bit) & my Jaunty partition as well.
Actually 'xeddog' has described the login/connection issue very well.
Benn running excellent for quite awhile until a few days ago.
Thanks for any help/solution you may come up with 'loell' :):)

---

### Post by buckeyered80 on 2009-08-20
I'll eventually get around to some troubleshooting on this and see what this server is and what it is trying to pull from it.  It can't be the main connection server...they just changed that.  It seems I can't connect to Yahoo through Pidgin anymore either.  Is Yahoo fooling around with their servers again?

---

### Post by inchkape on 2009-08-20
Suddenly...I can log in again. I tried it 4 times in a row, no problems whatsoever.
It feels a little like a traffic jam on a motorway...suddenly traffic jam clears...and you're happy it's gone, but also left with a slight feeling of frustration - all this trouble was caused by...nothing at all?  :lolflag:

---

### Post by inchkape on 2009-08-21
Today: Back to the traffic jam - same old log in problem and cannot connect to server ad nauseum

---

### Post by loell on 2009-08-21
might have something to do with the region your living in?

---

### Post by inchkape on 2009-08-21
> **loell said:**
> might have something to do with the region your living in?

Nope! - Because on the same desktop I can log in just fine through pidgin, Empathy, Kopete and even the yahoo messenger in windows when i boot it. I can also log into another yahoo account using gyachi. I can log in to both yahoo accounts using gyachi on my laptop instead of the desktop.

...besides, this a very nice region :P

---

### Post by DougieFresh4U on 2009-08-21
> **loell said:**
> might have something to do with the region your living in?

I'm still getting the 'freeze' after login and the can not connect error

---

### Post by ronmifflin on 2009-08-26
Hello all,

I have a problem installing Gyachi on my computer. It's giving me the error message - Error: Dependency is not satisfiable: libltdl3 (>= 1.5.2-2). Any suggestions on how to install this?

Thank you,
Ron

---

### Post by DougieFresh4U on 2009-08-30
Able to connect again.
I changed the yahoo server to:
```
cn.scs.msg.yahoo.com
```

---

### Post by xeddog on 2009-09-01
Interesting.   cn.scs.msg.yahoo.com   seems to be working for me too.

xeddog

---

### Post by inchkape on 2009-09-02
Seems to work here too. Thanks Dougie!
Still find it weird that on my laptop I can still connect through the other server, but hey, so long as it works!

---

### Post by riseringseeker on 2009-09-16
I tried to get the debs you have listed in the first post, but it seems they are dead links.

I am trying to get gyachi set up on my Jaunty 64bit install and have voice user to user, don't care about room chat voice.  If I read you directions correctly, I need to install the 32bit version as well as getlibs for this to work.  Everything *except* the voice is working fine right now, but really want to have voice.

---

### Post by riseringseeker on 2009-09-18
bump

---

### Post by amsum on 2009-09-18
I installed Gyachi 1.2.2 and gyachi-codecs both. I am able to text-chat and send files. But no voice chat success. Infact when I call from my yahoo msn in windows to Gyachi in Ubuntu 9.04, I dont even get the call receive or call reject option. It appears like nothing is happening. What extra tweaks I need to make it work?

---

### Post by riseringseeker on 2009-09-21
It appears loell is either on vacation, or not monitoring this thread at the moment/any longer.  Maybe we can get an answer when/if he returns.  I hope so, as this is something I want to get working.

I've sent him a PM that has not been responded to as well.

---

### Post by loell on 2009-09-22
yep, been busy, besides, the question has  been answered couple if not many times in this thread already.  

for the nth time, you can't do voice call or in technical terms ( you can't make [SIP calls]("http://www.google.com.ph/search?hl=tl&defl=en&q=define:SIP+Phone")) with gyachi. if you notice the title thread, I did mention **Room Voice Chat**. 


I urge all of you, to those who really  want Yahoo Voice (SIP Phone calls) implemented in gyachi.

then please let the developer know that you also care about this particular feature.

**ask about this particular feature** : [HERE]("https://sourceforge.net/forum/forum.php?forum_id=533966")

I did my feature requests long time ago and most of them were implemented, save the yahoo voice feature. but now, perhaps it's your turn to do so.

hope to see your request messages in gyachi forum.

[http://gyachi.sourceforge.net/forums.shtml]("http://gyachi.sourceforge.net/forums.shtml")

thanks...

---

### Post by adroitster on 2009-09-25
Somebody please help me with connecting to Yahoo! India ID on gyachi. Am using ubuntu jaunty and using the 64 bit version of gyachi. I can login using my account which is made using Yahoo! US but not using the Yahoo! India account . All my friends and relatives on the Yahoo! India account and I don't want them to take the trouble of again adding one more account for me. I have been asking this question since quite a few months and Loell told me that its a bug. I have also reported the bug I don't know for sure that its a bug or problem with the settings. If there can be a workaround somebody please help me. Its the only thing which make me to boot up my Windows using Virtual box . I just don't want to use the windows OS any more just for Yahoo! . Its only Yahoo! India thing which has made me to keep my computer dual boot. :confused::(

Though I use windows in virtual box for my university projects (but thats a different issue)  :P

---

### Post by Night-Horse on 2009-09-26
Hello All,

Am having a problem with voice. When I try to use it I get this error on console: "sh: gyachivoice: not found"

I did not found any relevance errors on my searching and I read somewhere that gyachivoice is installed with the package. So what's wrong on my comp? :p

I am using jaunty x64 and installed gyachi from your repo loell. Thanks in Advance. :)

---

### Post by Sef on 2009-09-28
> I am using jaunty x64 and installed gyachi from your repo loell. Thanks in Advance

Did you install the 64 or 32-bit version of gyachi?

---

### Post by Mark76 on 2009-09-30
Can anyone explain this?

> ~/gyachi-1.2.2$ make
make  all-recursive
make[1]: Entering directory `/home/mark/gyachi-1.2.2'
Making all in intl
make[2]: Entering directory `/home/mark/gyachi-1.2.2/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mark/gyachi-1.2.2/intl'
Making all in po
make[2]: Entering directory `/home/mark/gyachi-1.2.2/po'
make[2]: Leaving directory `/home/mark/gyachi-1.2.2/po'
Making all in lib
make[2]: Entering directory `/home/mark/gyachi-1.2.2/lib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mark/gyachi-1.2.2/lib'
Making all in client
make[2]: Entering directory `/home/mark/gyachi-1.2.2/client'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mark/gyachi-1.2.2/client'
Making all in gyvoice
make[2]: Entering directory `/home/mark/gyachi-1.2.2/gyvoice'
gcc -DHAVE_CONFIG_H -I. -I.. -DLOCALEDIR=\"/usr/local/share/locale\" -I../lib -I../client -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/alsa      -g -O2  -Wall -Wno-pointer-sign -funsigned-char -MT afl.o -MD -MP -MF .deps/afl.Tpo -c -o afl.o afl.c
In file included from wine/winbase.h:5,
                 from afl.c:30:
wine/winnt.h:625:2: error: #error You need to define a CONTEXT for your CPU
In file included from wine/winbase.h:5,
                 from afl.c:30:
wine/winnt.h:628: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
wine/winnt.h:754:2: error: #error You need to define DEFINE_REGS_ENTRYPOINT macros for your CPU
wine/winnt.h:765:3: error: #error You must define GET_IP for this CPU
wine/winnt.h:1021: error: expected specifier-qualifier-list before ‘PCONTEXT’
wine/winnt.h:1034: error: expected declaration specifiers or ‘...’ before ‘PCONTEXT’
In file included from afl.c:30:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from afl.c:30:
wine/winbase.h:1342: error: expected declaration specifiers or ‘...’ before ‘CONTEXT’
wine/winbase.h:1481: warning: type defaults to ‘int’ in declaration of ‘CONTEXT’
wine/winbase.h:1481: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
afl.c: In function ‘ACM_GetStream’:
afl.c:52: warning: cast to pointer from integer of different size
afl.c: In function ‘acmDriverAddA’:
afl.c:79: warning: cast from pointer to integer of different size
afl.c: In function ‘acmDriverEnum’:
afl.c:140: warning: cast from pointer to integer of different size
afl.c: In function ‘acmDriverID’:
afl.c:163: warning: cast from pointer to integer of different size
afl.c: In function ‘acmDriverOpen’:
afl.c:238: warning: cast from pointer to integer of different size
afl.c: At top level:
afl.c:266: warning: cast from pointer to integer of different size
afl.c: In function ‘MSACM_UnregisterDriver’:
afl.c:309: warning: cast from pointer to integer of different size
afl.c: In function ‘MSACM_GetDriverID’:
afl.c:348: warning: cast to pointer from integer of different size
afl.c: In function ‘MSACM_GetDriver’:
afl.c:356: warning: cast to pointer from integer of different size
afl.c: In function ‘MSACM_GetObj’:
afl.c:364: warning: cast to pointer from integer of different size
afl.c: In function ‘acmStreamOpen’:
afl.c:420: warning: cast from pointer to integer of different size
afl.c:432: warning: cast from pointer to integer of different size
afl.c:470: warning: cast from pointer to integer of different size
afl.c:477: warning: cast from pointer to integer of different size
afl.c:499: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamClose’:
afl.c:523: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamConvert’:
afl.c:570: warning: cast from pointer to integer of different size
afl.c:570: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamPrepareHeader’:
afl.c:618: warning: cast from pointer to integer of different size
afl.c:618: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamReset’:
afl.c:656: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamSize’:
afl.c:699: warning: cast from pointer to integer of different size
afl.c:699: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamUnprepareHeader’:
afl.c:750: warning: cast from pointer to integer of different size
afl.c:750: warning: cast from pointer to integer of different size
make[2]: *** [afl.o] Error 1
make[2]: Leaving directory `/home/mark/gyachi-1.2.2/gyvoice'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mark/gyachi-1.2.2'
make: *** [all] Error 2


---

### Post by loell on 2009-09-30
compiling against a 64 bit machine?

---

### Post by Mark76 on 2009-09-30
Certainly ;)

---

### Post by loell on 2009-09-30
you need to pass **--disable-wine** on the ./configure parameter, of course that would disable room voice chat feature.

---

### Post by mwillams73 on 2009-10-08
> **xeddog said:**
> Interesting.   cn.scs.msg.yahoo.com   seems to be working for me too.

xeddog

Ok so up until a week ago everything was fine, then I logged in to chat everything works, i send an IM but they cant see me typing, so i did the cn. yahoo thing, and guess what IM works but now I cant get into any chat room, whats up with this? I get a not a valid id error but i can IM just fine but no chat rooms? This doesnt make any sense at all! PLease loell you gotta have a fix for this.

---

### Post by mwillams73 on 2009-10-08
Well an update, If i change the server back to the original one i can go into chat, but of course when i IM someone they cant see what I type,, also whats with this supposed gyache 1.2.2 everyones talking about, I went to the ppa page and got it all set up but when i do a synaptic search( for gyachi not gyachE cause that shows nothing at all) i cant find a newer version of gyache? And no updates for it either , whats the point of the archive and releasing a new version if nobody can get it? the debs for the new version are just dead links, I really need the web cam, but i dont care about voice chat, So loell are you working on these issues or what? It would be nice if you upload the 1.2.2 version in a deb form so we can get it! Also whats with the package saying gyachi and the messenger saying its gyachE, this seems like some ones not really paying attention to whats getting put into the packages.Oh one more thing the only way I can put the cn. server on is to copy and paste it from here, there is no option in the messenger itself is that why I cant get it to work right? again this goes back to the "id love to get some updates for it" but I cant because you archive doesnt seem to have any! I really appreciate your hard work, and I dont want you to think that Im complaining but it seems everyone else has it working now but me, and I cant figure out why. Some detailed instructions would be nice! Thanks for any help you or anyone else can provide.

---

### Post by mwillams73 on 2009-10-08
Ok so the only 1.2.2 version I can find is the compile from source version on source forge, I dont really understand the instructions on how to install this , so it it would be great to get a step by step rundown on how to do this, But really I wonder is why this isnt in a deb file format? it would be so much easier then.It also seems that using gyachi is more work than anything else, does anyone know of a yahoo messenger for hardy that has web cam support, cause I cant find one at all that works right. And yes i know pidgin has it for jaunty but I couldnt get the webcam support at all it seems that the new version only  supports webcam for gtalk and msn, so thats a no go. Again Im wondering why, if it can be done with gyachi( when it works right)then why cant i get it in pidgin in hardy, are the devs just lazy or what? I would gladly wait an extra month or 2 to get it in hardy but they decided to only support jaunty? which is full of glitches but not the LTS hardy? Supposedly the next LTS will have it but thats in 2011, are you serious? A year and a half for webcam with pidgin? that doesnt make any sense at all either, If theres a specific reason Id love to know. Linux is so behind the curve sometimes it makes me sick! I cant wait to get my mac so I can do everything i need to do without fixing crap all the time.

---

### Post by mwillams73 on 2009-10-08
well after a reboot the cn. server doesnt work at all it says it cant log me in, but if i switch it to the original server it works fine, again I cant up grade from 1.1.48 to anything else, why? The only version in synaptic is the one i have. this is really starting to tick me off!!Why is it that im the only person who cant use any of the newer versions? I have the ppa for hardy but its seems as though there are no updates or new versions at all. What the heck am I doing wrong? I uninstalled 1.1.48 and deleted the yahoorc  file and reinstalled and still nothing. can any of you that have actually fixed yours please post exactly what and how you did it, so that i can get a handle on this. Im really tired of people saying OH never mind i fixed it, but then dont post how they did it so those of who havnt can get some help, where are you guys getting the new versions, and updates? Cause i cant find them at all, are you guys using the ppa and if so how do you have it set up maybe I did something wrong although im sure i didnt cause the terminal told me it was done right. If there arent any new versions for hardy,The why ? Its the LTS it should be what everyone is working with first , not as an afterthought. I mean thats why its the LTS. I really wish the devs would stop ignoring all of us that use the LTS versions just because they dont want to do a little extra work.I might not like the mac OS but atleast it works, so I guess when I get my mac Im just gonna use that instead Im so tired of fixing things before i can use them , or fixing them because theres no updates.

---

### Post by picpak on 2009-10-08
Try this link:

[https://launchpad.net/~loell/+archive/ppa/+files/gyachi_1.2.2-1~jaunty_i386.deb](https://launchpad.net/~loell/+archive/ppa/+files/gyachi_1.2.2-1~jaunty_i386.deb)

and let me know if it works on Hardy. :)

I'm also having troubles with the cn server, which one is the original again? I don't remember.

---

### Post by roemasa on 2009-10-09
Today I have problem with Gyachi. Page server cn.scs.yahoo.com seems not working starting today. If I am using scsa.yahoo.com (I know it from pidgin), gyachi not fully working, I can receive messages but the problem is my buddies can't see my messages.

Anyone know other solutions that completely working for this problems?

---

### Post by mwillams73 on 2009-10-09
> **picpak said:**
> Try this link:

[https://launchpad.net/~loell/+archive/ppa/+files/gyachi_1.2.2-1~jaunty_i386.deb](https://launchpad.net/~loell/+archive/ppa/+files/gyachi_1.2.2-1~jaunty_i386.deb)

and let me know if it works on Hardy. :)

I'm also having troubles with the cn server, which one is the original again? I don't remember.

Thanks picpak, i couldnt find the deb anywhere! I'll install tonight or tomorrow, prolly more like tomorrow morning cause its late here now,
As for the server gyachi's original is scs.msg, or something like it, but I know for fact that the upgraded pidgin uses scsa. , which I tried in gyachi it works but still no IM's so it has to be gyachi and not yahoo. Well atleast for me anyways! I'll check this out and get back to you as soon as I have some Info, and thanks again!!

---

### Post by mwillams73 on 2009-10-09
the jaunty deb is a no go, it needs libasound2 for jaunty, and theres no way im installing jaunty's ppa just for that, it was worth the try though. Well im stumped, it makes no sense at all. Im pretty sure some day this will get fixed but Im also pretty sure that like alot of things in ububntu by the time it does get fixed I'll have found something that actually works.

---

### Post by mwillams73 on 2009-10-09
Well only 2 servers work for gyachi, first is" scs.msg.yahoo.com "
The second one is" scsa.msg.yahoo.com "( but of course I use the word "work" loosely because it doesnt "work" as intended) so does it or does it not seem ridiculous to have so many options that dont work, including this one" cn.scs.msg.yahoo.com " which isnt even on the list at all! All of them give me a failed to login error, or dns server failed or something else similar.
 I understand that it "could" have something to do with yahoo, but really if it did then why can pidgin do my IMs but gyachi can not? So in this case it has nothing to do with yahoo at all but something either with my install or with the actuall program itself. Im voting for gyachi being the culprit( because I already installed jaunty and had the same problems and then reinstalled hardy and Im back to square one) 
So to recap, my friends can IM me but I cant IM them, They can see that I'm online but all they get is "typing" they are using yahoo messengers and pidgin messengers , I'm the only person in my circle of friends who uses gyachi. I'm also the only person in my group that they cant see the text.
I can go into chat rooms fine and even use the webcam feature while I'm using IM, although they cant read my text they can see my cam just fine! Is this or is this not weird? There has to be something wrong with the way gyachi is configured if i can read my friends IM text but they cant see mine yet at the same time I can use the webcam and both sides can see each other just fine. 
So my suggestion is Upgrade the code for gyachi as soon as possible, patch it, get something going on with this because I rely heavily on this messenger every single day. I use it to see my daughter who lives with her mom, I use it to see my friends who live all over the world. It's an important part of my daily life and without it I might as well go back to windows. I havnt worked this hard to have something inferior to windows. Oh and I got so fed up I actually installed the official yahoo messenger in wine, it works up until I try to log in then it sits and thinks for like 5 minutes and then times out.( I think that for some reason it cant connect from inside wine) So yeah this really sucks, How did gyachi go from working perfectly fine last week to not working this week?
If anyone knows the answer Id love to hear it!

---

### Post by amitabhishek on 2009-10-09
Thanks it works like a charm...only UI is kinda cluttred.

---

### Post by Tony Flury on 2009-10-09
I am also having the same connection problems with both Gyachi (i can see incoming IMs but my MS WIndows based friends can't see my IMs), and kopete which wont even connect.

I can only assume that Yahoo has broken something (to stop non-standard Yahoo clients from working).

Any clues on how to get this working is appreciated.

---

### Post by xeddog on 2009-10-09
Well for me, things have gone from bad to worse the last couple of days.  I have not been able to login to YIM using the scs.msg.yahoo.com server because of the "f5.yahoofs.com" problem for quite some time.  I got around that by using the cn.scs.msg.yahoo.com server which worked well for me.   NOW, I can't even login using that one.  It times out.  I can't use Gyachi at all now, but Pidgin works fine. 

Any ideas?  (PLEEEEEEASE)

xeddog

---

### Post by xeddog on 2009-10-09
One more question.  I would like to add Gyachi to my Karmic installation, but there doesnt seem to be a repository for karmic yet.  Is this correct?

xeddog

---

### Post by Tony Flury on 2009-10-09
I can't connect with pidgin either :(

---

### Post by Mark76 on 2009-10-09
My Jabber server's Yahoo transport is working.

Obviously you don't get all the extras, but at least I can still chat.

---

### Post by mwillams73 on 2009-10-09
On pidgin you need the upgraded ppa from the pidgin web site, or just change the server to scsa. instead of scs. I know its not yahoo because if it was none of the third party messengers would work, like in the case of them changing servers and blocking pidgin which pidgin fixed. I think its because the lesser known messenger devs dont have the time or are just lagging behind because they dont have enough people to work on them, pidgin on the other hand comes with ubuntu by default so it has to work or people would stop using it.I.E. pidgins butt is on the line and has to report to canonicle because its packaged with ubuntu.
Begin Rant
 Therefore Pidgin should have included webcam and voice for those of us who arent using jaunty! Hardy is LTS and deserves to be treated that way, it should always be considered for upgrades to the existing programs before the developmental releases, always period! And whats with the gtalk and msn protocals in pidgin getting cam and voice but not yahoo protocals? I cant believe if I want any of the new features I have to either upgrade to jaunty( which I did and it failed epicly) or wait till 2011 for the new LTS! And then I can only use msn or gtalk of which I dont have accounts for, If i did use those I could just use the Clients that already exist and have those features.
End of Rant, 
So until gyachi can get some more devs to do the work its always gonna lag  behind pidgin, Back to the point , no one finds it odd that i can use webcam and see my friends IMs but they cant see mine in gyachi? Can anyone else test this in their boxes and comfirm? The cn.scs. server worked for the IM problem for about an hour but then I couldnt log in to chat, Then when I rebooted it wouldnt log in at all, so the issue has to be with gyachi and the other third party clients besides pidgin, it is probably the same problem, devs lagging behind on fixes. Its not their fault they can only do what they can do, but Its still annoying isnt it.

---

### Post by mwillams73 on 2009-10-09
Ok so I did a lil searching and just about every messenger except pidgin(for me atleast) will not login under any server, except for gyachi it logs in with the scs. or the scsa. prefixes( and I'll repeat for good measure the cn. prefix works for a lil while then stalls), theres a new messenger called maxium or something like that is supposed to work really well, unfortunately its for intrepid and above.
I tried to do a dirty install of it but I cant find any actuall debs or find it in the repos. Im starting to think that what ever pidgin did to fix their server problems works so the other messengers need to get ahold of the pidgin devs and start figuring this out, atleast for hardy.

Im really starting to think it is yahoo, and they are doing something with the servers again but it still doesnt explain why webcam works in IM and I can recieve IMs but I cant send them, Logicaly if i can send webcam streams through IM then I should also be able to send IMs. I really would like to hear some feed back on this, is any one else able to replicate this? its simple to try, start an IM with someone in gyachi, they wont get it so you should probably call them ahead of time to let them know and try it so you can find out from them directly, then send a webcam invite and wait for them to accept it, I know this works( as in works the way its supposed to,I.E. i can see her and she can see me) as Ive done it with my girlfriend while we we're on the phone. Please let me know what happens, maybe if we work together instead of saying "it doesnt work what do I do?" Then we can fix it ourselves I mean come on there are at least a few hundred of us having this problem if we work together we can do this!

---

### Post by tqft on 2009-10-09
1) Thanks loell 
2) thanks ghosler - you don't see him here but he is the main dev
3) some history - there was a branch of what is now pidgin (then called gaim) that had webcam support years ago but was shutdown by legal action (by AOL I think)
4) latest version of gyachi (pure 32bit) was working yesterday for me as much as it can - private voice conversation is the only thing which is not working, which brings me to 5
5) most of the problems are with yahoo itself (eg obscure private voice protocol) who make a great song and dance about openness and use a lot of open source, but support for a linux chat client - whinge to yahoo.

Check which login protocol you are using and try a different one if the current one isn't working.  Default login server and latest protocol worked for me.

---

### Post by mwillams73 on 2009-10-10
> **tqft said:**
> 1) Thanks loell 
2) thanks ghosler - you don't see him here but he is the main dev
3) some history - there was a branch of what is now pidgin (then called gaim) that had webcam support years ago but was shutdown by legal action (by AOL I think)
4) latest version of gyachi (pure 32bit) was working yesterday for me as much as it can - private voice conversation is the only thing which is not working, which brings me to 5
5) most of the problems are with yahoo itself (eg obscure private voice protocol) who make a great song and dance about openness and use a lot of open source, but support for a linux chat client - whinge to yahoo.

Check which login protocol you are using and try a different one if the current one isn't working.  Default login server and latest protocol worked for me.

Could you be more specific as to exactly which protocols are working for you, Are your sent IMs being received? I'm glad that its working for you but if you're going to post that its working give us some more details so we can get ours working as well. I have tried every server option available in gyachi( incuding the cn. prefix which isn't an option) and I'll repeat this, only the scs. and scsa. prefixes are working for me( but i still cant send IMs) I receive IMs and cam streams but no outgoing IMs actually make it to their destination, I really cant see how thats possible when i use the same server prefix in pidgin and it works fine. Which is the latest protocol? We need this info if we are going to get ours working. 
Oh I did a ping of some of the servers , The cn. prefix takes 300 millisecs while the scs. and scsa. prefixes only take an average of 40 millisecs, could this be why the login with the cn. is timing out? This is certainly odd as the cn. worked for about an hour and then timed out, Of course I could IM with cn. but not go into chat rooms, I really would like some insight as to why this is so difficult, I understand that yahoo is the most likely culprit and yet it seem that it could also be some kind of error within gyachi in conjunction with yahoo. So what can I do to have chat room access and IMs and streaming cam? Right now I use pidgin with the myspace client and gyachi to view my cam, but its a crappy inelegant work around but it works for seeing my daughter and IMing her at the same time while also having access to chat. But that doesnt help those who dont use myspace or have all their friends only on yahoo. I really wish that pidgin devs would have included hardy in their upgrades though and the yahoo voice and chat feature, but I understand that it takes time to get things working, so I really appreciate all the hard work that the gyachi team is doing, I really do! I love gyachi and for a long time it did everything i needed it to do. I wish I was a coder or programmer so I could be of more help, If i knew what I was doing then maybe I could help fix these issues and send the code upstream for the gyachi team.
I know I said in one of my earlier posts that I was getting a mac( which i am) but I'm not giving up on gyachi or ubuntu at all, besides I dont get the mac until january so i have to make due, who knows maybe all this might get worked out by then( I really hope so!) I hate mac osx, not the idea of it but the way it looks and the clunky nonsensical way that it works and the gui ( in my opinion is horrible) I love the color blue but I like being able to change themes and styles, and mac doesnt give me the choice. Well I'll be back with any news and updates soon.

---

### Post by Dr.C on 2009-10-10
Logging into Yahoo! Messenger via a 3rd-party client (such as Gyachi) has become difficult, if not impossible, as the corporation has been incrementally, server-by-server, changing its authentication protocol, phasing out older clients as it does.   Pidgin got on this problem weeks ago and prepared a fix – of course no voice or video support.  

Here is a list of YM servers formerly used.  When I lost Kopete a few weeks ago, I switched from scs.msg.yahoo.com to cn.scs.msg.yahoo.com, thinking incorrectly as it turned out, that, as the latter served Chinese chatters, it would not be soon changed. Both are lost to Kopete – and I think for Gyachi as well.  

scs.msg.yahoo.com
mcs.msg.yahoo.com
scg.msg.yahoo.com
 
scsa.msg.yahoo.com
scsb.msg.yahoo.com
scsc.msg.yahoo.com
scsd.msg.yahoo.com
scse.msg.yahoo.com
scsf.msg.yahoo.com
scsg.msg.yahoo.com
scsh.msg.yahoo.com

cs101.msg.mud.yahoo.com
cs102.msg.mud.yahoo.com

cn.scs.msg.yahoo.com

relay.msg.yahoo.com

vcs.msg.yahoo.com
vcs1.msg.yahoo.com
vcs2.msg.yahoo.com

scs.dcna.msg.yahoo.com
scs.dcnb.msg.yahoo.com

 I don't know which, if any, are still accessible.  


Pax, ~rc

---

### Post by tqft on 2009-10-11
> **mwillams73 said:**
> Could you be more specific as to exactly which protocols are working for you, Are your sent IMs being received?

YMSG-16/Messenger 9   login protocol

scs.msg.yahoo.com   port 5050

IMs - sent and received (occasionally receiving twice)
CAMs - watched and viewed
voice in chat room (I have medibuntu codecs installed)

Karmic Koala 4 October 2009 downloaded

gyachi built from latest cvs

Just logged in and no problem

---

### Post by Tony Flury on 2009-10-11
So how do i change the protocols and servers to be used in Gyachi ??

---

### Post by tqft on 2009-10-11
> **Tony Flury said:**
> So how do i change the protocols and servers to be used in Gyachi ??

Up thread is a list of servers and recommendations - copy and paste

The protocol and port numbers can be changed using the drop down boxes on the login screen.  You may need to go into setup and disable the auto login option so you can play with the settings.

---

### Post by xeddog on 2009-10-11
After not being able to login at all for a couple of days, cn.scs.msg.yahoo.com is working for me again today.  I have only sent/received messages but that is all I have needed.  Don't use a webcam so the only other feature I really use is photo sharing, but have not had the need lately.

xeddog

---

### Post by xeddog on 2009-10-11
btw, the ONLY server that I can use is cn.scs.msg.yahoo.com.  when I select any of the servers that begin with scs... I get several of the errors that say "Could not connect to server: f5.yahoofs.com" in rapid succession and Gyachi goes to lunch.  All of the others I just get a "cannot connect" type of message.

xeddog

---

### Post by xeddog on 2009-10-27
No messages here for two weeks????   Is this thread still alive??

xeddog

---

### Post by loell on 2009-10-28
I don't have any idea as to what might cause the disconnection, couple of weeks ago, Greg and I have some discussion on this, gyachi might have a little difference in implementing the ssl connection from say Pidgin. other than that there was no really concrete solution, lately he's doesn't have time on gyachi development. me on the other is on to other things like web development.

---

### Post by jrandolph on 2009-10-28
None of the messages that i send are being received by the people i send them to
I dont have any idea why

---

### Post by f1nn on 2009-11-02
> **loell said:**
> edited! O:) for your satisfaction. ;)

tol, have you test it on 9.10?

---

### Post by YannBuntu on 2009-11-08
EDIT: I saw you created another thread, so I asked my question there: [http://ubuntuforums.org/showpost.php?p=8270165&postcount=340](http://ubuntuforums.org/showpost.php?p=8270165&postcount=340)

---

### Post by xeddog on 2009-11-14
Is there any progress being made on the login problems that some of us are having?  I can only get logged in using the cn. server.

xeddog

---

### Post by loell on 2009-11-15
> **xeddog said:**
> Is there any progress being made on the login problems that some of us are having?  I can only get logged in using the cn. server.

xeddog

until no one could figure out what's causing it, he couldn't make any fix regarding the problem,

usually, or rather in the past, when i want to advocate a fix for a certain bug, i'd go to great extent describing the problem while posting questions like, why is gyachi doing this? while pidgin is doing that? i'd also list the possible components that might be doing the wrong thing... 

but that's just me though.

---

### Post by inchkape on 2009-11-15
> **xeddog said:**
> Is there any progress being made on the login problems that some of us are having?  I can only get logged in using the cn. server.

xeddog

Still the same here, on one comp i need the "cn" server, on the other the usual server works...at least both work!

---

### Post by xeddog on 2009-11-16
Some of us have been having this problem for a long time and I have described the problem in as much detail as I could in post #549 from Jul 25.   I have also done so on the Gyachi forum on Sourceforge (I think).  Anyway, if there is anything else I can do to help debug this, please let me know.  Also, if I am mis-interpreting what you are saying, please let me know that too.  

xeddog

---

### Post by syafrizal on 2009-11-20
Why suddenly I've got this type of message on my IM windows repeatedly unlimited times?

 ** 'Your buddy image has been offered to the user.' **

And when I look at the Chat tabbed, it always comes up with this message but the url is different:

** 'Your buddy image has been uploaded': [http://f36.yahoofs.com/msgr/PbTpGwPHl8yfqmp2bTQl2g--/.friend_icon.png?msA8HCLBepSN3dd5](http://f36.yahoofs.com/msgr/PbTpGwPHl8yfqmp2bTQl2g--/.friend_icon.png?msA8HCLBepSN3dd5) **

Can anyone explain it to me? Is it something got to do with protocol error?

---

### Post by jrusso2 on 2009-11-20
Is there anyway to get an .rpm that works with Mandriva 2009.1.  The one i found won't login to yahoo.

---

### Post by a.dehqan on 2009-11-25
In The Name Of God The compassionate merciful

Good day everyone ;
How to have voice call with a yahoo user on ubuntu 9.04 ? 
how about webcam ?
Gyache shows webcam here but the other side in chat can not view it  ...

Regards dehqan

---

### Post by Tank Jr on 2009-11-28
Hi everyone,
I am unable to login to Yahoo with GyachEI for any of the servers.
I get an error stating wrong username or password, but I know they are ok, for I can use them to login to the web messenger. Am I missing something here?
I use Karmic, and GyachEi 1.2.2.
I had this problem on Hardy as well, on version 1.1.48.x or something, I dont remember exactly. It used to work like a charm and then one fine morning poof, it was not working any more.

---

### Post by xx58 on 2009-11-29
:rolleyes: I have message **[COLOR=Red] 'Your buddy image has been offered to the user[/COLOR].' ** and it [COLOR=Red]repeating[/COLOR] every 7-8 seconds. I had this kind message before too, but it was only when I start chat and thats it. Now [COLOR=Blue]repeating and repeating[/COLOR] and not ending.[COLOR=DarkGreen] Anybody[/COLOR] have solution??

---

### Post by Airsix on 2009-11-29
> **xx58 said:**
> :rolleyes: I have message **[COLOR=Red] 'Your buddy image has been offered to the user[/COLOR].' ** and it [COLOR=Red]repeating[/COLOR] every 7-8 seconds. I had this kind message before too, but it was only when I start chat and thats it. Now [COLOR=Blue]repeating and repeating[/COLOR] and not ending.[COLOR=DarkGreen] Anybody[/COLOR] have solution??


I get this message, 
it happens when the friend i'm talking to is using the new yahoo messenger release (version 10!) , 
I went to gyachi setup menu, chat and conferences, shows avatar (i unchecked), now it works fine.

edit, the problem is still here, it didn't solve the problem

---

### Post by justborn on 2009-11-30
> **Tank Jr said:**
> Hi everyone,
I am unable to login to Yahoo with GyachEI for any of the servers.
I get an error stating wrong username or password, but I know they are ok, for I can use them to login to the web messenger. Am I missing something here?
I use Karmic, and GyachEi 1.2.2.
I had this problem on Hardy as well, on version 1.1.48.x or something, I dont remember exactly. It used to work like a charm and then one fine morning poof, it was not working any more.

i tried the same version on my karmic too i have the same probo.

pls help

---

### Post by andyshedd on 2009-12-01
how do i install this? i'm on debian lenny i386 and i have 1.22 installed.

---

### Post by andyshedd on 2009-12-02
is the logitech webcam pro 9000 supported by gyachi? i'm getting errors similar to this post [http://ubuntuforums.org/showpost.php?p=4676727&postcount=5]("http://ubuntuforums.org/showpost.php?p=4676727&postcount=5")

---

### Post by stevo1977 on 2009-12-03
I just installed Gyachi by adding the repos from [https://launchpad.net/~loell/+archive/ppa](https://launchpad.net/~loell/+archive/ppa).

When I start it up, it logs me in fine and loads my buddy list.  It then repeatedly pops up a window "Could not connect to server. (IP address)"  where it actually lists an IP.  It just keeps popping up this window and not letting me change any settings.

Any ideas?  Thanks.

---

### Post by purifiedmadness on 2009-12-03
installed the intrepid 64bit one in 9.10 64 webcaming works great no problems connecting, but have not tested audio chat

---

### Post by M J on 2009-12-04
I just installed the same version (intrepid 64) in 9.10, and it works for me too.  Chat did not work, but I'm not sure if it was me or the person on the other end.  Cam worked fine.

---

### Post by gradinaruvasile on 2009-12-04
I dont know if chat works one to one. It seems that it works only in chatrooms with more than 10 (?) people.

---

### Post by purifiedmadness on 2009-12-04
the only peoblems i seem to be having is the captcha to get into chatrooms sometimes it just doesnt work. not that i really care.

---

### Post by justborn on 2009-12-08
i'm on Karmic,i installed the latest version of Gyache-Improved v1.2.2 from the loell repos.webcam chat works,thats not a probo.

but voice chat doesn't,i did install the voicecaht -plugin also ,but still it doesn't .i tried sending and receiving voice chat invitation,it jus dosen't work.i get the [COLOR="Red"]VOICE ENABLED[/COLOR]notification on the screen but it does no good.

and instead of receiving voice from the other end ,they are packed into voice-mails and i get it in ma mailbox.(tried with different users [COLOR="Magenta"]<who use YM! 8&9>[/COLOR] on the other end,so i am sure the know how to voice chat.)

do i need someother plugin(s)or encoder/decoder essentials?

---

### Post by xeddog on 2009-12-11
Loell - 

I have been playing with Ubuntu Karmic 64-bit and see from your first entry in this thread that for 64-bit we are supposed to get version 1.1.48.  If I remember right, Yahoo made some changes to the login that required version 1.2.xx or later.  (I really don't want to go through all of the entries in this thread to confirm.  Sorry about that.)  Anyway, what is the latest version of Gyachi for 64-bit Karmic?

Thanks,

xeddog


P.S.  I have updated the sources for 64-bit Karmic to include your PPA, but I don't think I am getting any of the latest "stuff" from it.  I downloaded and installed version 1.2.1 but I see a lot of people running 1.2.2 and 1.2.2-1.

---

### Post by loell on 2009-12-12
there is no 64 bit karmic, i tried building but it failed, multiple times, really needs to investigate why, you can still download the 64 bit jaunty build though. still works with karmic.

---

### Post by mathew-dong on 2009-12-12
glad to be of service

---

### Post by xeddog on 2009-12-12
[SIZE="1"]Here is something that may be interesting.  For the past few months I have been having problems loggin into Yahoo with Gyachi.  The only server that I have been able to use was cn.scs.msg.yahoo.com.  Any other server I have tried has caused a flood of error messages, would hang Gyahci for several minutes, and NOT log in.  I have been trying to change to scs.msg.yahoo.com about every two weeks or so and I have not had any success.  UNTIL YESTERDAY.  For two days now I have been able to login to the "normal" server without any problems.  I sure hope it stays that way.

xeddog[/SIZE]

---

### Post by justborn on 2009-12-13
> **justborn said:**
> i'm on Karmic,i installed the latest version of Gyache-Improved v1.2.2 from the loell repos.webcam chat works,thats not a probo.

but voice chat doesn't,i did install the voicecaht -plugin also ,but still it doesn't .i tried sending and receiving voice chat invitation,it jus dosen't work.i get the [COLOR="Red"]VOICE ENABLED[/COLOR]notification on the screen but it does no good.

and instead of receiving voice from the other end ,they are packed into voice-mails and i get it in ma mailbox.(tried with different users [COLOR="Magenta"]<who use YM! 8&9>[/COLOR] on the other end,so i am sure the know how to voice chat.)

do i need someother plugin(s)or encoder/decoder essentials?

i did replace the voicechat plugin ,wid jus win32 codecs,and also tried both alsa and pulse-audio setting ,but nothing works,help me.....


if GyachI had proper documentation,i would have had ma way by now.

---

### Post by loell on 2009-12-14
voice chat only works in rooms, could you be looking for 
(Yahoo Voice)TM and not Voice chat?

---

### Post by justborn on 2009-12-14
> **loell said:**
> voice chat only works in rooms, could you be looking for 
(Yahoo Voice)TM and not Voice chat?

i know that,and i tried it in rooms only wid 10+ ppl.

---

### Post by justborn on 2009-12-14
loell,jus reminding u.

v4l2 is already complied for karmic ppa packages,but there is no documentation abt that too(not even a small note),neither on the gyachi homepage or on launchpad.

---

### Post by loell on 2009-12-15
> **justborn said:**
> loell,jus reminding u.

v4l2 is already complied for karmic ppa packages,but there is no documentation abt that too(not even a small note),neither on the gyachi homepage or on launchpad.

where? it's  not probably on my PPA,  gyachi is built with libv4l by default.

---

### Post by xeddog on 2009-12-15
Well, it was good while it lasted.  I had 4 days of being able to use scs.msg.yahoo.com, but today I am unable to login to it again.  I guess I will have to start using a different IM client.  :-(

xeddog

---

### Post by t12121 on 2009-12-17
> **xeddog said:**
> Well, it was good while it lasted.  I had 4 days of being able to use scs.msg.yahoo.com, but today I am unable to login to it again.  I guess I will have to start using a different IM client.  :-(

xeddog

I am able to connect and recieve messages but I cannot send out messages.  With gyachi.  I am using 1.1.48 but that is due to I am on 8.04.  I like the program but if I am unable to use it I guess I will have to use pidgin.  Which I am able to send and recieve just fine.

---

### Post by ReisceakaLP on 2009-12-18
Im trying to install it but I get

~$ sudo apt-get install gyachi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gyachi

I had saved it to my Home Folder. Where should it go? Im using Ubuntu 9.04

---

### Post by NT4usB on 2009-12-18
It's a .deb file, isn't it?
You ought to be able to right click on it and install, or open with package manager, or something along those lines.
(not in front of a Linux box atm...)

---

### Post by andyshedd on 2009-12-20
i'm reiterating my problems getting the logitech webcam pro 9000 to work under debian lenny i386 and applying the patch to 1.22 in debian and also adding that i'm not able to get the signing key in ubuntu karmic. requesting it in terminal times out and i can't access its webpage from your ppa webpage.

---

### Post by DemonSharkKisame on 2010-01-04
*sigh* wish I'd known not to put "@yahoo.com" at the end of my username before trying to log in... just installed GyachI, and now I can't figure out how to stop it from logging in and out constantly... I think it's because I can't figure out how to change my login information... please help, this is EXTREMELY frustrating!

---

### Post by loell on 2010-01-04
maybe there two gyachi processes which keeps logging in and out, look at the icon tray if there are two gyachi icons.

---

### Post by DemonSharkKisame on 2010-01-04
No, it's just one process... is there any way for me to get to my login information and change it so GYachI doesn't automatically try to log me in? (I'm using version 1.2.2 on Ubuntu 9.10, if this helps). Also, I'm using my "default" account, and the Edit My Accounts window will not let me change how I log in...

---

### Post by loell on 2010-01-04
you can change the username, but the password is encrypted.
at **~/.yahoorc/gyach/gyachrc**


though you could disable the auto login
try killing gyachi
```
killall gyachi
```
then edit 
```
gedit ~/.yahoorc/gyach/gyachrc
```
set **auto_login** to **0**
then start gyachi to change the login account.

---

### Post by DemonSharkKisame on 2010-01-04
Thank you! It worked like a charm! :)

---

### Post by inchkape on 2010-01-05
> **loell said:**
> you can change the username, but the password is encrypted.
at **~/.yahoorc/gyach/gyachrc**


though you could disable the auto login
try killing gyachi
```
killall gyachi
```
then edit 
```
gedit ~/.yahoorc/gyach/gyachrc
```
set **auto_login** to **0**
then start gyachi to change the login account.

Good one Loell! I had the same problem ages ago, but my fix was more brutal - I deleted the .yahoorc :P

---

### Post by outc4st on 2010-01-22
So after days of deliberation and constant googling i've resolved to the forums and i'm hoping someone can help me... running ubuntu intrepid on an old dell inspiron e1405 and i finally got everything working the way i want it to...except gyachi that is... im running v. 1.2.1 and am having voice issues i login to the room and can chat away... sometimes i have to play with the servers i log in to to get chat and instant messaging but hey no big deal... now heres my problem i start voice chat and the window loads up fine... pick a server click on and nothing happens... doesnt matter what server i try nothing happens i click off and the window goes dark and i have to force quit it... any help guys???  im kind of a newbie to ubuntu but pretty advanced as far as computers themselves go any suggestions would be great thanks in advance

---

### Post by tqft on 2010-01-22
Sometimes you have to leave the room and come back in as yahoo has reset something somewhere when voice just won't work in the room.

---

### Post by outc4st on 2010-01-22
i try to leave and rejoin ive tried restarting gyachi in general still to no avail :( i really like gyachi the only way ive been able to get voice though is to load yahelite through wine with a different account as the interface sucks!!! really a pain in the *** too... oh well maybe i will be stuck doing it this way

---

### Post by bjorkiii on 2010-02-05
Problem :confused: im trying to sign in on my reg id its saying wrong name or password but i use exactly same name and password on another client and its working fine ? lets me sign into mail and chat through browser so i know name and password is fine. Anyone got any idea's?

---

### Post by zouriel on 2010-02-05
Looks like there is an issue logging into gyachi using a rocket mail account.  I have a yahoo and rocketmail account same password.. try rocketmail with and without @rocketmail and it doenst work change user to the yahoo account works peachy... retyped password when at rocketmail name and still no love...

---

### Post by loell on 2010-02-05
yesterday i had issues logging in, but it seemed to have resolved itself, if it's persistent,

try removing gyachrc in   /.yahoorc/gyach/  directory.

---

### Post by bjorkiii on 2010-02-06
Done what you said and still no luck :( not to worry i'll just have to use another client for now.

---

### Post by zouriel on 2010-02-06
Did the same .... Im going to roll back client to the last version... didnt start happening to version 1.2.3

---

### Post by bjorkiii on 2010-02-06
I tried that as well but its still playing up :p

---

### Post by crjackson on 2010-02-06
Hello loell,

It's been a long time since I posted here.  I helped swat a bug a while back and you wrote a script for me that allowed video capture.

Anyway, I have a friend that wants me to grab a good quality web cam for his Jaunty install that works well with Gyachi.  Any suggestions?

Now, I've just installed Gyachi from your PPA and having strange issues.  logon / logoff  logon / logoff  and it goes on endlessly..
Can you help?
View the Video [http://www.facebook.com/profile.php?v=app_2392950137&ref=profile&id=1581353997#!/video/video.php?v=1278731580000]("http://www.facebook.com/profile.php?v=app_2392950137&ref=profile&id=1581353997#!/video/video.php?v=1278731580000")

---

### Post by loell on 2010-02-06
yeah there's a gyachi-wide problem  atm, where gyachi couldn't find the yahoo crumb or something like that, still waiting for the developer's response.

---

### Post by loell on 2010-02-07
there is now a fix, it's  v 1.2.4

if you're in karmic, use this PPA repo

[https://launchpad.net/~baudm/+archive/ppa/+packages](https://launchpad.net/~baudm/+archive/ppa/+packages)

or just  **sudo add-apt-repository ppa:baudm**

---

### Post by crjackson on 2010-02-07
> **loell said:**
> there is now a fix, it's  v 1.2.4

if you're in karmic, use this PPA repo

[https://launchpad.net/~baudm/+archive/ppa/+packages](https://launchpad.net/~baudm/+archive/ppa/+packages)

or just  **sudo add-apt-repository ppa:baudm**

Okay I did and it seems to have fixed the problem.  I have another problem however.  It won't show an image from my Phillips 900N cam anymore.  It seems to default to VL1 and I think I need VL2 but it won't let me change it.  It locks up and I have to force quit it.  I don't have this problem on my HP laptop webcam.  

Suggestion?

---

### Post by kung fu buntu on 2010-02-08
> **loell said:**
> there is now a fix, it's  v 1.2.4

if you're in karmic, use this PPA repo

[https://launchpad.net/~baudm/+archive/ppa/+packages](https://launchpad.net/~baudm/+archive/ppa/+packages)

or just  **sudo add-apt-repository ppa:baudm**
I haven't update my gyachi version for a looooooooong time since I had made some tweaks in the code for my convinience.

But I've noticed in this version that the buddy images don't show up on the right side of the PM window like they did previously. Am I the only one with this problem?

---

### Post by rayliam on 2010-02-08
> **loell said:**
> there is now a fix, it's  v 1.2.4

if you're in karmic, use this PPA repo

[https://launchpad.net/~baudm/+archive/ppa/+packages](https://launchpad.net/~baudm/+archive/ppa/+packages)

or just  **sudo add-apt-repository ppa:baudm**
Will there be an update for Jaunty?

---

### Post by crjackson on 2010-02-08
loell,

It seems I faulted Gyachi wrongly.  I unplugged my cam to took it to one of my other 9.10 'puters and it works fine.  I have borked my main system somehow (and it's a fairly new install).

I tested and I can't pull in ANY video from the cam using any apps.  It was working just fine a couple of weeks ago with cheese and others, but now nothing.

Any clue how to star trouble shooting this?  I really don't want to reinstall if I can get around it.

TIA

PS, can you throw those mencoder commands at me again please.  This version looks like it's been re-enabled.  It captured perfectly and I'd like to make use of it.  Thanks.

---

### Post by tankboy138 on 2010-02-09
i've downloaded and installed GYachE Improved v.1.2.1 on Ubuntu 8.1.. Everytime I try to login, it says that I have an incorrect username/password. I've checked, double checked, and triple checked my login info and even logged in to Yahoo.com with the info and it worked there. Any advice? I've Tried Pidgin (same problem) and Kopete (same problem)

---

### Post by needhelppeeps on 2010-02-09
Empathy works fine, but gyachi on ubuntu no longer works with certain passwords for some reason even though yahoo IM and the webmail work fine (so it's not a yahoo issue). On the same machines with diff userid/passwords gyachi still works. I would consider the package somewhat broken currently and suggest you try to find other means of connecting.

---

### Post by loell on 2010-02-09
> **crjackson said:**
> loell,

It seems I faulted Gyachi wrongly.  I unplugged my cam to took it to one of my other 9.10 'puters and it works fine.  I have borked my main system somehow (and it's a fairly new install).

I tested and I can't pull in ANY video from the cam using any apps.  It was working just fine a couple of weeks ago with cheese and others, but now nothing.

Any clue how to star trouble shooting this?  I really don't want to reinstall if I can get around it.

TIA

PS, can you throw those mencoder commands at me again please.  This version looks like it's been re-enabled.  It captured perfectly and I'd like to make use of it.  Thanks.

probably a module that handles your webcam had berserk with that machine, or something had trip off somewhere, module related.

do you still have the python script, i gave you, probably a year ago? i still have to sort through my scripts, see if it's their or on another disk that i already detached, i'll just let you know.

---

### Post by Tank Jr on 2010-02-09
> **needhelppeeps said:**
> Empathy works fine, but gyachi on ubuntu no longer works with certain passwords for some reason even though yahoo IM and the webmail work fine (so it's not a yahoo issue). On the same machines with diff userid/passwords gyachi still works. I would consider the package somewhat broken currently and suggest you try to find other means of connecting.

Now who would have thought that.... :D

I changed my password and I realize that it was the special character that was doing funny things.

Thanks a ton.

---

### Post by crjackson on 2010-02-10
> **loell said:**
> probably a module that handles your webcam had berserk with that machine, or something had trip off somewhere, module related.

do you still have the python script, i gave you, probably a year ago? i still have to sort through my scripts, see if it's their or on another disk that i already detached, i'll just let you know.

I'm looking for the script.  Everything has been upgraded since then so I'm not sure.  I've got 12 machines to search through.

---

### Post by stevo1977 on 2010-02-10
Hey, guys.  I'm trying to encode the captured .jpg's from my webcam.  I posted the script I think you guys were looking for, but it doesn't seem to be working for me.  I ran it in the terminal to see the problems, but I'm not sure what it means.

Any help would be most appreciated.  Thanks.

Cheers,
stevo

---

### Post by kung fu buntu on 2010-02-11
Is anyone else experiencing problems with the users buddy images?

When you start a private message with a buddy, does it always shows their buddy image?

---

### Post by sports fan Matt on 2010-02-12
This fix works excellently:)

---

### Post by loell on 2010-02-13
> **stevo1977 said:**
> Hey, guys.  I'm trying to encode the captured .jpg's from my webcam. 

here is the url of the working script.

[http://gyachi.cvs.sourceforge.net/viewvc/*checkout*/gyachi/gyachi/webcam/gyachi-encoder.py?revision=2.4](http://gyachi.cvs.sourceforge.net/viewvc/*checkout*/gyachi/gyachi/webcam/gyachi-encoder.py?revision=2.4)

you'll be needing **mencoder** package for the actual encoding.

---

### Post by kung fu buntu on 2010-02-14
I repeat my question since I had no feedback:
> **kung fu buntu said:**
> Is anyone else experiencing problems with the users buddy images?

When you start a private message with a buddy, does it always shows their buddy image?

---

### Post by rayliam on 2010-02-14
Will there or will there not be an update for Jaunty in the PPA package repositories for Gyachi for 1.2.4? It's a shame to have to re-install Linux just to have the ability to use Yahoo with webcam support. I'm using a EEEbuntu distro that's Jaunty based and I'm waiting for the EEEbuntu 4.0 that's still in beta at the moment which is not based on ubuntu from what I understand. I tried compling Gyachi 1.2.4 from sourceforge and could not get it to work. Just for the heck of it I tried installing gyachi 1.2.4 for karmic and of course that also didn't work. Thanks for all your help.

---

### Post by taladan on 2010-02-17
Okay, I've returned to trying Gyachi out after several years, hoping that the development would bring it somewhat farther along.  I must say so far I like what I see, but I also want to report a bug.

In Gyachi Voice Chat (in a room) I am unable to hear anything.  When I attempt to click 'off' it freezes the voice chat window completely and I have to force it to close/terminate.  Also, the 'talk' button is completely greyed out.  I've tried switching from Alsa to Pulseaudio with no luck, tried restarting gyachi between switches, no luck, and I've tried looking through debug logs and can see no errors that would explain this (even after checking the log debug checkbox).  

I'm currently on Jaunty running 2.6.28-11-generic kernel.

What am I missing here?

Thanks in advance for your help,

Tal

---

### Post by taladan on 2010-02-17
Alright, I figured out how to get around this issue.

The issue with no sound in gyachi (and freezing of the gyachi-voice) client is solved by actually being able to connect to one of the correct voice servers.  The ones in the list apparently are incorrect.  The ones listed in the old gyach-e website appear to work however.  For ease of configuration, I'll c/p it.  You need to go into ~/.yahoo/gyach/gyvoicerc and change the default voice server to one of the following (as well as ensuring that you have the gyachi-voice codecs installed).

```

Reference: List of Known Y! Voice Chat Servers:

66.218.70.32  # v1.vc.scd.yahoo.com
66.218.70.33
66.218.70.34
66.218.70.35
66.218.70.36
66.218.70.37  # v6.vc.scd.yahoo.com
66.218.70.38
66.218.70.39
66.218.70.40
66.218.70.41
66.218.70.42
66.218.70.43
66.218.70.44  
66.218.70.45 
66.218.70.46  
66.218.70.47  # v14.vc.scd.yahoo.com
	# Below are servers we usually get forwarded to,
	# but most of these can also be used for 
	# initial connections
216.109.118.144   # v1.vc.dcn.yahoo.com
216.109.118.145   # v2.vc.dcn.yahoo.com
216.109.118.146
216.109.118.147 
216.109.118.148 
216.109.118.149 
216.109.118.150 
216.109.118.151 
216.109.118.152 
	# The following 'rsvd' servers exist but do
	# not appear to currently accept connections	
#  216.109.118.153  # rsvd-153.vc.dcn.yahoo.com, 'reserved'
#  216.109.118.154  # rsvd-154.vc.dcn.yahoo.com, 'reserved'
#  216.109.118.155  # rsvd-155.vc.dcn.yahoo.com, 'reserved'
#  216.109.118.156  # rsvd-156.vc.dcn.yahoo.com, 'reserved'
#  216.109.118.157  # rsvd-157.vc.dcn.yahoo.com, 'reserved'
#  216.109.118.158  # rsvd-158.vc.dcn.yahoo.com, 'reserved'

216.109.118.159   # vc1.vc.vip.dcn.yahoo.com
68.142.226.64   # v1.vc.re2.yahoo.com
68.142.226.65
68.142.226.66
68.142.226.67
68.142.226.68
68.142.226.69   # v6.vc.re2.yahoo.com
68.142.226.70
68.142.226.71
68.142.226.72   # v9.vc.re2.yahoo.com
68.142.226.73   # vc1.vc.vip.re2.yahoo.com

```

Hope this helps someone else.

Tal

---

### Post by taladan on 2010-02-17
Alright, next problem is when I try to run webcam.  The window pops up, freezes there for a sec then closes down.  The cam's little light comes on at the same time and goes off when the window goes down.  Again checked debug log and got nothing at all whatsoever about the cam (wondering what exactly the debug function in gyachi debugs if it's not the stuff it's trying to do).  Checked lsusb and the cam shows up there correctly (cheap little webcam I had in a box). And I checked dmesg on the off chance that it might show something.  Found this:

gyachi-upload[4627]: segfault at 4b7c3e49 ip b789a302 sp bfc971f0 error 4 in libgobject-2.0.so.0.2000.1[b7871000+3c000]


Gonna try and research that but I'm not holding my breath.  System specs still the same as before.

Tal

---

### Post by taladan on 2010-02-17
well...I /thought/ I had voicechat fixed.  Worked for a little while then started doing the same thing again, so I'm not sure exactly what's causing it.

And webcam still isn't working but I'm thinking it's this old cam.

Tal

---

### Post by loell on 2010-02-17
has the webcam worked in other applications, recently?

---

### Post by Achayaan on 2010-02-18
I am really happy with Gyachi , after waiting long time at last its working now . But i have one issue , I can send my webcam and others can view it also . But if i am trying to watch others webcam nothing happening . I am using [https://launchpad.net/~baudm/+archive/ppa/+packages](https://launchpad.net/~baudm/+archive/ppa/+packages) this one .

Any one know why its happening like this ?? . Do I need to enable something ?? :KS

Thanks

Achayan

---

### Post by taladan on 2010-02-19
loell - I figured out the problem with the webcam.  It was a problem with the webcam itself.

The Voice Chat in a chatroom still is /really/ hit & miss.  90% of the time it doesn't work right...won't connect up or load the list or anything.  Only about 1 time out of every 15 or 20 times that I try to connect to a voicechat does it actually work, but it only works for a few minutes and then stops.  So I'm not sure what's going on there.

I'm hoping that these issues can be resolved because...well...I hate to be defeated by any piece of software.

Tal

---

### Post by crjackson on 2010-02-19
loell,

I purchased an HP Pro webcam for a friend of mine (about 1500 miles away) and tested it with a live cd of Jaunty.  It worked well so I sent it out.

Cheese works fine, aMSN works fine.  He had Gyachi 1.23 and got nothing out of the webcam.

I had him add the karmic source and he managed to use that PPA to install 1.24.  Still nothing.

He booted into windows and used the webcam.  Then back into Jaunty and was able to view himself using Gyachi, but no one else could (it said cam was not connected, yet he could see himself).

He then changed the setting from V4L1 to V4L2 and now he can't even get the window to stay open.  It blinks and for a brief moment, his cam icon will show in MY buddy list.

How can I get this thing to go back to V4L1?  How can I get a proper DEB for Jaunty?

Neither of us can compile code, we're both too stupid for that.  Any help would be much appreciated.  He is a Yahoo chat junkie (very old lonely guy) and wants this super bad.

Please help

---

### Post by loell on 2010-02-20
would you know what webcam driver is that hp webcam using?

```
lsmod | grep videodev 
```

---

### Post by crjackson on 2010-02-20
> **loell said:**
> would you know what webcam driver is that hp webcam using?

```
lsmod | grep videodev 
```

I'll call him tonight and post the results after he gets them.

---

### Post by crjackson on 2010-02-21
> **loell said:**
> would you know what webcam driver is that hp webcam using?

```
lsmod | grep videodev 
```

```
israel@israel-desktop:~$ lsmod | grep videodev
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
israel@israel-desktop:~$ 
```

This is getting really frustrating.  I had him purge Gyachi and remove the .yahoorc folder.  Then I had him reinstall from the loell PPA.  

The webcam works fine with cheese and aMSN.  With Gyachi, the webcam will blink on and then the window closes with no video broadcasting.

I tried pidgin and empathy which both show cam options, but they are greyed out and don't work.

What can I do to make this HP Pro webcam work with Gyachi?

---

### Post by loell on 2010-02-21
you can have him preload v4l1  as a last attempt,
if it doesn't work, then just probably let him use windows.
```
 LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so gyachi
```

---

### Post by crjackson on 2010-02-22
> **loell said:**
> you can have him preload v4l1  as a last attempt,
if it doesn't work, then just probably let him use windows.
```
 LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so gyachi
```

I'll send this along and give it a try.  If it doesn't work I hope that doesn't mean I must give up.  If the camera works in Ubuntu and other linux video applications there should be a way to make it work in Gyachi shouldn't there?

---

### Post by crjackson on 2010-02-22
UPDATE:

Okay, we did make some progress today. After changing the webcamrc file to load **V4L1** and **REBOOTING** his cam started to broadcast. The issue at hand now is that when he views someone else, his cam then stops and vice versa. It seems it won't let him broadcast and view at the same time.

Any ideas?

---

### Post by loell on 2010-02-22
> **crjackson said:**
> UPDATE:
Any ideas?

the webcam viewer and the webcam uploader are two separate processes, they even use different components (libraries) to do their purposes.

theoretically though, the webcam viewer should always work because it only receives streams of images which then the viewer decodes and renders. if it doesn't work (on some occasions maybe ) it's probably yahoo's doing, or the bandwidth? is probably not enough, this is just me shooting in the dark.

the webcam uploader however is different, for quite sometime now gyachi  uses the libv4l library to detect and use webcam devices,

now cheese is also probably using libv4l library, what gyachi is not aware though, if cheese is doing something extra to detect that particular webcam or gyachi may have miss something on it's libv4l interface.

---

### Post by crjackson on 2010-02-22
> **loell said:**
> the webcam viewer and the webcam uploader are two separate processes, they even use different components (libraries) to do their purposes.

theoretically though, the webcam viewer should always work because it only receives streams of images which then the viewer decodes and renders. if it doesn't work (on some occasions maybe ) it's probably yahoo's doing, or the bandwidth? is probably not enough, this is just me shooting in the dark.

the webcam uploader however is different, for quite sometime now gyachi  uses the libv4l library to detect and use webcam devices,

now cheese is also probably using libv4l library, what gyachi is not aware though, if cheese is doing something extra to detect that particular webcam or gyachi may have miss something on it's libv4l interface.

Well, at least progress is being made.  I thought about the bandwidth issued too, but it really didn't at up to me.  The reason I don't think it's bandwidth is because aMSN doesn't have that issue at all.  It works great.  Also booting to winxp and using yahoo doesn't exhibit that problem either.

Something isn't quite right just yet.  I would love to try the 1.2.5 version on the Jaunty system but I don't know how to build packages.  I wouldn't mind installing Jaunty on my system just to get it done, but I've never been able to successfully compile anything.

---

### Post by xeddog on 2010-02-23
I must really be doing something wrong here, but I am trying to get the latest Gyachi to see if it takes care of my login problems.  When I go here:   [https://launchpad.net/~baudm/+archive/ppa/+packages]("https://launchpad.net/~baudm/+archive/ppa/+packages") and download what I think is the right file for my Ubuntu Karmic 64-bit, the deb installer gives me this:  > Error: Dependency is not satisfiable: gyachi-data (= 1.2.5-0.1~baudm1)

How do I get this?

Thanks,

xeddog

---

### Post by loell on 2010-02-23
there is also a gyachi-data.deb in that repo.

---

### Post by xeddog on 2010-02-23
Thanks Loell, I now have 1.2.5 installed but unfortunately it does not solve my login problem which may be unique.  Whenever my daughter is logged into her Yahoo IM account, it throws Gyachi into a caniption fit and I cannot get logged in unless I use the server cn.scs.msg.yahoo.com.  No other server that I have tried will work, and I have tried many of them.  If she is not logged in or if I remove her as a buddy, I can use whatever server I want.  

I don't know how this is working at all for her, but someone has her exact same Yahoo id, and she is running into a brick wall trying to get it resolved.

Xeddog

---

### Post by crjackson on 2010-02-23
loell,

I have downloaded the .deb files for 1.2.5 that were intended for Karmic.  Will these debs install under Jaunty?

---

### Post by loell on 2010-02-24
> **crjackson said:**
> loell,

I have downloaded the .deb files for 1.2.5 that were intended for Karmic.  Will these debs install under Jaunty?

as far as I know, most possibly Yes. :)

---

### Post by crjackson on 2010-02-24
Okay,  I'll give this a shot in a day or so and let you know how it went.

If anyone else wants to download the debs, go to the webpage below.


[[SIZE="4"]**[COLOR="Blue"]http://home.roadrunner.com/~crjackson/gyachi/[/COLOR]**[/SIZE]]("http://home.roadrunner.com/~crjackson/gyachi/")

---

### Post by tartanraven on 2010-04-20
Bloody hell!  I'm using Lynx Beta 2, and everything is grand...cam works, but voice isnt.  Same stuff as before, interface works, but when you click ON, it freezes.  This happens with both sound servers, and any of the voice addresses.  I've had the same issues with Sabayon, and Ubuntu Karmic.

---

### Post by Nick_Jinn on 2010-05-19
Can anyone help me install this in 10.04 or in Mint-9 for my mom?

---

### Post by Nick_Jinn on 2010-05-19
I got this installed ok after downloading (In Mint) the 'factory settings'....basically it will restore all the apps that your system came with without having to reinstall....pretty nifty. Is this also on Ubuntu?


So far I got some noises but I dont know if anyone was using voice chat or not.



Woul anyone be willing to help me out? I need someone with a webcam who can tell me whether i am broadcasting, or help me see if i can receive.....just an image of a blank wall would be just fine, as long as its an image.

---

### Post by inchkape on 2010-05-19
> **Nick_Jinn said:**
> I got this installed ok after downloading (In Mint) the 'factory settings'....basically it will restore all the apps that your system came with without having to reinstall....pretty nifty. Is this also on Ubuntu?


So far I got some noises but I dont know if anyone was using voice chat or not.



Woul anyone be willing to help me out? I need someone with a webcam who can tell me whether i am broadcasting, or help me see if i can receive.....just an image of a blank wall would be just fine, as long as its an image.

Hi Nick,

This backup tool is a Linux Mint specific one I believe (I'm using it to do a backup as I write this).
I'd be happy to help you try out your cam and sound if we can sort out the timing. Personally I never tried to use the sound. Send me a private message with your nickname on Y and we'll have a go.

---

### Post by Nick_Jinn on 2010-05-20
Well three cheers for mint. Trying to screw around with this manually, trying to figuring out which dependency is incompatible in the past would have made me too frustrated and forced me to do a clean install from scratch....I almost considered it until I stumbled on the backup tool.....you download it just like a program in the software manager and it restores all the default programs and drivers without getting rid of anything else not involved.

I am really happy that somebody had the good sense to think about this :)

Maybe Ubuntu should copy some of the innovations found in Mint.

---

### Post by g.oostema on 2010-05-25
hey guys,
i got gyachi and it works fine, besides the occasional errors.
Only 2 problems i have.

1. the screen is 5 times wider then my display, meaning i can never see the scrollbar etc on the right side. little irritating but not life threatening.

2. i can start my cam and invite others, they seem to be connected but the timer does not run. the cam stops after being like that for a couple of seconds. can watch other peoples cam though. not sure what it the problem.

hope you guys can help me.

tnx

---

### Post by ubu_lin on 2010-08-01
hello everybody, I m new to linux world. I had installed ubuntu 10.04 lucid_desktop_i368. now i want to install Gyachi, Please anyone help me where to get ppa for latest version of gyachi on my 32 bit ubuntu lucid, thank you.

---

### Post by ChadMMc on 2010-08-01
> **ubu_lin said:**
> hello everybody, I m new to linux world. I had installed ubuntu 10.04 lucid_desktop_i368. now i want to install Gyachi, Please anyone help me where to get ppa for latest version of gyachi on my 32 bit ubuntu lucid, thank you.


I have the lLucid on my old P4 system and have gyachi installed through
[http://ppa.launchpad.net/baudm/ppa/ubuntu](http://ppa.launchpad.net/baudm/ppa/ubuntu)

HOpe this helps.

---

### Post by Nick_Jinn on 2010-08-01
Why isnt this awesome app in Synaptic yet?

When is somebody going to write a deb file for this?

---

### Post by ubu_lin on 2010-08-01
> **ChadMMc said:**
> I have the lLucid on my old P4 system and have gyachi installed through
[http://ppa.launchpad.net/baudm/ppa/ubuntu](http://ppa.launchpad.net/baudm/ppa/ubuntu)
 
HOpe this helps.
 
thankyou for reply, I also dont know how to install from this link, can anyone help me plz ..

---

### Post by Sef on 2010-08-01
To install gyachi from [loell's PPA]("https://launchpad.net/~loell/+archive/ppa?field.series_filter="):

Applications > Accessories > Terminal 

then copy and paste this code:

```
sudo add-apt-repository ppa:loell/ppa

```

once that is done then copy and paste in this code:

```
sudo apt-get update

```

---

### Post by ChadMMc on 2010-08-01
I have had problems with the loell ppa being down a lot of times. (usually when doing updates).  I had found the baudm one to be up all the time.

---

### Post by ubu_lin on 2010-08-01
> **Sef said:**
> To install gyachi from [loell's PPA]("https://launchpad.net/~loell/+archive/ppa?field.series_filter="):
 
Applications > Accessories > Terminal 
 
then copy and paste this code:
 
```
sudo add-apt-repository ppa:loell/ppa

```
 
once that is done then copy and paste in this code:
 
```
sudo apt-get update

```
 
I dont know exactly, but on visiting loell's PPA page, it says gyachi build failed for lucid i386 version.
It means, only option for me is ppa:baudm/ppa ?
thankyou for giving me installation details.

---

### Post by Gregory_NZL on 2010-08-07
> **Sef said:**
> To install gyachi from [loell's PPA]("https://launchpad.net/~loell/+archive/ppa?field.series_filter="):

Applications > Accessories > Terminal 

then copy and paste this code:

```
sudo add-apt-repository ppa:loell/ppa

```

once that is done then copy and paste in this code:

```
sudo apt-get update

```

Hi I tried the above instructions but when I attempt to install the ppa I get the following error. I am running **10.04 64bit**. Do you guys have any ideas?

```
gregory@gregory-desktop:~$ sudo apt-get install gyachi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gyachi: Depends: gyachi-data (= 1.2.9-0.1~lucid1) but it is not installable
E: Broken packages
gregory@gregory-desktop:~$ 

```

---

### Post by pezball on 2010-08-10
I am also running 10.04 64-bit, and get the same error about the **gyachi-data** package missing... Synaptic shows only gyachi and gyachi-dbg, so clearly the gyachi-data is not there...

If I change from lucid to karmic repo, the gyachi-data is available, so I guess the problem is that Loell has forgotten to add that package in the lucid repo... #-o

The karmic version should work very well for 10.04, it's probably more or less the same ;) so that's a temporary solution to this issue...

---

### Post by stalkingwolf on 2010-08-10
I have installed it on two systems running 9.10 Super OS.  text part works fine.

Web cam doesnt.  Can see the cam on host system  but not broadcasting.

get the invitation click yes and nothing.

Any ideas?

---

### Post by maddbaron on 2010-08-28
> **stalkingwolf said:**
> I have installed it on two systems running 9.10 Super OS.  text part works fine.

Web cam doesnt.  Can see the cam on host system  but not broadcasting.

get the invitation click yes and nothing.

Any ideas?

same problem, did u get yours resolved? if so, how?

---

### Post by stalkingwolf on 2010-09-07
yes I did using CLI and the following

```
sudo add-apt-repository ppa: loell/ppa

sudo apt-get update

sudo apt-get install gyachi.
```


I have used this from the terminal and from the command prompt in the recovery and it works great for me.

ymmv.


as a word of caution, there is a virus coming through yahoo messenger that is a particularily bad one.   it come as an im and starts is this your picture.    it will effect linux.

---

### Post by stanz on 2010-10-08
good day....
I'm trying for gyachi also, and still...
```
The following packages have unmet dependencies:
 gyachi: Depends: gyachi-data (= 1.2.9-0.1~lucid1) but it is not installable
E: Broken packages
```something one can do to help??

do we need the period after?
> sudo apt-get install gyach[COLOR=Black]i[/COLOR][COLOR=Black].[/COLOR]
I don't think so....but ask.

I'm on 64bit also.

---

### Post by mahmoodkamal on 2010-10-09
how can i install gyachi for lucid? please help

---

### Post by xeddog on 2010-10-23
Just to let someone know that there is at least one person that is anxiously awaiting a deb for 64-bit Maverick.  :)

Wayne

---

### Post by xx58 on 2010-10-30
:rolleyes:My problem are next: When I chat, then I receive message and about 5-6 seconds I receive this message again. So everything work nicely, only messages receiving double. Anybody can help?

---

### Post by ChadMMc on 2010-10-30
> **xx58 said:**
> :rolleyes:My problem are next: When I chat, then I receive message and about 5-6 seconds I receive this message again. So everything work nicely, only messages receiving double. Anybody can help?

Have had that problem myself off and on through the years, but not with all contacts and not all the time.  haven't the slightest idea what it's cause could be.  May be something to do with the yahoo servers?

---

### Post by heehoo on 2010-11-13
Nevermind, thanks!

---

### Post by GeoPirate on 2010-11-19
have you tried this ppa?


sudo add-apt-repository ppa:adilson/experimental

---

### Post by bubulescu on 2010-12-11
> **GeoPirate said:**
> have you tried this ppa?


sudo add-apt-repository ppa:adilson/experimental




It works! The repository can safely be added. Thank you.

---

### Post by cgroza on 2010-12-11
Isn't this project dead? The site was updated the last time in 2006!

---

### Post by xx58 on 2010-12-17
:rolleyes: I have like last month same problem. Computer starting freezing. So then I find out why, that is Gyachi who make that problem. So what happened? When I chatting over Gyachi and turn on web camera, [COLOR=Red]THEN WEB CAMERA[/COLOR],[COLOR=Blue] silently RECORDING[/COLOR] and last time I find[COLOR=Red] 8000[/COLOR] pictures was record, so because computer freezing. So today I was again at yahoo with my friend and again start freezing my laptop, so I just delete all record pictures and it works again, BUT IT IS NOT SOLUTION. [COLOR=Red]HOW I CAN STOP AUTOMATICALLY RECORDING PICTURES. [/COLOR]Anybody?

---

### Post by fikrionline on 2011-01-17
> **GeoPirate said:**
> have you tried this ppa?


sudo add-apt-repository ppa:adilson/experimental
Hi there,

if I use this guide, I receive error message like this
> Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 50AB22E78528C1C33363EE08D715961D27B81625
gpg: requesting key 27B81625 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Anybody help me please?
:p :p :p

---

### Post by Script Warlock on 2011-01-17
you can use this also its fine and working ***ppa:ferramroberto/extra***

---

### Post by gofurygo on 2011-02-23
Hello

I have the following issues with Gyachi Enhanced:

1) When I login, I can see all my buddies, also if they are online - nevertheless, in the status bar on the bottom, Gyachi showes, "Currently not connected to chat"...

2) When I click "Send webcam invitation" to one of my buddies (he is using windows Yahoo-Messenger), he gets the request, accepts, but then nothing happens, no video is opening... How can I get the video/voice chat to work?

I can open my webcam though and see the video just fine...

thanks in advance

---

### Post by duplicate150 on 2011-03-19
hello everyone.

I am new to using ubuntu at home and still use vista at office. I have functional knowledge of working my way around things in both operating system as an average user and i'm in no way an expert.

Now here's my problem. I use LAN both at home and office and at both places it is provided by my organisation. Over the past few days it appears, that ports for yahoo messenger have been blocked. So now i cannot use yahoo messenger at office or from home too. Yahoo mail and other browser based services work fine. So i can log into yahoo web messenger or through meebo.com but i cannot use webcam or voice or pic sharing.

So i installed gyachE Improved v1.2.10 for my home pc running ubuntu 10.10. Installation is fine and gyachi fires up without any problem. But it disconnects almost immediately and heres what i get on the gyachi window:
"[Saturday 19 March 2011 12:31:59] CONNECTED: type /help for help

[Saturday 19 March 2011 12:32:15] ** Could not login: Connection timed out. [ Could not login: Connection timed out. ] **
[Saturday 19 March 2011 12:32:15] Disconnected from Yahoo! See Ya! Online for 0 : 00 : 19"

What do i do in this case? I have tried using different ports like 8001, 8002, 23, 80 etc but the result is same everytime. Is there no way gyachi can connect?

I have tried and i did not find any solution to this issue anywhere though similar log is repeated in some other threads. Incidentally i have wine installed on my pc and it is working fine.

Any suggestion and help is welcome.


Thanks all

---

### Post by johnlvs2run on 2011-06-22
I've been using Gyache successfully and it's been working great.
All of a sudden last night it started having two problems.

1) the program requires me to sign in every time, and it won't keep my settings;
2) the webcam stopped working and won't go back on.
Update:  the webcam works today but gyache still is not saving the settings.

All of these things had been working quite well previous to last night.

Update2:  Gyachi started working again the next day.

---

### Post by phudq90 on 2011-08-12
Sorry guys, i know this thread is old. But i dont like to start a new one.

I'm using 11.04 and gyachi 1.2.10, when i've login first time, everything is fine, but when log back it's said that i've been disconnected because of Broken Pie.
It's still running in background, i know, there are notifiy about my buddies on/offline when i closed it. But i cant get it comes in front. Run it again? Disconnected and it's like a loop.

Anyone can fix this? I'd like to keep it 'alive' when i closed it.

Or please, suggest me another alternative for Yahoo! protocol with webcam supported application.

Thank you so much!

---

