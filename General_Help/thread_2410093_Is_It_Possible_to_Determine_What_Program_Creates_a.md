---
title: "Is It Possible to Determine What Program Creates a Directory?"
date: 2019-01-10
forum: General Help
---

### Post by rebeltaz on 2019-01-10
I don't like having to capitalize directory names when working in command line, so I have renamed my Documents, Downloads, Music, Videos and Pictures directories to all lowercase names. For some reason, some program keeps recreating the Downloads directory with a capital D. Normally, I wouldn't care - I'd just forget about the capitalized one. The problem is, though, that when I run a windowsXP VM, it confuses the heck out of the windows OS and nothing works right when trying to read/write from the downloads directory until I remember to delete the capitalized directory. 

Is there any way that I can tell what program keeps recreating this directory so I can tell it to freaking stop!?

---

### Post by pending... on 2019-01-11
As far as I know, from what I've read out there about files, there is no way to check who or what created a file. I assume it's the same thing with directories.

---

### Post by dragonfly41 on 2019-01-11
You might be able to apply [inotify]("http://manpages.ubuntu.com/manpages/bionic/man1/inotifywait.1.html") to watch for changes to a file or directory and associate that detected change with launching some applications.

---

### Post by Holger_Gehrke on 2019-01-11
There should be a file named 'user-dirs.dir' in the hidden directory '~/.config'. The names for standard directories are set in this file and these directories are created during system start-up if they don't exist. Edit that file to contain the names you want the directories to have and the problem should be fixed ...

Holger

---

### Post by CatKiller on 2019-01-11
> **rebeltaz said:**
> Is there any way that I can tell what program keeps recreating this directory so I can tell it to freaking stop!?

In general, no. In this case, it's [xdg-user-dirs](https://www.freedesktop.org/wiki/Software/xdg-user-dirs/) doing exactly what it's supposed to: making sure you have the standard directories and making sure they're called what you've configured them to be called.

It's easy to configure those directories to be called something else. The whole point of the XDG spec is to separate their name from their function, for localisation, and user preference, and the like.

---

### Post by rebeltaz on 2019-01-11
> **Holger_Gehrke said:**
> There should be a file named 'user-dirs.dir' in the hidden directory '~/.config'. The names for standard directories are set in this file and these directories are created during system start-up if they don't exist. Edit that file to contain the names you want the directories to have and the problem should be fixed ...

Holger

> **CatKiller said:**
> In general, no. In this case, it's [xdg-user-dirs](https://www.freedesktop.org/wiki/Software/xdg-user-dirs/) doing exactly what it's supposed to: making sure you have the standard directories and making sure they're called what you've configured them to be called.

It's easy to configure those directories to be called something else. The whole point of the XDG spec is to separate their name from their function, for localisation, and user preference, and the like.

Apparently, and I have long since forgotten, but this must have been how I changed the directory names to begin with. This is the contents of that file:

```

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/downloads"
XDG_TEMPLATES_DIR="$HOME"
XDG_PUBLICSHARE_DIR="$HOME"
XDG_DOCUMENTS_DIR="$HOME/documents"
XDG_MUSIC_DIR="$HOME/music"
XDG_PICTURES_DIR="$HOME/pictures"
XDG_VIDEOS_DIR="$HOME/videos"

```

---

### Post by TheFu on 2019-01-12
I'm just brainstorming, but you could set the permissions to prevent your userid to access the configured directory, then either an alert or log entry would probably contain the program that failed to work.

Unix is case sensitive, BTW.  That's a feature.  Actually, every popular OS is case sensitive except 1, within the limitations of the file system(s) being used.  Different file systems have different limitations.

---

### Post by rebeltaz on 2019-01-13
> **TheFu said:**
> I'm just brainstorming, but you could set the permissions to prevent your userid to access the configured directory, then either an alert or log entry would probably contain the program that failed to work.

Unix is case sensitive, BTW.  That's a feature.  Actually, every popular OS is case sensitive except 1, within the limitations of the file system(s) being used.  Different file systems have different limitations.

How would I go about setting those permissions? 

As far as the capitalization goes, normally, I don't mind - I actually use that to my advantage. It's just this one instance that is giving me fits because I am sharing one directory between two OS's.

---

### Post by TheFu on 2019-01-13
> **rebeltaz said:**
> How would I go about setting those permissions? 
 

```
chmod 000 ~/path/to/directory
```
 
Be certain to keep track of what the permissions were before, so you can put them back.

---

### Post by rebeltaz on 2019-01-13
So I set these permissions on the directory I do **not** want - the one with the capitalized D, right?

---

### Post by HermanAB on 2019-01-14
Hmm, nothing is ever easy.  If the directory already exists then the app will not make it.  If it doesn't exist, then you cannot set a permission or ACL on it.  That seems like a Catch 22.

I think you could craft an App Armor rule to prevent creation of the directory, but don't ask me how.

---

### Post by rebeltaz on 2019-01-30
I would still like to know what is insisting on creating this directory and why, but in the meantime, for those interested, I have come up with a work around. I created renamed my "downloads" directory "Downloads" and then created a symlink to that called "downloads". That way I can access the directory in my preferred lowercase format while the system quits trying to create an uppercase version.

---

