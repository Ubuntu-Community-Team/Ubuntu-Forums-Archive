---
title: "Double chocolate latte - installation"
date: 2007-07-18
forum: General Help
---

### Post by daenney on 2007-07-18
Hey guys,

I've been Google'ing the whole day but I just can't seem to find anything about this.
We just set up a testing enviroment here on a Ubuntu desktop to test Double Chocolate Latte, which can be installed by apt-get install dcl

It installs nicely in /usr/share/dcl/ and I built a symlink /var/www/dcl that points to /usr/share/dcl/www

So i thought, lets try it, ofcourse, deosn't work, you're supposed to run a setup first, in order to do some configuration and add some things to the database. 
Turns out, the /setup dir isn't anywhere on the system.
Now I guess there's a very good reason for this not to be there but what am I supposed to do next, looked into the documentation, couldn't find anything usefull so I'm stuck with an uncofigured and hence broken install of Double Chocolate Latte

We really need this package to be up and running as fast as we can in order to make clear to management that buying a 20000$ program that does the same but with less options really is a stupid idea.

So please guys, what am I supposed to do to get this thing working?

---

### Post by daenney on 2007-07-20
Turns out, the dcl package is broken.
It includes a quite ancient sql dump which just doesn't seem to work with Mysql4 or Mysql5.

After some digging I decided to check out the SVN repository and there we go, problems solved, some new functionality and a much nicer and functional theme too.

If anyone from the package maintainers reads this, it would be best to exit the dcl package for now until the forthcoming release of it, we're now at 0.9.5RC7

---

