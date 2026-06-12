---
title: "Finding Source Packages and Recompiling"
date: 2007-01-11
forum: General Help
---

### Post by kq6up on 2007-01-11
is there a howto or can someone tell where I can find source packages for apps (specifically xastir).  I want to re-compile with different options.  What packages do I need to re-compile (gcc and others I assume).

---

### Post by bodhi.zazen on 2007-01-11
Well to start with you will need build-essential

You may also want to look at checkinstall:

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

[http://www.howtoforge.com/howto_linux_debian_deb_checkinstall](http://www.howtoforge.com/howto_linux_debian_deb_checkinstall)

Source forge is a good place to look as is your application's home page ....

---

### Post by kq6up on 2007-01-11
Thanks, I've used check install before for slackware.

---

### Post by mcduck on 2007-01-11
'sudo apt-get build-dep packagename' will install dependencies needed to compile a package.
'sudo apt-get source packagename' will download the package's source code to current directory.

---

### Post by kq6up on 2007-01-11
That is awesome, I didn't know I could do that.  That opens up a lot of possibilities.

---

### Post by marx2k on 2007-01-11
> **mcduck said:**
> 'sudo apt-get build-dep packagename' will install dependencies needed to compile a package.
'sudo apt-get source packagename' will download the package's source code to current directory.

Question: Let's take the package 'conky' for instance.  Ubuntu repository for Conky is version 1.4.2

Latest build is 1.4.5

So what is the method to use to get it to actually work with the latest build 1.4.5 and not give me 1.4.2?

---

### Post by majoridiot on 2007-01-11
if you always want the latest, don't apt-get or use a package manager.  get the latest source from the developer's page and compile it yourself.

---

### Post by kq6up on 2007-01-12
You can still use the package managers with the latest sources.  Just use checkinstall.

---

### Post by Delkster on 2007-01-12
> **mcduck said:**
> 'sudo apt-get source packagename' will download the package's source code to current directory.

That is correct and very useful. You don't need root privileges (sudo) for the "apt-get source" command like you would with other apt-get commands, however, since it doesn't actually install anything in the system directories. Instead, it just extracts the source archive into the current working directory so as long as you're within the realm of your home directory (and you should be) you'll be able to do it without root privileges.

In fact it's even better to extract the source without sudo because if you do it with root privileges, the resulting directory will be owned by root, and in order to make modifications or add files (which compilation does) within that directory you'll also need root privileges (or need to change the owner or permissions of the files after extracting).

If you extract the source without sudo, the only part where you'll need root privileges is actually installing the software after compiling.

Just a little tip.

---

### Post by marx2k on 2007-01-12
Sorry, wasnt thinking very clearly with my last post.  I guess since for the most part, repository versions and advanced versions of the same software have the same dependencies (usually), i can just use this method to get the dependencies for the earlier version and then when that's done, compile the later version!

I also really enjoy using checkinstall to create the deb distributable so I can track where everything goes through a package installer and remove everything if need be.

These 2 methods of compiling from source make everything a breeze (relatively)... until something goes wrong, of course, or if what I'm trying to get the dependencies for isn't in the repository. Then I'm screwed :)

---

