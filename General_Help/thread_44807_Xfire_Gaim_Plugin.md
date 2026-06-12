---
title: "Xfire Gaim Plugin"
date: 2005-06-27
forum: General Help
---

### Post by rathel on 2005-06-27
This is probably a stupid question, but oh well, im newbie.
```

rathel@ubuntu:~/Downloads/gaim-xfire-0.5.6$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for pkg-config... /usr/bin/pkg-config
checking for gaim... Package gaim was not found in the pkg-config search path.
Perhaps you should add the directory containing `gaim.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gaim' found

configure: error: Library requirements (gaim) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```
What's wrong? How do I fix?

---

### Post by jobo on 2005-06-27
Just to be on the safe side; this is you attempting a build of a plugin for gaim, right? -Now then, since i havn't touched this bit of software before, Im prob. not the best to answer, but in genral - the biuld cant find your gaim-file gaim.pc
 I'm guessing here, but you might find a clue in *.configure --help* like a parameter setting the path to the "missing" file.

Edit: Adding some...
 do a *locate gaim.pc* and compare that location to those in  *echo $PKG_CONFIG_PATH *
If it's not present add it: PKG_CONFIG_PATH = $PKG_CONFIG_PATH;path/to/gaim.pc
and retry .configure. Else; I'm at a loss :/

---

### Post by tread on 2005-06-27
What you need is the gaim-dev package. This will have the header files needed to compile the plugin. (Note: whenever you try to compile something, if it depends on some package, you need the dev files for that package)

---

### Post by rathel on 2005-06-27
okay thank you, i'll downlaod gaim-dev and give it atry

---

### Post by tread on 2005-06-27
Did I mention that its there on the ubuntu repos? Nah, I didn't :) But I'm just posting to say you can install this via synaptic.

---

### Post by rathel on 2005-06-27
yup that's the way i installed it :), okay i installed the plugin, i got no error, but it's not listed in the plugin section of gaim

---

### Post by tread on 2005-06-27
Did you restart gaim?
Check where you installed it and in the .gaim directory in you home, there should be a place to create plugins. Either drop the plugin here or create a symbolic link to it.

Hopefully that will work. :)

---

### Post by rathel on 2005-06-27
yah first thing i did was restart gaim, i check the .gaim directory and there isn't a plugins folder in there..

---

### Post by tread on 2005-06-27
Hmm .. I'm pretty sure its a paths thing. I'm not in Linux at the moment, so I can't check this. 
Heres a suggestion: find some other gaim plugin via synaptic, install it, then rightclick it in synaptic .. there is some way to see the list of files installed by the package and their locations.

---

### Post by rathel on 2005-06-27
/usr/lib/gaim is where gaim-encrypt goes and that's what i install via synaptic, i check there, and there isn't anything relating to xfire, it's like it went through the install process and didn't put anything anywhere

---

### Post by tread on 2005-06-27
well, if you just did the standard ./configure; make; make install

then do the make install again without sudo .. it should fail and the error message will tell you where its trying to put the files.

---

### Post by rathel on 2005-06-27
```

rathel@ubuntu:~/Downloads/gaim-xfire-0.5.6$ make install
Making install in src
make[1]: Entering directory `/home/rathel/Downloads/gaim-xfire-0.5.6/src'
make[2]: Entering directory `/home/rathel/Downloads/gaim-xfire-0.5.6/src'
make[2]: Nothing to be done for `install-exec-am'.
/bin/sh ../mkinstalldirs /usr/local/lib/gaim
/bin/sh ../libtool --silent  --mode=install /usr/bin/install -c libxfire.la /usr/local/lib/gaim/libxfire.la
/usr/bin/install: cannot remove `/usr/local/lib/gaim/libxfire.so': Permission denied
make[2]: *** [install-pluginLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/rathel/Downloads/gaim-xfire-0.5.6/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/rathel/Downloads/gaim-xfire-0.5.6/src'
make: *** [install-recursive] Error 1

```
weird

---

### Post by skirkpatrick on 2005-06-27
I tried using Synaptic when I first tried this plugin and gave up.  Instead, I DL'd the Gaim source and extracted it in /usr/local/src.  I then extracted the XFire plugin source in the /usr/local/src/gaim-1.3.0/plugins directory.  Rather than using sudo, I used "su -" to build and install it.  Under Synaptic, Gaim is installed in the /usr tree instead of the /usr/local tree.  So configure the plugin by using "./configure --prefix=/usr", then "make", then "make install".  It will try to install files in several places that you need root access to.

The XFire plugin won't show up in Gaim's plugin list.  However, if you go to Accounts, then Add, you'll notice it is listed in the the Protocol drop-down list.  You will have to keep it "updated" to XFire's current version.  Modify the account and in Show More Options, change Version to the last 2 digits of what XFire is currently using.

---

### Post by rathel on 2005-06-27
Hey, thanks!, that worked

---

### Post by DarkManX4lf on 2005-07-17
ok i cant get this to work, i followed post #13 but with gaim 1.4.0 and xfire-gaim 0.5.7, and gaim 1.4.0 compiled fine and its working but the xfire protocol doesnt show up in the accounts section, and nor does it show up in the plugins....how do i fix this ?

---

### Post by DarkManX4lf on 2005-07-17
ok i think i got it to work, but what version  should i put in

---

### Post by DarkManX4lf on 2005-07-17
ok i got it to work changed the version to 42 or anything higher and it seemd to work fine, it logs in and i can chat with xfire ppl so it works....now another problem...when installing gaim 1.4.0 it was fine, but there areno sounds, like when i im someone or someone signs on/off...no sound...sound works everywhere else tho (in ut2004, ubuntu desktop etc) i made sure sounds are enabled in the options....how do i fix this ?

---

### Post by DarkManX4lf on 2005-08-09
anyone ?

---

### Post by Stolen on 2005-10-09
[QUOTE=DarkManX4lf]anyone ?[/QUOTE]
I just installed this today and had to put in version 46.  just keep incrementing it, or look on the gaim-xfire page ( [http://www.fryx.ch/xfire/](http://www.fryx.ch/xfire/) ) and they usually tell you there.

oh, nevermind, misread your problem.

I always turn sounds off so I won't be any help for ya. :)

---

### Post by absentbird on 2005-11-04
hey i still cant get it to work i am having the same problem DarkMan had, i compile and make but it wont appear. i am using gaim 1.5.0 and xfire 0.5.8 i could really use some help thanks.

---

### Post by burzuum on 2005-11-22
Hi guys,

If you want, try this.

Take my x_packets.c [here]("http://julien.hascoet.free.fr/x_packets.c")
Go to your /gaim-xfire-0.5.8/src directory
Backup your x_packets.c file and copy my file in this place.
Compile with ./configure --prefix=/usr 
Then move /usr/local/lib/gaim/libxfire.so to /usr/lib/gaim/ if needed.

Launch Gaim and go in Account -> Add, you should have a Xfire protocol listed.

Enjoy !

I compiled instructions from [https://sourceforge.net/forum/forum.php?thread_id=1348817&forum_id=474407]("https://sourceforge.net/forum/forum.php?thread_id=1348817&forum_id=474407")

---

### Post by Griff on 2005-12-15
Thank you Burzuum!  Been messing with wine/xfire and the gaim plugin for xfire for 2 weeks now.  Did a search and found your post.  Now it works.  (had to change to version 48 I believe)  Thanks a ton!:p

---

