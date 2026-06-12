---
title: "upgrade vmplayer 1.xx to 2.xx Feisty"
date: 2007-05-31
forum: General Help
---

### Post by longlegs on 2007-05-31
I would like instructions on how to upgrade the vmplayer that installed with Feisty to the latest version from Vmware. (2.0xx)

I have Feisty 7.04  installed and seemingly running well.

thanks
longlegs

---

### Post by PFilter on 2007-05-31
I'm working on a project along these lines, and it may end up producing a vmplayer-2 .deb.

Our goal is to 
a. Boot live media
b. Run VMWare Player
c. Launch our Windows image

The purpose of this setup is to remove any dependency on the underlying operating system (we still need a minimum hardware requirement to meet our performance needs).

So far, I can install VMPlayer 2 on Ubuntu Fiesty using the tar.gz installer from vmware.com.
Everything appears to work.

But, using checkinstall to follow the installer and make a deb isn't working.
Checkinstall gives an error, asks if I want to review the logs.
The log says it failed when installing a new module, paraport.ko, because it conflicts with another paraport.ko included in an updated Ubuntu kernel package.

If anyone knows of another project working along similar requirements, I'd be glad to check with them to see if I can help them / they can help me. Any pointers are appreciated.

Thanks,

~Rob

---

### Post by chaumurky on 2007-05-31
This worked for me:
* uninstall vmware-player (keep the installed vmware-player+tools kernel modules)
* Install my kernel's header package and build-essntial
* download the new vmware tar from the official site
* run the install script.
* if it complains about an existing install let it remove the install database.

Ba da bing...

---

### Post by longlegs on 2007-06-06
Thanks folks!
I'll have time to try that in a few days. Will post results in same thread.

Longlegs

---

### Post by longlegs on 2007-06-09
Hi chaumurky , 
I tried that last set of instructions you gave and it worked fine after I figured how to tell  terminal the right command and use sudo in front.
In addition, I copied the files from the VM i have in win2000 to ubuntu, (I had made a projects dir so put them there ) then when I started VMPlayer 2.0 it let me browse for those files and ran my VM just fine. Now if I can make Ubuntu see my WD "My Book" 329g USB drive i'll be tickeld pink.

Thanks a bunch
longlegs

---

