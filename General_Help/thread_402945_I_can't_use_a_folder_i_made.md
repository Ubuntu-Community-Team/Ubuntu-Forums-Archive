---
title: "I can't use a folder i made"
date: 2007-04-06
forum: General Help
---

### Post by Death_Sargent on 2007-04-06
I made a cedega game folder and for some reason every time i try to open the folder in nautilus it crashes.

The strange thing is the sub folders can be navigated. It seems that just the root folder is the problem.

I'm using feisty fawn but made the folder while using edgy

---

### Post by dbbolton on 2007-04-06
you might try running ```
gksudo nautilus /
``` navigating to the folder you're having problems with, right-clicking it, then checking to make sure all the 'properties' are correct.

---

### Post by Death_Sargent on 2007-04-09
acutally i had some other problems with it before i could fix it and ended up deleting it. but the properties where correct

---

### Post by Mrs Twaddle on 2007-06-11
I am also having a similar problem. I downloaded a folder from my web space. And no matter what i try, i cannot open it. Every time i try, nautilus closes. If i use sudo nautilus or gksudo nautilus it freezes my system. The properties on the folder appear fine.  and i can see the files in there when i loook with filezilla.
I've tried renaming any funny characters, redownloading the folder and changing nautilus perferences. But I am getting nowhere.
To say my patience is running out is an understatement, i have managed to crash ubuntu 3 times today..

Is there anything else i can do to get this folder open, i need it.

---

### Post by dbbolton on 2007-06-11
> **Mrs Twaddle said:**
> I am also having a similar problem. I downloaded a folder from my web space. And no matter what i try, i cannot open it. Every time i try, nautilus closes. If i use sudo nautilus or gksudo nautilus it freezes my system. The properties on the folder appear fine.  and i can see the files in there when i loook with filezilla.
I've tried renaming any funny characters, redownloading the folder and changing nautilus perferences. But I am getting nowhere.
To say my patience is running out is an understatement, i have managed to crash ubuntu 3 times today..

Is there anything else i can do to get this folder open, i need it.
cd to that folder in a terminal, then use 'ls' command to list the contents of the folder. then you can copy and paste the contents of the folder to a new one like so:

```
cd /path/to/broken/folder
ls

```
that will let you look at what's in the folder. if you had, for example, and openoffice document, you could then open it as such:

```
ooffice -writer file.odt
```

or, you can move all of the files in the directory like this
```
mv *.* /path/to/new/folder
```

---

### Post by Mrs Twaddle on 2007-06-12
I did another way.

I turned thumbnail preview off in nautilus which allowed me into the folder.
It was a corrupted jpg. Took a bit of time to  preview them all one at a time until i found it though.

---

