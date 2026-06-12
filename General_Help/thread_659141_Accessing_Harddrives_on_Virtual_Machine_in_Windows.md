---
title: "Accessing Harddrives on Virtual Machine in Windows VM"
date: 2008-01-05
forum: General Help
---

### Post by kioshis on 2008-01-05
So I have a HDD that was formatted using a program only windows xp can recognize. I've switched to linux and wanted to know if using a vmware [or any virtual machine prog] would allow me to see the files on that drive. Usually when i have a virtual machine im limited to what space or files i see and windows xp doesnt recognize my linux partition at all. Is it possible for a virtual machine to see files on the main hard disk partition or not? If so could someone help me in my trials?

---

### Post by .nedberg on 2008-01-05
If it is an external drive then a virtual machine can access it, yes. If it is an internal, I don't know, but I believe it is possible.

---

### Post by MrFSL on 2008-01-05
> So I have a HDD that was formatted using a program only windows xp can recognize

I'm assuming some sort of disk encryption software? I can vouch for vmware. Worked for me.

---

### Post by p_quarles on 2008-01-05
In Virtualbox, you can make any directory that's accessible from the host machine available as a "shared folder" to the Windows VM. These will become available as network shares from within the VM. I haven't used VMWare, but I imagine it's the same deal. 

In any case, that method would only work if the external can at least be mounted by Linux. If by "only XP can recognize," you mean "Linux can't even mount the drive," then that could be a problem. There are ways of getting USB devices to interface directly with the VM, but from everything I've read they're hardly foolproof.

---

