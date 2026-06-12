---
title: "[SOLVED] I cannot copy/cut paste in Ubuntu 8.04"
date: 2008-04-27
forum: General Help
---

### Post by Rytron on 2008-04-27
At present I cannot copy and paste in Ubuntu 8.04. I can however drag and drop. Sometimes I can copy and paste (only sometimes).
Does someone have a solution?
Thanks.

---

### Post by fjgaude on 2008-04-27
Copy and paste text? What's your setup, RAM quanity?

The clipboard uses RAM to temporarily store a copy. Let's hear more.

---

### Post by Rytron on 2008-04-27
Hi.
I refer to copy/cut and pasting files and folders.
Text copy/cut pasting is ok.
My RAM is 2GB.

---

### Post by Endolith on 2008-05-04
I've been having problems with Copy and Paste since upgrading to Heron.  Paste works fine, but Copy doesn't always work, so I'll paste the wrong thing.   It's very annoying and I have no idea what causes it.  I'm getting to the point where I press Ctrl+C repeatedly to make sure it actually copies.

---

### Post by fjgaude on 2008-05-04
> **Rytron said:**
> Hi.
I refer to copy/cut and pasting files and folders.
Text copy/cut pasting is ok.
My RAM is 2GB.

You might have to use samba to copy over files and certainly folders. You are moving from NTFS to ext3 and vice versa, eh?

---

### Post by Rytron on 2008-05-05
> **fjgaude said:**
> You might have to use samba to copy over files and certainly folders. You are moving from NTFS to ext3 and vice versa, eh?

Hi,
The folders on my desktop allow copy/cut and paste to the desktop and to other directories, but folders everywhere else do not. The folders on my desktop are of a different colour. I referring to moving files around my pc (Ext3).

I also notice that under properties > permissions; there is no folder access option for folders bar the folders on my desktop.

---

### Post by fjgaude on 2008-05-05
> **Rytron said:**
> Hi,
The folders on my desktop allow copy/cut and paste to the desktop and to other directories, but folders everywhere else do not. The folders on my desktop are of a different colour. I referring to moving files around my pc (Ext3).

I also notice that under properties > permissions; there is no folder access option for folders bar the folders on my desktop.

Not sure I understand what your issue is. Sure you can copy/paste within Ubuntu files and folders, but I thought we were talking about going from a WinXP guest and Ubuntu host under vmware server. That's when samba is required to handle the file type conversion.

You can't do that on a normal ext3 desktop, copy/paste files?

---

### Post by Rytron on 2008-05-05
> **fjgaude said:**
> Not sure I understand what your issue is. Sure you can copy/paste within Ubuntu files and folders, but I thought we were talking about going from a WinXP guest and Ubuntu host under vmware server. That's when samba is required to handle the file type conversion.

You can't do that on a normal ext3 desktop, copy/paste files?

Hi,
I never mentioned anything about vmware or windows in this thread!

---

### Post by fjgaude on 2008-05-05
But, but you, we are in the Virtualization Forum... Sorry about that.

---

### Post by Rytron on 2008-05-05
> **fjgaude said:**
> But, but you, we are in the Virtualization Forum... Sorry about that.

:oops:

I am the one to be sorry. Simple mistake to make. Thanks friend.

---

### Post by Rytron on 2008-06-09
I use ```
sudo nautilus
``` to copy/cut/paste when I cant copy/cut/paste via the normal method.

---

### Post by Rytron on 2008-06-10
Hi,
I notice that when I go to Places>Home Folder>Help>About;
it says I am using Thunar file manager(this is for Xcfe and not Gnome!). I use Gnome. However I have Nautilus installed also. I now know why I cannot cut/copy/paste from my Documents folder - Thunar is being used there.
Nautilus is being used on my Desktop.
I have now uninstalled Thunar but the only way I can access my Documents is via terminal: nautilus.

My question is this; how can I make Nautilus as the default file manager for all of my computer?
Thanks.

---

