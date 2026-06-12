---
title: "After installing Ubuntu, Vista will not boot"
date: 2007-06-10
forum: General Help
---

### Post by nym725 on 2007-06-10
hello i am a first time ubuntu user. when i get to the grub loader, it gives me the ubuntu options and then two windows vista options. i chose the vista option and it gets to the loading screen and after that it turns black. i used the ubuntu partitioner in the beginning of installation..i am unable to use the "chkdsk" prompt by loading the vista DVD because after it boots the screen never loads, and it never gives me any options. also the gateway recovery thing does not work and just turns a black screen. ubuntu loads perfect though. i really appreciate the help.

---

### Post by nym725 on 2007-06-11
would the best option be to reinstall vista now and lose all my files? :(

---

### Post by jimbob on 2007-06-11
You may end up having to reinstall Vista.

I have read about problems like this happening because of not using the Vista partitioning manager.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by nym725 on 2007-06-11
ok thanks, im going to wait another day, and if no one can help, im going to cut my losses

---

### Post by nym725 on 2007-06-12
anyone know how i can reinstall vista if when insert the CD it boots and freezes?

---

### Post by jimbob on 2007-06-12
I have zero experience with Vista so can only guess.

 Boot Ubuntu back up and download and burn a stand-alone bootable copy of Gparted.  (It is a good tool to have around in situations like this).

    [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Boot that up and take a look at your partitions - you may need to delete and recreate the first partition before Vista will accept it.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

