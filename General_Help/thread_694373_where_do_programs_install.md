---
title: "where do programs install?"
date: 2008-02-12
forum: General Help
---

### Post by genuchelu on 2008-02-12
I've installed some deb packages, but I don't know where to find them. For example I installed crossover, and it said that installation was complete, but I don't know how to run it. Its not under "Applications" "places" or "System" menus, Other applications I install are the same I don't know how to run them because I don't know where they are. Can somebody please help me with this...its so frustrating.

---

### Post by PeterJS on 2008-02-12
The menu's are just a helpful abstraction for the user but have nothing to do with the underlying structure of where things actually are, odds are they're in /usr/bin/ because they're non-essential programs. See the link in my signature for a full description of what's where. To find where things in specific packages are, open up synaptic find the package you're looking for, right click and select properties > installed files, that will give you a listing of everything it package installed, the program itself is in one of the bin folders.

---

### Post by mivo on 2008-02-12
An exception are Windows programs that you use with Wine or Crossover -- those are stored in your /home partition. Likewise, some native Linux programs that you install manually (not the ones you compile, usually)  may be in your /home partition as well, but you'll know that since you will have put them there. :)

---

### Post by apetresc on 2008-02-12
If I recall correctly, the Crossover installer asks you for the installation directory when you set it up. It'll be there wherever you told it to be :)

---

### Post by Christmas on 2008-02-12
Also, you may find [this link](http://forums.debian.net/viewtopic.php?t=9685) helpful. See Grifter's second post.

---

