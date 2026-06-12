---
title: "Linux vmware: read virtual machines from windows partition"
date: 2007-09-21
forum: General Help
---

### Post by bibawa on 2007-09-21
Hello,

I've installed windows and ubuntu. Now i've installed vmware server in Windows..

Now I wan't to access the same virtual machines in Linux, I've installed vmware server in linux I've runned the config file, all things gone fine..

When I open the virtual machines from my windows partition in linux (i've mounted it) and press the power up button the virtual machine screen gone black for a 30 seconds an then the system go directly to "shut down"..

When I copy the virtual machine from my windows partition to my linux desktop and run it from there than everythings gone fine....

What's wrong with my config ?

---

### Post by MrHippocampus on 2007-09-21
Your windows partition is probably read-only at the moment (thats the default behaviour). Making it read/write should make the virutal machine's work, [this]("http://ubuntuforums.org/showthread.php?t=555594&highlight=ntfs+config") post has instructions on how to do that.

---

### Post by bibawa on 2007-09-21
No, I've installed sudo apt-get install ntfs-config to make them read / writable , I can create folders etc...

---

### Post by MrHippocampus on 2007-09-21
Searching google seems to show that a few people are having this problem, its mentioned (in this case it crashes vmware but it may be the same problem) on the ntfs-3g support page [here]("http://www.ntfs-3g.org/support.html#vmware").

---

### Post by bibawa on 2007-09-21
When I do that everything is ****** up :s

---

### Post by MrHippocampus on 2007-09-21
Have you tried opening the virtual machine files with virtualbox instead of vmware? I seem to remember that it can happily read vmware files.

---

