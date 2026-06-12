---
title: "Cannot delete items off of USB flash drive"
date: 2012-10-28
forum: General Help
---

### Post by cymbri on 2012-10-28
I just started using linux (xubuntu) and have yet do to any of the code command prompts though I would be happy to do so if you could please give me detailed instructions. 

I think I overloaded my USB stick, i tried to move too many files to it and now when i go to delete a file It will not let me. I get a pop up that says: "Unable to create trashing info file No space left on device". I get the same pop up when i try to delete the .Trash-1000 folder. I don't care about the files on the disk, so if a solution involves wiping the disk I'm game

Thank you in advance to anyone who can help!

---

### Post by balkrish999 on 2012-10-28
How About    Formatting the USB which will Erase all data

---

### Post by cymbri on 2012-10-28
> **balkrish999 said:**
> How About    Formatting the USB which will Erase all data

I would, but I don't know how. I literally just starting using linux two weeks ago and most of the instructions can find on formatting a usb stick are for higher level users (aka greek to me)

---

### Post by cymbri on 2012-10-28
i'm going to start by reading a beginner guide to the xubuntu terminal

---

### Post by balkrish999 on 2012-10-28
> **cymbri said:**
> I would, but I don't know how. I literally just starting using linux two weeks ago and most of the instructions can find on formatting a usb stick are for higher level users (aka greek to me)

So, im guessing you know how to use Windows?


Go on to a Window PC

Plug in USB 

Right Click Format USB 

Click FAT/FAT32

Click Format 

Click OK 


Should Be Done :) ENjoy

---

### Post by Impavidus on 2012-10-28
You can also use the command line, if you don't want to wipe everything. It's best to learn that anyway if you want to use linux.

Insert your usb-stick and wait for it to auto-mount. Then open a terminal (applications -> tools -> terminal) and type
```

cd /media
ls
```It will show you a number of directories, one of wich is the usb stick. Get into a directory using
```

cd <directory name>
```get out using
```

cd ..
```and list its contents with
```

ls
```Removing a file is possible using
```

rm <file name>
```and removing an entire directory with
```

rm -r <directory name>
```Using the command line should prevent the creation of a trash folder, wich seems the problem, as there is no space to create the trash folder.

If any of the file or directory names contain spaces, make sure to put a backslash before it (as in "rm file\ name\ with\ a\ lot\ of\ spaces.txt"). Also keep in mind that linux is very case sensitive.

---

### Post by JKyleOKC on 2012-10-28
And if you prefer to work from the GUI, just hold down the shift key while you click on Delete or use the DEL key to get rid of a file. That will prevent it going to the trash, and permanently delete the file in the first place. This should solve the "no space" problem if you delete the .trash-1000 folder first.

The "rm" command in terminal does not remove folders (or directories, as they are known in the Linux world); it only works on files. The DEL and Shift-DEL actions in the GUI work on both.

Hope this helps!

---

### Post by cymbri on 2012-10-30
> **JKyleOKC said:**
> And if you prefer to work from the GUI, just hold down the shift key while you click on Delete or use the DEL key to get rid of a file. That will prevent it going to the trash, and permanently delete the file in the first place. This should solve the "no space" problem if you delete the .trash-1000 folder first.

I Tried this first, being the easiest solution to my problem. And It worked like a charm! Thank you!

I do Plan on learning more about the terminal, and I appreciate the detailed terminal instructions i will use them to get more familiar with it!

:):):)

---

