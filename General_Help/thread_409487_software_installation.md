---
title: "software installation"
date: 2007-04-14
forum: General Help
---

### Post by thebluejay on 2007-04-14
still having lots of problems learning Linux. Trying to install software using tar and/or rpm and having no success. In my latest effort, I received this message from ./configure:

/bin/sh is needed by xbiff2-1.9-0.noarch

I have lots of sh stuff on my computer. How do I know what exactly is missing and how do I find it? (And, BTW, how distressing it is to find something else missing each time another thingie is added!)

hmmmmm.... Am I ever going to get this stuff straight? (Yes, I know, use apt-get or synaptic - but not available for all apps)

---

### Post by energiya on 2007-04-14
First, you need Tcl/Tk (v8.0 or more) - says so on the webpage - then download installxbiff2-1.9.tcl and execute it, or untar xbiff2-1.9.tgz under / .

---

### Post by 23meg on 2007-04-14
> (Yes, I know, use apt-get or synaptic - but not available for all apps)

Are you sure you've [enabled extra repositories]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html")?

These may help you with the basics of installing software:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by thebluejay on 2007-04-14
> **energiya said:**
> First, you need Tcl/Tk (v8.0 or more) - says so on the webpage - then download installxbiff2-1.9.tcl and execute it, or untar xbiff2-1.9.tgz under / .

Yes, I have Tcl/Tk. It tells me I need bin/sh - what's that?

and using tar gives me other problems 

simple answers are never adequate here....

---

### Post by thebluejay on 2007-04-14
> **23meg said:**
> Are you sure you've [enabled extra repositories]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html")?

These may help you with the basics of installing software:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)


I have so many repositories it takes forever to search for stuff! What I want is answers regarding installation using rpm and tar. I still don't know what the missing sh is.

---

### Post by thebluejay on 2007-04-14
By the way, I have read all of  the instructions found here and there about doing these installations. The problem is that that there always seem to be difficulties encountered which require greater explanation.

---

### Post by Maestro23 on 2007-04-14
Compiling from source(tar files) is always tricky because of dependency issues.  Also need to read the INSTALL/README files of the program when installing from source. Below are some links that will help you on installing software(.deb, .rpm, etc...).

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

---

### Post by thebluejay on 2007-04-14
> **Maestro23 said:**
> Compiling from source(tar files) is always tricky because of dependency issues.  Also need to read the INSTALL/README files of the program when installing from source. Below are some links that will help you on installing software(.deb, .rpm, etc...).

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)
  

Just spent hours reading all of this stuff! Not much help when there are 14 dependencies to install. LOL And I still don't know what the missing sh is.

Any ideas anyone?

---

### Post by 23meg on 2007-04-14
RPM isn't native to Ubuntu, and you should use RPM packages only as a very last resort. 

Is there any feature in xbiff 2 that you absolutely must have? If not, an older version of xbiff is in the repositories and you can install it with ```
sudo apt-get install xbiff
``` or you can use another similar program such as Mail Notification or gnubiff.

[QUOTE=thebluejay]and using tar gives me other problems [/QUOTE]

What problems? What exactly do you enter and what are the errors you get? Please copy and paste instead of describing.

[QUOTE=thebluejay]I have so many repositories it takes forever to search for stuff![/QUOTE]

That in itself may be a problem. As a beginner, it's good practice to start with the official Ubuntu extra repositories (Universe and Multiverse) and add other ones only if absolutely necessary.

To reset your sources.list to the default plus Universe and Multiverse, open it

```
gksudo gedit /etc/apt/sources.list
```

delete everything and paste the following

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main 
```

and do 

```
sudo apt-get update
```

---

### Post by Maestro23 on 2007-04-14
Great post 23meg.  Getting ready to post something along those lines myself.:D

---

### Post by thebluejay on 2007-04-14
> **Maestro23 said:**
> Great post 23meg.  Getting ready to post something along those lines myself.:D

Pretty good advice Greg. I will do that. I have tried many of the mail notification programs and have problems installing ALL of them! The ReadMe files don't provide much info. For example, one says in options indicate "X server" or "files". Duh! What server, what file? Instructions seem to be for very experienced users. No indication as to how to tell the program to monitor a certain mail program or mail server.

I won,t give up though. I know that eventually some kind Linux geek will come up with a few wise words that will make me smile.

Thx for all the input guys.

---

### Post by 23meg on 2007-04-14
[QUOTE=thebluejay]The ReadMe files don't provide much info. For example, one says in options indicate "X server" or "files". Duh! What server, what file? Instructions seem to be for very experienced users. No indication as to how to tell the program to monitor a certain mail program or mail server.[/QUOTE]

Look at the manual and help pages or online documentation for usage info, not readme files. If you mean the readme files that come in source packages, those usually include compilation and system wide configuration info that tends to be technical and only of interest if you'll be compiling.

To read manual pages for an app you've installed, type ```
man app_name
```

[QUOTE=thebluejay]I have tried many of the mail notification programs and have problems installing ALL of them! [/QUOTE]

Have you asked for help on those problems?

---

### Post by thebluejay on 2007-04-15
[QUOTE=23meg;2454022]Look at the manual and help pages or online documentation for usage info, not readme files. If you mean the readme files that come in source packages, those usually include compilation and system wide configuration info that tends to be technical and only of interest if you'll be compiling.

To read manual pages for an app you've installed, type ```
man app_name
```



Have you asked for help on those problems?[/Q

Thx for the reply. When I go to the manual for kbiff, for example, I am referred to --help-all, which says this:

Usage: kbiff [Qt-options] [KDE-options] [options]

Full featured mail notification utility.

Generic options:
  --help                    Show help about options
  --help-qt                 Show Qt specific options
  --help-kde                Show KDE specific options
  --help-all                Show all options
  --author                  Show author information
  -v, --version             Show version information
  --license                 Show license information
  --                        End of options

Qt options:
  --display <displayname>   Use the X-server display 'displayname'
  --session <sessionId>     Restore the application for the given 'sessionId'
  --cmap                    Causes the application to install a private color
                            map on an 8-bit display
  --ncols <count>           Limits the number of colors allocated in the color
                            cube on an 8-bit display, if the application is
                            using the QApplication::ManyColor color
                            specification
  --nograb                  tells Qt to never grab the mouse or the keyboard
  --dograb                  running under a debugger can cause an implicit
                            -nograb, use -dograb to override
  --sync                    switches to synchronous mode for debugging
  --fn, --font <fontname>   defines the application font
  --bg, --background <color> sets the default background color and an
                            application palette (light and dark shades are
                            calculated)
  --fg, --foreground <color> sets the default foreground color
  --btn, --button <color>   sets the default button color
  --name <name>             sets the application name
  --title <title>           sets the application title (caption)
  --visual TrueColor        forces the application to use a TrueColor visual on
                            an 8-bit display
  --inputstyle <inputstyle> sets XIM (X Input Method) input style. Possible
                            values are onthespot, overthespot, offthespot and
                            root
  --im <XIM server>         set XIM server
  --noxim                   disable XIM
  --reverse                 mirrors the whole layout of widgets

KDE options:
  --caption <caption>       Use 'caption' as name in the titlebar
  --icon <icon>             Use 'icon' as the application icon
  --miniicon <icon>         Use 'icon' as the icon in the titlebar
  --config <filename>       Use alternative configuration file
  --dcopserver <server>     Use the DCOP Server specified by 'server'
  --nocrashhandler          Disable crash handler, to get core dumps
  --waitforwm               Waits for a WM_NET compatible windowmanager
  --style <style>           sets the application GUI style
  --geometry <geometry>     sets the client geometry of the main widget - see man X for the argument format

Options:
  --secure                  Run in secure mode
  --profile <profile>       Use 'profile'

Now maybe I'm stupid, but I find this totally incomprehensible. Perhaps a programmer could understand it.
 --display <displayname>   Use the X-server display 'displayname'
  --session <sessionId>     Restore the application for the given 'sessionId'

What in the world does that mean? Maybe it's just a bad help file but I find most are like that. An explanation and example would be so nice so I could understand exactly what the command does and what information needs to be inserted to configure the command. Where do i find a displayname, an X-server and a sessionId, and what the heck are they anyway?

See what I mean?

---

### Post by thebluejay on 2007-04-15
> **23meg said:**
> RPM isn't native to Ubuntu, and you should use RPM packages only as a very last resort. 

Is there any feature in xbiff 2 that you absolutely must have? If not, an older version of xbiff is in the repositories and you can install it with ```
sudo apt-get install xbiff
``` or you can use another similar program such as Mail Notification or gnubiff.



What problems? What exactly do you enter and what are the errors you get? Please copy and paste instead of describing.



That in itself may be a problem. As a beginner, it's good practice to start with the official Ubuntu extra repositories (Universe and Multiverse) and add other ones only if absolutely necessary.

To reset your sources.list to the default plus Universe and Multiverse, open it

```
gksudo gedit /etc/apt/sources.list
```

delete everything and paste the following

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main 
```

and do 

```
sudo apt-get update
```

Now THAT is the way to give instructions! THX! I fixed up my repository list. Finally got kbiff working (not sure how! LOL) but now faced with two new issues: 1) kbiff doesn't seem to be loading at startup. I check the processes and don't see it there. If I put it in apps to start using the kbiff command alone, it runs the configuration utility which I no longer need because that has been done. I just want the program to run in the background and notify me if mail arrives.
2) Even if that succeeds somehow, it won't work because I don't get a network connection on bootup. Network-admin shows the connection as activated, but I have to deactivate and  reactivate to get it operative. Can that be fixed?

I must say that even though I am facing all of these difficulties it is real fun because so much help is willingly offered in this forum. Greatly appreciated. :)

---

### Post by thebluejay on 2007-04-15
[QUOTE=23meg;2453919]

What problems? What exactly do you enter and what are the errors you get? Please copy and paste instead of describing.

OK - taking you at your word.  ;)

I am trying to install program cbb-0.9.5. I downloaded cbb-0.9.5b.tgz and extarcted it to my "extract" directory. I then ran ./configure followed by make install which gave me the following result (sorry about the length):

--------------------------------------------------------------------
root@linux:/home/jaylinux/extract# ls
cbb-0.9.5
root@linux:/home/jaylinux/extract# cd cbb-0.9.5
root@linux:/home/jaylinux/extract/cbb-0.9.5# ./configure
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for perl... (cached) /usr/bin/perl
checking for wish4.2... no
checking for wish4.1... no
checking for wish4.0... no
checking for wish... no
***************************************
 CBB requires tcl!  Please check your
 tcl installation, or specify the
 fully-qualified wish filename with the
 --with-wish option.
***************************************
creating ./config.status
creating Makefile
creating contrib/Makefile
creating cbb
creating cbbdb
creating docs/Makefile
creating docs/cbb-man/Makefile
creating docs/cbb-man/icons.png/Makefile
creating etc/Makefile
creating graphs/cat-col.pl
creating graphs/cat-pie.pl
creating graphs/cat2-col.pl
creating graphs/desc-pie.pl
creating graphs/txn-list.pl
creating graphs/Makefile
creating graphs/descpie
creating graphs/graphbal
creating graphs/graphcol
creating graphs/graphcolpos
creating graphs/graphpie
creating images/Makefile
creating languages/Makefile
creating perl/Makefile
creating reports/ave-by-cat.pl
creating reports/by-cat.pl
creating reports/by-payee.pl
creating reports/miss-check.pl
creating reports/shrt-by-cat.pl
creating reports/rep-txn-list.pl
creating reports/uncleared-txn.pl
creating reports/Makefile
creating tcl/Makefile
creating Version
root@linux:/home/jaylinux/extract/cbb-0.9.5# make install
Making install in contrib
make[1]: Entering directory `/home/jaylinux/extract/cbb-0.9.5/contrib'
umask 022; \
        if test '!' -d /usr/local/bin; then \
                mkdir -p /usr/local/bin; \
        fi; \
        if test '!' -d /usr/local/lib/cbb-0.9/contrib; then \
                mkdir -p /usr/local/lib/cbb-0.9/contrib; \
        fi;
if test -n ""; then \
                /usr/bin/install -c  /usr/local/bin; \
        fi;
if test -n "change.pl conv-french-qif.pl emacs-edb emacs-forms fetch-latest.pl importcat.README importcat.pl invest.pl loan.gnuplot loan.pl loan_recur.pl mym_to_cbb.pl recur.pl term.pl trimold.pl txn txn.README upgrade-splits.pl yearend.pl"; then \
                /usr/bin/install -c change.pl conv-french-qif.pl emacs-edb emacs-forms fetch-latest.pl importcat.README importcat.pl invest.pl loan.gnuplot loan.pl loan_recur.pl mym_to_cbb.pl recur.pl term.pl trimold.pl txn txn.README upgrade-splits.pl yearend.pl /usr/local/lib/cbb-0.9/contrib; \
        fi;
make[1]: Leaving directory `/home/jaylinux/extract/cbb-0.9.5/contrib'
Making install in docs
make[1]: Entering directory `/home/jaylinux/extract/cbb-0.9.5/docs'
Making install in cbb-man
make[2]: Entering directory `/home/jaylinux/extract/cbb-0.9.5/docs/cbb-man'
Making install in icons.png
make[3]: Entering directory `/home/jaylinux/extract/cbb-0.9.5/docs/cbb-man/icons.png'
umask 022; \
        if test '!' -d /usr/local/bin; then \
                mkdir -p /usr/local/bin; \
        fi; \
        if test '!' -d /usr/local/lib/cbb-0.9/docs/cbb-man/icons.png; then \
                mkdir -p /usr/local/lib/cbb-0.9/docs/cbb-man/icons.png; \
        fi;
if test -n ""; then \
                /usr/bin/install -c  /usr/local/bin; \
        fi;
if test -n "blueball.png change_begin.png change_delete.png change_end.png contents_motif.png cross_ref_motif.png foot_motif.png greenball.png image.png index_motif.png next_group_motif.png next_group_motif_gr.png next_motif.png next_motif_gr.png orangeball.png pinkball.png previous_group_motif.png previous_group_motif_gr.png previous_motif.png previous_motif_gr.png purpleball.png redball.png up_motif.png up_motif_gr.png whiteball.png yellowball.png"; then \
                /usr/bin/install -c blueball.png change_begin.png change_delete.png change_end.png contents_motif.png cross_ref_motif.png foot_motif.png greenball.png image.png index_motif.png next_group_motif.png next_group_motif_gr.png next_motif.png next_motif_gr.png orangeball.png pinkball.png previous_group_motif.png previous_group_motif_gr.png previous_motif.png previous_motif_gr.png purpleball.png redball.png up_motif.png up_motif_gr.png whiteball.png yellowball.png /usr/local/lib/cbb-0.9/docs/cbb-man/icons.png; \
        fi;
make[3]: Leaving directory `/home/jaylinux/extract/cbb-0.9.5/docs/cbb-man/icons.png'
umask 022; \
        if test '!' -d /usr/local/bin; then \
                mkdir -p /usr/local/bin; \
        fi; \
        if test '!' -d /usr/local/lib/cbb-0.9/docs/cbb-man; then \
                mkdir -p /usr/local/lib/cbb-0.9/docs/cbb-man; \
        fi;
if test -n ""; then \
                /usr/bin/install -c  /usr/local/bin; \
        fi;
if test -n "cbb-man.html index.html img1.png img2.png img3.png"; then \
                /usr/bin/install -c cbb-man.html index.html img1.png img2.png img3.png /usr/local/lib/cbb-0.9/docs/cbb-man; \
        fi;
make[2]: Leaving directory `/home/jaylinux/extract/cbb-0.9.5/docs/cbb-man'
umask 022; \
        if test '!' -d /usr/local/bin; then \
                mkdir -p /usr/local/bin; \
        fi; \
        if test '!' -d /usr/local/lib/cbb-0.9/docs; then \
                mkdir -p /usr/local/lib/cbb-0.9/docs; \
        fi;
if test -n ""; then \
                /usr/bin/install -c  /usr/local/bin; \
        fi;
if test -n "cbb-man.txt graphs.txt notes perl.commands perl.functions plsubs tcl.functions todo.txt update.notes"; then \
                /usr/bin/install -c cbb-man.txt graphs.txt notes perl.commands perl.functions plsubs tcl.functions todo.txt update.notes /usr/local/lib/cbb-0.9/docs; \
        fi;
make[1]: Leaving directory `/home/jaylinux/extract/cbb-0.9.5/docs'
Making install in etc
make[1]: Entering directory `/home/jaylinux/extract/cbb-0.9.5/etc'
umask 022; \
        if test '!' -d /usr/local/bin; then \
                mkdir -p /usr/local/bin; \
        fi; \
        if test '!' -d /usr/local/lib/cbb-0.9/etc; then \
                mkdir -p /usr/local/lib/cbb-0.9/etc; \
        fi;
if test -n ""; then \
                /usr/bin/install -c  /usr/local/bin; \
        fi;
if test -n "default.cat extern.conf"; then \
                /usr/bin/install -c default.cat extern.conf /usr/local/lib/cbb-0.9/etc; \
        fi;
make[1]: Leaving directory `/home/jaylinux/extract/cbb-0.9.5/etc'
Making install in graphs
make[1]: Entering directory `/home/jaylinux/extract/cbb-0.9.5/graphs'
umask 022; \
        if test '!' -d /usr/local/bin; then \
                mkdir -p /usr/local/bin; \
        fi; \
        if test '!' -d /usr/local/lib/cbb-0.9/graphs; then \
                mkdir -p /usr/local/lib/cbb-0.9/graphs; \
        fi;
if test -n ""; then \
                /usr/bin/install -c  /usr/local/bin; \
        fi;
if test -n "cat-col.pl cat-pie.pl cat2-col.pl desc-pie.pl descpie graphbal graphcol graphcolpos graphpie graphs.conf txn-list.pl"; then \
                /usr/bin/install -c cat-col.pl cat-pie.pl cat2-col.pl desc-pie.pl descpie graphbal graphcol graphcolpos graphpie graphs.conf txn-list.pl /usr/local/lib/cbb-0.9/graphs; \
        fi;
make[1]: Leaving directory `/home/jaylinux/extract/cbb-0.9.5/graphs'
Making install in images
make[1]: Entering directory `/home/jaylinux/extract/cbb-0.9.5/images'
umask 022; \
        if test '!' -d /usr/local/bin; then \
                mkdir -p /usr/local/bin; \
        fi; \
        if test '!' -d /usr/local/lib/cbb-0.9/images; then \
                mkdir -p /usr/local/lib/cbb-0.9/images; \
        fi;
if test -n ""; then \
                /usr/bin/install -c  /usr/local/bin; \
        fi;
if test -n "author.xbm cbb.xbm mini-cross.gif mini-exclam.gif splash-32.gif"; then \
                /usr/bin/install -c author.xbm cbb.xbm mini-cross.gif mini-exclam.gif splash-32.gif /usr/local/lib/cbb-0.9/images; \
        fi;
make[1]: Leaving directory `/home/jaylinux/extract/cbb-0.9.5/images'
Making install in languages
make[1]: Entering directory `/home/jaylinux/extract/cbb-0.9.5/languages'
umask 022; \
        if test '!' -d /usr/local/bin; then \
                mkdir -p /usr/local/bin; \
        fi; \
        if test '!' -d /usr/local/lib/cbb-0.9/languages; then \
                mkdir -p /usr/local/lib/cbb-0.9/languages; \
        fi;
if test -n ""; then \
                /usr/bin/install -c  /usr/local/bin; \
        fi;
if test -n "english.tcl french.tcl german.tcl"; then \
                /usr/bin/install -c english.tcl french.tcl german.tcl /usr/local/lib/cbb-0.9/languages; \
        fi;
make[1]: Leaving directory `/home/jaylinux/extract/cbb-0.9.5/languages'
Making install in perl
make[1]: Entering directory `/home/jaylinux/extract/cbb-0.9.5/perl'
umask 022; \
        if test '!' -d /usr/local/bin; then \
                mkdir -p /usr/local/bin; \
        fi; \
        if test '!' -d /usr/local/lib/cbb-0.9/perl; then \
                mkdir -p /usr/local/lib/cbb-0.9/perl; \
        fi;
if test -n ""; then \
                /usr/bin/install -c  /usr/local/bin; \
        fi;
if test -n "accounts.pl categories.pl common.pl engine.pl export.pl file.pl groups.pl import.pl log.pl memorized.pl reports.pl"; then \
                /usr/bin/install -c accounts.pl categories.pl common.pl engine.pl export.pl file.pl groups.pl import.pl log.pl memorized.pl reports.pl /usr/local/lib/cbb-0.9/perl; \
        fi;
make[1]: Leaving directory `/home/jaylinux/extract/cbb-0.9.5/perl'
Making install in reports
make[1]: Entering directory `/home/jaylinux/extract/cbb-0.9.5/reports'
umask 022; \
        if test '!' -d /usr/local/bin; then \
                mkdir -p /usr/local/bin; \
        fi; \
        if test '!' -d /usr/local/lib/cbb-0.9/reports; then \
                mkdir -p /usr/local/lib/cbb-0.9/reports; \
        fi;
if test -n ""; then \
                /usr/bin/install -c  /usr/local/bin; \
        fi;
if test -n "ave-by-cat.pl by-cat.pl by-payee.pl miss-check.pl reports.conf shrt-by-cat.pl rep-txn-list.pl uncleared-txn.pl"; then \
                /usr/bin/install -c ave-by-cat.pl by-cat.pl by-payee.pl miss-check.pl reports.conf shrt-by-cat.pl rep-txn-list.pl uncleared-txn.pl /usr/local/lib/cbb-0.9/reports; \
        fi;
make[1]: Leaving directory `/home/jaylinux/extract/cbb-0.9.5/reports'
Making install in tcl
make[1]: Entering directory `/home/jaylinux/extract/cbb-0.9.5/tcl'
umask 022; \
        if test '!' -d /usr/local/bin; then \
                mkdir -p /usr/local/bin; \
        fi; \
        if test '!' -d /usr/local/lib/cbb-0.9/tcl; then \
                mkdir -p /usr/local/lib/cbb-0.9/tcl; \
        fi;
if test -n ""; then \
                /usr/bin/install -c  /usr/local/bin; \
        fi;
if test -n "balance.tcl balloon.tcl bindings.tcl categories.tcl common.tcl dates.tcl file.tcl filebox.tcl help.tcl init.tcl main.tcl menu.tcl prefs.tcl reports.tcl splits.tcl undo.tcl"; then \
                /usr/bin/install -c balance.tcl balloon.tcl bindings.tcl categories.tcl common.tcl dates.tcl file.tcl filebox.tcl help.tcl init.tcl main.tcl menu.tcl prefs.tcl reports.tcl splits.tcl undo.tcl /usr/local/lib/cbb-0.9/tcl; \
        fi;
make[1]: Leaving directory `/home/jaylinux/extract/cbb-0.9.5/tcl'
umask 022; \
        if test '!' -d /usr/local/bin; then \
                mkdir -p /usr/local/bin; \
        fi; \
        if test '!' -d /usr/local/lib/cbb-0.9; then \
                mkdir -p /usr/local/lib/cbb-0.9; \
        fi;
if test -n "cbb"; then \
                /usr/bin/install -c cbb /usr/local/bin; \
        fi;
if test -n "cbbdb"; then \
                /usr/bin/install -c cbbdb /usr/local/lib/cbb-0.9; \
        fi;
root@linux:/home/jaylinux/extract/cbb-0.9.5# 

------------------------------------------------------------------------
I then looked for my installed cbb and it is nowhere to be found. The only cbb file found with the "find" command was a text document  here:
cbb: /usr/local/bin/cbb which reads as follows (and which makes no sense at all to me):

______________________________________________
#! not_found
#
#  'CBB' -- Check Book Balancer
#           Front end to the perl engine.
#
#  Written by Curtis Olson.  Started August 25, 1994.
#
#  Copyright (C) 1994 - 1999  Curtis L. Olson  - [email]curt@me.umn.edu[/email]
#
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this program; if not, write to the Free Software
#  Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#
# cbb.in,v 0.11 2001/07/13 04:05:58 briank Exp

set lib_path /usr/local/lib/cbb-0.9

# load needed functions
source "$lib_path/tcl/common.tcl"

# Load first tcl piece (creates splash screen procedure)
source "$lib_path/tcl/init.tcl"

# read the default user files
set cbb(splash) 1
cbb_init_language english 
cbb_init_vars

if { $cbb(splash) } {
    # disable main window and draw splash screen
    wm withdraw .
    cbb_splash
}

# Load the rest of the tcl pieces
source "$lib_path/tcl/balance.tcl"
source "$lib_path/tcl/balloon.tcl"
source "$lib_path/tcl/bindings.tcl"
source "$lib_path/tcl/categories.tcl"
source "$lib_path/tcl/dates.tcl"
source "$lib_path/tcl/file.tcl"
source "$lib_path/tcl/filebox.tcl"
source "$lib_path/tcl/help.tcl"
source "$lib_path/tcl/main.tcl"
source "$lib_path/tcl/menu.tcl"
source "$lib_path/tcl/prefs.tcl"
source "$lib_path/tcl/reports.tcl"
source "$lib_path/tcl/splits.tcl"
source "$lib_path/tcl/undo.tcl"

# initialize variables, parse command line, setup main window, etc.
cbb_setup

_______________________________________________

Did I do something wrong? What happened to my program? 

Thanks in advance.

---

### Post by 23meg on 2007-04-15
[QUOTE=thebluejay]
What in the world does that mean? Maybe it's just a bad help file but I find most are like that. An explanation and example would be so nice so I could understand exactly what the command does and what information needs to be inserted to configure the command. Where do i find a displayname, an X-server and a sessionId, and what the heck are they anyway?

See what I mean?[/QUOTE]These are options that you should enter as suffixes to the command "kbiff". For example "kbiff --bg white" is supposed to launch it with a white background. You only need to know what the display name is, what an X server is etc. if you need to run kbiff on a non-default, specific display. They're options, hence the name; if you just type "kbiff", it will run with default settings. Besides, most graphical applications have graphical option dialogs as well.

---

### Post by thebluejay on 2007-04-15
thx for the reply 23meg. It would still be nice to know what the options do and how to use them simply as a matter of intellectual curiosity. When I begin to write my own programs, I'll put in all the details. :)

---

### Post by ipguru99 on 2007-04-19
Also might be the same issue here:
[http://ubuntuforums.org/showthread.php?t=410424&highlight=compiling](http://ubuntuforums.org/showthread.php?t=410424&highlight=compiling)

Several things I was trying to compile were not working and complaining about 'no sh'

The developers are using dash instead of bash.. and linking /bin/sh to dash instead of bash

Do a ls -l /bin/sh  
If you see /bin/sh -> dash, you can do a 
sudo dpkg-reconfigure dash
Answer NO
Then do a ls -l /bin/sh
It should now be /bin/sh -> bash

This has worked for me...

Of course, everything else being said in this post is true as well, but when i saw the 'missing sh'.. I had to throw my .02 in!

ipguru99

---

### Post by thebluejay on 2007-04-22
I give up! Things weren't working on my desktop so I decided to reinstall and found there was an upgrade with a GUI installer. Just what I needed. So I downloaded it and the installation files told me that I needed a bunch of "dependencies". Spent an hour or so hunting for those--and there are different ones for different distros apparently--and finally was ready to go. Ran the installer and was told gcc was missing - whatever that was.  After much searching, I finally found something that looked right and installed a bunch of stuff that meant nothing to me. Tons of stuff in Synaptic called gcc* Just added about everyting with gcc in it. LOL. Tried again--oh, yes--had to find some Glib stuff and GModules or something like that--again stuff that could not clearly be identified in Synaptic. One more time, oooops gtk missing. What the....????

This was getting discouraging. Well after about three hours, I finall got the installer to run. Whooooopeeee! I get a graphic interface: wizard to install wfce4. Excellent! I click next and get a message. These are the files you need to run the installer: I get a list of many files, of which it tells me I am missing 12!!

Not again!!

Determined, I go hunting. sudo apt-get install libxml--Result: not found. Lots of files with those letters in Synaptic, but which ones do I need. Install a bunch. Replies that all could not be found, some missing. Hmmm....

Then I hunted for vte. Nowhere to be found. Some files with those letters in Synaptic. Installed a few. Told parts missing.

Enough! Enough! After about 5 hours of this, I QUIT. Never did get my desktop upgrade.

Do all Linux users go through this crap or is it just me? 

Jay

---

### Post by jfinkels on 2007-04-22
> **thebluejay said:**
> I give up! Things weren't working on my desktop so I decided to reinstall and found there was an upgrade with a GUI installer. Just what I needed. So I downloaded it and the installation files told me that I needed a bunch of "dependencies". Spent an hour or so hunting for those--and there are different ones for different distros apparently--and finally was ready to go. Ran the installer and was told gcc was missing - whatever that was.  After much searching, I finally found something that looked right and installed a bunch of stuff that meant nothing to me. Tons of stuff in Synaptic called gcc* Just added about everyting with gcc in it. LOL. Tried again--oh, yes--had to find some Glib stuff and GModules or something like that--again stuff that could not clearly be identified in Synaptic. One more time, oooops gtk missing. What the....????

This was getting discouraging. Well after about three hours, I finall got the installer to run. Whooooopeeee! I get a graphic interface: wizard to install wfce4. Excellent! I click next and get a message. These are the files you need to run the installer: I get a list of many files, of which it tells me I am missing 12!!

Not again!!

Determined, I go hunting. sudo apt-get install libxml--Result: not found. Lots of files with those letters in Synaptic, but which ones do I need. Install a bunch. Replies that all could not be found, some missing. Hmmm....

Then I hunted for vte. Nowhere to be found. Some files with those letters in Synaptic. Installed a few. Told parts missing.

Enough! Enough! After about 5 hours of this, I QUIT. Never did get my desktop upgrade.

Do all Linux users go through this crap or is it just me? 

Jay

If you give us a list of exactly what dependencies you need, we can help explain what you need to do! For the most part, if you need to install a package, Synaptic will automatically mark necessary dependencies for installation. And if, for some reason, you are installing a program outside of Synaptic (which you should NOT be doing yet), then you can search Synaptic for it (installing the highest version number is usually the best way to go).

---

### Post by Dave54 on 2007-04-22
When I was new to linux I had many experiences like this. Now that I'm more experienced, I have a new rule of thumb:

If I want to install something, I use synaptic. If it isn't there, I search online to see if someone has a file ending in **.deb** to download. (once downloaded, a simple double click will install it, kinda like an exe.) If there isn't a deb, then I download something ending in a .rpm, and use "sudo alien -i [file].rpm" to turn it into a deb. If I can't find a deb or rpm, I either ask someone to compile it for me, or give up.

If I ever run into dependency problems, that means there was an error in what I was trying to install, and I don't try to install it anymore.

Linux can be nice, but it has a lot of traps to fall in.

Good luck!
-Dave

EDIT: oh, I almost forgot. It's also good to check for a repository that you can add in order to install a piece of software with synaptic.

---

### Post by jfinkels on 2007-04-22
> **Dave54 said:**
> When I was new to linux I had many experiences like this. Now that I'm more experienced, I have a new rule of thumb:

If I want to install something, I use synaptic. If it isn't there, I search online to see if someone has a file ending in **.deb** to download. (once downloaded, a simple double click will install it, kinda like an exe.) If there isn't a deb, then I download something ending in a .rpm, and use "sudo alien -i [file].rpm" to turn it into a deb. If I can't find a deb or rpm, I either ask someone to compile it for me, or give up.

If I ever run into dependency problems, that means there was an error in what I was trying to install, and I don't try to install it anymore.

Linux can be nice, but it has a lot of traps to fall in.

Good luck!
-Dave

EDIT: oh, I almost forgot. It's also good to check for a repository that you can add in order to install a piece of software with synaptic.

Just give us a holler if you need help compiling :D

---

