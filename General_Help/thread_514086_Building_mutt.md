---
title: "Building mutt"
date: 2007-07-31
forum: General Help
---

### Post by chombee on 2007-07-31
I'm trying to build (or otherwise install) mutt 1.5.15 or later (1.5.16 is the most recent right now) because I want the new built-in SMTP support. I have build-essential installed, but I'm getting this error:

[http://paste.ubuntu-nl.org/32033/](http://paste.ubuntu-nl.org/32033/)

Can anyone tell me what I'm missing? I mean, a curses library obviously, but I'm not sure what package to install.

Alternatively if anyone has a deb for it that'd work.

Thanks

---

### Post by nitro_n2o on 2007-07-31
get it from the repositories  
```
sudo apt-get install ncurses
```

---

### Post by chombee on 2007-07-31
Thanks for the help, but it looks like there's no ncurses package:

```
$ sudo apt-get install ncurses
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ncurses is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ncurses has no installation candidate
```

I have libncurses5, libncursesw5, ncurses-base and ncurses-bin installed.

I also tried installing the mutt 1.5.15 package from gusty but I got "Dependency is not satisfiable: libgnutls13."

Then I decided that maybe I needed the dev package so I installed libncurses5-dev and libncursesw5-dev and... it works!

At least the ./configure and make steps work, I haven't run make install cause I want to ask something first:

If I install mutt the /configure; make; sudo make install way can someone tell me how I:

* Uninstall it if I want to
* Upgrade it. Can I just download a newer version and install it over the top? What if I download a package for a newer version?

Also, should I uninstall the mutt package before I installed mutt from source?

Thanks

---

### Post by andrew.46 on 2007-08-01
Hi,

 Always get a little excited when someone posts on mutt:


> **chombee said:**
> I'm trying to build (or otherwise install) mutt 1.5.15 or later (1.5.16 is the most recent right now) because I want the new built-in SMTP support. I have build-essential installed, [...] Can anyone tell me what I'm missing? I mean, a curses library obviously, but I'm not sure what package to install.

The file you are after is:

```
sudo apt-get install libncurses5-dev
```

 which is in the repositories. You might also be interested enough to read of my page:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

 which may be of some assistance to you. I suspect you may have to run:

```
./configure --enable-smtp 
```

 All the best with this. Let me know if any of the info on my page was any use to you!

                   Andrew

---

### Post by andrew.46 on 2007-08-01
Hi,

 Partly answered your question in a preceding post:

> **chombee said:**
> [...] If I install mutt the /configure; make; sudo make install way can someone tell me how I:

* Uninstall it if I want to
* Upgrade it. Can I just download a newer version and install it over the top? What if I download a package for a newer version?Also, should I uninstall the mutt package before I installed mutt from source?Thanks

 Definitely uninstall one before installing the other. To uninstall you need a program called checkinstall:

```
sudo apt-get install checkinstall
```

 Once that is in place you should run install as:

```
./configure --enable-smtp
make
sudo checkinstall -D

```

 This will create a deb file and install it for you, you can uninstall from Synaptic then.

                   Andrew

---

