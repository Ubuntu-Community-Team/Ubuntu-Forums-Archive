---
title: "Mounted Drive Permission"
date: 2007-02-21
forum: General Help
---

### Post by ClayPTino on 2007-02-21
I have a usb hard drive that I am mounting in order to access it through a proftpd server.

The only way I can mount the drive to where there is any sort of write access is to use the umask=020 option.  However, I want to be able restrict the folders that are write enabled on the drive.

It appears chmod doesn't work on mounted volumes, so I'm kind of stuck as to how to limit write access to only certain folders, as the umask route enables write access on every folder.

Thanks

---

### Post by bettlebrox on 2007-02-21
You can specify what UID or GID the drive is mounted as. 

Is this a FAT32 filesystem? If it is, it doesn't support permissions & ownerships the same way as native Linux filesystems do (such as ext3), which is why chmod won't work.

---

### Post by ClayPTino on 2007-02-21
It is a FAT32 system, so I guess that explains it.

I'm not sure I know what you mean about the GID and UID settings though.  I think I'm going to need somewhat of a primer.

Thanks again.

---

### Post by bettlebrox on 2007-03-05
Every user has a UID: User ID, and a GID: Group ID.

See here for info on how to mount Windows formatted partitions:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

---

