---
title: "Brutus + Evolution?"
date: 2006-08-17
forum: General Help
---

### Post by Julolidine on 2006-08-17
The last tidbit in my way of ditching XP on my computer is email.  At this university, they utilize MS Exchange server 5.5, which I must access for group calenders and so on.  

I've read a little about this plugin 'brutus' for evolution 2.4 and 2.6 - which is supposed to enable exchange 5.5 for evolution.  I've gone to their website 
[http://www.omesc.com/](http://www.omesc.com/)

However, being the ignorant newb I am, I can't figure out if I can install this or not.  Does anyone have any experience with this at all?  

Thanks,
Dave

---

### Post by srf21c on 2006-09-19
I'm in the same boat, where you able to find an answer to your question somewhere else?

---

### Post by dcstar on 2006-09-24
.

---

### Post by dcstar on 2006-09-24
> **Julolidine said:**
> The last tidbit in my way of ditching XP on my computer is email.  At this university, they utilize MS Exchange server 5.5, which I must access for group calenders and so on.  

I've read a little about this plugin 'brutus' for evolution 2.4 and 2.6 - which is supposed to enable exchange 5.5 for evolution.  I've gone to their website 
[http://www.omesc.com/](http://www.omesc.com/)

However, being the ignorant newb I am, I can't figure out if I can install this or not.  Does anyone have any experience with this at all?  

Thanks,
Dave

This seems to rely on a Brutus server being installed on the network to act at the "go between" linking Evolution with Exchange, so I doubt if you would be able to use it without this server running:

[http://www.omesc.com/modules/xoopsfaq/index.php?cat_id=6#q22](http://www.omesc.com/modules/xoopsfaq/index.php?cat_id=6#q22)

---

### Post by srf21c on 2006-09-24
As luck would have it, I happen to be the adminstrator for the Exchange 2003 server in question.  However it is the version bundled with Small Business Server 2003.  

The biggest roadblock so far is that I have so far been unable to find any Ubuntu packages for the evolution-brutus client.  I reckon I'll have to install from source for the time being. Do you think it's a good/bad idea to remove the all the original Evolution packages on my system beforehand?

-Seth

---

### Post by dcstar on 2006-09-25
> **srf21c said:**
> As luck would have it, I happen to be the adminstrator for the Exchange 2003 server in question.  However it is the version bundled with Small Business Server 2003.  

The biggest roadblock so far is that I have so far been unable to find any Ubuntu packages for the evolution-brutus client.  I reckon I'll have to install from source for the time being. Do you think it's a good/bad idea to remove the all the original Evolution packages on my system beforehand?

-Seth

Not sure on compiling your own Evolution package, but I'm fairly sure if you do a basic removal of the existing client all of your data will remain (and you can re-install later).

I think the SBS Exchange should work the same as the "normal" one, just the accounts may be in the SBS OUs rather than the basic Exchange ones.

---

### Post by colding on 2006-09-25
Hi,

I'm the developer of Brutus as well as evolution-brutus so I'll better compose some sort of answer to 
the questions here.

First of all... evolution-brutus (e-b) depends on the presence of a Brutus server to mediate the communication 
to the Exchange server. The Brutus server is installed as any other win32 application. It does not need to
(and should not) be installed on the Exchange server itself.  Brutus Server will take care of the:

    <any client> <--> <any Exchange server> 

communication.

The Evolution plugin that enables Evolution 2.[4,6,8] to talk to a Brutus server is installed as any other 
application but (naturally) depends on a functioning Evolution installation. You should *never* uninstall
Evolution before installing e-b. e-b is not used by Evolution until you have configured an e-b mail account. 
The using_evolution-brutus document, as distributed with the RPMs and the source, descibes how to do this.

Exchange Calendar and Tasks will also be present in Evolution when the e-b account is up and running. You 
do not need to do anything to configure these sub-accounts but you can disable them if you do not want 
them.

I've recently looked into having e-b added to Fedora Extras but that is a long and tedious process. I'll 
appreciate any help in getting e-b into Ubuntu if you want it.

Last, but not least, do not hesitate to mail me directly at <colding AT omesc DOT com> or just join one 
of the Brutus lists if you need help getting up and running.

Best regards,
  jules

---

### Post by srf21c on 2006-09-28
> **colding said:**
> The Brutus server is installed as any other win32 application. It does not need to
(and should not) be installed on the Exchange server itself.  

Jules, I appreciate you dropping in to help out.

In this particular case, I was hoping that I could run the brutus server on the exchange server.  My plan was to make the MS Small Business Server 2003 the only Windows box on the network.

What kinds of problems might arise from running the Brutus server on the same box as the exchange server?  Having to dedicate another Windows box just to run the Brutus server  is not something I get very excited about from  sys admin perspective.  :frown:  

Also I will try building the evolution brutus plugin from source for now, but how might I go about helping you to get a package into the Ubuntu repositories?

Cheers,
Seth

---

### Post by colding on 2006-09-28
Hi Seth,

You can certainly run Brutus Server on the Exchange box if that is what you want. There should be no problems 
whatsoever but Exchange sys admins are generally very reluctant to touch a running Exchange server which is 
why I generally advise not to install Brutus Server on the Exchange box itself.

As for the Ubuntu repotories... I don't know if you can do anything to help expect for advising me on how to 
get e-b in there as smoothly as possible. I took a look at the pages that describes how to get a new package 
into Ubuntu and it just looked like a really tedious task :-(

-- 
  jules

---

### Post by srf21c on 2006-09-28
alright, that is good news.   I wonder if getting a new package into the repositories is any more tedious than building from source. ;)  

I keep getting stuck at the /brutus/idl/products/evolution/autogen.sh script, pasted below is the error I get.

```
checking Evolution Data Server version... Package evolution-data-server-1.2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `evolution-data-server-1.2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'evolution-data-server-1.2' found
configure: error: Evolution Data Server development libraries not installed
```

---

### Post by colding on 2006-09-28
Building from source should be relatively straightforward once all the build dependancies are 
present, but it does take a relatively long time to build once configured. 

The reason your autogen.sh step is failing is simply that the evolution-data-server headers 
are absent from your system. I don't know about Ubuntu, but RPM based systems have 
'-devel' packages that installs all of the headers and other development related 
resources. Maybe there is an evolution-data-server-devel.dep for Ubuntu?

-- 
  jules

---

### Post by dcstar on 2006-09-29
> **colding said:**
> Building from source should be relatively straightforward once all the build dependancies are 
present, but it does take a relatively long time to build once configured. 

The reason your autogen.sh step is failing is simply that the evolution-data-server headers 
are absent from your system. I don't know about Ubuntu, but RPM based systems have 
'-devel' packages that installs all of the headers and other development related 
resources. Maybe there is an evolution-data-server-devel.dep for Ubuntu?

-- 
  jules

There certainly is an **evolution-data-server-dev** package in my repositories.

---

### Post by srf21c on 2006-09-29
Yep, that was it, I installed the evolution-data-server-dev package and now the autogen.sh script apparently finishes.  w/possible errors listed below. 

```

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

```
```

checking for A11Y... configure: error: Package requirements (atk) were not met:

No package 'atk' found

```

Next I tried running the ./configure script and it choked with this error
```
checking for A11Y... configure: error: Package requirements (atk) were not met:

No package 'atk' found

```

So I ran ```
ais-cache search atk
``` and choose to install the libatk1.0-dev - Development files for the ATK accessibility toolkit

Ran autogen.sh again...now it's complaining about 
```
checking for GTKHTML... configure: error: Package requirements (libgtkhtml-3.8) were not met:

No package 'libgtkhtml-3.8' found

```
 
Once again ```
ais-cache search libgtkhtml
``` and apt-get install libgtkhtml3.8-dev, then run autogen.sh

I keep getting these ```
configure.in:67: warning: AC_ARG_PROGRAM invoked multiple times
``` error messages too, don't know if that can safely be ingnored or not.

...and autogen.sh has returned yet another error!  What an absolute joy building from source is.

```
checking for CAMEL_GROUPWISE... configure: error: Package requirements (camel-provider-1.2 libedataserver-1.2 >= 1.7.90 libegroupwise-1.2 >= 1.7.90) were not met:

Requested 'libedataserver-1.2 >= 1.7.90' but version of libedataserver is 1.6.1
Requested 'libegroupwise-1.2 >= 1.7.90' but version of libegroupwise is 1.6.1
```

So I run ```
dpkg -l|grep libedataserver
``` to see what's installed:

```
ii  libedataserver1.2-7                    1.6.1-0ubuntu5                         Utility libr ary for evolution data servers
ii  libedataserver1.2-dev                  1.6.1-0ubuntu5                         Utility libr ary for evolution data servers (
ii  libedataserverui1.2-6                  1.6.1-0ubuntu5                         Utility libr ary for evolution data servers
ii  libedataserverui1.2-dev                1.6.1-0ubuntu5                         Utility  

```

Then run ```
ais-cache search libedataserver
``` to see what's available
```

libedataserver1.2-7 - Utility library for evolution data servers
libedataserver1.2-dev - Utility library for evolution data servers (development files)
libedataserverui1.2-6 - Utility library for evolution data servers
libedataserverui1.2-dev - Utility library for evolution data servers (development files)

```

And now I'm stuck again.

---

### Post by dcstar on 2006-09-30
> **srf21c said:**
> 
......
Then run ```
ais-cache search libedataserver
``` to see what's available
```

libedataserver1.2-7 - Utility library for evolution data servers
libedataserver1.2-dev - Utility library for evolution data servers (development files)
libedataserverui1.2-6 - Utility library for evolution data servers
libedataserverui1.2-dev - Utility library for evolution data servers (development files)

```

And now I'm stuck again.

Have a look at:

[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fe%2Fevolution-data-server%2Flibedataserver-dev_1.0.4-1_i386.deb&md5sum=242a2acae290eda3a386afbf3df1e8b8&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fe%2Fevolution-data-server%2Flibedataserver-dev_1.0.4-1_i386.deb&md5sum=242a2acae290eda3a386afbf3df1e8b8&arch=i386&type=main)

---

### Post by colding on 2006-10-02
> **srf21c said:**
> Yep, that was it, I installed the evolution-data-server-dev package and now the autogen.sh script apparently finishes.  w/possible errors listed below. 

```
checking for GTKHTML... configure: error: Package requirements (libgtkhtml-3.8) were not met:

No package 'libgtkhtml-3.8' found

```
```
checking for CAMEL_GROUPWISE... configure: error: Package requirements (camel-provider-1.2 libedataserver-1.2 >= 1.7.90 libegroupwise-1.2 >= 1.7.90) were not met:

Requested 'libedataserver-1.2 >= 1.7.90' but version of libedataserver is 1.6.1
Requested 'libegroupwise-1.2 >= 1.7.90' but version of libegroupwise is 1.6.1
```

And now I'm stuck again.

libedataserver* should be installed along evolution-data-server-dev (it is on Gentoo and FC[4,5,6]) but this may naturally not be the case on Ubuntu 
where the packaging could be different. I can also add that I have no explicit check for gtkhtml in "configure.in". This must be an Ubuntunism of autogen.sh. 
I also find it strange that configure is checking for camel-groupwise. evolution-brutus is definitely _not_ using anyhing from camel-groupwise.

---

### Post by NachoMas on 2006-10-09
Hi!
I am trying as well to build a deb package with evolution-brutus. I have installed all the dependencies and succesfully run configure on the source, but I am getting linking errors when compiling with make. I am attaching the whole output of the compilation process... Any help appreciated here! Once I get it to compile I'll use checkinstall to create a deb and I'll post it here..

Cheers!
/Nacho

---

### Post by colding on 2006-10-09
I caught me at a bad time (fetching the kids). I'll dig into this tomorrow.

-- 
  jules

---

### Post by colding on 2006-10-10
> **NachoMas said:**
> Hi!
I am trying as well to build a deb package with evolution-brutus. I have installed all the dependencies and succesfully run configure on the source, but I am getting linking errors when compiling with make. I am attaching the whole output of the compilation process... Any help appreciated here! Once I get it to compile I'll use checkinstall to create a deb and I'll post it here..

Cheers!
/Nacho

Please do a 'make distclean' and post the output from autogen.sh and make. The error log above contain only the link errors so I can't really see what the root cause is.

Thanks,
  jules

---

### Post by NachoMas on 2006-10-10
Here they go! the output of autogen.sh and the subsequent make

Thanks for the help!
/Nacho

---

### Post by colding on 2006-10-10
No problem, I'll look at them tomorrow (kid fetching time again).

---

### Post by colding on 2006-10-11
OK, let's see:

Your output:
```

if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/tmp/kk/evolution-brutus-1.1.6/idl_output  -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libIDL-2.0    -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare  -Werror -Werror-implicit-function-declaration -std=gnu89 -D_REENTRANT -O3 -march=pentium3 -pipe -fomit-frame-pointer -funroll-loops -fexpensive-optimizations -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -O2 -DG_LOG_DOMAIN=\"libBrutusSTUBS\" -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libIDL-2.0    -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare  -Werror -Werror-implicit-function-declaration -std=gnu89 -D_REENTRANT -O3 -march=pentium3 -pipe -fomit-frame-pointer -funroll-loops -fexpensive-optimizations -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -O2 -MT IDistList-common.lo -MD -MP -MF ".deps/IDistList-common.Tpo" -c -o IDistList-common.lo IDistList-common.c; \
	then mv -f ".deps/IDistList-common.Tpo" ".deps/IDistList-common.Plo"; else rm -f ".deps/IDistList-common.Tpo"; exit 1; fi
mkdir .libs

```
My output:
```

source='IDistList-common.c' object='IDistList-common.lo' libtool=yes \
	depfile='.deps/IDistList-common.Plo' tmpdepfile='.deps/IDistList-common.TPlo' \
	depmode=gcc3 /bin/sh ../depcomp \
	/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include -I/home/colding/tmp/evolution-brutus-1.1.6/idl_output  -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib64/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libIDL-2.0    -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare  -Werror -Werror-implicit-function-declaration -std=gnu89 -D_REENTRANT -g -O2 -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -O2 -DG_LOG_DOMAIN=\"libBrutusSTUBS\" -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib64/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libIDL-2.0    -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare  -Werror -Werror-implicit-function-declaration -std=gnu89 -D_REENTRANT -g -O2 -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -O2 -c -o IDistList-common.lo `test -f 'IDistList-common.c' || echo './'`IDistList-common.c
mkdir .libs

```

Your output doesn't contain the libtool 'source=' line at all and you are using different optimization options. I don't think the optimization options are significant, but the libtool 'source=' think might be.

Unfortunately I think that I need to be on Ubuntu to solve this...

---

### Post by colding on 2006-10-11
BTW, I should add that evolution-brutus builds fine on Gentoo, FC4, FC5 and the current FC6 beta.

---

### Post by NachoMas on 2006-10-11
Umm...
I am going to try to build it in a pure debian box and see what happens...

---

### Post by colding on 2006-10-13
OK, I've just tried installing Ubuntu 6.06 to see if I could fix the build problems. A bunch of development 
packages (evolution-data-serverver-dev, gnome-common and automake among others) was easily 
installed with Synaptic. 

Now I'm stalled by the ORBit2 requirement of evolution-brutus. It requires at  least 2.14.1 but the newest 
version in Synaptic is 2.14.0. 

Can I persuade Synaptic to fetch a newer version from somewhere else?

I could naturally install from source, but this whole exersize is about getting evolution-brutus to build 
on Ubuntu using no dirty tricks.

Thanks,
  jules

BTW: I tried to current version of Debian and found it lacking and hopelessly outdated. Evolution is only 
at 2.0 so an unmodified Debian box is not an option.

---

### Post by NachoMas on 2006-10-13
Hi Jules,
I guess you are using Dapper to try to build. Just change your /etc/apt/sources.list from dapper to edgy and then you'll find orbit2 2.14.3. Just watch out with the update, since there has been some nasty effects on Xorg with some recents package upgrades... But it should work fine...

I tried as well building in a Debian experimental, and I had major problems as well...

Thanks for the efforts! Let me know if I can be of more help somehow!
/Nacho

---

### Post by colding on 2006-10-13
Hi Nacho,

I assume that it means that I simply has to replace every occurrence of "dapper" with "edgy"?

Thanks,
  jules

---

### Post by colding on 2006-10-18
I just posted build instructions for evolution-brutus 1.1.6 on Ubuntu edgy on the ubuntu-users and ubuntu-devel lists.

HTH,
  jules

---

### Post by radix0 on 2006-10-31
I followed your build instructions ([https://lists.ubuntu.com/archives/ubuntu-users/2006-October/097145.html]("https://lists.ubuntu.com/archives/ubuntu-users/2006-October/097145.html")) and got everything built & installed.  However, Evolution doesn't seem to pick up the plugin - it's not listing it as an available account type.  I've tried both 1.1.6 and 1.1.7 versions of evolution-brutus ](*,) 

Looking at your site, I found the new Ubuntu binaries, but when I attempted to install them, I get:

dpkg: dependency problems prevent configuration of evolution-brutus:
 evolution-brutus depends on libgnome-keyring (>= 0.4.2); however:
  Package libgnome-keyring is not installed.

I have libgnome-keyring0 installed - any idea what's going on here?

Thanks,
-r0

---

### Post by colding on 2006-11-01
Yes, I made a mistake. It's fixed now. Thanks for letting me know.

Best regards,
  jules

---

### Post by radix0 on 2006-11-02
The .deb packages installed correctly now, but the Brutus account type still doesn't show up as an option for account types.  I've done an "evolution --force-shutdown", and verified that there's nothing evolution-related running (via a ps).  Is there something else that needs to happen to let evolution know that the Brutus addon is installed?  

Thanks,
-r0

---

### Post by colding on 2006-11-03
Very strange... I've installed the exact same debs and I do not have your problem. Could you please confirm that all of the fiels in the deb are installed in the right location? You can get a list of files in the deb by doing "dpkg -c ./<DEB FILE>".

-- 
  jules

---

### Post by radix0 on 2006-11-08
It looks like everything is in the correct location - I've even removed everything evolution-related (via "sudo aptitude remove --purge") and re-installed, no luck.  When the "Evolution Setup Assistant" pops up, there's no option for Server Type that's related to Brutus.

At this point, I'm willing to chalk it up to something hosed in my Ubuntu install (upgraded from Breezy to Dapper to pre-release-Edgy to released-Edgy ;) ).  I'll try to get it going on a VM just to be sure.

Thanks,
-r0

---

### Post by colding on 2006-11-09
Please let me know if you figure out why it doesn't work. Have you tried installing e-b directly from source?

Best regards,
  jules

---

### Post by Julolidine on 2006-11-09
Hey...I thought I had a similar issue, but I have it installed now and at least evolution picks it up.  :D 

The thing was I thought 'brutus' would show up under plugins.  Instead, go to preferences, add new user, and then under "server type" MS exchange courtesy of Brutus shows up.

Got that one going, thanks for all the help!

Anyways, now I get a "could not connect to Brutus server"

I have windows running Brutus server next to this computer...I installed, and then started it in service.  Looks good so far.

So I go to setup in Evolution: 

Whats the difference between "windows domain" and "brutus server" ??

I assume that I enter the IP for the brutus server in that box, but what do I put in "Windows Domain"?  

I also assume that Exchange Mailbox is the user ID I use to log on to my mail account normally, correct?  

I thought perhaps I couldn't connect because of a firewall blocking the IIOP ports, so I switched it to port 80 on both the ubuntu box and in brutus.conf on the windows - however, that didn't improve the situation.  

Anyways, so clossssssse.  I'll be the happiest man in the world when I can finally delete that windows partition.

---

### Post by colding on 2006-11-09
OK, glad you got the account up and running :-)

The first thing to remember is that there must be no firewall(s) in between the Brutus server and the Brutus client. Most linux distributions enables some kind of local firewall. Try to disable it and see if it makes a difference.

"Brutus server" is the box where the Brutus Server application is running. "Windows domain" is the Windows domain to which the Brutus server box belongs. This domain must be the same as the domain of your Windows user.

Everything is OK as long as you enter a DNS resolvable name or IP address in the Brutus server box. 

The Exchange mailbox could be your Windows username but that is not always the case. Your Windows username is the username that your are using when logging onto the Windows network. The Exchange mailbox is the name of your, you guessed it, Exchange mailbox. 

As to ethernet ports... The initial bootstrap contact between the Brutus server and the Brutus client is done on port 951, but further communication can occur on (almost) any port. That is why all firewalls must be inactive to guarantee that the Brutus server and the Brutus client can talk.

HTH,
  jules

---

### Post by rundgren on 2007-03-01
just a tip if anyone else is having problems starting the service (I was getting and error indicating something like: "This software is not configured") after installing Brutus on a windows server: You will need some Visual C++ runtime files. I found some that worked for me in a file from MS called vcredist_x86.exe.

---

### Post by colding on 2007-03-02
You can also use the latest test release of Brutus Server. The dll problems above is due to problems when installing on Windows 2003. They have now been fixed.

---

### Post by rundgren on 2007-03-08
thanks!

I've now gotten as far as this:
[LIST]
[*]Installed and started Brutus Server (on win2003 server in the same domain as Exchange server)
[*]Compiled, installed and configured evolution-brutus.
[*]Confirmed that I can connect to port 951 on the machine running Brutus Server. (telnet/nmap)
[/LIST]

Still I get "Cannot connect to Brutus Server" from Evolution.

Can you, or anybody else, point me in the right direction for troubleshooting??

PS: Jules: Have you considered a wiki for this project?

---

### Post by colding on 2007-03-09
Build evolution-brutus with --enable-brutus-debug. Then run Evolution as:

export BRUTUS_DEBUG=yes evolution &>eb.log

You should be able to see where it fails otherwise just send(*) me the terminal output directly and I'll take a look at it.

HTH,
  jules

(*) colding AT omesc DOT com

---

### Post by ciAnd7 on 2007-04-24
Hi!
Is it possible to use evolution-brutus with Evolution 2.10 (from fiesty 7.04)? 
I just install evolution-brutus evolution-brutus_1.1.22-1_i386.deb from [www.omesc.com](www.omesc.com). But it seems that plugin requires Evolution 2.8... (libcamel-1.2.so.8?). 
Drop down list of server types do not contains any entries about Brutus...

---

### Post by colding on 2007-04-30
Yes, it should be readily usable but you must build from source yourself. I haven't got the time to   make binaries for fiesty just yet. Just build with:

$ ./autogen.sh --enable-brutus-target=ubuntu && make && make dist-deb

That should give you the debs to install. Please remember that e-b on Ubuntu need this workaround due to a bug in ORBit2 as shipped by fiesty:

[https://bugs.launchpad.net/ubuntu/+source/orbit2/+bug/66560](https://bugs.launchpad.net/ubuntu/+source/orbit2/+bug/66560)


HTH,
  jules

---

### Post by ThomasNovin on 2007-06-04
I read the FAQ for e-b but I could not find anything about your contacs? I have a (active directory?) catalog of some sort where I can lookup all my collegues.

The installation with the Feisty deb went smoothly. It would be nice though if there was a repository to add so it would automatically keep track of updates.

I am yet to install the server at a Windows PC at work and test it but I must say already, great work! Just was I was looking for. The WebDAV/OWA implementation works for the most common operations but is very limited and very slow compared to native access.

---

### Post by zed_at_uw on 2007-06-18
Hi 

I got Evolution + brutus running.

But when i change message i'm viewing, evolution crashes.
at the same time my win box with the brutus service running displays: proxy.exe has encountered a problem and needs to close. 

Soooooo close....

Serge Vleugels

---

### Post by zed_at_uw on 2007-06-18
Hi 

I got Evolution + brutus running.

But when i change message i'm viewing, evolution crashes.
at the same time my win box with the brutus service running displays: proxy.exe has encountered a problem and needs to close. 

Soooooo close....

Serge Vleugels

---

