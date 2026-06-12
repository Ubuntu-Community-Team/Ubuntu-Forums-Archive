---
title: "How to Compile?"
date: 2005-05-09
forum: General Help
---

### Post by ntrsfrml on 2005-05-09
Can somebody please help me with Compiling tips? I'm a Linux noob so i really need spoon feeding on this one :(

I was trying to Install Ettercap.. extracted the source to a new folder.. read the Install file which says: 

```
 1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

```

What i dont understand is where to Type these commands( make install/configure, etc) what are the steps one should follow in order to compile a source and install?


Please help  ](*,)

---

### Post by kori.mendocino on 2005-05-09
you need to type all of this into a terminal window. you should be able to open one via the menu > system tools > terminal. try doing this, follow all the guidelines in the readme and if you have more questions, reply here

---

### Post by dodger on 2005-05-09
why don't you just

sudo apt-get install ettercap

it's in the universe repository.

iy however, you really want to compile it yourself, I think you first have to 

sudo apt-get install build-essential

which will install some packages that you need to compile anything.

then you open a console and cd to the directory where you unpacked your source-files to.
there you type the commands.

make sure to sudo the make install command.

hope this helps.

have fun,

dodger

---

### Post by Xian on 2005-05-09
[QUOTE=ntrsfrml]What i dont understand is where to Type these commands( make install/configure, etc) what are the steps one should follow in order to compile a source and install?[/QUOTE]
Just right-click on the desktop and select 'Open Terminal'.
That's where you input the commands.

The 'make install' command you need to do with the 'sudo' preface:
$ sudo make install

Read [THIS](http://www.tuxfiles.org/linuxhelp/softinstall.html) link. It will answer many of your questions.

---

### Post by ntrsfrml on 2005-05-10
[QUOTE=Xian]Just right-click on the desktop and select 'Open Terminal'.
That's where you input the commands.

The 'make install' command you need to do with the 'sudo' preface:
$ sudo make install

Read [THIS](http://www.tuxfiles.org/linuxhelp/softinstall.html) link. It will answer many of your questions.[/QUOTE]
 I tried everything..but its still not helping :(

[[IMG]http://img176.echo.cx/img176/5663/stillnothelping4bf.th.jpg[/IMG]](http://img176.echo.cx/my.php?image=stillnothelping4bf.jpg)


> iy however, you really want to compile it yourself, I think you first have to

sudo apt-get install build-essential

which will install some packages that you need to compile anything.

then you open a console and cd to the directory where you unpacked your source-files to.
there you type the commands.

make sure to sudo the make install command.


Yes, i have the Basic build installed..when you say Open console and CD to the directory..what console you are talking about? Menu>>system tools>>Terminal ??

Can somebody please give me a "step by step" guidelines on this one..i really need this :(

many thanks :)

---

### Post by Xian on 2005-05-10
[QUOTE=ntrsfrml]I tried everything..but its still not helping :(

[[IMG]http://img176.echo.cx/img176/5663/stillnothelping4bf.th.jpg[/IMG]](http://img176.echo.cx/my.php?image=stillnothelping4bf.jpg)[/QUOTE]
That only shows the 'make install' session.
Were you able to complete the './configure' and 'make' commands successfully?

Did you receive any errors?
If so and one of those other sessions aborts then 'make install' can't finish.

---

### Post by ntrsfrml on 2005-05-10
[QUOTE=Xian]That only shows the 'make install' session.
Were you able to complete the './configure' and 'make' commands successfully?

Did you receive any errors?
If so and one of those other sessions aborts then 'make install' can't finish.[/QUOTE]

Yes i was able to complete those commands..here is a screenshot

[[IMG]http://img159.echo.cx/img159/470/makenew1ho.th.jpg[/IMG]](http://img159.echo.cx/my.php?image=makenew1ho.jpg)

what should i do next?

---

### Post by ntrsfrml on 2005-05-10
[QUOTE=ntrsfrml]Yes i was able to complete those commands..here is a screenshot

[[IMG]http://img159.echo.cx/img159/470/makenew1ho.th.jpg[/IMG]](http://img159.echo.cx/my.php?image=makenew1ho.jpg)

what should i do next?[/QUOTE]
 Bump!

---

### Post by bored2k on 2005-05-10
[QUOTE=ntrsfrml]Bump![/QUOTE]

I dont see any screenshot..

---

### Post by ntrsfrml on 2005-05-10
[QUOTE=bored2k]I dont see any screenshot..[/QUOTE]

[http://img159.echo.cx/img159/470/makenew1ho.jpg](http://img159.echo.cx/img159/470/makenew1ho.jpg)

see now? :)

---

### Post by Xian on 2005-05-10
That's not going to quite get it, I'm afraid. :)

Download the file ettercap-NG-0.7.2.tar.gz to your /home directory.

Open the file browser (nautilus) and goto /home, then right-click on the file and choose 'Extract Here'. Then open a terminal and type in the following:

$ cd /home/<your_user-name_here>/ettercap-NG-0.7.2.tar.gz_FILES/ettercap-NG-0.7.2
$ ./configure

You will then see some text scrool by that looks like this:
```
Configuring ettercap NG-0.7.2...

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
</snip>
```

After this finishes and IF you get no errors then issue the next two commands in sequence.

$ make
$ sudo make install

---

### Post by ntrsfrml on 2005-05-10
[QUOTE=Xian]That's not going to quite get it, I'm afraid. :)

Download the file ettercap-NG-0.7.2.tar.gz to your /home directory.

Open the file browser (nautilus) and goto /home, then right-click on the file and choose 'Extract Here'. Then open a terminal and type in the following:

$ cd /home/<your_user-name_here>/ettercap-NG-0.7.2.tar.gz_FILES/ettercap-NG-0.7.2
$ ./configure

You will then see some text scrool by that looks like this:
```
Configuring ettercap NG-0.7.2...

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
</snip>
```

After this finishes and IF you get no errors then issue the next two commands in sequence.

$ make
$ sudo make install[/QUOTE]


Okay, i followed the instructions.. here is what i get:

[[IMG]http://img148.echo.cx/img148/2600/newmakeinstall3qp.th.jpg[/IMG]](http://img148.echo.cx/my.php?image=newmakeinstall3qp.jpg)

```
checking for library containing gethostbyname... none required
checking for library containing socket... none required
checking for library containing poll... none required
checking for library containing gzopen... no
configure: error: not found.
manu15@MSHOME:~/ettercap-NG-0.7.2.tar.gz_FILES/ettercap-NG-0.7.2$ make
make: *** No targets specified and no makefile found.  Stop.
manu15@MSHOME:~/ettercap-NG-0.7.2.tar.gz_FILES/ettercap-NG-0.7.2$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
manu15@MSHOME:~/ettercap-NG-0.7.2.tar.gz_FILES/ettercap-NG-0.7.2$

```

I don't understand ^^this^^ part..Am I missing some install tools?

thanks.

---

### Post by Xian on 2005-05-10
[QUOTE=ntrsfrml]I don't understand ^^this^^ part..Am I missing some install tools?[/QUOTE]
Try this:
$ sudo apt-get install zlib1g-dev liblzo-dev

Then start the ./configure process again.

---

### Post by ntrsfrml on 2005-05-10
[QUOTE=Xian]Try this:
$ sudo apt-get install zlib1g-dev liblzo-dev

Then start the ./configure process again.[/QUOTE]

still getting errors :(

[[IMG]http://img235.echo.cx/img235/1293/nolibcap3hb.th.jpg[/IMG]](http://img235.echo.cx/my.php?image=nolibcap3hb.jpg)

---

### Post by Xian on 2005-05-10
[QUOTE=ntrsfrml]still getting errors :([/QUOTE]
Well, yes...but they're not the same errors. :) 

You need to grab the packages listed below, as they are obviously included in the missing dependencies for this installation. When you get things like this just look at what the error message is referring to and then search for that and the corresponding dev file (if it exists) in Synaptic. For example, you got the message "checking for libpcap....no". That package is in Synaptic and so is libpcap-dev. They both need to be installed.

After this you will get another error message about a missing dep, but I've taken care of that ahead of time by including it as well in this command:

$ sudo apt-get install libpcap0.8-dev libnet1-dev

---

### Post by ntrsfrml on 2005-05-11
[QUOTE=Xian]Well, yes...but they're not the same errors. :) 

You need to grab the packages listed below, as they are obviously included in the missing dependencies for this installation. When you get things like this just look at what the error message is referring to and then search for that and the corresponding dev file (if it exists) in Synaptic. For example, you got the message "checking for libpcap....no". That package is in Synaptic and so is libpcap-dev. They both need to be installed.

After this you will get another error message about a missing dep, but I've taken care of that ahead of time by including it as well in this command:

$ sudo apt-get install libpcap0.8-dev libnet1-dev[/QUOTE]

Okay, I installed libcap, etc and still getting errors :(

[[IMG]http://img132.echo.cx/img132/6278/newerrors3gp.th.jpg[/IMG]](http://img132.echo.cx/my.php?image=newerrors3gp.jpg)

---

### Post by Xian on 2005-05-11
Try this: 

sudo apt-get install libgtk2.0-dev

---

### Post by ntrsfrml on 2005-05-11
[QUOTE=Xian]Try this: 

sudo apt-get install libgtk2.0-dev[/QUOTE]

Looks like some repository is down?

[[IMG]http://img224.echo.cx/img224/3392/repositorydown6jj.th.jpg[/IMG]](http://img224.echo.cx/my.php?image=repositorydown6jj.jpg)

I tried running apt-get update and get this halt..its stuck there :(

[[IMG]http://img142.echo.cx/img142/7363/aptgetupdate9ki.th.jpg[/IMG]](http://img142.echo.cx/my.php?image=aptgetupdate9ki.jpg)

---

### Post by bored2k on 2005-05-11
[QUOTE=ntrsfrml]Looks like some repository is down?

[[IMG]http://img224.echo.cx/img224/3392/repositorydown6jj.th.jpg[/IMG]](http://img224.echo.cx/my.php?image=repositorydown6jj.jpg)

I tried running apt-get update and get this halt..its stuck there :(

[[IMG]http://img142.echo.cx/img142/7363/aptgetupdate9ki.th.jpg[/IMG]](http://img142.echo.cx/my.php?image=aptgetupdate9ki.jpg)[/QUOTE]
 The repository are OK. I just dist-upgraded. Get that marillat's out of the way and It will go smooth. Cool car. And what the heck who listening to lol

---

### Post by ntrsfrml on 2005-05-11
[QUOTE=bored2k]The repository are OK. I just dist-upgraded. Get that marillat's out of the way and It will go smooth. Cool car. And what the heck who listening to lol[/QUOTE]

hey bud, thanks for the compliments :).. I'm very new to Ubuntu/Linux scenario.. how do i get rid of marillat repository?

thanks :)

---

### Post by kori.mendocino on 2005-05-11
in your terminal, type $sudo gedit /etc/apt/sources.list and delete or uncomment (place a # in the beginning of the line) all the lines that contain 'marillat', then save and refresh your list.

---

### Post by ntrsfrml on 2005-05-11
alright..i did all that..tried the 

 # ./configure
# make
# make install 

and the terminal went nuts with all that code..lol (finally compiling eh??)

now i get this:

[[IMG]http://img202.echo.cx/img202/4520/newnewnew8dq.th.jpg[/IMG]](http://img202.echo.cx/my.php?image=newnewnew8dq.jpg)

refreshed the Gnome..now where is the installed program? I Looked everywhere but can't find the Ettercap?

thanks :)

---

### Post by void_false on 2005-05-11
[QUOTE=ntrsfrml]alright..i did all that..tried the 

 # ./configure
# make
# make install 

and the terminal went nuts with all that code..lol (finally compiling eh??)

now i get this:

[[IMG]http://img202.echo.cx/img202/4520/newnewnew8dq.th.jpg[/IMG]](http://img202.echo.cx/my.php?image=newnewnew8dq.jpg)

refreshed the Gnome..now where is the installed program? I Looked everywhere but can't find the Ettercap?

thanks :)[/QUOTE]
Try typing in console ettercap

---

### Post by ntrsfrml on 2005-05-11
[QUOTE=void_false]Try typing in console ettercap[/QUOTE]

alright.. typed and i get this:


```
ettercap NG-0.7.2 copyright 2001-2004 ALoR & NaGA


Please select an User Interface
```

how/where i select an User Ineterface? and where is the program?  :?

also..Is this is the same way I should compile all my future source codes?

---

### Post by abhaysahai on 2007-08-11
> **ntrsfrml said:**
> alright.. typed and i get this:


```
ettercap NG-0.7.2 copyright 2001-2004 ALoR & NaGA


Please select an User Interface
```

how/where i select an User Ineterface? and where is the program?  :?

also..Is this is the same way I should compile all my future source codes?

Hey try either of these

ettercap -G  ( GTK GUI ) 
ettercap -C ( Curses based ) 
ettercap -T ( Text based) 

Whatever suits you. Enjoy

---

