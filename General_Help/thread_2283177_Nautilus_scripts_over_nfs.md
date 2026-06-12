---
title: "Nautilus scripts over nfs"
date: 2015-06-19
forum: General Help
---

### Post by agibby5 on 2015-06-19
I tried to setup a symbolic link to a folder on a remote nfs share and a "Scripts" menu option does not show up.  When I delete the link and paste the scripts that were in the nfs folder to my local /home/USER/.local/share/nautilus/scripts folder, the "Scripts" menu option shows up.  I'm on 14.04 if it matters.  Ideas?

---

### Post by TheFu on 2015-06-19
GUI or shell?  Did you type **ln -s**

Does the NFS mount allow exec or is it noexec in the export options?

Is it really NFS or could it be sshfs?

---

### Post by agibby5 on 2015-06-19
> **TheFu said:**
> GUI or shell?  Did you type **ln -s**

Does the NFS mount allow exec or is it noexec in the export options?

Is it really NFS or could it be sshfs?

GUI.  Yes, it's a symbolic link.

I didn't think to check the mount options.  They are: user,rw,hard,intr.  When I add exec to the end, it does't appear to actually care that I put it there... as mtab still shows noexec.

100% sure it's NFS.

---

### Post by TheFu on 2015-06-19
What is the NFS server and file system on it?

Can you please post the full permissions (ls -al) for the link source and target?  We can assume no ACLs for now.

The noexec option is server-side. Don't know that it matters, but ... 

I've **NEVER** in my life used a GUI to make any links, sorry. Don't know if there are any differences in doing it that way.

---

### Post by agibby5 on 2015-06-19
It works with hard,intr,exec but not with user,hard,intr,exec

---

