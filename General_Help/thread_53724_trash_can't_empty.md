---
title: "trash can't empty"
date: 2005-08-01
forum: General Help
---

### Post by wellery on 2005-08-01
When i try to delete what is in the trash i get an error which says Error file not found when deleting /video/.Trash-...ontents.tar.gz". would you like to continue? I keep getting this message when I try to continue. I changed into the directory where it's having trouble deleting and I get this error when i do ls. ls: #ontents.tar.gz: No such file or directory. There is some problem with this weird file. How do i remove it? When i type rm and hit space then tab it comes up with "rm \#ontents.tar.gz" when i hit enter i get "rm: cannot remove `#ontents.tar.gz': No such file or directory". Can someone please help me delete this?

---

### Post by BKonkle on 2005-08-01
Sometimes I have trouble deleting things in the trash can too.  What I would suggest is a little trip through the console to try to wipe your trash can clean.

First, open a console and go into your trash directory:
```
cd ~/.Trash
``` 

Then, remove all the regular files and directories with sudo:
```
sudo rm -Rf *
``` 

Now, remove all the hidden files:
```
sudo rm -Rf .*
``` 

By now, you should be clean.  If not, let us know!

---

### Post by wellery on 2005-08-01
There is nothing in the ~/.Trash folder. The files that I can't remove are in another partition which is formated in reiserfs. It has a folder called .Trash-home where home is the username. When i type:

```
sudo rm -Rf *
``` 

It says:

```
rm: cannot remove directory `Documentation2': Directory not empty
``` 

When i type:

```
 sudo rm -Rf .*
``` 

It says:

```
rm: cannot remove `.' or `..'
rm: cannot remove `.' or `..'
``` 

and when i type:

```
 sudo rm -Rf *.*
``` 

nothing happens.

---

### Post by cjoshuav on 2005-08-06
I'm just a newbie, but what if you did 

```
sudo rm -d -Rf *
```

?

Joshua

---

### Post by kalle314 on 2005-08-06
If it says ```
rm: cannot remove directory `Documentation2': Directory not empty
``` 

I would try
```
rm -r Documentation2
```

---

### Post by Sam on 2005-08-06
```
$ sudo rm -rf ~/.Trash/*
```

---

### Post by tkaplan1983 on 2007-06-18
HAHA you guys are funny.  This is a very very simple problem to solve.

All you have to do is open a terminal and do the following:

sudo chmod 777 -R ~/.Trash

and then you can open your recycle bin in your GUI and hit empty trash.  DONE & DONE!

Hope this helps,

Terry

---

### Post by dannyboy79 on 2007-06-18
> **tkaplan1983 said:**
> HAHA you guys are funny.  This is a very very simple problem to solve.

All you have to do is open a terminal and do the following:

sudo chmod 777 -R ~/.Trash

and then you can open your recycle bin in your GUI and hit empty trash.  DONE & DONE!

Hope this helps,


Terry

ha ha, you're funny. How in the world would a GUI help?????? Next time I suggest you lay of the arrogance just a little bit. I have this same problem and it's because the files were deleted from a network share in my case and for some reason, they won't go away not matter what I've tried. So there they sit for eternity.

---

### Post by steve8track on 2007-07-31
Wow, it worked!  Thanks!  I had a problem where I couldn't delete two folders on my desktop.  I could move them to the trash, but I couldn't empty the trash.  Shift Delete would bring up the same error as emptying the trash, that I couldn't delete some of the files, I can't remember the reason.  I tried to cd to the directory, and it wouldn't even let me go in because it said "permission denied," yet Nautilous let me browse in it.  That was VERY strange to me that the GUI would let me, but the console wouldn't.  I tried to change the permissions which chmod and chown, but chmod -R u+rwx, nor anything else I tried, **until you suggested chmod 777 -R.**

Thanks, it worked like a charm!

I am curious though, what is the difference between using 777 and a+rwx or u+rwx.  I mean, how can I tell what number does what?  At least a+rwx makes sense to me by it's symbolism, "allow permissions to ALL to READ, WRITE, and EXECUTE", but what aboue a number?  Are the numbers the same things, only in different form?  Or are there permission options you can't do with a+r u+rw, etc.

Either way, thanks for helping me empty my trash without spilling any garbage water ;-)

---

### Post by dannyboy79 on 2007-07-31
chmod -R a+rwx does the same thing as chmod -R 777, it will recursively change the permissions on the specified folder as well as all the folders and files within it (the -R means to apply the change recursively)

---

### Post by stchman on 2007-07-31
> **wellery said:**
> There is nothing in the ~/.Trash folder. The files that I can't remove are in another partition which is formated in reiserfs. It has a folder called .Trash-home where home is the username. When i type:

```
sudo rm -Rf *
``` 

It says:

```
rm: cannot remove directory `Documentation2': Directory not empty
``` 

When i type:

```
 sudo rm -Rf .*
``` 

It says:

```
rm: cannot remove `.' or `..'
rm: cannot remove `.' or `..'
``` 

and when i type:

```
 sudo rm -Rf *.*
``` 

nothing happens.

Then do the following

```

sudo rm -r -f <path to Trash>/.Trash/*

```

---

### Post by TheMacOne on 2007-09-16
hi all,

you could do the whole thing as a script - the chmod and the rm.

For GUI-minded users (Ubuntu feisty):
1. Go to the desktop and open TextEditor
2. Enter this code into the text documnet:
```
#!/bin/bash
sudo chmod 777 -R ~/.Trash
cd ~/.Trash
sudo rm -Rf *
sudo rm -Rf .*

```
3. Save as <filename>.sh (I called mine chmod_trash.sh)
4. It should have saved to your home folder so, close the TextEditor and go into your home folder (Places menu > Home folder)
5. Right mouse click on the newly created file and select Properties.
6. Click on the Permissions tab and make sure you have read & write permissions.
7. Make sure the "Allow executing file as a program" option is ticked. Close the Properties window.
8. Right mouse click on the file again and now select make link.
9. Drag the newly created link to the desktop.
10. Double mouse click the link and when a dialog pops up asking if you want to "Run in Terminal", "Display", "Cancel" or "Run", just click on "run" and the job should be done in a few seconds.

If you need to get to this file in Terminal, just type in: ```
./<filename>.sh
``` then hit enter. It may ask you for your password (for sudo) and may come back with "cannot remove ." or "cannot remove ..". That is fine. So long as the trash is empty, that is the main thing.

Hope this helps someone.

---

### Post by slumbergod on 2008-01-31
in the interests of helping anyone else who encountered the same variation of the problem as me...

I could not empty my trash can either - permission denied. When I used the command line the trash folder was empty. Opening it in the GUI showed it had a folder in it that I deleted. 

chmod 777 technique did not work. 

I found the only way to sort it out was to restore the deleted folder from within the GUI's right click context menu, then to delete the folder from where it originally was using the command line.

---

