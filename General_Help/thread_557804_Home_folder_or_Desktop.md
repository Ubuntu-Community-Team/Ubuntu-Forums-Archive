---
title: "Home folder or Desktop?"
date: 2007-09-23
forum: General Help
---

### Post by manatee7 on 2007-09-23
Hi, just a quick question:

Just wondering what the etiquette is with saving all of my stuff into my home folder, or onto my desktop slash does it not matter? 

I didn't want all of the random folders created by programs in with all my documents... so it is all on the desktop.

thanks

---

### Post by PmDematagoda on 2007-09-23
I just create folders like "My Computer" or "My Documents" within "Desktop":p, call me a traitor but it is easier for me. You can do the same, put one base folder in the Home folder or on the Desktop and build from there.

---

### Post by manatee7 on 2007-09-23
so the documents folder can stay on the desktop?

---

### Post by questpro on 2007-09-23
I use Home folder for keeping my stuff. And use the  Desktop folder as in windowsOS desktop.  

As you possibly know, the terminology is different in linux and windows. 

Check this link I found in this forums, might help you

[http://www.secguru.com/files/linux_file_structure.jpg](http://www.secguru.com/files/linux_file_structure.jpg)

---

### Post by PmDematagoda on 2007-09-23
> **questpro said:**
> I use Home folder for keeping my stuff. And use the  Desktop folder as in windowsOS desktop.  

As you possibly know, the terminology is different in linux and windows. 

Check this link I found in this forums, might help you

[http://www.secguru.com/files/linux_file_structure.jpg](http://www.secguru.com/files/linux_file_structure.jpg)

Same here. I find it easier to have the vital folders on my desktop than hidden around, but I don't over do it and I'm not organised, you should have a look at my Home folder:p.

---

### Post by manatee7 on 2007-09-23
so how do i stop programs from dumping ugly folders in the home folder, or is that just what happens?

---

### Post by PmDematagoda on 2007-09-23
> **manatee7 said:**
> so how do i stop programs from dumping ugly folders in the home folder, or is that just what happens?

Programs like Azureus, etc need to store data somewhere, data meaning your data, such as movies, songs, etc. Since the Filesystem is usually out of bounds for those programs they need to use the only folder that is open. Your Home folder, so it will be very difficult to stop programs from littering your Home folder.

P.S. Windows is even more disorganised than Linux.;)

---

### Post by Wolki on 2007-09-23
> **manatee7 said:**
> Just wondering what the etiquette is with saving all of my stuff into my home folder, or onto my desktop slash does it not matter? 

Personally, I just make my home folder my desktop (it's an option in gconf). No need to keep separate top-level hierarchies for my data, makes it easier to find stuff and to keep things somewhat clean.

> I didn't want all of the random folders created by programs in with all my documents... so it is all on the desktop.

Most folders that programs create are hidden, so I don't mind them that much. Programs that create non-hidden folders and don't allow me to choose the location are evil, but there shouldn't be many of them.

Plus there's always .hidden files - create a file called .hidden and write file or folder names in there. They'll be treated like hidden files.

---

### Post by strabes on 2007-09-23
> **manatee7 said:**
> so how do i stop programs from dumping ugly folders in the home folder, or is that just what happens?

You can't. Those "ugly" folders (the ones with a "." in front of them) are the settings and temporary data for each of the programs. If you delete them you'll lose your preferences. The easiest thing to do is to just hide the hidden files. To do this, inside nautilus go to "View" then uncheck "Show Hidden Files."

I like having a clean desktop so I don't store anything on it. I even disabled mounted media from showing up on it and I just use the disk mounter panel app. I also don't store anything in my home folder. I have a separate data partition that I keep all of my documents, music, etc. on. This way I can access it in windows or ubuntu since my laptop is dual booted and I don't have to worry about copying my data elsewhere when I reinstall or upgrade.

---

