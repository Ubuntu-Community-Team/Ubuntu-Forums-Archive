---
title: "Opening Trash requiring authentication"
date: 2023-06-27
forum: General Help
---

### Post by cscj01 on 2023-06-27
Ubuntu 22.04 x64.  Suddenly, out of nowhere, Ubuntu is requiring authentication to open Trash.  This was not this way until today.  What's going on here?

---

### Post by tea for one on 2023-06-27
Assuming that you have logged in using a user name and password, there should be no difficulty accessing Trash.

Perhaps, try via the terminal:-
```
cd .local/share/Trash
```
Any error messages?

---

### Post by cscj01 on 2023-06-27
> **tea for one said:**
> Assuming that you have logged in using a user name and password, there should be no difficulty accessing Trash.

Perhaps, try via the terminal:-
```
cd .local/share/Trash
```
Any error messages?

No, no messages.  However, I went to ~/.local/share/trash, and I could open the directories.  Then I went to the Trash icon on my desktop, and it opened as before (no authentication required).  I don't know why that would fix it but I'm happy that things are as they were before.

---

### Post by TheFu on 2023-06-28
So, trash is stored per file system. That means that trash directories may be located on different disks, not just in your $HOME.  If there's an external storage device connected and it has a Trash directory and that directory conflicts with your userid, then it is possible for your user NOT to have permissions for access.

Using relative paths in commands often doesn't produce good results.  Try
**cd ~/.local/share/Trash**
instead.  That's just 1 location. Depending on the number of file systems on a system, there may be a few other locations holding trash or hundreds. Hard to know.

---

### Post by MAFoElffen on 2023-06-29
??? Trash on filesystems? Trash (~/.local/share/Trash) is under ~/.local/share/, where where XDG-compliant programs store user data... As such, the contents moved to Trash is from GUI file managers such as nautilus and thunar, using dbus, gio, and GVfs, independent of which filesystem is being used... So is stored by each User. So if multiple users on a machine, may have multiple folders located under /home/$USER/.local/share/Trash. Server Edition and WSL doesn't have this by default, because there is no GUI.

On filesystems? Are you talking about lost+found for EXT filesystems? That is the obsolete data from fsck... Right?

---

### Post by TheFu on 2023-06-29
> **MAFoElffen said:**
> ??? Trash on filesystems? Trash (~/.local/share/Trash) is under ~/.local/share/, where where XDG-compliant programs store user data... As such, the contents moved to Trash is from GUI file managers such as nautilus and thunar, using dbus, gio, and GVfs, independent of which filesystem is being used... So is stored by each User. So if multiple users on a machine, may have multiple folders located under /home/$USER/.local/share/Trash. Server Edition and WSL doesn't have this by default, because there is no GUI.

On filesystems? Are you talking about lost+found for EXT filesystems? That is the obsolete data from fsck... Right?

Say you mount a file system to /d/D6 ... er ... like I do. If you use a GUI file manager with "trash enabled", and delete files using it, they get placed into the /d/D3/.Trash/{uid} subdirectory.  This is because it would be inefficient to copy the file(s) across file systems, so for each mounted file system that a user can delete files, if they are allowed to create a /{mount point}/.Trash/ directory, then one will show up.  It is similar to the lost+found/ directory that each file system has.  

It became enough of a problem for me that I added trash clean up tasks to my "pre-backup" script.
```
    function EmptyTrash(){
      LogItDebug
        if [[ -x /usr/bin/gio ]] ; then
           echo "INFO: Empty GIO trash"
           /usr/bin/gio trash --empty
        fi
      LogItDebug
    }
```

Of course, if the mount point is owned by root and permissions don't allow the end-users of the system to have the .Trash at that level, none can be created.  Perhaps this is file manager-specific?  IDK.

---

### Post by cscj01 on 2023-07-01
First off, I am speaking of a single user system.  From what I can tell, there is a directory labeled Trash-1000 created on each file system and/or partition once a write to that file system is applied.  The one in ~/.local/share seems to be the one that is available on the Desktop.  There are other trash directories that are specific to aplications such as those for evolution.  These do not contain the items "trashed" by the user.  So I do not know nor have I been able to determine why the Trash icon on the Desktop wanted authentication.  I suppose what removed that requirement was the fact that I opened the Trash directory in ~/.local/share, but I cannot confirm that.

Umless anyone feels I should keep this open, I will mark this as solved in a few days.

BTW, thank you to all who responded.

---

### Post by TheFu on 2023-07-01
Linux isn't a single user system regardless of how you use it.  It is multi-user from the start and all aspects of the OS work in a multi-user way.  That is worth always remembering.  Always.

---

### Post by cscj01 on 2023-07-01
> **TheFu said:**
> Linux isn't a single user system regardless of how you use it.  It is multi-user from the start and all aspects of the OS work in a multi-user way.  That is worth always remembering.  Always.

Of course you are correect.  I just wanted to establish that I was the only person who uses this system.  I chose a poor way of expressing that.  Thanks for your observation.

---

