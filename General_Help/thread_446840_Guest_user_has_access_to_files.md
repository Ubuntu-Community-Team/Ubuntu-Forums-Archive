---
title: "Guest user has access to files"
date: 2007-05-17
forum: General Help
---

### Post by Klarsin on 2007-05-17
I've set up a "guest user" on my computer that I don't want to see any of "my user" documents but where they still have the ability to use CD drive, internet access and printer. Basically I want them to be able to use all my program applications but not view any of my user documents and settings. After setting up the guest user I've found they can read and write to all my files except without admin privilages. How do I block this one user yet still communicate across my network drives with others.

Using Dapper

---

### Post by fanatik on 2007-05-17
you need to remove "world" permissions from your files!

chmod o-rwx file

---

### Post by Klarsin on 2007-05-17
> **fanatik said:**
> you need to remove "world" permissions from your files!

chmod o-rwx file

How is this accomplished? Like what's the procedure?

---

### Post by Delkster on 2007-05-17
> **Klarsin said:**
> How is this accomplished? Like what's the procedure?

If you remove the "execute" (or, in case of directories, traversal) permission for your home directory from the "other" users, they won't be able to read anything that is within that directory. If you also take away the read permission, they won't be able to get a listing of files in the home directory, thus hiding the contents of your home directory completely from everyone except you (and users in your default group, which is probably just you, and of course users with admin privileges who can read anything).

Edit:
I assume that you use Ubuntu with the Gnome desktop. The same results can be obtained in KDE but probably in a slightly different way.


In the file browser, find your way to /home (note: that's not your own home folder but the parent folder of it -- that is, the folder that *contains* all user home folders, including yours) and open the properties of your home folder (for example, right-click on it and select "Properties"). Find the "Permissions" tab. In the "Others" section (as in users other than the owner of the folder, which is you) set both folder access and file access to "None".

Alternative way: Open a terminal (Applications > Accessories > Terminal) and issue the following command:
```
chmod o-rwx .
```

---

### Post by Klarsin on 2007-05-17
> **Delkster said:**
> If you remove the "execute" (or, in case of directories, traversal) permission for your home directory from the "other" users, they won't be able to read anything that is within that directory. If you also take away the read permission, they won't be able to get a listing of files in the home directory, thus hiding the contents of your home directory completely from everyone except you (and users in your default group, which is probably just you, and of course users with admin privileges who can read anything).

Edit:
I assume that you use Ubuntu with the Gnome desktop. The same results can be obtained in KDE but probably in a slightly different way.


In the file browser, find your way to /home (note: that's not your own home folder but the parent folder of it -- that is, the folder that *contains* all user home folders, including yours) and open the properties of your home folder (for example, right-click on it and select "Properties"). Find the "Permissions" tab. In the "Others" section (as in users other than the owner of the folder, which is you) set both folder access and file access to "None".

Alternative way: Open a terminal (Applications > Accessories > Terminal) and issue the following command:
```
chmod o-rwx .
```


me@:~$ chmod o-rwx
chmod: missing operand after `o-rwx'
Try `chmod --help' for more information.

This command didn't work. I also tried from the file browser, but your instructions arn't exactly what I see. did you mean right click on my folder and share folder then don't share ( but this would mean don't share with anyone). I just want to block one user.

---

### Post by Klarsin on 2007-05-17
> **Klarsin said:**
> me@:~$ chmod o-rwx
chmod: missing operand after `o-rwx'
Try `chmod --help' for more information.

This command didn't work. I also tried from the file browser, but your instructions arn't exactly what I see. did you mean right click on my folder and share folder then don't share ( but this would mean don't share with anyone). I just want to block one user.

OK, to add to this - I found the instructions were for edgy and not dapper, but went ahead and unchecked rwx for others. But this blocks all others, and not just one user. Is there a way to block just one specific user while keeping all others open?

---

### Post by Delkster on 2007-05-18
> **Klarsin said:**
> me@:~$ chmod o-rwx
chmod: missing operand after `o-rwx'
Try `chmod --help' for more information.

The command is literally as I wrote it within the code box, including the trailing period after the space.

> I also tried from the file browser, but your instructions arn't exactly what I see. did you mean right click on my folder and share folder then don't share ( but this would mean don't share with anyone). I just want to block one user.

I suggest you try again with the text command because it's easier to write (and follow) than writing relatively complex instructions for finding certain things in the GUI.

However, just for the record, sharing refers to offering folders to other computers for reading and/or writing over the network. It's different than changing the access permissions within your own computer, which is what you want. In Gnome you should be able to find a "Properties" entry in the menu when you right-click on a file or folder, and within Properties there's a "Permissions" tab. If you use something other than Gnome (which ships with Ubuntu by default) it may be a little different.

---

### Post by fanatik on 2007-05-18
> **Klarsin said:**
> I just want to block one user.

so you want 1 user to be blocked and any other user to be able to read/write all your files?

ok. it's not great security wise, but it's your call.

so you would need to create a group called noaccess, add this one user to the noaccess group, then change the group owner of all your files to noaccess, remove all permissions for the group noaccess on all your files, then allow permissions for everyone else on your files.

You can do this via the gui, or use:

```
$ sudo groupadd noaccess
$ sudo usermod -a noaccess <user>
$ chgrp -R noaccess *
$ chmod -R g-rwx *
$ chmod -R o+rwx *

```

---

### Post by Klarsin on 2007-05-18
> **Delkster said:**
> The command is literally as I wrote it within the code box, including the trailing period after the space.



I suggest you try again with the text command because it's easier to write (and follow) than writing relatively complex instructions for finding certain things in the GUI.

However, just for the record, sharing refers to offering folders to other computers for reading and/or writing over the network. It's different than changing the access permissions within your own computer, which is what you want. In Gnome you should be able to find a "Properties" entry in the menu when you right-click on a file or folder, and within Properties there's a "Permissions" tab. If you use something other than Gnome (which ships with Ubuntu by default) it may be a little different.

Aaah! The trailing period looked suspicious so I cut and pasted without it. I  have set up the others rwx as no access. So all is OK for this computer now.

---

### Post by Klarsin on 2007-05-18
> **fanatik said:**
> so you want 1 user to be blocked and any other user to be able to read/write all your files?

ok. it's not great security wise, but it's your call.

so you would need to create a group called noaccess, add this one user to the noaccess group, then change the group owner of all your files to noaccess, remove all permissions for the group noaccess on all your files, then allow permissions for everyone else on your files.

You can do this via the gui, or use:



I'll have to rethink the security issue. It would seem convenient at times to be able to single out specific users from accessing my files. But is this something that is uncommon, or considered a no-no?

---

