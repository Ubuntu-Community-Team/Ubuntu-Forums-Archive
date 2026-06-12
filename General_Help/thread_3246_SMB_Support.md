---
title: "SMB Support?"
date: 2004-11-04
forum: General Help
---

### Post by Gamefreak on 2004-11-04
Just got Ubuntu and I was wondering how one might aquire "SMB Support" (for Windows filesharing on a network). The computer it's on isn't online however and I'm a bit of a Linux newbie so if you could point me in the right direction of files to get, that'd be swell.

Thanks ya'll.
-Gamefreak

(Edit: Also, a tad off topic but; what type of files should I be looking for when downloading? I think I remember hearing .rpms were Redhat and so that won't do I'm assuming. .debs sound ok since it's Debian based but then I don't want to assume anything.)

---

### Post by donut on 2004-11-05
Hi Gamefreak

You should have SMB support ('samba' on Linux) installed by default. To test that this is the case, search for the package name 'samba' using the GUI Synaptic Package Manager or run the following from the command line:

```
dpkg --list | grep samba
```
You can use the file manager (Nautilus) to browse the SMB shares on your network. Choose the panel menu option 'Computer | Network' and open the WindowsNetwork icon that appear in Nautilus - this should let you drag and drop files accross the network, etc.

Good luck

Paul

---

