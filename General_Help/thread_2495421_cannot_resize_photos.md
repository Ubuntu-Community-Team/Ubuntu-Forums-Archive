---
title: "cannot resize photos"
date: 2024-02-18
forum: General Help
---

### Post by pjstock on 2024-02-18
I once had a very handy feature where I could RightClick on a photo and in the dropdown options I had Resize Images and Rotate Images.
on a reinstall I lost these But found these tips on how to reinstall them with Nautilus.
[https://itsfoss.com/resize-images-with-right-click/](https://itsfoss.com/resize-images-with-right-click/)

following the instructions I seem to have the Resize and Rotate options back But
I am getting an error: "FILENAME cannot be resized. check whether you have permissions to write to this folder” 
Can anyone advise me as to how I would correct this?

Peter

---

### Post by TheFu on 2024-02-19
Did you check that your permissions allow writing to the output directory?  Like the error shows?

---

### Post by pjstock on 2024-02-19
These are hadrdrives I have been reading and writing to for years.

this is what I see when I do: ls -l

peter@peter-OptiPlex-990:~$ ls -l
total 36
drwxr-xr-x 2 peter peter 4096 Oct  3 16:33 Desktop
drwxr-xr-x 3 peter peter 4096 Jan  1 13:11 Documents
drwxr-xr-x 2 peter peter 4096 Feb 19 12:33 Downloads
drwxr-xr-x 2 peter peter 4096 Dec 13  2020 Music
drwxr-xr-x 5 peter peter 4096 Feb 18 11:04 Pictures
drwxr-xr-x 2 peter peter 4096 Dec 13  2020 Public
drwx------ 8 peter peter 4096 Dec 30 19:20 snap
drwxr-xr-x 2 peter peter 4096 Dec 13  2020 Templates
drwxr-xr-x 2 peter peter 4096 Dec 13  2020 Videos
peter@peter-OptiPlex-990:~$ 


and when I cd over to try to see my big external HDD (the Seagate) I see:

peter@peter-OptiPlex-990:/media/peter$ ls -l
total 48
drwxr-xr-x 4 root  root   4096 Nov 22  2018  427bb13e-0609-4207-9628-10860c5d6586
drwxrwxrwx 1 peter peter 12288 Oct 18  2021  9664092D640911A3
drwxr-xr-x 3 peter peter  8192 Dec 31  1969  E115-004D
drwxrwxrwx 1 peter peter 24576 Oct 16 22:36 'Seagate Expansion Drive'
peter@peter-OptiPlex-990:/media/peter$ 

which seems to be showing me full permissions doesn't it?

---

### Post by TheFu on 2024-02-19
>  which seems to be showing me full permissions doesn't it? 
I can't tell. What are the permissions on the /media/peter/ directory? Those shouldn't be an issue, but I never know that gvfs or gio is going to do.

Sometimes programs use a temporary directory. If your account cannot write to that temporary location, where ever it is, that could prevent it.

If any of the programs involved are **snaps**, 
a) they have to allow removable media to be written - this is controlled by the snap packager, not you. Not me. Not any admin on the system.
b) each snap that allows that "connection" needs to be told to allow it, specifically.  For chromium, 
```
$ snap connect chromium:removable-media
```

So you'll need to figure out which snap is getting in your way, if any.

If they aren't snap programs/packages, I haven't any clue.


Those permissions are quite scary.  750 is typical for data to be used by 1 person.  If you didn't format the drive to be a native Linux file system, only mount options can control the owner and permissions.  This is typically done through the /etc/fstab.

For troubleshooting, I always 
a) check the system logs for warnings and errors.
b) run the program(s) involved from a terminal to see if there are other errors output to stderr or stdout that are hidden by GUI use.

---

