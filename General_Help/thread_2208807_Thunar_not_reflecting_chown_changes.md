---
title: "Thunar not reflecting chown changes"
date: 2014-03-02
forum: General Help
---

### Post by sebsanch on 2014-03-02
Hello people
I'm having some problems with file permissions.
I've copied some files from an NTFS flesystem through sftp to ext4 fs.
later I Changed their ownerships and access permissions from root:root to my regular user and group with this command in shell:
 chown -c -R sebsanch:sebsanch /home/sebsanch/Pictures/*

In command line it shows ok. But when I try to access the files with Thunar filemanager or any other GUI filemanager, the files still appear owned by root and unaccessible.

Am I missing something ?
Please advice.

I'm running 13.10

Thanks in advance

---

