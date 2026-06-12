---
title: "All my apps are gone! Help!"
date: 2007-03-13
forum: General Help
---

### Post by jlist on 2007-03-13
I did something stupid. I just wanted to try gcc 3.x for a problem I was having so I removed gcc 4.0 and gcc 4.0 base packages. But lots of other packages were removed i guess because they depend on those two packages. The gone packages include x window, aptitude, apt-get, and many many others. 

Now that I don't even have apt-get, is there still a way to get them back?

I wish the OS at least had warned me that it would be a dangerous thing to do before i realized it was too late!

Thanks,
jlist

---

### Post by peabody on 2007-03-13
No apt?  Are you sure you only told it to remove gcc?  Do you still have dpkg?  If so, you could copy the dpkg file over to the system and use sudo dpkg -i file to install apt-get.  The trouble will be in managing the dependencies yourself.

---

### Post by Gerard Barberi on 2007-03-13
Go here and you can reinstall apt (replace dapper with your version in the URL)
[http://packages.ubuntu.com/dapper/base/apt](http://packages.ubuntu.com/dapper/base/apt)

Hopefully you can still have dpkg to install it

afterwards you can
sudo apt-get install synaptic

Also, I'm not sure which way you removed the gcc package (GUI or CLI), but it should have notified you of any other packages it would remove.  In synaptic's GUI, a window pops up listing all packages to be removed.  The command line says it before it asks you y or n.

---

### Post by jlist on 2007-03-14
Thanks for the replies. I was luck that I still got dpkg and wget. So I downloaded apt deb file, and got apt back. Then I installed kubuntu-desktop and pretty much got the important things back. I'm still missing something but at least I'm able to work in GUI :)

btw, i use Adept from kubuntu. No, it doesn't show me a list of packages that will be removed! I'm using breezy though. New versions could have changed.

---

