---
title: "How to take ownership of a folder"
date: 2017-08-26
forum: General Help
---

### Post by offir on 2017-08-26
After I could not fix the computer
[https://ubuntuforums.org/showthread.php?t=2367755]("https://ubuntuforums.org/showthread.php?t=2367755")



I decided to format it and reinstall Ubuntu 16.04
But before that
I wanted to copy all the files I have there

I started the computer from the installation disk in demo mode
And when I went to the folder
I received a message that I do not have permission to access the folder


Right click on the folder and then go to the properties
And I saw that the folder belongs to root

How to take ownership of a folder from root
in Demo mode

---

### Post by forgeuk on 2017-08-26
Not sure if it will work in demo mode, but from the terminal you can use the chown command.

sudo chown your-username some-folder
eg.
sudo chown offir /home/offir

adding an -R to the command will do all sub-folders too.

more info on [chown]("http://pubs.opengroup.org/onlinepubs/9699919799/utilities/chown.html").

---

### Post by offir on 2017-08-26
like this
```
sudo chown -R offir /home/offir
```
?
The files do not appear in the folder you specified

The files are on a hard disk in another folder
As if the hard disk was connected to the computer externally

---

### Post by Bashing-om on 2017-08-26
offir; Hello;

There are a number of ways:
> 
to copy all the files I have there


A lot depends on how many files, and the locations of the files .
Might be easiest to copy files from the GUI file manager .
In (u)buntu the file manager is nautilus.
Start the file manager with the elevated authority to execute the needed elevated permissions:
In terminal:
```

sudo -H nautilus

```
Open the manager to the target files to be copied, and then open another window of the manager where the instance is the destination of the files .
Drag and drop the directories and files between the 2 windows.

A huge amount ? WE might want then to consider copying files via the terminal :
mount the target(s) and employ a tool like rsync to copy off the files.

[INDENT][INDENT]many paths to an end
[/INDENT][/INDENT]

---

