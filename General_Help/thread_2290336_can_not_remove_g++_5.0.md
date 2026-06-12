---
title: "can not remove g++ 5.0"
date: 2015-08-11
forum: General Help
---

### Post by newcfd on 2015-08-11
I installed g++ 5.0 because the current version of g++ in Ubuntu is 4.9.2.
When I tried to uninstall 5.0 and rolled back 4.9.2, I was not allowed to do it because of too many dependencies.
How can I remove it? Thanks for your help.

---

### Post by mc4man on 2015-08-11
Below assumes you installed a g++ package for 5.0, if not then describe what you did in detail...

The g++ package is a dependency package, other than pulling in required dep packages it installs 2 symlinks to the gcc-X.X it was built for. 
So you'd just install the default g++ package to return to the default supplied gcc-X.X using sudo dpkg -i /path/to/g++ package
If on vivid that package could be retrieved from here for whatever arch you have
[http://packages.ubuntu.com/vivid/g++-4.9](http://packages.ubuntu.com/vivid/g++-4.9)

Did you also install a newer gcc dependency  package or just the g++ one?
( run in a terminal to see - 
gcc --version

---

### Post by newcfd on 2015-08-11
I installed only g++5. It was automatic. I tried to purge g++-5-base. The whole OS is broken. Now I have to reinstall ubuntu. Shoot.
I can not boot to reinstall from my usb key after I copied the ubuntu iso into it

---

