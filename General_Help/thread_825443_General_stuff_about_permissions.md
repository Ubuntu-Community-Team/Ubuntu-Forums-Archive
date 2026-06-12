---
title: "General stuff about permissions"
date: 2008-06-11
forum: General Help
---

### Post by theedudenator on 2008-06-11
Where should I look to understand the permissions and how to change them.

I am logged in as my standard user name and I can open and edit a file, but cannot save it because I am not the owner.

Can I change my profile to be an administrator and do what I want?

---

### Post by dudude on 2008-06-11
The command to change the permissions to a file is chmod.

There is a lot of information about it in its man page.

The command to change the owner is chown. This will remove the ownership errors.

To see what the current permissions are on a file you can right click on it in Nautilus and go to properties, and to see it in the terminal you can use ls -l

You can also switch to root, or, in Ubuntu, use sudo to get root-level privileges to do anything to any file.

---

### Post by theedudenator on 2008-06-11
But the commands need to be in the terminal window.

The file I want to change is owned by root.
So I have the directory with the file open on the desktop.

So then I need to open a terminal window, go to the directory to change the permission.

This seems like a lot of steps to save a file??

---

### Post by barboachtraner on 2008-06-11
You can run a GUI application with root privileges by prefacing the command with gksu (or kdesu if you're using Kubuntu). For example, if you wanted to edit a text file owned by root you could type gksu gedit in a terminal. Changing file permissions like you were trying to do probably isn't the best idea.

---

### Post by Xiong Chiamiov on 2008-06-11
Just to reiterate, to open a graphical application as root, preface it with gksudo:
```

gksudo gedit [file]

```
or
```

gksudo nautilus

```
For terminal applications, use sudo.

[Here]("http://ubuntuforums.org/showthread.php?t=425260") is an excellent post on permissions.

---

