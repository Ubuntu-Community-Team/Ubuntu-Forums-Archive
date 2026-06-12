---
title: "Stupidly changed permissions on all folders"
date: 2007-03-26
forum: General Help
---

### Post by Pale_Buddha on 2007-03-26
OK, so I'm a complete and total idiot.

Because I was getting "unable to write" errors when I was installing Doom, I decided to change the folders' permissions by running Nautilus as root.  I set them so that the owner didn't change but the group access changed to read/write access for my group (Admin)

That worked until I rebooted.  That's when I started getting errors saying that my home couldn't be found.  So, then I changed the entire file system permissions giving myself read/write permissions but did not change the owner.

I rebooted and now it's worse than ever.  Basically, nothing can be found.

My question is:  Can I fix this or am I better to re-install (and lose all my settings)?

Thanks for any help you can give
PB

---

### Post by zvacet on 2007-03-26
[http://linuxcommand.org/learning_the_shell.php]("http://linuxcommand.org/learning_the_shell.php")

---

### Post by khedron on 2007-03-26
You don't have to lose all your settings, just copy your /home folder over to the new installation. 

Unless you custom installed some programs. You would have to reinstall those if you reinstalled Ubuntu.

---

### Post by Pale_Buddha on 2007-03-26
> **zvacet said:**
> [http://linuxcommand.org/learning_the_shell.php]("http://linuxcommand.org/learning_the_shell.php")

I'm sorry but this is quite a substantial website (which I've bookmarked) but where in there should I look to find the answer to my question?

Thanks
PB

---

### Post by Pale_Buddha on 2007-03-26
> **khedron said:**
> You don't have to lose all your settings, just copy your /home folder over to the new installation. 

The problem would come with it no?  The permissions would still be screwed up.


Unless you custom installed some programs. You would have to reinstall those if you reinstalled Ubuntu.

Yeah, I had Beryl working and everything
:( 
PB

---

