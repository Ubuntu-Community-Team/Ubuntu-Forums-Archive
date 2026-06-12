---
title: "Desktop Permissions/Drag and Drop Default"
date: 2007-05-26
forum: General Help
---

### Post by mooshimi on 2007-05-26
A little while ago I noticed that I couldn't download files from firefox onto the desktop, so i fixed this by fooling with the permissions of ~/Desktop 

That worked great and now I can download straight to the desktop. The problem is that for folders on the desktop, whenever I want to move them around using drag and drop, the default action is to copy the folder to the desktop, so I'll be stuck with two copies whenever I try to do this. I can always hold *shift* down whenever I drag and drop in order to force it to move the folder, but I would like the default action to be just to move the folder. 

Currently my permission settings for ~/Desktop are set to u=rwx,g=rwx,o=rwx

I noticed that whenever I changed the permission settings to o=rw the drag and drop default action changes to *move* rather than *copy*. But then I can't download to the desktop, I can't open folders on the desktop, and I can't even "cd" into the desktop from the terminal. 

I just want to be able to open stuff on the desktop and have the drag and drop default be to move the folders rather than copy them. Any help would be greatly appreciated.

---

### Post by taurus on 2007-05-26
You should be the owner of your own $HOME/Desktop!  What are the output of these two commands from a terminal?

```
id
ls -la ~/Desktop
```

---

### Post by mooshimi on 2007-05-26
Actually it turned out that root was the owner of /home/<user>/Desktop while <user> still owned all the files/folders on the Desktop, which is probably why drag and drop was default to copying. 

I just changed the ownership to <user> using chmod and it fixed my problems. 

Thanks for the help, I don't really know how root ended up owning my Desktop.

---

### Post by shrikant on 2007-06-04
Hello , I too had the problem of Drag and Drop on the desktop ..I ended with copies of folders. The issue was sorted when i changed the owner of Desktop to the current user.

Is this a bug in Feisty ???

---

