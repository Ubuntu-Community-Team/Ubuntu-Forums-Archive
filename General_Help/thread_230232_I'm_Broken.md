---
title: "I'm Broken"
date: 2006-08-05
forum: General Help
---

### Post by LinuxLemur on 2006-08-05
Gooffing around with everything caused bad things to happen.  I was trying to install the ri-li train game and it needs a libc6 dependecy.  I looked in synaptic and I had libc6 2.3.6-0 and it wanted 2.3.6-6.  So I downloaded -18 from a debian web site and ran it and it needed tzdata.  Well, I tried to install that with no luck either.  Now I went into synaptic and all my libc6 installs are broken and if I mark for removal or reinstall, it wants to uninstall practically my whole system.  Now if I knew is knew of the chances of this great of a curruption, I would have never done it.  The damage is done and I need an alternative and maybe I can learn something

Anyone can help?

---

### Post by em3raldxiii on 2006-08-05
Have you tried opening a console and using ```
sudo apt-get install *whatever_thing_is_missing*
```?
 
Usually this will grab the required dependencies on the fly.  In many cases, it will fix b0rken stuff too.

---

### Post by LinuxLemur on 2006-08-05
> Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-18 is to be installed
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-18 is to be installed
  ri-li: Depends: libgcc1 (>= 1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
         Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.9-0.0ubuntu2 is to be installed
         Depends: libstdc++6 (>= 4.1.0) but 4.0.3-1ubuntu5 is to be installed
         Depends: ri-li-data (= 1.2.0-1) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

In synaptic, it says 2.3.6-18 is installed already and broken along with libc6-dev and libc6-i686.  I would like to revert back to 2.3.6-0 that ubuntu was previously at.

---

### Post by LinuxLemur on 2006-08-05
Maybe I can try to updat the -dev and -i386 to -18 too.  I just need to fix this up.

---

### Post by em3raldxiii on 2006-08-05
Well, I admit, I am somewhat out of my element with this one, but I am posting partly to keep this thread alive :D
 
Have you tried the <tt>sudo apt-get -f install</tt>?

---

### Post by LinuxLemur on 2006-08-05
First I removed ri-li with:

sudo dpkg -r ri-li

Then I noticed that when I right click on libc6 in synaptic I can bring up the properties and view version information which listed the previous -0 version.  As I read, all I had to do is click on libc6 in the synaptic, then select "force version" from the packages menu.  I selected the correct version to revert back to and it all got fixed.  Not sure how to accomplish this on the command line though.

I'm fixed!

---

### Post by LinuxLemur on 2006-08-05
Now I go on to break it again another day. :D

---

### Post by em3raldxiii on 2006-08-05
Good work, my friend.  Now ... the hard part is to remember it all ;)
 
Happy b0rking!

---

### Post by az on 2006-08-05
Avoid adding non-ubuntu repositories.

---

### Post by LinuxLemur on 2006-08-05
After doing a search of the forums, other people seem to have the same problem with the tzdata.  The solution usually seems to be something other than installing it, like updating jave through synaptic.  I am just wondering if there is another solution to installing ri-li than to try to update libc6 to 2.3.6-18. (watever the -18 means - come on, how many different #'s need to be in the version?)

Sticking with the repository given 2.3.6-0 means waiting till Unbuntu wants upgrade the repositories to play the game?

---

### Post by az on 2006-08-05
> **LinuxLemur said:**
> 
Sticking with the repository given 2.3.6-0 means waiting till Unbuntu wants upgrade the repositories to play the game?

Or compile from source.  Or build the package from source.

---

### Post by LinuxLemur on 2006-08-05
Found a klik install at ri-li.klik.atekon.de/ but the link didn't work.  

I will try the compile a build thing.  Gonna have to do some learning.

---

