---
title: "how do you  make a .deb (or can someone do it for me)?"
date: 2007-12-05
forum: General Help
---

### Post by bionnaki on 2007-12-05
I'd like to install the latest rubyripper: [http://code.google.com/p/rubyripper/downloads/list](http://code.google.com/p/rubyripper/downloads/list)

when I attempt to compile, I get the following error:

> [~/rubyripper-0.4.4] ->> $ ./rubyripper_gtk2.rb
RubyGems is not found. Please install ruby-gettext.
/home/bill/rubyripper-0.4.4/rr_lib.rb:91: undefined method `bindtextdomain' for Gui_support:Class (NoMethodError)
        from ./rubyripper_gtk2.rb:27:in `require'
        from ./rubyripper_gtk2.rb:27
        from ./rubyripper_gtk2.rb:27:in `each'
        from ./rubyripper_gtk2.rb:27


when I install sudo apt-get install libgettext-ruby1.8

and try again, the gui of rubyripper comes up. 

following the readme, I do: ./configure --enable-lang-all --enable-gtk2 --enable-cli --prefix=/usr or

and I get:

> $ ./configure --enable-lang-all --enable-gtk2 --enable-cli --prefix=/usr or
Creating the Makefile...
A summary of your settings:

Using the following locations for install:
* Executables: /usr/bin
* Localization files: /usr/share/locale
* Icon file: /usr/share/pixmaps
* Desktop file: /usr/share/applications
* Ruby library: /usr/lib/site_ruby/1.8

Gtk2 frontend will be installed
Cli frontend will be installed
Languages to be installed: nl, de, hu, ru

You can now run make install
Make sure you've got the writing privileges


at this point, I'd like to make a .deb so I share it. so I run sudo checkinstall:

> $ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@ubuntu ]
1 -  Summary: [ rubyripper-0.4.4 ]
2 -  Name:    [ rubyripper ]
3 -  Version: [ 0.4.4 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ rubyripper-0.4.4 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
`ruby configure --update-lang` #update the locale files
/usr/lib/ruby/1.8/gettext/parser/ruby.rb:15:in `require': no such file to load -- irb/ruby-lex.rb (LoadError)
        from /usr/lib/ruby/1.8/gettext/parser/ruby.rb:15
        from /usr/lib/ruby/1.8/gettext/parser/erb.rb:13:in `require'
        from /usr/lib/ruby/1.8/gettext/parser/erb.rb:13
        from /usr/lib/ruby/1.8/gettext/rgettext.rb:40:in `require'
        from /usr/lib/ruby/1.8/gettext/rgettext.rb:40
        from /usr/lib/ruby/1.8/gettext/rgettext.rb:33:in `each'
        from /usr/lib/ruby/1.8/gettext/rgettext.rb:33
        from /usr/lib/ruby/1.8/gettext/utils.rb:10:in `require'
        from /usr/lib/ruby/1.8/gettext/utils.rb:10
        from configure:52:in `require'
        from configure:52:in `update_lang'
        from configure:105
        from configure:83:in `each'
        from configure:83
make: *** [all] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.



So, what do I do?



[quote]

---

### Post by jonathan21 on 2007-12-05
install alien

in terminal go to where file is located by typing cd and then where the file is located

once in folder type

sudo alien (then name of the file)

hope it works

---

### Post by bionnaki on 2007-12-05
> sudo alien (then name of the file)

what file?

and why would I want to use alien? I'm not installing an .rpm...im trying to make a .deb from **source**

---

### Post by oscarsfriend on 2007-12-05
Install the "checkinstall" package (it's in the repos), then "man checkinstall" from a terminal for the documentation.

> 
installation tracker

CheckInstall keeps track of all the files created or modified by your installation script ("make install" "make install_modules", "setup", etc), builds a standard binary package and installs it in your system giving you the ability to uninstall it with your distribution's standard package management utilities.

Homepage: [http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/)


---

### Post by bionnaki on 2007-12-05
I ran checkinstall. see the errors I received.

---

### Post by logos34 on 2007-12-05
Mine fails too (checkinstall):
> ========================= Installation results ===========================
`ruby configure --update-lang` #update the locale files
configure:52:in `require': no such file to load -- gettext/utils (LoadError)
        from configure:52:in `update_lang'
        from configure:105
        from configure:83:in `each'
        from configure:83
make: *** [all] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


---

### Post by oscarsfriend on 2007-12-05
> **bionnaki said:**
> I ran checkinstall. see the errors I received.

:oops: So you did -- I read the title and skipped down.  It looks like a plain old compilation error rather than anything to do with checkinstall or making a .deb.  Presumably just a plain "make" will give the same error?  I see that you had to install the libgettext-ruby1.8 package (whatever that might be) -- was there a corresponding dev package?  (I'm sorry, I can't check as my internet connection is all out of whack and everything is running stupidly slow here.)

---

### Post by logos34 on 2007-12-05
yeah, I guessed and installed

ruby-pkg-tools (0.11.5)
ruby1.8-dev

and got a little further this time...checked the README and grabbed the dependency [ruby-gettext-package-1.10.0]("http://www.yotabanana.com/hiki/ruby-gettext.html?ruby-gettext")

it went in fine and so did rubyripper (I think) but making the .deb pkg/checkinstall inexplicably failed--the pkg is sitting there in the folder but I got this at the end:

> ...
./locale/po/nl/rr_lib.po
....... done.
./locale/po/hu/rr_lib.po
....... done.
./locale/po/ru/rr_cli.po -> ./locale/ru/LC_MESSAGES/rr_cli.mo
./locale/po/ru/rr_lib.po -> ./locale/ru/LC_MESSAGES/rr_lib.mo
./locale/po/ru/rr_gtk2.po -> ./locale/ru/LC_MESSAGES/rr_gtk2.mo
./locale/po/de/rr_cli.po -> ./locale/de/LC_MESSAGES/rr_cli.mo
./locale/po/de/rr_lib.po -> ./locale/de/LC_MESSAGES/rr_lib.mo
./locale/po/de/rr_gtk2.po -> ./locale/de/LC_MESSAGES/rr_gtk2.mo
./locale/po/nl/rr_cli.po -> ./locale/nl/LC_MESSAGES/rr_cli.mo
./locale/po/nl/rr_lib.po -> ./locale/nl/LC_MESSAGES/rr_lib.mo
./locale/po/nl/rr_gtk2.po -> ./locale/nl/LC_MESSAGES/rr_gtk2.mo
./locale/po/hu/rr_cli.po -> ./locale/hu/LC_MESSAGES/rr_cli.mo
./locale/po/hu/rr_lib.po -> ./locale/hu/LC_MESSAGES/rr_lib.mo
./locale/po/hu/rr_gtk2.po -> ./locale/hu/LC_MESSAGES/rr_gtk2.mo
install -D rr_lib.rb /usr/lib/site_ruby/1.8/rr_lib.rb
[COLOR="Red"]install: setting permissions for `/usr/lib/site_ruby/1.8/rr_lib.rb': No such file or directory
install -m 755 -D rubyripper_gtk2.rb /usr/bin/rrip_gui
install: setting permissions for `/usr/bin/rrip_gui': No such file or directory
install -D rubyripper_22.png /usr/share/pixmaps/rubyripper_22.png
install: setting permissions for `/usr/share/pixmaps/rubyripper_22.png': No such file or directory
install -D rubyripper.desktop /usr/share/applications/rubyripper.desktop
install: setting permissions for `/usr/share/applications/rubyripper.desktop': No such file or directory
install -m 755 -D rubyripper_cli.rb /usr/bin/rrip_cli
install: setting permissions for `/usr/bin/rrip_cli': No such file or directory
install -D locale/nl/LC_MESSAGES/rr_cli.mo /usr/share/locale/nl/LC_MESSAGES/rr_cli.mo
install: setting permissions for `/usr/share/locale/nl/LC_MESSAGES/rr_cli.mo': No such file or directory
install -D locale/nl/LC_MESSAGES/rr_gtk2.mo /usr/share/locale/nl/LC_MESSAGES/rr_gtk2.mo
install: setting permissions for `/usr/share/locale/nl/LC_MESSAGES/rr_gtk2.mo': No such file or directory
install -D locale/nl/LC_MESSAGES/rr_lib.mo /usr/share/locale/nl/LC_MESSAGES/rr_lib.mo
install: setting permissions for `/usr/share/locale/nl/LC_MESSAGES/rr_lib.mo': No such file or directory
install -D locale/de/LC_MESSAGES/rr_cli.mo /usr/share/locale/de/LC_MESSAGES/rr_cli.mo
install: setting permissions for `/usr/share/locale/de/LC_MESSAGES/rr_cli.mo': No such file or directory
install -D locale/de/LC_MESSAGES/rr_gtk2.mo /usr/share/locale/de/LC_MESSAGES/rr_gtk2.mo
install: setting permissions for `/usr/share/locale/de/LC_MESSAGES/rr_gtk2.mo': No such file or directory
install -D locale/de/LC_MESSAGES/rr_lib.mo /usr/share/locale/de/LC_MESSAGES/rr_lib.mo
install: setting permissions for `/usr/share/locale/de/LC_MESSAGES/rr_lib.mo': No such file or directory
install -D locale/hu/LC_MESSAGES/rr_cli.mo /usr/share/locale/hu/LC_MESSAGES/rr_cli.mo
install: setting permissions for `/usr/share/locale/hu/LC_MESSAGES/rr_cli.mo': No such file or directory
install -D locale/hu/LC_MESSAGES/rr_gtk2.mo /usr/share/locale/hu/LC_MESSAGES/rr_gtk2.mo
install: setting permissions for `/usr/share/locale/hu/LC_MESSAGES/rr_gtk2.mo': No such file or directory
install -D locale/hu/LC_MESSAGES/rr_lib.mo /usr/share/locale/hu/LC_MESSAGES/rr_lib.mo
install: setting permissions for `/usr/share/locale/hu/LC_MESSAGES/rr_lib.mo': No such file or directory
install -D locale/ru/LC_MESSAGES/rr_cli.mo /usr/share/locale/ru/LC_MESSAGES/rr_cli.mo
install: setting permissions for `/usr/share/locale/ru/LC_MESSAGES/rr_cli.mo': No such file or directory
install -D locale/ru/LC_MESSAGES/rr_gtk2.mo /usr/share/locale/ru/LC_MESSAGES/rr_gtk2.mo
install: setting permissions for `/usr/share/locale/ru/LC_MESSAGES/rr_gtk2.mo': No such file or directory
install -D locale/ru/LC_MESSAGES/rr_lib.mo /usr/share/locale/ru/LC_MESSAGES/rr_lib.mo
install: setting permissions for `/usr/share/locale/ru/LC_MESSAGES/rr_lib.mo': No such file or directory
[/COLOR]
======================== Installation successful ==========================

Copying documentation directory...
./
./README
[COLOR="Red"]grep: /var/tmp/GPqjkldVXXBJVRkMdlbdp/newfile: No such file or directory[/COLOR]

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

[COLOR="Red"]Installing Debian package... FAILED!

*** Failed to install the package

Do you want to see the log file?  [y]: y[/COLOR]

*** SIGINT received ***

Cleaning up...OK

Bye.

However, you don't need to install it--the README says you can run it from the ruby folder:

> Run from directory:
(1) ./rubyripper_gtk2.rb or
(1) ./rubyripper_cli.rb

But I can't get it to recognize the audio CD in the drive!

> No audio-disc found !

tried 

/dev/cdrom
and 
/dev/hdc

it is already mounted.

You've got me interested in this ripper and I wish it would cooperate!

???

ADD: BTW, to install I ran

> $ **auto-apt run** ./configure --enable-lang-all --enable-gtk2 --enable-cli --prefix=/usr
$ sudo checkinstall

---

### Post by bionnaki on 2007-12-05
hmmm
this is a mystery.

try /dev/scd1 for the cd drive.

but what about making a .deb? anyone?

---

### Post by shirilover on 2007-12-05
After some trial and error, I have managed to make a deb for rubyripper-0.4.4
This deb is compiled for Feisty.
If you wish to compile for Gutsy or whatever, I have included the source, diff and dsc files as well.
Remove the .txt extension from the dsc file.

---

### Post by bionnaki on 2007-12-06
very nice. thanks!

I am running gutsy & installed the .deb. it seems to work just fine.

but how exactly do you make it for gutsy?

thanks

---

### Post by logos34 on 2007-12-06
well that's odd, it recognizes the cdrom drive enough so that the tray toggle switch 'open tray/close tray' works, but it keeps saying 'no disc found'!  (/dev/scd doesn't work...hdc or cdrom should)...weird...if I could just figure this one little thing out I'd be good to go it seems.

Too bad I'm on x64 ubuntu studio otherwise I'd try that .deb...It seems mine did NOT go in after all because the .deb pkg build failed (so it couldn't then intall the deb).  I'll try it again from the source.

This has got me intrigued because rubyripper would be a nice tool to have...looks like an extra-secure ripper...not sure if it qualifies as someone said for title 'EAC of linux' (which has tons more features) but it's a step in that direction...

---

### Post by bionnaki on 2007-12-06
this might be a stupid way of finding out drives, but if you install k3b and then go to settings>configure k3b>devices your drive will be listed with all the information about that drive.

---

### Post by logos34 on 2007-12-06
k3b says /dev/hdc just like my fstab...beats me...opens the tray but can't recognize any audio cd...guess I'll have to be satisfied with one-pass full cdparanoia on grip and abcde

---

### Post by bionnaki on 2007-12-07
or eac in wine or virtualbox.

---

### Post by logos34 on 2007-12-07
> **bionnaki said:**
> or eac in wine or virtualbox.

tried it already...same story--cd drive box is blank (ditto for cdex).  Other programs I can run in wine just fine, like dBpoweramp, foobar2000 and mp3directcut.  

So you're able to use eac on wine?

UPDATE: 
I got it to install (turns out I needed libgettext-ruby1.8, libgtk2-ruby--thanks shirilover for the -.dsc.txt file).  But still same problem.  What is it with this app?

---

### Post by bionnaki on 2007-12-07
yeah, eac works fine in wine - kinda slow, but works.

and rubyripper works with my drive - maybe your drive is not supported / not as common..?

---

### Post by logos34 on 2007-12-07
I envy you--I love EAC in windows...too bad it won't see the drive.

I don't have anything exotic, just an asus cd/dvd-rw (2 yrs old).  It's probably some other manufacturer underneath (Pioneer? Lite-on?).  I know it doesn't have a couple features like C2 error (too bad) and something else I can't remember.  It's worked great so far.  I checked the ubuntu ripping page (the one linked from REstrictred Formats page) and found the Cd ripping page with stuff on Rubyripper, but no mention of any bug related to what I'm encountering.

Frankly, I'd have given up on this (full cdparanoia is adequate to my needs), but it's little things like this with no apparent explanation that 'bug' me!

---

### Post by shirilover on 2007-12-08
I actually use EAC in wine.
All that is needed is to actually have a CD in the drive before starting it.

---

### Post by logos34 on 2007-12-12
> **shirilover said:**
> I actually use EAC in wine.
All that is needed is to actually have a CD in the drive before starting it.

I just ran winecfg and checked the settings...added CDex and EAC to the programs list, tried different cdrom detect parameters.  CDex now sees my cd/dvd drive, but EAC is still blank no matter what audio cd is in the tray.  Man, if I could just get EAC to work in linux I couldn't care less about rubyripper

---

### Post by shirilover on 2007-12-12
Check the following setting.
After opening EAC, press F9.
Go to the Interface tab and make sure 'Native Win32 interface for WinNT/2000/XP is checked.
Restart EAC.

---

### Post by logos34 on 2007-12-12
> **shirilover said:**
> Check the following setting.
After opening EAC, press F9.
Go to the Interface tab and make sure 'Native Win32 interface for WinNT/2000/XP is checked.
Restart EAC.

that was one of the first things I tried...when I restart eac it's back to the top one (external interface).  

Thing is CDex sees the drive and works now, fetches the tracks from freedb and the whole bit.  Why not eac?  I've gone trough the drive options, eac options and everyhting...I know my way around eac pretty well--have tons of rip profiles in windows and just about every available lossy and lossless encoder   installed even if I never actually use those formats! Iif cdex sees it then obviously the symlink to the cdrom in wine is correct.  It's not a wine issue anymore I don't think. It's things like this that make me feel like a noob all over again!  
 
Thanks for the help so far.  Any other ideas are welcome, because I would really like to figure this out, it shouldn't be this hard.  This isn't my week. (I had to fiddle for hours to get hibernate to work after sudden;y stopping last night. Had to add 'resume=' option to kernel line--never have I needed that before.  hmm).

---

### Post by logos34 on 2007-12-13
Bingo! Got it...Tried changing the Interface again and it finally 'took'.  About time, it's only taken me about TWO DAYS to get this working. 

Thanks again shirilover--might not have given it a second try if it weren't for your suggestion.

---

### Post by Major_Kong on 2008-01-31
Any deb packages avaliable for version 0.5 ?

---

### Post by Major_Kong on 2008-02-07
I'm trying to create a deb package for v. 0.5, but for some reason the destination directory i keep geting is /usr/usr/bin instead of /usr/bin... Any ideas ?

---

### Post by bwtranch on 2008-02-07
A really good tutorial for making .deb packages is available on the web The Debian Maintainer's Guide (sorry I don't have the URL handy, but you can Google) although very slightly dated, it is still the bible for doing this. If someone has a worthwhile project in mind, I could donate a little time to it.

---

### Post by Major_Kong on 2008-02-09
> **bwtranch said:**
> A really good tutorial for making .deb packages is available on the web The Debian Maintainer's Guide (sorry I don't have the URL handy, but you can Google) although very slightly dated, it is still the bible for doing this. If someone has a worthwhile project in mind, I could donate a little time to it.

Already got some help from shirilover on another thread. Thanks anyway.

---

