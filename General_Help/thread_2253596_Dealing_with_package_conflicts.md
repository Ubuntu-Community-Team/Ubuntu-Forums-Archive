---
title: "Dealing with package conflicts"
date: 2014-11-20
forum: General Help
---

### Post by pwabrahams on 2014-11-20
Recently I tried to install Skype in Kubuntu 14.10 and failed, despite all the reports of success with a simple sequence of three commands.  I encountered the usual sorts of error messages: unmet dependencies, packages held back, etc.  The problem was that I attempted the installation after I had installed a whole bunch of other stuff, though nothing extraordinary - mostly the repositories found in Software Sources. So I did a clean reinstall of Kubuntu and then installed Skype before I did anything else, and it worked perfectly.  So I'd like to ask about that in general.

My question is simple, but it might not have a simple answer.  When you encounter package conflicts, how do you determine what already-installed packages have to be removed in order to resolveall the conflicts?  Like many other Kubuntu users, I install lots of packages through automated procedures, including but not limited to updates and upgrades.  So I don't really know everything that's in my system, particularly when it comes to library packages.

Is there any hope for solving these issues without becoming an expert on Kubuntu internals?

---

### Post by ian-weisser on 2014-11-20
The initial error message tells you what packages are affected.
Try to install one of those affected package. That error message will tell you either the next package in the chain of dependencies...or give you the actual reason it cannot be installed.
Then you know what to uninstall.

---

### Post by Bucky Ball on 2014-11-20
How did you install Skype?

---

### Post by pwabrahams on 2014-11-21
Here is an example where I don't know what I specifically need to do to fix the problem:
```
ome packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gdebi : Depends: gir1.2-gtk-3.0 but it is not going to be installed
         Depends: gir1.2-vte-2.90 but it is not going to be installed
         Recommends: libgtk2-perl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

This happened when I was trying to install Skype.  Clearly I can't install gdebi -- that's what it says and that was my experience.  I don't know anything about gir1, and hardly anything about libgtk2-perl.  I might be able to get a list of all my installed packages, but that wouldn't help much since I still won't know what package in that list needs to be removed.

---

### Post by pwabrahams on 2014-11-21
I don't remember precisely what i did, but I got the command sequence from one of the posts gotten by a googlesearch on "kubuntu 14.04 skype".  Here's a sketch of what I remember:

1. sudo dpkg --add-architecture i386

2. Make sure the Canonical Partners repository is in your repository list   One way to do this is through the Sources option of Muon Discover.

3. sudo apt-get update

4. sudo apt-get upgrade

5. sudo apt-get install skype

*Warning:* If you don't do this immediately after the initial installation of your system, #5 will fail with puzzling messages. When that happened to me, I concluded that the only way out of the impasse was to do a clean install of the entire system, and install Skype (as above) as the first action after the system came up.  That worked for me.

---

### Post by ian-weisser on 2014-11-21
> **pwabrahams said:**
> Here is an example where I don't know what I specifically need to do to fix the problem:
```
The following packages have unmet dependencies:
 gdebi : Depends: gir1.2-gtk-3.0 but it is not going to be installed
         Depends: gir1.2-vte-2.90 but it is not going to be installed
         Recommends: libgtk2-perl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Next you would try to install either gir1.2-gtk-3.0, gir1.2-vte-2.90,  or libgtk2-perl to find out those error messages.

dpkg, the application sending those error messages, only works one-package-at-a-time, and stops at the first failure. So the first error message may not be the entire story.

---

### Post by pwabrahams on 2014-11-21
Unfortunately I can't recreate the situation (or maybe fortunately, since I got Skype installed by doing it first).  Buit if I understand what the messages are telling me, the gir1 packages can't be installed.  The messages say that they aren't going to be installed, but why wouldn't they be installed if it was possible to install them?

I've often seen problems with packages being held back or broken, but had no clue as to what to do about them.   The next time it happens, I'll post the circumstances to this very thread.

---

### Post by ian-weisser on 2014-11-21
If it is possible to install a needed package, apt will install it.
You will find out *why* a dependency package cannot be installed when you explicitly try to install it.

Usually a package that cannot be installed has a version conflict or a file conflict with a similarly-named package in a different repository.
In other words, it's often the fault of a non-Ubuntu package. We keep telling people that non-Ubuntu packages can be risky...that's the risk.

---

### Post by pwabrahams on 2014-11-22
I assume that any conflict of this kind can be resolved by removing the right package(s), probably the non-Ubuntu ones.  But how to find out which packages need to go?

---

### Post by ian-weisser on 2014-11-22
When you try to install a conflicting package, the error message will tell you the nature of the problem.

Example:
1) You get an error that the 'foo' and 'libfoo' packages cannot be updated. Not too helpful.

2) First, you try updating 'foo' manually on the command line with the same result. Now you know that the problem is caused by one of the listed dependencies of foo. Since there's only one listed dependency (libfoo), that narrows the field of possible candidates considerably!

3) Next, you try updating 'libfoo' manually on the command line. This time, the error is *different* and provides more information.
The error message is that package 'libfoo-1.1.1~ubuntu1' cannot be installed because the older version of 'foo' requires 'libfoo-1.1~ppa'
See the difference? In this example, the problem is caused by a PPA-supplied version of libfoo (and foo).

It's not just removing the appropriate package. Remember to disable the source of that package too.

---

