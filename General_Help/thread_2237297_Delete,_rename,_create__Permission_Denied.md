---
title: "Delete, rename, create : Permission Denied"
date: 2014-08-01
forum: General Help
---

### Post by andy69 on 2014-08-01
Hey guys,

The problem is, i tried to install Vmware workstation, i had the .bundle on desktop and tried the following comands

```
chmod -x ./vmware....bundle

```

then there was an error that said Permission denied.

i tried restarting the computer and now there are files on my desktop that i can not delete, because apperantly i dont have permission, i can not create a folder on the desktop because i dont have permission, and i cant rename.
this is all on the desktop, even when trying to navigate to the desktop in terminal, it gives me a permission denied,

but when trying to navigate to other folders and not desktop, it works fine.

Anyone have any ideas of why this is happening ??

Thanks

---

### Post by mooreted on 2014-08-01
The command would have been chmod +x to make it executable.

From your home folder try:

chmod -R ugo+rw Desktop

---

### Post by mooreted on 2014-08-01
If your vmware bundle was downloaded to your Downloads folder you would run this from your home folder:

cd Downloads
chmod +x vmware.bundle (or whatever the name is)
sudo sh vmware.bundle (using the correct name)

---

### Post by andy69 on 2014-08-01
```
user@user:~$ chmod -R ugo+rw Desktop
chmod: cannot access ‘Desktop/eclipse.desktop~’: Permission denied
chmod: cannot access ‘Desktop/vmware-workstation-full-10.0.2-1744117.x86_64.bundle’: Permission denied
chmod: cannot access ‘Desktop/Untitled Document 2~’: Permission denied
chmod: cannot access ‘Desktop/Untitled Document~’: Permission denied
chmod: cannot access ‘Desktop/Untitled Document 3~’: Permission denied
chmod: cannot access ‘Desktop/e-wl1001’: Permission denied


```

this is what happends

i went to my desktop folder and changed the access to create and delte files, on all 3 tabs,
for some reason it was on can not create and delete files..

thank you for your help

---

### Post by UltimateCat on 2014-08-01
Permissions can drive one crazy in some cases-

[http://www.linuxcommand.org/lts0070.php](http://www.linuxcommand.org/lts0070.php)

[http://www.linuxclues.com/articles/16.htm](http://www.linuxclues.com/articles/16.htm)

---

### Post by mooreted on 2014-08-01
That sort of thing can happen if ownership changes too. You have to be careful about who owns what.

If it's working now, please mark the thread as solved as it may help others with similar problems.

---

