---
title: "sudo rm -rf Fails to Remove Files on External HD"
date: 2017-02-08
forum: General Help
---

### Post by webmanoffesto on 2017-02-08
I'm trying to free up space on an external HD. I suspect that in the past files on there were deleted but the "trash wasn't emptied".
Now I get error messages (below). 
I have many GBs tied up in "not emptied trash". Please help me resolve this problem.

```
tom@TomsAsusK55A:/media/Seagate Backup Plus Drive$ sudo rm -rf .Trash-1000/
[sudo] password for tom: 
rm: cannot remove `.Trash-1000/expunged/1297937391/Bezeq.Netgear.Modem.v01.docx': Is a directory
rm: cannot remove `.Trash-1000/expunged/1297937391/Netgear.DGN2200.FAQ.v01.docx': Is a directory
rm: cannot remove `.Trash-1000/expunged/1297937391/~$zeq.Netgear.Modem.v01.docx': Is a directory
rm: cannot remove `.Trash-1000/expunged/1297937391/~WRL3197.tmp': Input/output error
rm: cannot remove `.Trash-1000/files/Anglit.Mipooee/J.wma': Input/output error
rm: cannot remove `.Trash-1000/files/Anglit.Mipooee/K.wma': Input/output error
rm: cannot remove `.Trash-1000/files/Anglit.Mipooee/L.wma': Input/output error
rm: cannot remove `.Trash-1000/files/Anglit.Mipooee/M.wma': Input/output error
rm: cannot remove `.Trash-1000/files/Anglit.Mipooee/N.wma': Input/output er
```ror

```
tom@TomsAsusK55A:/media/Seagate Backup Plus Drive/.Trash-1000/files$ chmod -R 777 /media/Seagate\ Backup\ Plus\ Drive/.Trash-1000
chmod: cannot access `/media/Seagate Backup Plus Drive/.Trash-1000/expunged/1297937391/~WRL3197.tmp': Input/output error
chmod: cannot access `/media/Seagate Backup Plus Drive/.Trash-1000/files/Anglit.Mipooee/&#1513;&#1497;14.wma': No such file or directory
chmod: cannot access `/media/Seagate Backup Plus Drive/.Trash-1000/files/Anglit.Mipooee/&#1513;&#1497;15.wma': No such file or directory
chmod: cannot access `/media/Seagate Backup Plus Drive/.Trash-1000/files/Anglit.Mipooee/&#1513;&#1497;16  &#1491;&#1497;6.wma': No such file or directory
```

---

### Post by wildmanne39 on 2017-02-08
The input/output error means there is a problem with the drive and it is most likely failing, I will leave the rest of it to someone else.

---

### Post by #&amp;thj^% on 2017-02-08
Have you yet looked at /home/<user_name>/.local/share/Trash
sudo rm -rf .local/share/Trash/files/*



You can use this command as root:

 ```
rm -rf ~/.local/share/Trash/*
```
_**Be careful how you use the rm command because any misuse may cause deleting sensitive system folders and files **._
The rm command removes (delete) files or directories.

-f, --force     Ignore nonexistant files, and never prompt before removing.
-r, -R, --recursive     Remove directories and their contents recursively.

The trash folder is found at: $HOME/.local/share/Trash

Or you can also use something like this:
With trash-cli installed, you can do

```
trash-empty
```

more interesting details about trash handling: Here:
[http://manpages.ubuntu.com/manpages/precise/man1/trash-empty.1.html](http://manpages.ubuntu.com/manpages/precise/man1/trash-empty.1.html)

```
DESCRIPTION

       Remove  for  ever any trashed file and trashed directory.  This command
       is a part of trash-cli package that provides a command  line  interface
       trashcan    utility    compliant   with   the   FreeDesktop.org   Trash
       Specification.  It remembers the name, original  path,  deletion  date,
       and permissions of each trashed file.

ARGUMENTS

       To remove all trashed files, use 'emtpy-trash'.

       To remove files that have been in the trash more than a given number of
              days, use 'trash-empty x', 'x' representing the number of days.

EXAMPLES

       $ date
       Tue Feb 19 20:26:52 CET 2008
       $ trash-list
       2008-02-19 20:11:34 /home/einar/today
       2008-02-18 20:11:34 /home/einar/yesterday
       2008-02-10 20:11:34 /home/einar/last_week
       $ trash-empty 7
       $ trash-list
       2008-02-19 20:11:34 /home/einar/today
       2008-02-18 20:11:34 /home/einar/yesterday
       $ trash-empty 1
       $ trash-list
       2008-02-19 20:11:34 /home/einar/today
       $ trash-empty
       $ trash-list
       <none>

```
Hope this helpful.

---

### Post by webmanoffesto on 2017-02-08
This seems to have solved the problem

sudo chown $USER:$USER /media/Seagate\ Backup\ Plus\ Drive/.Trash-1000

---

### Post by #&amp;thj^% on 2017-02-08
> **webmanoffesto said:**
> This seems to have solved the problem

sudo chown $USER:$USER /media/Seagate\ Backup\ Plus\ Drive/.Trash-1000

Good to hear this...I was wondering about the permissions on that drive.;)
If it is Solved then... to your liking...Please Mark as Solved as to help others.
Kind Regards

---

