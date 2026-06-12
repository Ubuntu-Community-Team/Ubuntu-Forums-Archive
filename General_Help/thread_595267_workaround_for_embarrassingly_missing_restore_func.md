---
title: "workaround for embarrassingly missing restore functionality for erased files"
date: 2007-10-28
forum: General Help
---

### Post by gumbeto on 2007-10-28
Hi there,

I have the following problem:

I wanted to erase my library from rhythmbox but, by mistake, I selected all the songs and "moved to trash" instead of removing them.
I had a well organized directory structure for my music. Now, all the structure remais, but all the music is in the trash. I went to use the restore over all files and, guess what, there is no such thing!!!

I've read this rather embarrassing thread: [http://ubuntuforums.org/showthread.php?t=409817](http://ubuntuforums.org/showthread.php?t=409817)

My question is, since there is no restore functionality, is there a workaround, besides manually placing each file in it's previous location??? (I'm talking about 15gb).

All the information regarding the location of each file is in rhythmbox, in the "missing" tab. I wonder if this could be printed to a file and used with some voodoo magic shell programming to bring everything back...

Please, any help would be** very very much appreciated**
Gumbeto

---

### Post by commonlyUNIQU3 on 2007-10-28
There are probably a few sweet ways of accomplishing this by a shell script, and using some tag editing tools (such as the very powerful exfalso), but according to the article you linked to this functionality already exists in thunar.

Have you tried to install thunar, and opening your trash from there?

```
sudo apt-get install thunar
```

If you try that and it doesn't work (you may need to log out, and log back in to fully test it), I could give you some other ideas, but I'm a shell scripting noob, so I won't be able to take you all the way...

EDIT:  FYI - Thunar is the default file browser of the xfce desktop environment (in case you don't know), and so you will be prompted to install some components of the xfce environment when you use the above stated command - nothing to fear there, and you can always remove it when you're done (if you don't like using Thunar that is, but Thunar is a pretty cool FM):

```
sudo apt-get autoremove --purge thunar
```

---

### Post by gumbeto on 2007-10-28
Thank you for your reply.

Thunar couldn't help me because the files weren't deleted with it and it has no information about their original location. They don't even appear in thunar's trash. 

I had already seen in that thread that it wasn't possible to achieve it that way:

> 
[...]is there ANY FRIGGIN way to restore these to their original folders?[...]

[...]No, there's no way. The only way KDE or Thunar would help is if you'd used KDE or Thunar to delete those files in the first place.[...]

About the tag editing tools, I think I'll will go that way if I can't manage to restore the previous state, but I'd rather have everything back in it's place, in the appropriate folders, next to the right cover arts of the albums and to some occasional comment files...

So, those other ideas would come in handy :)

---

### Post by commonlyUNIQU3 on 2007-10-29
For going the tag editing route - I'd recommend exfalso:

```
sudo apt-get install exfalso
```

It has a file-renaming function that can batch rename your audio files based on metadata values (e.g. if your music is tagged properly you can rename the files in ANY syntax you can imagine).  The trick part would be to rename the files in a [artist]-[album]-[title].mp3 format, and build a script that would parse out the [artist], and the [album] values to use for your copy path...  

It shouldn't be to difficult to do with a little practice.

Let me know how it goes...

---

### Post by gumbeto on 2007-10-30
In rhythmbox there is a tab with the missing files and their supposed location. If I could get that information in a simple file, I could try to dig the shell scripting a little and use it to move the files.
Otherwise, I'll go with exfalso.

I'll try to fix it at the weekend and then I'll let you know how it went.

Thanks for the help mate

---

