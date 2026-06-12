---
title: "un-deletable files in my Trash"
date: 2008-05-07
forum: General Help
---

### Post by | MM | on 2008-05-07
Hi,

Somehow i have a folder with sub-folder and sub-files in my .Trash that seem to have root privileges.  Therefore, i cannot delete them ('Empty Trash') the simple way.  I don't know how they got root privileges because they were deleted from my home directory. :confused:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=69071&stc=1&d=1210135623[/IMG]

Anyways, I've tried to hunt down where the files are living atm so i could delete them whilst with elevated privileges, but i cannot find the right .Trash folder.

```
cd trash:///
```
doesn't work, and I've tried 
```
sudo nautilus trash:///
```

but that just takes you to the root Trash.

I've also tried
```
sudo nautilus /home/.Trash-0
```
similarly to no avail!

So which location would my user (matthew) have the Trash stored??

---

### Post by Barriehie on 2008-05-07
Have you tried /home/matthew/.Trash ?  If you open your home folder in Nautilus then ctrl-h will toggle the hidden files on/off.

Barrie

---

### Post by azredwing on 2008-05-07
I've got the exact same issue. Can't take out the trash (heh).

```
***@notebook:~> $ cd /home/***/.Trash
bash: cd: /home/****/.Trash: No such file or directory

```

Now what?

---

### Post by Xgen on 2008-05-07
Try it's new location: ~/.local/share/Trash as root.

---

### Post by peacewithall on 2008-05-07
Just to add, I had this problem too, today, and followed above and it deleted the 'undeleteable'. Seems like a bug to me, as we have all had this problem within the same timeframe.

I did have my first set of updates from Hardy, and wonder if one of those introduced the bug?.

---

### Post by _sAm_ on 2008-05-07
I have the same, a file in trash that I cant delete. I get the same "No such file or directory", in Ubuntu 8.04

---

### Post by perlluver on 2008-05-07
The full path is ./local/share/Trash/files look at the hidden folders in your home directory, that is where you can find ./local/.

---

### Post by wdaniels on 2008-05-07
> **Xgen said:**
> Try it's new location: ~/.local/share/Trash as root.

If the location has changed then do you think it could be that some upgrade process (running as root) moved some existing trash to the new location by some clumsy means that caused it to be owned by root?  Just a thought...

---

### Post by | MM | on 2008-05-07
Choice you fella's solved my problem!  I can sleep easy again.  :KS

---

### Post by Jive Turkey on 2008-05-21
I think in my case the undeletable files came from running "sudo make install" in the folder before sending it to the trash.  I think it would make more sense and be easier for users to deal with if the permissions prevented me from sending it to the trash, rather than deleting it from the trash.

---

### Post by ykcirt on 2008-08-30
I have the same problem with a directory I deleted (an extracted Baldur's Gate modification), but I'm wondering if there isn't just a simple terminal command I can sudo? Sudo take out the trash?

---

