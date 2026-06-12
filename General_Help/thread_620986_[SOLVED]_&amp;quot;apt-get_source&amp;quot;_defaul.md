---
title: "[SOLVED] &amp;quot;apt-get source&amp;quot; default config"
date: 2007-11-23
forum: General Help
---

### Post by CheShA on 2007-11-23
Hi folks,

this is a bit of a n00b question maybe, but I just wanted to sanity check before I went any further.

if I ```
apt-get source
``` and then do a basic```
./configure && make && make install
``` then is it reasonable to think that the installed application will have all the same properties as the ```
apt-get install
```-ed version?   i.e. if I add ./configure options, they will be options moving away from the default apt-get install configuration, I won't need to add a bunch of ./configure options to start off in order to get the same result as if I had installed from repo?

I hope this makes sense.

(apologies for cross posting; this was posted initially in the wrong forum topic in error. A request to move it was ignored.)

---

### Post by espressopigeon on 2007-11-23
There will probably be only two differences, one, you cannot remove the compiled program through the Synaptic package manager. Unless, however, you install a program called checkinstall and substitute "checkinstall" for the command "make install". checkinstall will make the program show up in Synaptic and thus enable easy removal in the future.

Two, using apt-get install is faster, and you won't have go out and manually fetch all the libraries that ./configure says you need.

So you should use apt-get if possible.

---

### Post by CheShA on 2007-11-23
> and you won't have go out and manually fetch all the libraries that ./configure says you need

i can always do 
```
apt-get build-dep
```

i need configuration which is slightly different from the default or i would use apt-get install. I just wanted to know that I could basically reconfigure and install over thr top without too much worry. Thanks for the info, and thanks  for the tip re: checkinstall, sounds useful.

---

