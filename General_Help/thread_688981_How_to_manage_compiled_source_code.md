---
title: "How to manage compiled source code"
date: 2008-02-05
forum: General Help
---

### Post by roastbeef on 2008-02-05
This is not really a technical question, more of a philosophy question which I haven't been able to find much information about.

I've reached the point in my linux-fu where I can compile code from source, however I suppose I still have some questions about this process.  Packages are nice and neat in that if I need to remove them, I just do a 'aptitude remove pkg-name', but with source code once I compile it the only way to remove it is 'make uninstall' (if I still have the source code on my system), or through some other process like a uninstall python script.

For one such example of this, I use duplicity to make backups to amazon s3, and the current package is older than the current version (which I'll need to install from source).  I just don't want to be in a position when the package gets updated to have to uninstall the compiled-version.  I also could create a package of the compiled code, but I'm not sure what would happen if I tried to install the official debian/ubuntu package when the official package gets updated.

Further more, I can easily keep track of all my installed packages through synaptic, but with installed code it's hard for me to keep track of it - I'm sure I have some program installed that I have since forgotten about.

Finally, some programs provide access to their svn builds, but to manage those I need to go into the directory and pull down the newest code - something I neglect to do, and tedious if it is across multiple directories.

Does anyone have recommendations on how to manage compiled code and svn repositories?

---

### Post by bodhi.zazen on 2008-02-06
You can make a .deb with checkinstall :

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

	[http://www.howtoforge.com/howto_linux_debian_deb_checkinstall](http://www.howtoforge.com/howto_linux_debian_deb_checkinstall)

	[http://pwet.fr/man/linux/commandes/checkinstall](http://pwet.fr/man/linux/commandes/checkinstall)

[list][*]./configure --prefix=/usr
	[*]make
	[*]sudo checkinstall -D[/list]

Now you can install / manage with dpkg

The only problem is that occasionally checkinstall fails ...

Is that what you are looking for ?

---

