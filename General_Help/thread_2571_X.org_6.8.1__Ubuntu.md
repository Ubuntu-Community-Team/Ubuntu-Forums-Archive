---
title: "X.org 6.8.1 / Ubuntu"
date: 2004-10-29
forum: General Help
---

### Post by mkools on 2004-10-29
Hi all,

Why did Ubuntu included an updated version of XFree86 4.3.0 in
the 4.1 release?

It's a great distro, all packages are the latest, but one of the most
important, X-Windows, is very very old crap, I don't get it.

Is there a way to upgrade to X.org 6.8.1 without screwing up my
whole system?

I downloaded the X.org 6.8.1 source code and compiled it.
It works ok, but my GNome didn't work anymore after installing the new X.

Re-installation of gnome didn't work either and after a lot of bugging I ended up
with a whole screwed up, not working ubuntu linux x-system, so I think
I'll start over again :)

Glad this was a test install :)

Any documents that cover this upgrade?
I really need 6.8.1 since Sun Project Looking glass uses it.

Thanks in advance!

---

### Post by normnmiles on 2004-10-29
Xorg will be included in Hoary (next release).  
[http://www.ubuntulinux.org/support/documentation/faq/x.org](http://www.ubuntulinux.org/support/documentation/faq/x.org)

---

### Post by jdong on 2004-10-29
[QUOTE=mkools]Hi all,

Why did Ubuntu included an updated version of XFree86 4.3.0 in
the 4.1 release?

It's a great distro, all packages are the latest, but one of the most
important, X-Windows, is very very old crap, I don't get it.

Is there a way to upgrade to X.org 6.8.1 without screwing up my
whole system?

I downloaded the X.org 6.8.1 source code and compiled it.
It works ok, but my GNome didn't work anymore after installing the new X.

Re-installation of gnome didn't work either and after a lot of bugging I ended up
with a whole screwed up, not working ubuntu linux x-system, so I think
I'll start over again :)

Glad this was a test install :)

Any documents that cover this upgrade?
I really need 6.8.1 since Sun Project Looking glass uses it.

Thanks in advance![/QUOTE]

X.org will be included in Hoary Hedgehog release (~April next year). The development tree has just opened, and I think we'll see X.org in there soon. 


Installing X from source is _NOT_ recommended.

X 4.3.99 is  shipped with Ubuntu 4.10, and I don't think it's old or crap.

---

### Post by oddabe19 on 2004-10-29
X 4.3.99 (Oct. 18, 2004) that doesn't seem too old... unless you consider 11 days too old. :-P

It's X 4.3 with massive hardware improvements, basically, this version is only lacking the composite and stuff that X.org 6.8 has.

---

### Post by mkools on 2004-10-29
[QUOTE=jdong]X.org will be included in Hoary Hedgehog release (~April next year). The development tree has just opened, and I think we'll see X.org in there soon.[/quote]

April next year, damn :S

> Installing X from source is _NOT_ recommended.

Ehmm not recommended I know, but I got it to run, only gnome didn't
work anymore after that, but i'll give it another try with a clean install :)

> X 4.3.99 is  shipped with Ubuntu 4.10, and I don't think it's old or crap.

Yes, it is old crap, it's old crap covered with a silver layer so you can't see
what's inside :)

---

### Post by mkools on 2004-10-29
[QUOTE=oddabe19]X 4.3.99 (Oct. 18, 2004) that doesn't seem too old... unless you consider 11 days too old. :-P

It's X 4.3 with massive hardware improvements, basically, this version is only lacking the composite and stuff that X.org 6.8 has.[/QUOTE]

I started using this distro because it's only 1 CD, it's a very clean distro and it
has only the packages you really need/want.
The package managment system is great, never used debian packaging before,
i have to admit i'm impressed.

Second reason I use this distro is that it uses the latest packages , like gnome 2.8,
so I don't care if 4.3.99 is 11 days old, it's still the 4.3 engine with improved hard-
ware support and it just doesn't work for me.

Everybody is using xorg 6.8.1 since Xfree 4.40 has licensing issues so why
include the latest packages and forget the latest x-windows and use some
old crap product that nobody supports after 4.3?

---

### Post by Joeb on 2004-10-29
[QUOTE=mkools]I started using this distro because it's only 1 CD, it's a very clean distro and it
has only the packages you really need/want.
The package managment system is great, never used debian packaging before,
i have to admit i'm impressed.

Second reason I use this distro is that it uses the latest packages , like gnome 2.8,
so I don't care if 4.3.99 is 11 days old, it's still the 4.3 engine with improved hard-
ware support and it just doesn't work for me.

Everybody is using xorg 6.8.1 since Xfree 4.40 has licensing issues so why
include the latest packages and forget the latest x-windows and use some
old crap product that nobody supports after 4.3?[/QUOTE]

Actually, if I'm not mistaken the version of xorg that would have been available to include in Warty  is basically XFree 4.4RC2.  While 4.3.99 isn't the same, it has many of the patches, but is lacking some of the hardware support.  You have to be careful, though, because there are a number of comments on various websites that xorg broke this or that.

From a development standpoint, I would think you'd want to stick with something that is stable instead of switching something as important as  x-windows mid-stream.  By including it in the next version, well, one, the latest xorg can be used and two, most of the bugs will be worked out.

Just my two-cents.

Joeb

---

### Post by daniels on 2004-10-30
[QUOTE=mkools]Everybody is using xorg 6.8.1 since Xfree 4.40 has licensing issues so why include the latest packages and forget the latest x-windows and use some
old crap product that nobody supports after 4.3?[/QUOTE]

Debian still uses 4.3.0, because the packagers have not had the time to convert to X.Org.  When we started, using Debian as a base, 4.3.0 was already there, and we did not have time to switch to X.Org.  Such a conversion would've been too risky and invasive so late in our release cycle.

Our plans clearly say that we are going to switch to using the X.Org tree, and that's what we intend to do, for various reasons -- pragmatic (everyone works on it), and licensing (the XFree86 1.1 licence sucks).  It wasn't because we thought 4.3 was better in any way.

---

### Post by FLeiXiuS on 2004-10-30
In reply to daniles will xorg be on the hoary releast?

---

### Post by mkools on 2004-10-30
The reason for not including x.org is clear to me now, thanks for your replies.

I can't wait for X.org 6.8.1 to be included, that would make this the perfect
linux distro for me 8)

---

### Post by nuopus on 2004-10-31
[QUOTE=mkools]Hi all,

Why did Ubuntu included an updated version of XFree86 4.3.0 in
the 4.1 release?

It's a great distro, all packages are the latest, but one of the most
important, X-Windows, is very very old crap, I don't get it.

Is there a way to upgrade to X.org 6.8.1 without screwing up my
whole system?

I downloaded the X.org 6.8.1 source code and compiled it.
It works ok, but my GNome didn't work anymore after installing the new X.

Re-installation of gnome didn't work either and after a lot of bugging I ended up
with a whole screwed up, not working ubuntu linux x-system, so I think
I'll start over again :)

Glad this was a test install :)

Any documents that cover this upgrade?
I really need 6.8.1 since Sun Project Looking glass uses it.

Thanks in advance![/QUOTE]
 I think you are seeing JUST the number. 4.3.0 is not an extremely old version. Sure XORG is at 6.8 but its a different project. 

Anyway, the drivers from ATI do not work well with XORG 6.8. ATI says that they will support it but have not released anything yet. If they are going to move to XORG they should also include the OPTION of Xfree 4.3 or Ubuntu is a useless distribution to me and would just switch ... and a lot of users using ATI Radeons will be frustrated as well.

And no ... the build in radeon drivers are NOT an option ... they are way too slow when compared to the actual drivers from ATI.

---

### Post by HiddenWolf on 2004-10-31
However, the included drivers work, and work smoothly, as opposed to ati-fglrx

---

### Post by cseg on 2004-10-31
For what its worth, here is the script that I used to compile x.org 6.8.1.  

THIS IS NOT A GENERIC SCRIPT.

You will need to read through the script and customize it according to your environment.

```
#!/bin/sh
#
# This script downloads, compiles and installs the X.org 6.8.1
# X server on a ubuntu warty warthog system.
#

[ `id -u` != 0 ] && {
   echo This script must be run as root.
   echo in order to be able to invoke apt-get
   echo and to perform make install
   exit 1
}

HOME=/home/$USERNAME
build=xorg681cvs
buildDir=$HOME/$build
ProjectRoot=/usr/local/$build


# get requisite tools
apt-get update
apt-get -y install gcc bison flex g++ libpam0g-dev libncurses5-dev libpng12-dev cvs

mkdir -p $buildDir
cd $buildDir || {
   echo Could not change to $buildDir
   exit 1
}

# checkout from cvs
grep -sq :pserver:anoncvs@cvs.freedesktop.org: $HOME/.cvspass || {
        echo Press RETURN the password prompt
        cvs -z3 -d :pserver:anoncvs@cvs.freedesktop.org:/cvs login
}
cvs -z3 -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg co -P -rXORG-6_8_1 xc

# create shadow tree
localBuildDir=$buildDir-local-build
mkdir -p $localBuildDir/xc

# -- change to xc directory

cd $localBuildDir/xc
lndir ../../$build/xc

# read through the OS-specific README file in programs/Xserver/hw/xfree86/doc

##
## This section has been configured for my EPIA system.
## You will need to configure this for your environment.
##

cat <<EOF > config/cf/host.def
#define DefaultGcc2i386Opt -march=i686 -msse -mmmx -mfpmath=sse,387 -O3 -fomit-frame-pointer -ffast-math -finline-functions
/* #define BuildServersOnly YES */
#define GccWarningOptions -pipe
#define HasMTRRSupport YES
#define HasMMXSupport YES
#define HasSSESupport YES
#define ProjectRoot $ProjectRoot
#define NothingOutsideProjectRoot YES
#define EtcX11Directory $ProjectRoot/etc/X11
#define XF86CardDrivers via
#define XInputDrivers mouse keyboard
#define DriDrivers /*built from Mesa CVS*/
EOF

##
## My first compilation attempt resulted in compilation errors.
##

# xmlconfig.c:34:19: expat.h: No such file or directory
cp ./extras/expat/lib/expat.h .

#/usr/bin/ld: cannot find -lexpat
ln -s /usr/lib/libexpat.so.1.0.0 /usr/lib/libexpat.so

##
## commence build
##
date
time make WORLDOPTS= World >world.log 2>&1
date

# and install into ProgramRoot (see host.def)
time make install >install.log 2>&1

#
# Now make sure everyone can find the new X11
#

# ld.so.conf
[ ! -f /etc/ld.so.conf-pre-$build ] &&
   mv -f /etc/ld.so.conf /etc/ld.so.conf-pre-$build
echo "$ProjectRoot/lib"                               >  /etc/ld.so.conf
grep -vFx "$ProjectRoot/lib" /etc/ld.so.conf-pre-$build >> /etc/ld.so.conf
ldconfig

# /etc/profile
cat >>/etc/profile <<-END
if [ -n "\${PATH##$ProjectRoot/bin:*}" ]; then
    export PATH="$ProjectRoot/bin:\$PATH"
fi
if [ \$LD_LIBRARY_PATH ]; then
   export LD_LIBRARY_PATH="$ProjectRoot/lib:\$LD_LIBRARY_PATH"
else
   export LD_LIBRARY_PATH="$ProjectRoot/lib"
fi
export C_INCLUDE_PATH=$ProjectRoot/include
export CPLUS_INCLUDE_PATH=$ProjectRoot/include
END

# /etc/X11/X
rm -f /etc/X11/X
ln -sf $ProjectRoot/bin/XFree86 /etc/X11/X

# X11 development directories
ln -sf $ProjectRoot             /usr/X11
[ ! -f /usr/X11R6-pre-$build ] &&
    mv /usr/X11R6 /usr/X11R6-pre-$build
ln -sf $ProjectRoot             /usr/X11R6

# /usr/include/X11
rm -f /usr/include/X11
ln -sf $ProjectRoot/include/X11 /usr/include/X11
ln -sf $ProjectRoot/include     /usr/include/X11R6

# /usr/lib/X11
rm -f /usr/lib/X11
ln -sf $ProjectRoot/lib/X11 /usr/lib/X11
ln -sf $ProjectRoot/lib     /usr/lib/X11R6

# /etc/X11/xorg.conf
[ ! -f /etc/X11/xorg.conf ] &&
        sed < /etc/X11/XF86Config-4 > /etc/X11/xorg.conf -e 's@"vesa"@"via"@'


```

---

### Post by nuopus on 2004-10-31
[QUOTE=HiddenWolf]However, the included drivers work, and work smoothly, as opposed to ati-fglrx[/QUOTE] How to the ati-fglrx drivers NOT work smoothly? You just get it from the ATI website ... not the outdated stuff in the repos .. install with alien -i
 
 cd to /lib/modules/fglrx/build_mod, do an sh make.sh
 cd to /lib/modules/gflrx, do an sh install.sh
 do an fglrxconfig and configure. It works smoothly and can get 1800 fps with glx_gears as opposed to only 900 with the build in drivers.
 
 You know ... sometimes there is more to Linux than apt and the repos.

---

### Post by Gaeldir on 2004-11-12
[QUOTE=nuopus]How to the ati-fglrx drivers NOT work smoothly? You just get it from the ATI website ... not the outdated stuff in the repos .. install with alien -i
 
 cd to /lib/modules/fglrx/build_mod, do an sh make.sh
 cd to /lib/modules/gflrx, do an sh install.sh
 do an fglrxconfig and configure. It works smoothly and can get 1800 fps with glx_gears as opposed to only 900 with the build in drivers.
 
You know ... sometimes there is more to Linux than apt and the repos.[/QUOTE]
How did you manage ATI's drivers to work using *alien -i* ?

:!: I tried this method ant that did not work, the *make.sh*  script tells me something like 
*"Please update to a kernel >= 2.4.x for this driver to be installed"*, but in Ubuntu 4.10 we have a 2.6.8.1 kernel ! :confused: So this is really frustrating ...

Could you explain (in detail) how you did to make ATI's drivers work, From the packages installed to the drivers' installation ? 
That would be nice, I'd like to upgrade to the latest 3.14.6 drivers from ATI ! ;-)

PS : Ubuntu 4.10 is by far the best Linux distribution I have ever installed on my Acer Aspire 1681WLMi laptop ... It recognized all my hardware and configured it as well ! I definitively use Ubuntu rather than Mandrake (I used to work on Mdk) or Suse ... Ubuntu, defintively Ubuntu ! Keep making such a good work, guys ! :mrgreen:

---

### Post by jdodson on 2004-11-12
[QUOTE=mkools]pckages are the latest, but one of the most
important, X-Windows, is very very old crap, I don't get it.
[/QUOTE]

funny.  i had to get over the "if it wasnt released in the last 6 months it is trash" attitude when i started using redhat 9.0 at work a few months ago.  as it is a few years old, the software still works really well.  i had to install firefox 1.0, beyond that its fine.  now we are talking gnome 2.2 but hey, its not that bad and it is strikingly stable.

then again according to your statement winXP is a decrepid dinosaur cause it was released in 2001.  then again, i agree.  winXP is a crusty old man in a fast running world of linux releases.  funny as redhat 9.0 was released after winXP and people still use XP avidly and wouldnt install redhat 9.0 on a box to save thier life anymore because it is considered "old hat."  i feel for the people who use windows 2000, NT or 98 and are still using flint to light log fires and skinning deer for the pre-bronze age tribe:-)  

just some funny observations. :grin:

---

### Post by jdong on 2004-11-12
For those impatent X.org waiters, X.org 6.8.1 packages are in hoary. Knock yourselves out.

I've been using Hoary for a week or so, and it's pretty stable. I've yet to see any breakage.

---

