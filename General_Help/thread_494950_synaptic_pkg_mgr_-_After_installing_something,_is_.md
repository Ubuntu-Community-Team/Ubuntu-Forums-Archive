---
title: "synaptic pkg mgr - After installing something, is there a way to list what was instal"
date: 2007-07-07
forum: General Help
---

### Post by tenkamuteki82 on 2007-07-07
Hi guys,

First post, Love Ubuntu... Great Linux distro. Finally made the switch from red hat 9 to ubuntu (yeah I know im a little late haha)

With synaptic package manager, is there a way to list all of the apps you recently installed? I know it makes an icon for packages that are installed, but I want to manage something to keep a list of the latest apps. (Instead of doing a ls -lrt on /usr/bin lol...)

Any ideas? 
Thanks!

---

### Post by ajgreeny on 2007-07-07
One way to sort of do what you want is to use the File>History menu in synaptic.  This is the nearest that I know of to a list of what you installed, though it does it by date of each time you used it rather than all in one list.

---

### Post by tenkamuteki82 on 2007-07-07
Aha neat feature.. Kinds like windows last time you used it feature...

Any ideas on how to get a list of recently installed programs? The purpose of this is to kinda have a start menu / programs listing of all installed symtantic apps (since most of them do not install in the same location).

Thanks for your help

---

### Post by tenkamuteki82 on 2007-07-08
What i did was make a Program Files Directory in my home directory:

/home/rudy154/ProgramFiles

then for every single app i installed i did:
ln -s pathtoapp myappshortcut.ln


ex)
Synaptic Manager
Installed App "Joy2key"
ln -s /usr/bin/joy2key /home/ruby154/joy2key.ln



Is this how you guys keep track of your installed apps?

---

