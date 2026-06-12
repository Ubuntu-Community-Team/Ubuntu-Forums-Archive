---
title: "Wine freezes when I run programs with it"
date: 2006-11-25
forum: General Help
---

### Post by bluecheese on 2006-11-25
When I try to run winecfg, if the there is already a .wine directory, it makes a window with a title bar that says "wine configuration", but the inside of the window doesn't show anything. It just shows what was behind the window when it was created. If I try to run it without having a .wine directory, it says:

wine: creating configuration directory '/home/master/.wine'...
Failed to open the service control manager.

...and hangs without opening a window.

I can get some other programs to run if the .wine directory already exists, but they don't respond to input. Some parts of the window show what they're supposed to, and other parts show what was behind the window.

BTW, I'm using 0.9.25 from Wine's repository.

---

### Post by tomcheng76 on 2006-11-25
just a guess.
I think you are runing beryl, right ?
try to close it before running wine. (probably other things like Xgl also need to be closes)
hope this help :)

---

### Post by bluecheese on 2006-11-25
No, I'm just running Metacity and am not running Xgl. Thanks, though.

---

### Post by bluecheese on 2006-11-25
I found out that the problem only occurs when the SCIM input method editor is used. If I disable it, wine can start up normally. This is still a problem, though. I guess it's a bug in wine.

EDIT:
It is not a bug in wine. It was a bug in libX11. I found a patch for it, and compiled libX11, and it seems to work perfectly now.

---

### Post by __Alex__ on 2006-12-04
I am facing the same problem. I'll try to recompile libX11 as well, but this is very painful. Thanks for your hint.

---

### Post by ezphilosophy on 2006-12-09
> **bluecheese said:**
> I found out that the problem only occurs when the SCIM input method editor is used. If I disable it, wine can start up normally. This is still a problem, though. I guess it's a bug in wine.

EDIT:
It is not a bug in wine. It was a bug in libX11. I found a patch for it, and compiled libX11, and it seems to work perfectly now.


I'm having this same problem.  
How do I go about compiling libX11?

---

### Post by dyzzy on 2007-01-04
> **ezphilosophy said:**
> I'm having this same problem.  
How do I go about compiling libX11?
Same here. Can anyone actually post what to do?

---

### Post by zivagolee on 2007-01-11
anyone know what's up with this?  Where to get the patch, etc etc..

---

### Post by zivagolee on 2007-01-11
> **zivagolee said:**
> anyone know what's up with this?  Where to get the patch, etc etc..

Just replying to my own message.  I found the patch on winehq.com and here are the instructions for anyone who wants to know:

On the known issues page in the wine wiki url ([http://wiki.winehq.org/KnownIssues)](http://wiki.winehq.org/KnownIssues)), there is bug 6547 ([http://bugs.winehq.org/show_bug.cgi?id=6547)](http://bugs.winehq.org/show_bug.cgi?id=6547)).  On comment #17, it links you back to bug 1182 on freedesktop.org ([https://bugs.freedesktop.org/show_bug.cgi?id=1182)](https://bugs.freedesktop.org/show_bug.cgi?id=1182)).  On comment #8, someone posts a patch to this issue.  So, now we got the patch...

1. Make sure your sources.list is set to get the edgy source packages
2. create a temp dir and change directory to it
2. apt-get source libx11 (downloads libx11 source)
3. go to libx11-1.0.3/src and find the FilterEv.c file
4. edit FilterEv.c.  Cut line 101 and add it to line 99:

Before:

        if (win == p->window) {
            if ((mask & p->event_mask) ||
                (ev->type >= p->start_type && ev->type <= p->end_type)) {
                ret = (*(p->filter))(ev->xany.display, p->window, ev,
                                      p->client_data);
                UnlockDisplay(ev->xany.display);
                return(ret);
            }

After:

        if (win == p->window) {
            if ((mask & p->event_mask) ||
                (ev->type >= p->start_type && ev->type <= p->end_type)) {
                UnlockDisplay(ev->xany.display);
                ret = (*(p->filter))(ev->xany.display, p->window, ev,
                                      p->client_data);
                return(ret);
            }

5. save the file
6. jump out to the libx11-1.0.3 dir and run dpkg-buildpackage -rfakeroot -uc -b (this will build the deb packag)
7. install the libx11-6_1.0.3-0ubuntu4_i386.deb package (no need to the install the other ones).

That's it!  Hope this helps somebody...

---

### Post by CodeNosher on 2007-01-13
It should become evident soon, but I'm a real noob.  I've been trying to get wine running on xubuntu for three days now.  This post seemed helpful, but I ran into trouble and now I'm stuck.

I made the changes, no prob.

I ran the build and got this:

jason@ubuntu:~/temp/libx11-1.0.3$ sudo dpkg-buildpackage -rfakeroot -uc -b
dpkg-buildpackage: source package is libx11
dpkg-buildpackage: source version is 2:1.0.3-0ubuntu4
dpkg-buildpackage: source changed by Kees Cook <kees@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 1.0.3-0ubuntu4
dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 4.0.0) pkg-config xtrans-dev x11proto-bigreqs-dev x11proto-core-dev x11proto-kb-dev x11proto-input-dev x11proto-xext-dev x11proto-xf86bigfont-dev libxdmcp-dev (>= 1:1.0.0-1) libxau-dev (>= 1:1.0.0-1) x11proto-xcmisc-dev quilt
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)

I saw I didn't have fakeroot, so I installed it and ran it again without the -d and it failed again, so I added the -d and got this:

son@ubuntu:~/temp/libx11-1.0.3$ sudo dpkg-buildpackage -rfakeroot -uc -b -d
dpkg-buildpackage: source package is libx11
dpkg-buildpackage: source version is 2:1.0.3-0ubuntu4
dpkg-buildpackage: source changed by Kees Cook <kees@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 1.0.3-0ubuntu4
 fakeroot debian/rules clean
rm -f stampdir/genscripts
rm -f debian/*.config \
              debian/*.postinst \
              debian/*.postrm \
              debian/*.preinst \
              debian/*.prerm
rm -f stampdir/patch
Unapplying patches...nothing to do.
dh_testdir
make: dh_testdir: Command not found
make: *** [xsfclean] Error 127

I'm not sure what to do now.  

libx11-6_1.0.3-0ubuntu4_i386.deb package is not anywhere I can find, so I'm guessing it didn't get created.

I need to get wine running so I can get LingaLinks running.  It's a Folio app, so any help with getting that running would be extra nice, too.

Thanks

---

### Post by zivagolee on 2007-01-14
> **CodeNosher said:**
> 

dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 4.0.0) pkg-config xtrans-dev x11proto-bigreqs-dev x11proto-core-dev x11proto-kb-dev x11proto-input-dev x11proto-xext-dev x11proto-xf86bigfont-dev libxdmcp-dev (>= 1:1.0.0-1) libxau-dev (>= 1:1.0.0-1) x11proto-xcmisc-dev quilt



This line is what you should be looking at.  You don't have all the proper dev packages to build libx11.  Try running this:

sudo apt-get install debhelper pkg-config xtrans-dev x11proto-bigreqs-dev x11proto-core-dev x11proto-kb-dev x11proto-input-dev x11proto-xext-dev x11proto-xf86bigfont-dev libxdmcp-dev libxau-dev x11proto-xcmisc-dev quilt

If it installs all those packages, then try running dpkg-build again.

---

### Post by CodeNosher on 2007-01-14
Thanks a lot!  It worked without errors - at least that what it looked like.  Now, to the next wall.

**7. install the libx11-6_1.0.3-0ubuntu4_i386.deb package (no need to the install the other ones).**

I had a hard time finding the package.  I finally ran **dpkg -l '*libx11*'**.  It found libx11-6, with a version of 1.0.3-Oubuntu4, so I ran **apt-get install libx11**.

It results in: **libx11-6 is already the newest version**.  I tried to remove and autoremove it, but says 

E: broken packages.

And this:

Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed

Any thoughts??  

I'm guessing I'm not installing the package I just created.  But, how do I know?  Also not sure why it won't let me remove it.  Is it because other things depend on it?

Thanks for the help.

---

### Post by zivagolee on 2007-01-14
> **CodeNosher said:**
> Thanks a lot!  It worked without errors - at least that what it looked like.  Now, to the next wall.

**7. install the libx11-6_1.0.3-0ubuntu4_i386.deb package (no need to the install the other ones).**

I had a hard time finding the package.  I finally ran **dpkg -l '*libx11*'**.  It found libx11-6, with a version of 1.0.3-Oubuntu4, so I ran **apt-get install libx11**.

It results in: **libx11-6 is already the newest version**.  I tried to remove and autoremove it, but says 

E: broken packages.

And this:

Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed

Any thoughts??  

I'm guessing I'm not installing the package I just created.  But, how do I know?  Also not sure why it won't let me remove it.  Is it because other things depend on it?

Thanks for the help.

The package is *outside* the source tree.  I guess I should have modify my instructions:

7. cd out to the parent directory.  (ie.  cd ..)
8. don't use apt-get as it will try to install it from the sources.list.  Use dpkg.
bash# sudo dpkg -i libx11-6_1.0.3-0ubuntu4_i386.deb

See if that works.  Using dpkg will reinstall the package.

Try that.. let me know how it works.

---

### Post by zivagolee on 2007-01-14
> **CodeNosher said:**
> 
I'm guessing I'm not installing the package I just created.  But, how do I know?  Also not sure why it won't let me remove it.  Is it because other things depend on it?

Thanks for the help.

And to answer this question, yes, you are not installing the package you created.  It is trying to install it from the repo's.  There are too many dependencies for libx11, I wouldn't try to remove it.

---

### Post by CodeNosher on 2007-01-14
Thanks for the info.  I still can't find the .deb file.  I ran the dpkg from a couple of different spots and it always says it cannot find the package.  

I guess I'll start the process over again and see if I can figure out where it puts it.

I used find to look for it, but it never found the .deb file.  Any thoughts on that?

---

### Post by zivagolee on 2007-01-15
> **CodeNosher said:**
> Thanks for the info.  I still can't find the .deb file.  I ran the dpkg from a couple of different spots and it always says it cannot find the package.  

I guess I'll start the process over again and see if I can figure out where it puts it.

I used find to look for it, but it never found the .deb file.  Any thoughts on that?

Did you get any errors during compilation?  You should be able to see that it created the deb file in the output.  Maybe post the output?

Also, the deb file should be in the temp directory created.  Try doing an ls in the temp directory, what do you see?  Paste the output here...

---

### Post by CodeNosher on 2007-01-15
I dumped my temp dir and started over.  This time it went without a problem.  I can now run winecfg without any problems.  

I'm running xubuntu 6.10 on an old dell laptop someone gave me.  PIII 750.  Things seem to be a lot smoother than Ubuntu 6.10 on my new Gateway Tablet PC.  The Gateway seems to be having issues with the intel video card.  

Ok, I've got wine running, now let's see if I can get it to install my app :)

Thanks for the help.  These are things I couldn't do alone! :D

---

### Post by zivagolee on 2007-01-15
> **CodeNosher said:**
> 
Ok, I've got wine running, now let's see if I can get it to install my app :)

Thanks for the help.  These are things I couldn't do alone! :D

Sounds good.  Have fun!

---

### Post by hoyaabc on 2007-02-04
I following your instruction.
I got no error until making deb file.
here is last 4lines what I got from sudo dpkg-buildpackage -rfakeroot -uc -b
the other looks fine to me

checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [build-stamp] error 77

any suggestion?

---

### Post by hoyaabc on 2007-02-04
oops.
I didn't have compiler.
now i made deb file
solved.

---

### Post by hoyaabc on 2007-02-04
I can see winecfg now!
thank you.

---

### Post by zivagolee on 2007-02-04
> **hoyaabc said:**
> I can see winecfg now!
thank you.

Awesome!

---

### Post by sdhoigt on 2007-02-16
zivagolee, thanks for your fix.  And a tad esoteric I might add!

I've been struggling with Wine not working for some time.  If it wasn't for this thread, I would've never got it.

Also, I never knew how to pull down sources from a repo and compile and make a new package.  That's cool info to have too.

Thanks!!
SD

---

### Post by zivagolee on 2007-02-16
> **sdhoigt said:**
> zivagolee, thanks for your fix.  And a tad esoteric I might add!

I've been struggling with Wine not working for some time.  If it wasn't for this thread, I would've never got it.

Also, I never knew how to pull down sources from a repo and compile and make a new package.  That's cool info to have too.

Thanks!!
SD

No problem.. glad I could help :)

---

