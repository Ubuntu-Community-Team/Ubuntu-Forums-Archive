---
title: "Need  libgdk_pixbuf-2.0.so.0 in Order to get a Magnifier to Work"
date: 2015-09-30
forum: General Help
---

### Post by oldefoxx on 2015-09-30
I'm having a real hard time reading light characters on a white background, and everything is so small.  I have to boost the font size up to 18 or higher to make out characters.  This works in some cases like a browser where I can zoom in. or in LibreOffice where I can do a select all and change the size everywhere, but there are a lot of places where you can't do this.  I've tried changing the screen resolution, but this wide screen laptop isn't designed to show me the whole document, so I lose the controls at top and bottom.  Be nice if they started moving the controls to the left and right sides instead.

So I found a magnifier program where I can move the magnifier about with the mouse, and adjust the magnification and rhe size of the view window easily.  It was a lirrle tricky getting it installed, as the instructions are a bit off.  But now that it is in, it won't run.  It needs the  libgdk_pixbuf-2.0.so.0 library.  I need the library, and I need to know how to install it.  Can anyone help? 

These forums are sure handy for getting assistance when there is a problem.  It's one reason I stick with Ubuntu instead of trying a different distro.

---

### Post by steeldriver on 2015-09-30
What is the magnifier program? Where did you get it from and how did you install it?

---

### Post by oldefoxx on 2015-09-30
It;s the magnifier-linux-3.5.  I found it by searching for ubuntu magnifier:  [http://magnifier.sourceforge.net/](http://magnifier.sourceforge.net/)

 It warns you that the library is needed, but apparently it's only available in the 32-bit version according to one source.  But I searched for 64-bit libgdk_pixbuf-2.0.so.0 and found it available in  large number of RPM packagse for Fedora, so maybe it can be converted from RPM to DEB.  I did a bit of that about 12 years ago, and the how of it slips my mind. Another problem though, is there are over a hundred RPMs with it in them, so how do you know which one to go for?  [http://rpmfind.net/linux/rpm2html/search.php?query=libgdk_pixbuf-2.0.so.0()(64bit](http://rpmfind.net/linux/rpm2html/search.php?query=libgdk_pixbuf-2.0.so.0()(64bit)).  There are other RPM links as well.

I also found out about other possibilities like move to Mint, get rid of Unity (it doesn't offer support for the visually impared), use the Ubuntu Software Center and download xzoom.  I did that, but it's small and when you move it, wierd things happen.  I gave up on it.

Then this one:  [http://askubuntu.com/questions/164820/default-screen-magnifier](http://askubuntu.com/questions/164820/default-screen-magnifier)

It boils down to just two lines:> sudo apt-get install compizconfig-settings-manager
Once you invoke the program, look under Accessibility for magnifier, and click on it to configure it. 

A reader supplied a third line:> 	
In Ubuntu 14.04, the command to invoke the program is ccsm.

Trouble is, everything in the ccsm magnifier is flagged disabled, and there are no guidelines to go by.

But I did find something that works, sort of:  > gsettings set org.gnome.desktop.interface scaling-factor 2
But doubling the size means everything gets bigger, and twice as large means huge!  You want it smaller, just change the 2 to a 1.
It won't accept a decimal point or anything like 1.25 or 1.5.

---

### Post by steeldriver on 2015-09-30
What version of Ubuntu are you running? a libgdk-pixbuf2.0-0 package seems to be available on 14.04

```

$ apt-cache policy libgdk-pixbuf2.0-0
libgdk-pixbuf2.0-0:
  Installed: 2.30.7-0ubuntu1.1
  Candidate: 2.30.7-0ubuntu1.1

```

and the 64-bit version appears to contain the library file you are looking for

```

$ dpkg -S libgdk_pixbuf-2.0.so.0
libgdk-pixbuf2.0-0:amd64: /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0
libgdk-pixbuf2.0-0:amd64: /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0.3000.7

```

---

### Post by cariboo on 2015-09-30
Wouldn't it be easier to install an app from the repositories? I found kmag  and xzoom, the can be installed from the command line, or using the Software Centre.

---

### Post by mc4man on 2015-09-30
What you downloaded was a pre-compiled i386 binary.  You *may*  be able get it to work on amd64 if you install the i386 packages (packagename:i386) that provide the "not found" libraries shown when you run an ldd command on your downloaded binary.

Example of here

> ```
ldd  /home/doug/Downloads/magnifier-linux-3.5/magnifier
	linux-gate.so.1 =>  (0xf776d000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf771f000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf75eb000)
	libgdk_pixbuf-2.0.so.0 => not found
	libgtk-x11-2.0.so.0 => not found
	libgdk-x11-2.0.so.0 => not found
	libgobject-2.0.so.0 => not found
	libglib-2.0.so.0 => not found
	libgthread-2.0.so.0 => not found
	libgmodule-2.0.so.0 => not found
	libpango-1.0.so.0 => not found
	libatk-1.0.so.0 => not found
	libcairo.so.2 => not found
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf75e3000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7435000)
	/lib/ld-linux.so.2 (0xf776f000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf7413000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf740f000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf7408000)
```

edit:

This would fill in the above not founds, may or may not account for current founds  in above example.
```
sudo apt-get install libgdk-pixbuf2.0-0:i386 libgtk2.0-0:i386
```

Didn't install but app runs from cli & works fine though not a good way to use in that manner,(from cli), notice the errors in terminal, whatever.
You should read the on-site docu on use.

If tempted to try & may be wanting  to remove these i386 libs later then copy out the install info from the terminal & save to a file for list of i386 packages installed

---

### Post by oldefoxx on 2015-10-01
I'm sorry, but the last three posts were going sort of counter to each other.   I don't want to mix 32-bit code with a 64-bit OS.  Not good policy, and not good in practice.  I don't want something that I will have to remember to undo later.  I've 3/4ths of a century under my belt, and not counting on a full century as my lifetime goal.  Not practical. 

I tried xzoom, and it is really bad.  I could never make do with it  You have no real control over it, and I can't even figure out what part of the screen it is suppose to be magnifying.  It's certainly not showing where I drug it to.  Now magnifying is a bit tricky.  How do you keep the mafnifier from magnifying itself when it moves over a spot?  The obvious answers are:  Either put the magnifier image in a different location, or replicate the actual image elsewhere in memory and show that image with the magnified area superimposed on it on the screen.  The other software solution I had not read about.  I will give it a look over.

The first post showed me something I could try.  So this is what I have:```
apt-cache policy libgdk-pixbuf2.0-0
libgdk-pixbuf2.0-0:
  Installed: 2.30.7-0ubuntu1.1
  Candidate: 2.30.7-0ubuntu1.1
  Version table:
 *** 2.30.7-0ubuntu1.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.30.7-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

libgdk_pixbuf-2.0.so.0
libgdk-pixbuf2.0-0:amd64: /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0
libgdk-pixbuf2.0-0:amd64: /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0.3000

```
So if I have these packages, why can't I run the magnifier program?

Okay, the Ubuntu Software Center knew about kMag and gave it three stars.  I installed it and found it under the menu, meaning I don't have to try and run it from the terminal.  It's of the first type, meaning you pull it aside so that you can magnify a different part of the screen,  You can choose how it moves, and it has several layers of zoom.  That's better than zxoom already.

BUT, and this is a big one, it has fixed dimensions.  It's about 2" square.  That's not going to cut it.   When you need the magnifier most is when you are trying to read small text on the screen.. That means wide and short.  Ideally, the window should be adjustable so that you can make it as wide and tall as you want, but if it is going to be fixed sized, it should be full screen width and about 3/4ths of an inch tall.  It should hide the top if its window unless the mouse is positioned directly over it.  It should give you the ability to read more than just a few horizontal words at a time.

---

### Post by steeldriver on 2015-10-01
> **oldefoxx said:**
> I'm sorry, but the last three posts were going sort of counter to each other.   I don't want to mix 32-bit code with a 64-bit OS.  Not good policy, and not good in practice.  I don't want something that I will have to remember to undo later.  I've 3/4ths of a century under my belt, and not counting on a full century as my lifetime goal.  Not practical. 


You already mixed 32-bit and 64-bit code when you installed a 32-bit ELF binary into your 64-bit system

> **oldefoxx said:**
> So this is what I have:```
apt-cache policy libgdk-pixbuf2.0-0
libgdk-pixbuf2.0-0:
  Installed: 2.30.7-0ubuntu1.1
  Candidate: 2.30.7-0ubuntu1.1
  Version table:
 *** 2.30.7-0ubuntu1.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.30.7-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

libgdk_pixbuf-2.0.so.0
libgdk-pixbuf2.0-0:amd64: /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0
libgdk-pixbuf2.0-0:amd64: /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0.3000

```
So if I have these packages, why can't I run the magnifier program?


Because they are 64-bit packages, whereas the binary you downloaded needs the 32-bit library.

---

### Post by mc4man on 2015-10-01
> **oldefoxx said:**
> I'm sorry, but the last three posts were going sort of counter to each other.   I don't want to mix 32-bit code with a 64-bit OS.  Not good policy, and not good in practice.  
In general that last statement is completely false. That's one of the reasons for the switch to multi-arch packaging in Debian/Ubuntu.

---

### Post by oldefoxx on 2015-10-02
> You already mixed 32-bit and 64-bit code when you installed a 32-bit ELF binary into your 64-bit system

I'm sorry, but what 32-bit ELF package are you referring to?  I'm not disputing what you are saying, but I was not aware I had done this. I know that technically 32-bit code is a subset of 64-bit code, so you can put 32-bit packages into a 64-bit OS, but apparently it's not advised.  One of the posts above did it, and got warnings.

> In general that last statement is completely false. That's one of the reasons for the switch to multi-arch packaging in Debian/Ubuntu.I hadn't heard of multiarch before, so looked it up.  It is a move underway, and offers advantages.  But the Wiki says it does not extend to binaries.  So in that respect. the statement I made is not completely false.  Unless the Wiki is out of date.

If they can make it all fit together, that could be a good thing.  Now what I have found in the last hour is that this could all be unnecessary.  On another thread, I was introduced to a new plugin, and I found this video of it in action:  [https://www.youtube.com/watch?v=sI03Xr-55uw]("https://www.youtube.com/watch?v=sI03Xr-55uw")
The person suggesting this also suggested downloading and using Mate as the interface, but the video just says it was added to Ubuntu 14.04.  Check it out for yourself.

---

