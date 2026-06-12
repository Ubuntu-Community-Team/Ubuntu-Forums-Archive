---
title: "Nubuntu User...  Update Mgr on Fritz..."
date: 2008-06-28
forum: General Help
---

### Post by casparov on 2008-06-28
Hi, Everyone...  

Thanks to the generosity of these forums I have an OS (Ubuntu 8.04) that's just about everything (sans printing and a couple of other things) that I could desire.  But I cannot update the system because the Update Mgr generates this message:  

[HTML]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing libaudiofile-dEv (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/HTML]

Does anyone know how to troubleshoot this error?

(One day I look forward to helping another--for now, I'm just about helpless.) 

All Regards, 

Casp

---

### Post by VMC on 2008-06-28
If you go here, what do you have checked off for reporitories:

System --> Administration --> Software Sources

Also, what were you last trying to install that caused that error. Something with Package libaudiofile-dev.

---

### Post by nikgare on 2008-06-28
What error do you get when after closing the update manager you run the folowing in a terminal?

sudo aptitude update

---

