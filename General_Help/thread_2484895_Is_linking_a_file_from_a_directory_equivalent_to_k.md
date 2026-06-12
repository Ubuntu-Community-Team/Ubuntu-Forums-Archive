---
title: "Is linking a file from a directory equivalent to keeping it inside that directory"
date: 2023-03-13
forum: General Help
---

### Post by bjngchn on 2023-03-13
Let's say I want to edit a collection of files (image, audio etc) to create one file, using an editor. I would have lots of such collections, and I'm not ready to make editing, at the moment just creating collections. Each collection would be put inside in a separate  directory. So when I have time, or ready for the next step , I choose a collection, and start editing. But since a file would be used in many collections, copying the same file in many directories would occupy too much space. What if  I link files instead of actually putting them there. Will I get the same result?  One possible answer may be: depends on the editor, type of files, version of ubuntu. Another possible answer: just try it.  Better/more useful answer wellcome and appreciated in advance.

---

### Post by Dennis N on 2023-03-13
Functionally, yes in most cases.

When you edit any of the links, your editor changes the target file. You can have many links to the same target file.  A link can have the same name as the target if they are in different directories. If two links are in different directories, they can have the same name. 

A difference is that when you delete a link, you don't delete the target.

---

### Post by MAFoElffen on 2023-03-13
What you are decribing reminds me (both in the Linux and Windows worlds) as Symbolic Links: 
[https://www.redhat.com/sysadmin/soft-links-linux](https://www.redhat.com/sysadmin/soft-links-linux)
[https://learn.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/create-symbolic-links](https://learn.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/create-symbolic-links)

They are the same in both worlds...

---

### Post by TheFu on 2023-03-13
_Symbolic links_ almost always work the same when accessing data in nearly all programs, but there are limitations caused by some programs and some security tools (like snap packages) which will refuse to allow access to linked files that are outside a snap "approved" directories.

Unix people have been using symbolic links for 40+ yrs.  It is a common technique to make accessing the "current" project directory easier ... or a way to have 5 versions of a program installed under 5 different directory trees, but switch between them just by changing a symbolic link as desired.

Wikipedia has a good explanation of symlinks (aka symbolic links) of you want to understand more.  And the **ln** manpage has details about using links (hard and symbolic) on Linux/Unix systems.

---

### Post by bjngchn on 2023-03-14
Thanks never used linking before (except accidentally) before. Just learned how to do it with mouse right-click and it is really called symlink.

---

### Post by TheFu on 2023-03-14
> **bjngchn said:**
> Thanks never used linking before (except accidentally) before. Just learned how to do it with mouse right-click and it is really called symlink.

There are 2 different types of links on Unix file systems.  Hard links and symbolic (sym/soft) links.  Wikipedia has explanations for each. With an understanding of what happens at the file system level, you'll be able to understand the power for each and why hardlinks only work within a single file system.  Also, why symlinks can become orphaned.

---

### Post by Dennis N on 2023-03-14
The man page for the **ln** command has the information you need. I have always used a terminal command to make them. I have only used "soft" links myself. the **-s** option makes these. Links are very useful.

Basic (soft) Link Creation:
```
ln -s <path to target> <link name> 
```

creates the link in the working directory. The command may require sudo depending on the working directory permissions.

---

