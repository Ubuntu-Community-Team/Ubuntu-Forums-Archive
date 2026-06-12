---
title: "gimpshop"
date: 2005-06-06
forum: General Help
---

### Post by anatole on 2005-06-06
hi,
i've searched the forums and found earlier posts about gimpshop, but i don't know, what's the situation now? is gimpshop available for hoary, without messing it up?
i only found the source on the net ( [this](http://gimpshop.de/download/GIMPshop-source-2.2.4.tbz) one) but i couldn't compile it for "./configure"  made this fault :
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check

is gimpshop available in a deb, or can this problem be fixed?

---

### Post by sethmahoney on 2005-06-06
Gimpshop is not available in the repositories, as far as I can tell.  You might be able to find a deb for it, though.  As far as the errors you're getting installing it, it sounds like you don't have gcc installed.  Fire up Synaptic (System->Administration->Synaptic Package manager) and search for gcc-3.3-base or, at the terminal, type:

sudo apt-get install gcc-3.3-base

If you prefer, you can use gcc 3.4 or gcc 4.0.  Type:

sudo apt-get install gcc-3.4-base

or

sudo apt-get install gcc-4.0-base

or do it in Synaptic.  After that, install g++ the same way.  The package name is g++-x.x where x.x is the version number (so g++-3.3 or g++-4.0 or whatever).  Then try compiling gimpshop again.

---

### Post by anatole on 2005-06-06
thank you! it is being compiled in the moment. needed ~10 more packages though, mostly devs :)

---

### Post by sethmahoney on 2005-06-06
[QUOTE=anatole]thank you! it is being compiled in the moment. needed ~10 more packages though, mostly devs :)[/QUOTE]
 Glad it worked!

---

### Post by hampton on 2005-06-06
sethmahoney,

Nice to see someone else from Portland. Too bad its so damn rainy!

-hampton

---

### Post by sethmahoney on 2005-06-06
I know!  This weather is messed up!  We had Summer for Winter, and now we're getting Winter and Summer alternating every half hour!

---

### Post by sethmahoney on 2005-06-06
By the way, let me know how you like gimpshop.  I've been thinking of giving it a try, but haven't gotten around to it yet.

---

### Post by raven on 2005-06-09
Hi Guys, just a curiosity
I'm reading a lot about GimpShop,
is it the same as Gimp 2.2 (which is a great btw) that is available from repository
except the features and looks like Adobe PhotoShop ???
or is it a new version with a new features ???

---

### Post by radhaz on 2005-06-09
[QUOTE=raven]Hi Guys, just a curiosity
I'm reading a lot about GimpShop,
is it the same as Gimp 2.2 (which is a great btw) that is available from repository
except the features and looks like Adobe PhotoShop ???
or is it a new version with a new features ???[/QUOTE]

This [page](http://plasticbugs.com/index.php?p=241) explains it better than I could.

In a nutshell, it makes the Gimp layout similar to photoshop so that those of us who are familiar with Photoshop don't have to learn a whole new layout.

---

