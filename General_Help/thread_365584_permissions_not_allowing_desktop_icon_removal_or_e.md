---
title: "permissions not allowing desktop icon removal or emptying of trash"
date: 2007-02-19
forum: General Help
---

### Post by disembodied on 2007-02-19
Hello, I have two main issues:

I set a link to icon on my desktop for my windoze partition - I did this as root (gksudo nautilus etc.) - anyway I can't actually access the partition from that (permission problem) and I just want to remove the link to from my desktop, but the problem is I don't have permission to do that. Now if I attempt to do it as root (gksudo nautilus again) it tells me that its not on the same filesystem [its not, my /home directory is on a different harddrive from the installation, and thus the /root directory]. Is there a way to get around this? perhaps a command to run all from the terminal (I wasn't sure of the 'delete/move to trash' command in the terminal).

Secondly, I removed amarok and tried to delete a tarball of amarok that I downloaded (because apt was installing 1.4.3 instead of 1.4.5) but I am unable to delete the tarball from my trash because I don't have the permissions. I haven't been able to try to do this as root since I don't know (1) the terminal command for deleting or navigating to the trash and (2) how to get to the trash from nautilus if i were to run nautilus as root.

Also, a smaller side issue - I have ubuntu (edgy) on three different computers and all three seem to treat sudo a little differently - one laptop requires me to enter the password EVERYTIME i enter sudo in the terminal (even if I had just entered it one line and less then a minute before), while the other laptop NEVER asks me for the password inside the terminal (but if i run a gui program via the terminal under sudo it asks me for the password, and it asks for it before installing anything via gui) and then a desktop PC will ask for in the terminal once, and if I am running multiple sudo commands it won't ask for it again for awhile, unless I close the terminal and what not.
Is there a way to get all of these to do the same thing (preferably act like the desktop - remember the password for a short duration or until the terminal is closed - but asking for the password everytime is okay too, I just don't like it not asking for the password at all.

Thanks,
Marcus

---

### Post by tribble222 on 2007-02-19
Let's say you want to remove a file located on your desktop and is called "remove-me.txt"  To permanently delete this file as root, you would run in terminal:

```
$ cd ~/    (to change to your home directory)
$ sudo rm Desktop/remove-me.txt     (to permanently delete the file)

```

Your trash is located in your home directory and is called .Trash  (to get there in the terminal you'd run cd ~/.Trash).  You can see it in nautilus if you tell it to show you hidden files (in the view menu).

Be very careful removing files as root.  If you type the file name wrong and accidently tell it to remove the wrong file or directory, it will be very difficult or probably impossible to get it back.

Another solution would be to change the ownership of the file you can't remove.  If your login is disembodied, and you want to own remove-me.txt, you would run:

```

$ cd ~/
$ sudo chown disembodied Desktop/remove-me.txt

```

Edit: As you have found out, creating files or directories as root causes them to be owned by root.  Generally you want to avoid doing things as root if at all possible because it creates these permissions problems.  As for your 3rd question, I have no idea why it is treating your sudo differently.  I believe the default is for it to ask you once and then not ask you again for x minutes (~5 or 10).  You can change this but I don't remember how.

---

### Post by disembodied on 2007-02-20
Thanks for the help, I was able to get that pesky Amarok out of my trash can... but I am not able to remove the icon from my desktop.

First off, getting to nautilus via sudo and altering the permissions (via GUI because the chown didn't work for a reason I'll mention in a second) to make my regular user the owner and what worked to make me the owner with ability to create/delete... and I don't get an error when I attempt to just delete the file off the desktop but it doesn't go away.

Secondly, the reason I couldn't use chown, and the reason in general I think this is being difficult is because the icon is a 'link to' icon linking to my windoze partition. So the title of it is 'link to windoze' (with spaces) which the terminal didn't like when trying to chown.

How do I deal with files with spaces in the terminal?

Thanks

---

### Post by essex on 2007-02-20
I moved a folder into the Trash that I had copied from a Windoze box. I was able to delete most of the files from the Trash but there are still 1200+ files that have Read-Only permission. How can I delete them without having to change file permission on each file. There must be a way to do this for whole directories. :confused:  Thanks

---

### Post by tommcd on 2007-02-20
If the file names have something in common, (like all .jpg or .mp3 files for instance) you could <cd ~/.Trash> the do <sudo rm *.jpg> or <sudo chown essex:users *.jpg> and then empty the trash normally. If the files all have completely unique names and file extensions then you may have to deal with them individually.

---

### Post by tribble222 on 2007-02-20
disembodied:

If a file name has spaces in it, you have to put a \ before each space so that the terminal knows it's still part of the file name.  Or, you can put the name in quotes " ".

Example: to delete the file remove me, you'd type

```

$ rm remove\ me

or 

$ rm "remove me"
```

Also, there is a trick that helps you complete the names of files.  Just start typing the name of your file and then press tab and it will auto-complete the name for you.  Saves a lot of time especially with long file names.

essex:

Do delete all files in your .Trash, you can

```

$ cd ~/.Trash
$ sudo rm *
```

This will remove only files but not directories.  If you want to remove directories then you have to give the recursive option

```

$ cd ~/.Trash
$ sudo rm -r *
```

---

### Post by disembodied on 2007-02-20
Tribble -

Thanks for the help, I was able to delete the icon via terminal.

---

