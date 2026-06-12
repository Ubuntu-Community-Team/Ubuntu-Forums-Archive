---
title: "How To Select The Files With Same Name In Two Folders"
date: 2016-06-01
forum: General Help
---

### Post by Tanuj_Singh on 2016-06-01
[COLOR=#111111][FONT=Ubuntu]Let's guess I have two folders: A & B.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Now, there are 600+ files in folder A and 400+ files in folder B.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]There are many files which share the same name in these two folders.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I.E. file.so in folder A and file.so in folder B.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Now, there are also some files which are not present in both of the folders, I want to ignore them.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So, is there any software that can do this without much hassle?[/FONT][/COLOR]

---

### Post by David_Wright on 2016-06-01
> **Tanuj_Singh said:**
> Let's guess I have two folders: A & B.

Now, there are 600+ files in folder A and 400+ files in folder B.

I want to copy files with same name from folder A to folder B which is very hard if done manually.

So, is there any software that can do this without much hassle?

There is an example on [this page]("http://linuxcommand.org/wss0140.php") of a bash script that "[COLOR=#000000][FONT=verdana]compares the files in two directories and lists which files in the first directory are missing from the second[/FONT][/COLOR]", which seems like a good place to start if you want to write a script to do this regularly.

---

### Post by ajgreeny on 2016-06-01
You can not have two files in the same folder if the files are named identically, so I am not sure I understand exactly what you are trying to do; can you explain more please.

If David above has got nearer what you want you may find that unison (with its gtk GUI if you want it) is helpful.

---

### Post by Tanuj_Singh on 2016-06-01
> **ajgreeny said:**
> You can not have two files in the same folder if the files are named identically, so I am not sure I understand exactly what you are trying to do; can you explain more please.
No, I already said there are two folders, A and B.

---

### Post by Impavidus on 2016-06-01
Sounds to me as updating files in dir B from files in dir A. You could use rsync with the option --existing:```
rsync --existing /path/to/dirA/* /path/to/dirB/
```

---

### Post by howefield on 2016-06-01
> **Tanuj_Singh said:**
> Let's guess I have two folders: A & B.

Is this a hypothetical question or do you have an actual issue ?

> Now, there are 600+ files in folder A and 400+ files in folder B. I want to copy files with same name from folder A to folder B which is very hard if done manually...

Are you saying that you want to copy files from folder A, to folder B which already contains files with the same name as in folder A, but different file contents.

Your post is as clear as mud.

---

### Post by Tanuj_Singh on 2016-06-01
> **Impavidus said:**
> Sounds to me as updating files in dir B from files in dir A. You could use rsync with the option --existing:```
rsync --existing /path/to/dirA/* /path/to/dirB/
```
Awesome, that did it. Thank you :D

---

### Post by vasa1 on 2016-06-01
You could have had the courtesy to give impavidus credit in your Ask Ubuntu answer !!!

---

### Post by Tanuj_Singh on 2016-06-02
> **vasa1 said:**
> You could have had the courtesy to give impavidus credit in your Ask Ubuntu answer !!!
Sorry, I've given the credit. I was so into getting the work done that I forgot.

---

### Post by vasa1 on 2016-06-02
> **Tanuj_Singh said:**
> Sorry, I've given the credit. I was so into getting the work done that I forgot.

Great :cool:

---

