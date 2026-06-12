---
title: "installing a tar.gz"
date: 2008-06-13
forum: General Help
---

### Post by ktthomps on 2008-06-13
I'm fairly new to linux running ubuntu 8.04, and am having trouble installing a tar.gz file.  It is a compiz file I downloaded of of compiz.org and it is the file v0.6.2 (stable).  I downloaded the file, and created a folder on my desktop and extrated the files to the folder.  After I extracted the file the only file that remains in the file is the install file and this is what is says....

compiz uses libstartup-notification which is available at
[ftp://ftp.gnome.org/pub/GNOME/sources/startup-notification/](ftp://ftp.gnome.org/pub/GNOME/sources/startup-notification/)

compiz uses automake, in order to generate the Makefiles for compiz use:

	$ autogen.sh

After that, standard build procedures apply:

	$ make
	# make install

I have tried changing the directory to the Desktop in the terminal and running the autogen.sh in there but no luck.  All it says is 

kyle@kyle-laptop:~$ cd /home/kyle/Desktop/compiz
kyle@kyle-laptop:~/Desktop/compiz$ autogen.sh
bash: autogen.sh: command not found
kyle@kyle-laptop:~/Desktop/compiz$ 
kyle@kyle-laptop:~/Desktop/compiz$ 

Any luck installing this would be greatly appreciated.  Thanks

-Kyle

---

### Post by aysiu on 2008-06-13
Any problem with the Compiz in the software repositories?

---

### Post by ktthomps on 2008-06-14
i tried searching for compiz-0.6.2 and nothing was found.  I'm very new to linux, and am kinda lost would appreciate the help.

---

### Post by dexter on 2008-06-14
> **ktthomps said:**
> i tried searching for compiz-0.6.2 and nothing was found.  I'm very new to linux, and am kinda lost would appreciate the help.

Try searching for compiz, it will show up.

---

### Post by Joeb454 on 2008-06-14
Compiz is installed by default as of Ubuntu 7.10 and later :)

---

### Post by aysiu on 2008-06-14
Try this:
[http://www.psychocats.net/ubuntu/desktopeffects](http://www.psychocats.net/ubuntu/desktopeffects)

---

