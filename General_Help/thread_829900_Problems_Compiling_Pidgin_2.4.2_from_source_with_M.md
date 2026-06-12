---
title: "Problems Compiling Pidgin 2.4.2 from source with MSNP14 enabled"
date: 2008-06-15
forum: General Help
---

### Post by PRGUY85 on 2008-06-15
Hey:

I have compiled Pidgin 2.4.2 from source on two other Ubuntu distros (my laptop and a 64-bit one).  I edited the configure file to have it say enable_msnp14=yes...and everything worked great.

However, I tried doing the same on a fresh 32 bit Hardy install with no luck.  It does compile but it won't connect to MSN and crashes the software while trying to connect.  I know the MSNP14 branch is experimental, yet why does it work on other computers and not on this fresh install?

---

### Post by PRGUY85 on 2008-06-15
I am doing the following:

```
sudo ./configure --enable-msnp14 --disable-nm
```

Followed by:

```
sudo make
```

and:

```
sudo make install
```

I get no errors, yet it hangs while connecting to MSN, something my laptop running 32bit Hardy doesn't do.

---

### Post by y-lee on 2008-06-15
I don't know what is causing your problem but you are compiling wrong. You only need **sudo** with **make install** like below:

```
./configure
make
sudo make install
```

And also why are you **--disable-nm**? What does this do?


I recompiled pidgin this morning to enable msnnp14 support and what i did was open the file “configure” in a text editor and replace the line “enable_msnp14=no” with “enable_msnp14=yes”.
Save and quit.

and then

```
./configure
make
sudo make install
```

but in order to ./configure i had to install several other things to eliminate errors and warnings.

---

### Post by PRGUY85 on 2008-06-15
Yea I know, I have done that other times and it works. Yet, on my new install it doesn't...maybe it is that I installed OSS for my X-Fi...

---

### Post by y-lee on 2008-06-15
try compiling it without the **--disable-nm** (this disables network manager stuff and sounds like a bad idea to me) and edit the configuration file as i posted above.

btw i never heard of  X-FI OSS before but found some threads on it, like [this one]("http://ubuntuforums.org/showthread.php?t=734400"), does it work?

---

### Post by PRGUY85 on 2008-06-15
I have compiled it like you have said before and it does work.  I tried doing the same before but it doesn't.  Also, the --disable-nm is necessary to compile if you don't have network manager.  I compiled 2.4.1 which doesn't require the --disable-nm command and put enable_msnp14=yes with same results.

---

### Post by y-lee on 2008-06-15
> Also, the --disable-nm is necessary to compile if you don't have network manager.

I had to install network-manager-dev is all, you might have different results because i install and uninstall stuff alot helping ppl on the forums :)

---

### Post by PRGUY85 on 2008-06-16
I tested it installing network-manager-dev and now Pidgin would hang when starting up and does nothing afterwards...

---

### Post by PRGUY85 on 2008-06-16
I tried to open pidgin from the terminal:

```
pidgin
pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory

```

Only way to make it at least open is installing pidgin-data and libpurple0 from Synaptic...yet it never connects to MSN...just AIM, YIM,etc...

---

### Post by PRGUY85 on 2008-06-16
I did a fresh install and I still cannot compile it correctly from source no matter if I enable msnp14 or not.  When I click on the icon it hags and never starts.

Only way to make it start is to install libpurple0 and pidgin-data from Synaptic yet if I used enable_msnp14..it will not connect to MSN.

---

### Post by PRGUY85 on 2008-06-16
After compiling it again with --enable-msnp14 (or putting enable_msnp14=yes) it won't connect to MSN.

---

### Post by y-lee on 2008-06-16
Uninstall pidgin.

Now make sure the GNU Debugger is installed.

```
sudo apt-get install gdb
```

Install pidgin with debug turned on and msnp14 enabled, by adding --enable-debug to the configure statement.

Read the article on [backtrace]("https://wiki.ubuntu.com/Backtrace"), and start pidgin that way to generate an error report. Post whatever errors you get here.

Sorry I'm not more descriptive but I'm headed to work and rushing this answer, don't have time to test it all on my system. I think tho ya can get the idea.

Anyway I can't guarantee I can figure this out, you seem to have found a bug I can't duplicate. If so we may have to file a bug report on launchpad or pidgins site.

---

### Post by Ramses de Norre on 2008-06-16
This is how I did it on another distro:
```
  sed -i -e 's|enable_msnp14=no|enable_msnp14=yes|g' configure.ac
  # gconf won't die with the --disable-schemas-install option
  sed -i -e 's/gconftool-2/no/g' configure.ac

  # ugly hack to support building with new libtool
  # http://developer.pidgin.im/ticket/5346
  # http://bugs.archlinux.org/task/10012
  libtoolize --force --copy || return 1
  aclocal || return 1
  autoconf || return 1
  automake --add-missing || return 1

  ./configure --prefix=/usr --sysconfdir=/etc \
              --disable-perl --disable-cap \
              --disable-schemas-install \
              --enable-gtkspell --enable-gnutls=no \
              --enable-nss=yes --disable-gevolution \
              --enable-dbus --disable-mono \
              --disable-meanwhile --disable-nm \
              --disable-debug
  make || return 1
  make DESTDIR=${startdir}/pkg install
```

---

### Post by PRGUY85 on 2008-06-16
Did you paste that on the configure file or ran it from a terminal?

---

### Post by Ramses de Norre on 2008-06-16
That's the relevant piece of the build script, so yes it is supposed to be ran in a terminal.

---

### Post by PRGUY85 on 2008-06-16
I am not currently on my desktop so I cannot test it.  I uninstalled it oand reinstalled it on my laptop and I could reproduce the same behavior now on my laptop which had it running well (2.4.2)...don't know what's up.

---

### Post by PRGUY85 on 2008-06-16
UPDATE:

I got Pidgin to start on my laptop after my test by installing pidgin-data and libpurple0 from Synaptic.  On About...it says 2.4.2 so it's running the compiled version AND miraculously it could connect to MSN.

I am going to try to reproduce this.

---

### Post by PRGUY85 on 2008-06-16
And another UPDATE:

After a succesful trial, I removed pidgin-data and libpurple0 and sudo make uninstall my pidgin 2.4.2 compiled version...

I downloaded a fresh pidgin-2.4.2 tar, extracted it, ran ./configure --enable-msnp14, sudo make and sudo make install...When I ran Pidgin it hanged on startup and never opened (the Menu option for Pidgin doesn't even show the Pidgin icon)...

I installed libpurple0 and pidgin-data from Synaptic afterwards...and now it works perfectly...it starts and connects to MSN.  So what could be wrong with all of this?  At least right now it works.

---

### Post by PRGUY85 on 2008-06-18
Tried it on my desktop...didn't work.  Its a problem with enabling MSNP14 for the regular installation works.

---

