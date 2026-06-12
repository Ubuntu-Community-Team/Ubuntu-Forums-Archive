---
title: "/home/user/.fr-****** directories"
date: 2008-06-05
forum: General Help
---

### Post by DMM8787 on 2008-06-05
Recently I have noticed several .fr-****** directories located in my /home/user/ directory. I'm hoping to find out which application creates these directories, and a method to disable it. Within the directories are full copies of files which I have deleted up to a week ago.

I've emptied my trash bin, as well as /home/user/.local/share/Trash/, but the files still remain.

I'm running Gnome, on Hardy with all recent updates installed.

Thanks!

---

### Post by utsuprainfra on 2008-06-05
delete them?  move them to /tmp?

---

### Post by DMM8787 on 2008-06-05
Preferably, I would like them to not be created in the first place. I'm sure they serve some purpose other than to create exact copies of data I'd like removed... but I'm just not sure what that purpose is yet.

Yes, I can delete them now... but I'd like to know what is responsible for making them.

---

### Post by utsuprainfra on 2008-06-05
make / open a dummy file with suspect apps & delete it, checking after each experiment?

could it be fileroller?  can i have the full name of one of those directories?

---

### Post by DMM8787 on 2008-06-05
When looking further into File Roller, it seems that is the culprit.

The full name of one of these folders is "/home/david/.fr-LuX4yi/".

However, I think I may have found a bug already linked to this problem. It could be possibly be from something terminating file roller during an extraction. It seems the following bug is where I'll go next,

[https://bugs.launchpad.net/fileroller/+bug/90328](https://bugs.launchpad.net/fileroller/+bug/90328)

Thanks for your help.

---

