---
title: "Deleting file with illegal characters"
date: 2007-05-01
forum: General Help
---

### Post by nemo611 on 2007-05-01
Hi!

Sorry if this was already posted somewhere else, but i didn't managed to find it.
My problem is that i downloaded a file which had some asians characters, and when the download was finished, those characters turned into '?' (I was using windows when downloading that file, in a ext3 shared partition using FS Driver). So now I have a file with a funny name. I can't manage to delete it in windows nor in Ubuntu.
Since the file was in my ext3 partition, I guess it's better to delete it using Ubuntu.
I have tried some scripts found in the web using "rm -ri ..." but it says the file doesn't exists.
The file name starts and ends with '?', and has some normal characters in between.

Thanks for your help.

---

### Post by Rinzwind on 2007-05-01
3 things:

1. you can use TAB to autocomplete;
2. you can use wildcards (like ? and *). 
3. use **ls** to test what's going to be removed before you use rm.


Normally this:
ls *test* 
lists all files with test in it.

Let's say the file is named:
?kjaefh??d7t^?KJHNig
What does 
ls *kja* 
do?


Can you post the full name as it is shown inside terminal?

---

### Post by stchman on 2007-05-01
> **nemo611 said:**
> Hi!

Sorry if this was already posted somewhere else, but i didn't managed to find it.
My problem is that i downloaded a file which had some asians characters, and when the download was finished, those characters turned into '?' (I was using windows when downloading that file, in a ext3 shared partition using FS Driver). So now I have a file with a funny name. I can't manage to delete it in windows nor in Ubuntu.
Since the file was in my ext3 partition, I guess it's better to delete it using Ubuntu.
I have tried some scripts found in the web using "rm -ri ..." but it says the file doesn't exists.
The file name starts and ends with '?', and has some normal characters in between.

Thanks for your help.

If it is the only file inside a folder then you can enact the command:

sudo rm -r -f <folder_name>

This will take care of it.

If you have other files in that folder then relocate all the other files until the file with funky characters in its name is the only one in that folder then use the sudo rm command.

Hope this helps.

---

### Post by nemo611 on 2007-05-01
I forgot to say that it is a folder and not file (well in windows it appears as a folder but in Ubuntu it appears with the Gnome foot icon). I can't go inside the folder.

I tried "sudo rm -r -f <folder name>", but i get (the file is in the "DeleteMe" folder) :

rm: ne peut évaluer par lstat() `DeleteMe/???5???????? Special Edition - One more time, One more chance/??????': Aucun fichier ou répertoire de ce type

It can't evaluate the expression and therefore it can't delete the folder

Here is the file name as shown in the terminal : 
???5???????? Special Edition - One more time, One more chance/??????

---

### Post by nemo611 on 2007-05-01
I also tried this :  ls *Special*

But i get :

ls: ???5???????? Special Edition - One more time, One more chance/??????: Aucun fichier ou répertoire de ce type

---

### Post by klytu on 2007-05-01
Did you try renaming the file and then deleting it?

---

### Post by psusi on 2007-05-01
If you created it in windows, why don't you delete it from windows?

---

### Post by nemo611 on 2007-05-01
I have tried in Windows with no success. 
I have also tried renaming the file in Ubuntu but it launches the Bug Buddy.
When i'm in the navigator, the folder shows this name : 
%3F%3F%3F5%3F%3F%3F%3F%3F%3F%3F%3F%20Special%20Edition%20-%20One%20more%20time%2C%20One%20more%20chance%2F%3F%3F%3F%3F%3F%3F

The folder is not very big so it's not a big problem. But since I can't do anything with it I wanted to remove it.

---

### Post by nemo611 on 2007-05-02
Maybe the only solution is formating de partion ... :confused:

---

### Post by jwbaker on 2007-05-02
rm -rf *Special*

That will work.  There are no illegal characters in filenames on Linux with ext3.  Only '/' and the null character are disallowed.

---

### Post by jimcooncat on 2007-05-02
I found this, which looks good to me -- though I haven't tested it.

"A less dangerous method is to refer to the file by its inode number, which is its real name as far as Unix is concerned anyway. Use ls -i to find out the inode number, and then use 

find . -inum inode -ok rm '{}' \;

The advantage of this method is that it also allows you to rename the file if you actually want to keep it, but have been unable to access it because of the funny characters. To rename the file, use find . -inum inode -ok mv '{}' new-file-name \;. If you don't want the -ok safety check, use -exec instead."

Disclaimer: Be prepared that this is probably very dangerous. I don't know that it might pick up an inode number from another file system on your machine, and how that would work.

---

### Post by nemo611 on 2007-05-02
I tried rm -rf *Special* with no resutl

An when I do ls -i it gives a value of 0 for the inode of the file.

I have submited the bug using BugBuddy, I still have to give some more detailed stack traces so that they can look further.

Thanks for all of your answers.
If I get an answer to this problem i'll post it.

---

### Post by NT4usB on 2007-05-02
Did you try getting at the file\folder via a command prompt from your windows box?
If you can see it in the windows shell, maybe you can ren or del from there...
...worth a shot.

---

### Post by psusi on 2007-05-03
It sounds like the windows driver fouled up the filesystem.  You should run a fsck -f on the partition from the livecd.

---

### Post by stylishpants on 2007-05-04
Personally my favourite way to delete weirdly named files is using "mc", the midnight commander.  It's a curses-based file manager that runs in the terminal, and is very easy to use.

To use it, install the "mc" package, and enter the "mc" command.  Then just
move the arrow keys until the selection bar is over the problem file, and press the F8 key to delete the file.  (All the keys for the basic file operation commands are listed in the main window, so you don't even have to remember them.)

MC is very good at deleting files with bizarre names.

---

