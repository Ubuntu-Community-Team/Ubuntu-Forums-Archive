---
title: "hplip and all this gunk on my desktop"
date: 2008-05-19
forum: General Help
---

### Post by notesetter on 2008-05-19
Hello,

I downloaded and followed the install procedures for hplip given at the website 

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

and now I have all these files on my desktop from the install. Can I delete all of these files? Has anyone else had this problem? If so, what did you do about it?

Thanks,

Dave

---

### Post by redoscar3 on 2008-05-19
I suspect that you can delete all those installer files from your Desktop.  The important stuff was probably placed in /usr/bin or someplace safe.

Any reason why you didn't use the package already in the repositories?  Did you just need the newer version?

---

### Post by notesetter on 2008-05-19
Thanks.

Actually, I wasn't aware of a version available in the repositories. I might elect to use that one instead, since I suspect the installation will be more seamless. Already, when I choose Applications==>Accessories==>HP Device Manager, nothing happens.

How might I delete the installation I just performed?

Thanks.

---

### Post by redoscar3 on 2008-05-19
You might look to see if the installer you used has a remove function.  If so, then you could use that to get rid of the stuff that is not on your Desktop or your /home directory.  If it doesn't have an uninstaller, then you might have to go through and manually delete those files it deposited on your hard drive.  This can be pretty dangerous and a good way to break stuff.  This is one of the reasons why sticking with the package manager like synaptic is so good.  It can take care of most of the housekeeping chores.  Plus things might be better configured for your environment.  If a menu item is available it oftentimes will show up in your applications menu.

There is a pretty good possibility that installing the hplip package via synaptic will overwrite the stuff you just installed, unless they get placed in different directory.

If you are new to Linux and Ubuntu, it is very helpful to stay with the repositories until you get more experience.

---

### Post by notesetter on 2008-05-19
In addition to all the installation files left on the desktop, there was a folder created called "hplip-2.8.5" which I cannot access unless I login as root. There is a similar folder in /usr/share that is simply named "hplip" with no special permissions. When I searched the Synaptic Package Manager, I found that hplip was already installed, so I probably fouled it up when I tried to run the installer. I'm going to delete any related files that were plopped onto the desktop, then mark hplip for complete removal from within Synaptic, and then reinstall from Synaptic.

Thanks again.

replying now to the networking thread.

---

### Post by redoscar3 on 2008-05-19
I think the hplip package is installed by default.  It's on my system and I don't have any HP hardware.  It probably has the drivers necessary for printing, scanning, and whatever other functions are supported.

An Ubuntu package for my Samsung SCX-4100 would be nice.

---

