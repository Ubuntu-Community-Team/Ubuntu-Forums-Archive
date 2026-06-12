---
title: "Question about root"
date: 2006-10-27
forum: General Help
---

### Post by rhuarch on 2006-10-27
How can I change the permissions on a folder that is owned by root?  I mounted 2 extra hard drives on my linux pc and want to share out those drives via samba to my windows PCs.  With that in mind I just shared out the folders that the drives were mounted to but realized quickly I couldn't write to those drives either from my windows PCs or my linux PC because they are owned by root, and the permissions are set by default so that only root can write to them or change the permissions.  This is frustrating because I am very new to linux and don't really know what I am doing.  If I can't do it through the GUI I am pretty much lost (trying to break the windows addiction).  I hope someone can help me out with this.  I would like to either change the owner to myself, or failing that somehow access thos folders as root and change the permissions, but I don't really know how to do either.  Thanks in advance.

---

### Post by jd65pl on 2006-10-27
You could use a command "chown" [wikipedia]("http://en.wikipedia.org/wiki/Chown") explains it quite well, it could also give you some practice in using the terminal

---

### Post by aysiu on 2006-10-27
I don't know much about Samba, but if the drives appear to be "owned" by root, how you proceed probably depends a lot on whether those drives are FAT32/NTFS or Ext3. What filesystem are they?

---

