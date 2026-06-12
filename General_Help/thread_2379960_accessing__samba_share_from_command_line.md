---
title: "accessing  samba share from command line"
date: 2017-12-11
forum: General Help
---

### Post by RobertoRecordo on 2017-12-11
I can access my NAS from the command line:
```
me@dell-t1500:~$ ls /run/user/1000/gvfs/smb-share:server=hmnhd-tic587,share=documents
```

but on the occasions that i want to do so, I spend time reconstructing and testing that path. I don't understand the syntax, it is ugly and frankly, confusing.

The folders on the share are not mounted (although they appear in the file manager), and I can not locate a .gvfs folder.

Am I missing something? Is there a simple alias for the share drive that I do not know about?

I am on a Dell T1500 running Ubuntu Gnome 15.10, I will upgrade to 16.04.3 as soon as I can tar my files to the share drive.

-Rob

---

### Post by HermanAB on 2017-12-11
Use smbclient to learn how it really works, then make a shortcut.

---

### Post by RobertoRecordo on 2017-12-13
> **HermanAB said:**
> Use smbclient to learn how it really works, then make a shortcut.

Herman, thanks for the suggestion, but do I really need to install smbclient to make a shortcut? I had asked
> 
Am I missing something? Is there a simple alias for the share drive that I do not know about?

If you can, please tell me what a shortcut will look like, and why or how smbclient will make that simpler.

I looked at the shared drive designator in the file manager, it appears as smb://hmnhd-tic587/documents/

```
~$ ls smb://hmnhd-tic587/documents/
ls: cannot access smb://hmnhd-tic587/documents/: No such file or directory
``` 
apparently smb://hmnhd-tic587/documents/ is not valid on the command line

Regards 
 -Rob

---

