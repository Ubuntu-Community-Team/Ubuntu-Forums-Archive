---
title: "Trash will not empty"
date: 2015-06-11
forum: General Help
---

### Post by Frank_Callo on 2015-06-11
Hi folks

I am running ubuntu 14 on an OLD dell.  I've been noticing strange things happening lately.  For example, I'll delete a folder with 3 items in it and I'll get a message saying that the folder contains some way out number of files like 700.  So this morning I was cleaning up a bit, put a bunch of stuff into trash and hit empty.  The preparing to delete box with the meter comes up for a bit then just goes away.  Trash will not empty.  

So, anyone have this issue?
Thanks
Frank

---

### Post by sotiris2 on 2015-06-11
Files in the trash are located in .local/share/Trash/files inside your home folder . You can navigate there and try to delete them manually via **shift**+delete. To see the .local folder in your home you will have to enable "show hidden files" in the view menu or hit Ctrl+H. 

If that doesn't work there is probably some kind of permission issue that we could troubleshoot.

---

### Post by LastDino on 2015-06-11
Well, if it is just to clear trash box, 
 You can use this command :
  >  rm -rf ~/.local/share/Trash/*
  The rm command removes (delete) files or directories.
  -f, --force     Ignore nonexistant files, and never prompt before removing.
-r, -R, --recursive     Remove directories and their contents recursively.
  The trash folder is found at: $HOME/.local/share/Trash
  Be careful how to use rm command because any misuse may cause deleting sensitive system folders and files .

---

### Post by Frank_Callo on 2015-06-11
where do I go to navigate there.  When I go in through "search your computer", all that happens is that "-scopes:reference-extra-scopes:" is added before ".local/share/trash/files.  I assume this has to go through terminal but I can't remember how to get there.  Thanks for working on this with me guys.  This is an OLD box I'm working on but I gotta make it last a little longer.

---

### Post by vasa1 on 2015-06-11
> **LastDino said:**
> ...
  Be careful how to use rm command because any misuse may cause deleting sensitive system folders and files .
+1

Just to make things safer, I suggest you first *cd* to .Trash and **then** run *rm*.

---

### Post by Frank_Callo on 2015-06-12
Do I put that rm command into terminal?  I don't want to mess anything up :)

---

### Post by yancek on 2015-06-12
> Do I put that rm command into terminal?

Yes and do cd to your /home/user/.local/share/Trash directory before running the command.  You need the dot before local as it is a hidden file.

I usually use the Shift+Delete method which has always worked for me?

---

### Post by Frank_Callo on 2015-06-12
What does "cd" mean and how do I do it.  Also, ctrl. T is the way to get into terminal correct?

---

### Post by sotiris2 on 2015-06-12
Ctrl + Alt + T will get you a terminal. Paste the following in there. ```
cd ~/.local/share/Trash
``` Hit enter. Paste the following. ```
pwd
``` If the output ends at something other than /Trash DO not run the following command otherwise continue. ```
rm -rf * files info
```

---

### Post by Frank_Callo on 2015-06-12
This is what has happened:

frank@frank-OptiPlex-GX520:~$ cd ~/.local/share/Trash
[email]frank@frank-OptiPlex-GX520:~/.local[/email]/share/Trash$ pwd
/home/frank/.local/share/Trash
[email]frank@frank-OptiPlex-GX520:~/.local[/email]/share/Trash$ 

Before I enter the last line of code I want to be sure that "$" is cosher.

---

### Post by capnfred on 2015-10-28
Hello, I am a new user on this forum, not new to Ubuntu, I am running 14.04 and have been for some time, my problem is as follows:

I have five empty folders in my trash folder, no matter what I have tried will don remove these folders, I have just tried the instructions on this thread using the terminal, nothing happened...this is not causing any problems other than bugging me... I can put other files in the trash and when I empty the trash they are gone, but these five will not go away.. any help is appreciated... also when I try and us the ls command in the term it says that there is no such command.  

Thanks

Capn

quick update, I tried the ls command in a different dir, and it works fine, also rebooted the puter and it still has the empty folders in the trash,

---

### Post by tturrisi on 2015-10-28
just go to /home/<username>/.local/share/ and delete the Trash folder.  It will get recreated the next time you delete something.

---

### Post by capnfred on 2015-10-28
will give that a try....

---

### Post by capnfred on 2015-10-28
Nope, tried it they are still there......any other ideas....:) , even tried going in to the term, and doing it from the command line....nothing seems to work... there are no files, just empty folders.....open to suggestions, The only thing I have not done is to re-install the system, and I prefer not to do that...its just wierd...

---

### Post by tturrisi on 2015-10-29
in a termibal run: sudo nautilus and delete the trash folder.  It's possible you were root when you deleted the folders initially, in which case you cannot delete them unless you are root.

---

### Post by capnfred on 2015-10-30
was not in root, will try your suggestion and let you know what happens thanks ok here is a copy of my terminal screen after I executed the sudo command:


[sudo] password for fred: 

(nautilus:2784): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(nautilus:2784): GLib-CRITICAL **: Source ID 112 was not found when attempting to remove it

(nautilus:2784): GLib-CRITICAL **: Source ID 113 was not found when attempting to remove it

(nautilus:2784): GLib-CRITICAL **: Source ID 114 was not found when attempting to remove it


ran the following in term, and viola its gone.... 
sudo rm -rf ~/.local/share/Trash/*  it hink this is the same command string from before, but for whatever reason it worked this time....will have to examine it carefully to see what I did different

all is well thanks to evryone 
\
as far as I can tell the only difference is the sudo...which makes a big difference... again thanks to all... its gone

Fred

---

