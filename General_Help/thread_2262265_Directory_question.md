---
title: "Directory question"
date: 2015-01-23
forum: General Help
---

### Post by michael-piziak on 2015-01-23
When I attempt to change to my "Game Roms" directory using terminal, it gives an error.

Please explain why.

See screenshot below.

---

### Post by the3dman on 2015-01-23
It is most likely the space in the folder name causing it. Try doing it this way:

```
cd '/home/yourusername/Game Roms'
```

or

```
cd 'Game Roms'
```

The apostrophe's tell Term to look for the whole folder name and not stop at the space.

---

### Post by michael-piziak on 2015-01-23
that worked

thanks

---

### Post by Bucky Ball on 2015-01-23
Try 'Game_Roms'. Ubuntu sometimes doesn't seem to like a space in names in the terminal.

* Oops, ninja-ed. Already fixed. Disregard. ;)

Please mark the thread as solved from Thread Tools to help others. Thanks.

---

### Post by Bashing-om on 2015-01-23
michael-piziak; Hi !

The system sees "Game Roms" as two distinct entities - as a space is a delimiter in linux.
so when you do " ls Game Roms " you are asking to list two things . Games and another called Roms. These do not exist; so the system is correct .
Now what you can do.
a) rename the file in the file manager as 1 name ( say Game_Roms ) - preferred, OR
b) enclose the filename in quotes ( ls "Game Roms" )
c) escape that space with a escape character '\' ( ls Games\ Rom .

Again it is recommended to change the name to a single instance, It may prevent other troubles in other instances.

[INDENT][INDENT]all in the process
[INDENT][INDENT][INDENT]of learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by michael-piziak on 2015-01-23
Thanks so much.

The easiest way for me to do it is 
cd 'Game Roms'

which works perfect

thanks

---

