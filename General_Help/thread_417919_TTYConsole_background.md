---
title: "TTY/Console background?"
date: 2007-04-22
forum: General Help
---

### Post by DARKGuy on 2007-04-22
Hey guys :)

Great job with the Feisty Fawn! I haven't encountered any errors yet (fresh install) except the nasty nvidia error... I have to reinstall it everytime I boot my system... a royal PITA... I hope that gets solved soon! >.<.

Anyways... in hopes to make my desktop computer even prettier (and functional, too! :P) I've been wondering... how can I add a background to the framebuffer console? like the old Mandrake used to do... or the gentoo livecd with its background on the console?

I've searched around and I've found links to gentoo, kernel patches (UGH X_X), bootsplash, fbsplash and other stuff I'm not looking for. I don't want a bootscreen with a progress bar (I already have it!) but just a framebuffer background. Is there a way to have one WITHOUT having to compile a new kernel, patch it, or compile huge loads of code? (in example: the kernel).

Thanks in advance :)

---

### Post by Famicommie on 2007-04-22
From the terminal menu bar, select "Edit -> Current Profile -> Effects and there should be a radio box for a background image. From there, simply select the background image that you would like to use.

---

### Post by hikaricore on 2007-04-22
> **Famicommie said:**
> From the terminal menu bar, select "Edit -> Current Profile -> Effects and there should be a radio box for a background image. From there, simply select the background image that you would like to use.

This is not what the OP is looking for.
They're wanting a background image for cli without having to recompile the kernel.
I don't believe this is possible. >.<

---

### Post by DARKGuy on 2007-04-22
> **Famicommie said:**
> From the terminal menu bar, select "Edit -> Current Profile -> Effects and there should be a radio box for a background image. From there, simply select the background image that you would like to use.

Thanks for the reply, but that's inside X. I was wondering about something ***outside*** X... um, something like this: 

[img]http://img182.imageshack.us/img182/4992/themegentoolivecd20041vhj0.png[/img]

> **hikaricore said:**
> This is not what the OP is looking for.
They're wanting a background image for cli without having to recompile the kernel.
I don't believe this is possible. >.<

Dangit :(... isn't there then, an EASY way to do it? I guess I can stand compiling the kernel.. as long as the steps are easy or can be done in a script... if anybody knows, please reply!! :(

---

### Post by DARKGuy on 2007-04-25
I hate to bump but.... anybody?

---

### Post by jakub.lucky on 2007-04-25
Well, I suppose that tty's are binaries called getty, originally in location: /sbin/getty

But I'm not really sure, if editing sources of getty can make such nice console...

---

### Post by h4p0 on 2007-12-28
I've got your same question...u r not alone :)
I searched world wide for a solution but nothing.... :(
If I found something I will post just here the trick.
Hope someone could help us as soon as possible!!
bye,

-h4p0-

---

### Post by gillespie on 2008-01-02
Theres a patch called fbcondecor that will do the trick, but its a kernel recompile

Tom

---

### Post by ~LoKe on 2008-01-02
This interests me.  I've disabled gdm so maybe a little eye candy wouldn't be so bad.

---

### Post by threespacemen on 2008-05-30
For anyone who's interested... I've been looking for a way to do this for ages, ever since trying out Gentoo and Sabayon a while back, so this week I had a go at rolling a new kernel with the fbcondecor patch. While it seemed to compile fine (2.6.24-17 generic, using the 2.6.24-rc7 patch from [http://dev.gentoo.org/~spock/projects/fbcondecor/archive/](http://dev.gentoo.org/~spock/projects/fbcondecor/archive/)), aside from the new kernel suddenly not having any modules for my intel wireless card, all the fbcondecor utilities from splashutils (sid debs from [ftp://ftp.berlios.de/pub/fbsplash/debian/splashutils](ftp://ftp.berlios.de/pub/fbsplash/debian/splashutils)) don't seem to like working all that much:

```
$ sudo fbcondecor_ctl
Failed to open the fbcon_decor control device.
```

I don't know whether this is because the kernel patch hasn't come through, or because of the following dependency issue (I tried a force to get the package to install):

```
$ sudo dpkg -i splashutils_1.5.4-1_i386.deb 
Selecting previously deselected package splashutils.
(Reading database ... 112189 files and directories currently installed.)
Unpacking splashutils (from splashutils_1.5.4-1_i386.deb) ...
Adding `diversion of /lib/init/splash-functions to /lib/init/splash-functions.diverted_by_splashutils by splashutils'
dpkg: dependency problems prevent configuration of splashutils:
 splashutils depends on sysv-rc (>= 2.86.ds1-44); however:
  Version of sysv-rc on system is 2.86.ds1-14.1ubuntu45.
dpkg: error processing splashutils (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 splashutils
```

Tried building splashutils from source, but make complained about a missing file from libjpeg (jcapimin.o) that I couldn't seem to get around.

Does anyone in the know know what the chances of splashutils packages and the fbcondecor kernel patch (and fbsplash, for that matter) being included in ubuntu in the future (so that it "just works")? And what we'd need to do to give it a bit of a nudge in the right direction? Sure, it's a very "gentoo" thing, and a lot of ubuntu users probably won't go anywhere near a fb console, let alone modify their menu.lst to show boot sequences, but for those of us who occasionally operate outside X, it'd be a nice to have...

---

### Post by bLaCkMeTaLL on 2008-06-19
me too, very interested at a beautiful backdrop for my shell. Can somebody help?

---

### Post by shinji257 on 2008-06-20
If you can figure this one out I will be forever grateful.

---

