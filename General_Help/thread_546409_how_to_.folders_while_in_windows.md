---
title: "how to .folders while in windows?"
date: 2007-09-08
forum: General Help
---

### Post by bone2006 on 2007-09-08
In the past I had two EXT3 partitions (1 root and 1 home), and two NTFS (OS, backup).

Since I'm not using windows NTFS that often, I got rid of the NTFS partition and now I have just 3 partitions.

I'm sharing home partition with windows via [http://www.fs-driver.org](http://www.fs-driver.org)

Everything is working great, the only problem is that there are too many hidden folders and files that  make it a mess when I'm navigating.

I've been trying to search on a way to hide folders and files that start with a dot in windows and I've only see some commands for individual folders or files.

I'd like everything that's in my home/username partition that begins with a dot to be hidden for a little organization. 

Any help is appreicated

---

### Post by Jose Catre-Vandis on 2007-09-08
I'll second a need for a fix for this, when using shared folders in virtualbox (on Windows guest), the same thing happens. I know you can hide dot files with samba and apache, but there doesn't seem to be a way to hide them from within Windows?

---

### Post by merlinus on 2007-09-08
IIRC, there should be an option in windows explorer whether or not to show hidden and system files.

Maybe that will work.....

-merlin

---

### Post by bone2006 on 2007-09-09
windows doesn't recognize the dot infront of anything as being hidden. By default everything is hidden, but even going into explorer settings and show hidden or hide hidden files and folders doesn't change anything for the folders/files with a dot infront of them.

---

### Post by SPr on 2007-09-09
From a command prompt try
```

attrib +h .*

```

I seem to think attrib uses wild cards otherwise a batch file would be the answer. I don't know what the consequences of this would be for Linux though. Where does Windows store the file attributes?

---

### Post by vexorian on 2007-09-09
> **Jose Catre-Vandis said:**
> I'll second a need for a fix for this, when using shared folders in virtualbox (on Windows guest), the same thing happens. I know you can hide dot files with samba and apache, but there doesn't seem to be a way to hide them from within Windows?
I only share a minimal subfolder in with the windows guest, if I ever need to hand access to another folder to the virtual machine I create a symlink in the shared folder to the folder I want to share. It works pretty well, then I just remove the symlink , although since I always use the same folders I don't have to do it too much. There isn't a lot of reason to share the whole host hard drive to windows.

I don't think attrib +h would work in ext3 partitions although I am not sure about it.

---

### Post by bone2006 on 2007-09-09
vexorian
Wouldn't the symbolic link need to be created while in linux?  I am sometimes in windows when I'm looking for something, which would force me to reboot create the link then reboot back into windows.  I really like sharing the entire partition, but I can see it depend what you store on your computer.  If I have gigs of pictures, movies, and music for just starters I like to share then.  If anything since I'm really not using windows much, it's not applications that are being shared.  It's data that I like sharing between the two

---

### Post by vexorian on 2007-09-10
> **bone2006 said:**
> vexorian
Wouldn't the symbolic link need to be created while in linux?  I am sometimes in windows when I'm looking for something, which would force me to reboot create the link then reboot back into windows.  I really like sharing the entire partition, but I can see it depend what you store on your computer.  If I have gigs of pictures, movies, and music for just starters I like to share then.  If anything since I'm really not using windows much, it's not applications that are being shared.  It's data that I like sharing between the two
sorry, was being off topic replying to Jose Catre-Vandis regarding virtual machines.


In your case, ext3 does not support attrib's +h attribute but plenty of other system for user permissions, I have no experience with fs-driver, but I would say you'll have to deal with this annoyance, sorry.

But thanks for directing me to that page, I think I might reformat a NTFS big partition as ext3, I am keeping most of my harddrive as NTFS mostly because my brother still uses windows, but would be cool to have big shared space.

---

### Post by bone2006 on 2007-09-10
> But thanks for directing me to that page, I think I might reformat a NTFS big partition as ext3, I am keeping most of my harddrive as NTFS mostly because my brother still uses windows, but would be cool to have big shared space.

I actually found out about it by posting here.  I was using two partitions, which was annoying, then I had a partition in NTFS that I was sharing, but since I use Linux now more than windows I liked keeping it in ext3, which has worked out greatly, would just be nice if I could hide the dot files in windows, since I'm sharing home oh well :)

---

### Post by Jose Catre-Vandis on 2007-09-10
Hiding system files in Windows (under virtualbox shared folders) did work :)
Doesn't hide backup files though ( file~)

---

