---
title: "What are *.READLOCK and *.WRITELOCK files???!"
date: 2007-07-07
forum: General Help
---

### Post by diablo75 on 2007-07-07
VMware was abruptly killed during my last session, and upon reboot I can't access the virtual machine files needed to run the XP box I have on VMware.  Upon looking at the contents of my XP /vmware-server/virtual machines/windows xp professional/ folder, I find that there are a couple files that seem to just be 11 bytes each, named the same thing as another important file in the directory, with an added .READLOCK or .WRITELOCK extention.  I can't alter the name of it either.

If you don't know what it is yet like me, then you're probably still reading this...

To those who didn't even need to read this post and help me solve my problem that fastest, well KUDOS to you good sir!  =D>

Now, what do I do about those files?  Is it safe to just delete them?  Will I be able to delete them?

Edit:  I don't know exactly WHAT they are, but simply deleting these files allowed my virtual machine resources to be accessible by vmware-server.  Problem solved.

---

### Post by PilotJLR on 2007-07-07
Yes - delete them as root, then restart your VM once they are deleted.

These files are leftovers from the unexpected termination of the vm session... so they need to be manually removed in order to restart the vm


edit: but then... it seems you already saw that  :-)

---

