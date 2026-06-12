---
title: "Simultaneous file system access with Gutsy and Windows running within a VMWare"
date: 2008-03-17
forum: General Help
---

### Post by kmatthews812 on 2008-03-17
Hi,

I recently switch to Ubunty Gutsy after I got sick of Windows being horrible.  However, I still rely on some Windows programs (iTunes, Rhapsody, etc), so I installed VMWare and loaded Windows XP SP2 on there.  

Now I am trying to figure out a way to allow XP running in VMWare to be able to access a few filesystems that contain various files.  Is there any way to do this without using a network share (Samba, NFS, etc)?  If I do this using Samba, won't it operate very slowly?  

Originally, the fileystem I was trying to access was NTFS.  But I switched it to ext3 since, with NTFS, I could not export an NTFS fileystem with NFS.  Switching to ext3 allowed NFS to work without any problems.  

Then, I installed the ext3 driver in Windows XP running in VMWare, but it refused to access my ext3 filesystem since it was already mounted.  When I unmounted the ext3 filesystem, Windows XP could access it just fine.  But I need both Ubuntu(host) and XP(VMWare) to be able to access the filesystem simultaneously.  

So does anybody have the magic bullet for me?  This can't be that tough.  


Thanks,

Kev

---

### Post by raevin on 2008-03-17
> **kmatthews812 said:**
> Hi,

I recently switch to Ubunty Gutsy after I got sick of Windows being horrible.  However, I still rely on some Windows programs (iTunes, Rhapsody, etc), so I installed VMWare and loaded Windows XP SP2 on there.  

Now I am trying to figure out a way to allow XP running in VMWare to be able to access a few filesystems that contain various files.  Is there any way to do this without using a network share (Samba, NFS, etc)?  If I do this using Samba, won't it operate very slowly?  


From what I gather...you have a Windows XP virtual machine on top of an Ubuntu host?  If that's correct, then the only way to really accomplish this is using something like SAMBA...as for the speed being slow, I've been doing it this way for a few months and have not experienced any slowness on either host or guest.

---

