---
title: "/usr/bin/ld: cannot find -lX11 - Error using make command"
date: 2013-11-26
forum: General Help
---

### Post by tetarchus on 2013-11-26
[LIST]
[*][INDENT]Hi guys,

I'm relatively new to Ubuntu and am learning the ropes by reading several command line books but have come across an error when trying to compile an application called HTK.

I am using Ubuntu 13.10 (Saucy Salamander) and have installed only a few packages on the machine.

Once I had unpacked the tar.gz that the application came in and moved it to /usr/local/src as directed by a tutorial as somewhere to compile applications, i ran the 

./configure command

The terminal then told me to run: 'make all' to compile then: 'make install' to install the application

I had one error that told me i was missing X11/xlib.h which i installed after searching.

Now when I run 'make all' i get the error:
/usr/bin/ld: cannot find -lX11
collect2: error: ld returned 1 exit status
make[1]: *** [HSLab] Error 1
make[1]: Leaving directory `/usr/local/src/htk/HTKTools'
make: *** [htktools] Error 1

I've tried STFW but cannot find anything on this particular error and other similar errors say have specific packages to install, however there I cannot find the package that I need and lack the knowledge of how to locate this.

If someone could help me out I'd appreciate it.

Also if you could point me to documentation that could help me out or tell me how to find which packages need to be installed from the error messages it would be a great help.

Thanks in advance[/INDENT]



[B][RIGHT][[IMG]http://ubuntuforums.org/clear.gif[/IMG]Edit Post]("http://ubuntuforums.org/editpost.php?p=12858460&do=editpost")   [[IMG]http://ubuntuforums.org/clear.gif[/IMG]Quick Reply]("http://ubuntuforums.org/newreply.php?do=newreply&p=12858460&noquote=1")   [[IMG]http://ubuntuforums.org/clear.gif[/IMG]Adv Reply]("http://ubuntuforums.org/newreply.php?p=12858460&noquote=1")   [[IMG]http://ubuntuforums.org/clear.gif[/IMG]Reply With Quote]("http://ubuntuforums.org/newreply.php?do=newreply&p=12858460")   [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/multiquote_40b.png[/IMG] ]("http://ubuntuforums.org/newreply.php?do=newreply&p=12858460")[/RIGHT] [ ]("http://ubuntuforums.org/report.php?p=12858460")  


[/B]
[/LIST]
[COLOR=#000000][/COLOR]

---

### Post by steeldriver on 2013-11-26
See if you can find a list of prerequisites for the software you are trying to compile (sometimes these are listed in a README or INSTALL file inside the tarball - sometimes you need to look on the author's website). Based on the error you probably need the **libx11-dev** package at a minimum - possibly the whole **xorg-dev** package.

---

### Post by tetarchus on 2013-11-26
Thanks, I had a look on the website and the prerequisites are just GCC and gzip or tar.

I installed libx11-dev to correct the previous error that was saying 'X11/Xlib.h not found'

I have had a look at the README file and it tells you the steps (which i was following from the website but) but no prerequesites. and there is no INSTALL file (there is an install-sh file but that was also no help)

I have tried installing x-org-dev and that didn't help, same error. Would I need to restart the computer for the changes to take effect or run a command to refresh a file at all?

Thanks

---

### Post by steeldriver on 2013-11-26
Restarting shouldn't be necessary but it would be worth running the ./configure again I think. Are you trying to build on a 32-bit or 64-bit platform?

---

### Post by tetarchus on 2013-11-26
OK, so I tried a restart and that didn't fix the error either (I wasn't hopeful but there you go).

I've had a look at **/usr/bin/ld** and it points to **/usr/bin/ld.bfd **which I guess is normal but I thought I should check. When I run **file **on **ld.bfd**it displays:

ld.bfd: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x3a08db26b53f48e3028f47f36ffda074b6377afb, stripped

In terms of this what would -lX11 be? is it a file? a line within the code?

Would it be helpful if I posted the README file at all?

The pre-requisites from the website are:

[h=3]Prerequisites[/h]
[LIST]
[*]A C compiler. All Linux distributions suitable for developers will have a copy of gcc installed, but you can use other compilers such as the Intel compiler icc. If in doubt, please ask your system administrator.
[*]For testing, you will require a [Perl Interpreter]("http://cpan.perl.org/"). Most modern Linux/Unix systems include one by default.
[*]You will need either tar and gzip (if you download the sources via ftp or http) or CVS (if you download from our CVS server). These tools are usually included by default with Linux distributions. Many other modern UNIX variants also supply them, as optional packages if not by default.
[*]If compiling on **Apple Macintosh OS X**, you must have the XCode and XOrg-devel products installed. These are available for no cost from the [Apple Developer Connection]("http://developer.apple.com/tools/xcode/"). Registration with Apple is required.
[*][Register]("http://htk.eng.cam.ac.uk/register.shtml") on this site by accepting the HTK End User Licence Agreement, then download the latest HTK source code.
[*]Some experience of working with one of the Unix shells (e.g. bash, csh, tcsh). You will need to know which shell you are using, if unsure type:> echo $SHELL
[*]You will also need to know how to edit files and how to set environment variables.
[/LIST]


Using **which gcc **it points to **/usr/bin/gcc **which as far as I can tell means it is installed.

Perl is only necessary once the application is installed and I have everything else and am using the BASH Shell.

I'm running out of ideas so any further assistance would be great.

---

### Post by tetarchus on 2013-11-26
64 bit Ubuntu 13.10

The program is probably 32 bit though - That shouldn't be an issue though should it?

---

### Post by tetarchus on 2013-11-26
I found the problem!

I STFW again for 'problems with /usr/bin/ld' (i think I'd been to specific before!) and the second hit was the exact issue I was having (including the issue being with HTK).

Turns out the fix is:

sudo ln -s /usr/lib/i386-linux-gnu/libX11.so.6.3.0 /usr/lib32/libX11.so


I'm guessing (from limited knowledge) that this creates a link from the version numbered X11 (6.3.0) to the libX11 file that HTK is looking for. There was no explanation however soon the original thread so feel free to correct me)

Original Thread here:
[http://ubuntuforums.org/showthread.php?t=2013496](http://ubuntuforums.org/showthread.php?t=2013496)

---

