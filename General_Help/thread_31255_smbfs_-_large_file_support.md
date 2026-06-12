---
title: "smbfs - large file support?"
date: 2005-05-02
forum: General Help
---

### Post by qbase on 2005-05-02
I'm having problems unpacking a DVD to my file server, unrar says "File size limit exceeded". Google tells me that smbfs has problems with large files, over two gigabyte. [Large File Support in Linux](http://www.suse.de/~aj/linux_lfs.html) 

Is this true and is there a work around for this? Server runs Ubuntu and my desktop Kubuntu, the share is mounted with: mount -t smbfs -o username=kebab,password,uid=kebab,gid=kebab,fmask=700,dmask=700 //bola/files /media/files

Samba is needed by my xbox and when I'm running Windows :rolleyes:

---

### Post by shakin on 2005-05-02
What is the destination filesystem? A FAT or FAT32 filesystem would not be able to take a file larger than 2GB.

Try mounting the share with the lfs option to enable large files.

eg.

mount -t smbfs -o lfs //server/share /media/sharename

---

### Post by qbase on 2005-05-02
The lfs option did the trick! Thank you shakin! :D

---

