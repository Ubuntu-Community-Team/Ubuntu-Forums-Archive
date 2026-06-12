---
title: "Changing Permissions"
date: 2008-06-29
forum: General Help
---

### Post by WSCCGreg on 2008-06-29
I just did a clean install of Ubuntu 8.04. I made a copy of all my files on a DVD. When I went to copy them to the hard drive they are all locked. Is there a way to copy them so they won't be locked or a quick way to unlock the thousands of folders and files?

Thanks,
Greg

---

### Post by lukjad on 2008-06-29
> **WSCCGreg said:**
> I just did a clean install of Ubuntu 8.04. I made a copy of all my files on a DVD. When I went to copy them to the hard drive they are all locked. Is there a way to copy them so they won't be locked or a quick way to unlock the thousands of folders and files?

Thanks,
Greg

The quick answer is yes. The longer answer is Yes, but...
To access them you go to the terminal and type:
```
gksudo nautilus
```
and drill your way to them. When there right click them and select Properties. Then go to Permissions and then change the owner to you or your to login name. Now, this seems simple but for some reason this change is usually restricted to the actual icons you touch. If you have a folder  withing this folder or any files in that folder, they still are owned by root. I can't help you there except to say that I just go in each folder and change all the permissions. I hope you don't have too many folders. (I do Select all (Ctrl+a) then right click Properties->Permissions. Cuts out a lot of time.)

Hope someone can help you change the files recursively but I don't know enough to tell you how without possibly ruining your copy of Ubuntu. I hear you can really mess up your system if you just add an extra space in the command line.

I'll hunt around an see what I can come up with. Some key phrases to look for it you want to: Recursive file permission changing

These should help:

[HTML]https://help.ubuntu.com/community/FilePermissions[/HTML]

[HTML]http://www.linuxforums.org/forum/linux-security/39405-change-file-permissions-recursively-but-not-affecting-directories.html[/HTML]

[HTML]http://www.dartmouth.edu/~rc/help/faq/permissions.html[/HTML]
_________________
EDIT
Oh yeah, and like cariboo907 says, copy it **off** the DVD then try this.

---

### Post by cariboo on 2008-06-29
You won't be able to change the permissions on the dvd, as the dvd is read only, you would have better luck copying the files as root and then changing permissions and ownership once they are on yuor hard drive. I use mc to accomplish this. MC is available in the repositories and you can use synaptic to install it. Once you have it installed just open a terminal and type:

```
sudo mc
```

You will then be able to copy files to wherever you want. you can use a mouse with mc, but I find using the keyboard to navigate way faster.

Jim

---

