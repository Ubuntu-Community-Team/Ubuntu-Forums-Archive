---
title: "Install Directory, cmake, gnucash"
date: 2018-10-12
forum: General Help
---

### Post by webmanoffesto on 2018-10-12
I downloaded the most recent GnuCash (much newer than what's in the standard repo). I want to install it. It uses CMake. To do that I'll need to choose an install directory. If I go to /home/user/ I don't see software folders. In what folder does Ubuntu put software? I want to install this software there too.

Ubuntu 16.04 Gnome

---

### Post by TheFu on 2018-10-12
Software that you compile yourself should NOT be mixed into the same directories with the software installed via APT. IMHO.

 If it uses cmake, then you'll need to install any dependencies, compile those dependencies, compile gnucash, then you can install it so where ever you like. Usually manually installed software and libraries are placed into /usr/local/ , but you can put it anywhere you like. Just beware if you put it somewhere else, there might be unwanted impacts.  

Further, by building it from source, you've signed up to manually maintain the software from now on and all the dependencies.  Getting fresh libs and code then rebuilding it monthly would be lax, but probably more than most people are willing to do.  It is a pain, which is why staying with the repo is best for 99% of the world.

None of this is done from a GUI.

Going with a reputable PPA as suggested below by oldos2er, would be preferred over building from source, unless you are C software developer and doing the compiles/dependencies/linking and manual install  is 2nd nature already.

---

### Post by Tadaen_Sylvermane on 2018-10-12
Just because it is newer doesn't mean it's better. Should stick with repos unless you have an actual reason beyond just "the newest".

Most of the time the changes are so minor it isn't worth the effort. Just a thought to consider.

---

### Post by oldos2er on 2018-10-13
It would be easier to install from [PPA]("https://launchpad.net/~sicklylife/+archive/ubuntu/gnucash") rather than compiling, but it's your choice.

---

### Post by rbmorse on 2018-10-13
The GnuCash Wiki has an excellent Ubuntu specific section on building and installing GnuCash from source.  It can be viewed at 

[https://wiki.gnucash.org/wiki/Ubuntu](https://wiki.gnucash.org/wiki/Ubuntu)

There is also some additional useful information in the Gnucash-user mailing list archive ([https://wiki.gnucash.org/wiki/Mailing_Lists](https://wiki.gnucash.org/wiki/Mailing_Lists)) but the search function is temporarily compromised and it takes a bit of diligence to get to the good parts. 
 
I would normally agree with the advice to stick to your distribution's repository where possible, and only if absolutely necessary use a ppa version if it addresses a critical issue that affects you directly.  Having said that, I am a GnuCash user and the changes from the 2.X series to the 3.X series are significant and useful, especially where it comes to business reports.  I found that going through the monkey motion of building ver. 3.3 was worthwhile for my purposes.  

However...this just this morning I learned that the next Ubuntu release (cosmic), scheduled for release on 18 Oct,  has GnuCash 3.3 in repository.  If you intend to do that upgrade Gnucash 3.3 will come with it.

---

