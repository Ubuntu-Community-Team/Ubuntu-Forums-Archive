---
title: "Missing mounted hard drive icon"
date: 2007-10-26
forum: General Help
---

### Post by Danyl on 2007-10-26
I've followed this guide: [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

and have successfully mounted my 2nd internal hard drive.

However the only way I know I've been successful is under Places -> Computer -> Filesystem is I can see the mount point I created using the guide (in my case I called this mount point mp3s).  So I can see the folder called mp3s and I can access the files on it...however....

there was a hard drive icon visible (representing my second HD) before I used this guide under Places -> Computer that is no longer there. Why is that? How do I fix that?

Basically I want to be able to drag and drop files to and from this second hard drive/mount point but can't without the icon there.

Any ideas?

---

### Post by mikewhatever on 2007-10-26
Press Alt+F2 and type gconf-editor. Then navigate to apps/nutilus/desktop and check 'volumes visible'. Don't know why the icons went away or if you can drag and drop stuff.

---

