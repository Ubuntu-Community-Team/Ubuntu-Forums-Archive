---
title: "Retrieving arduino script file from hard disk image"
date: 2014-03-21
forum: General Help
---

### Post by Bronvu on 2014-03-21
The hard disk of my laptop crashed and I want to recover exactly  one file. The rest was either backed up or unimportant, but i missed  this one file.


The  file I am looking for is an adruino-script file (*.ino), which is basically  just a text file but with another extension . I've read into Foremost en  Magicrecue and it turns out that I'll have to write an own recipe. But  the fact that it's is just a text file makes it impossible, isn't it?  There is no pattern on which I can base this recipe...

Can someone tell me if I'm right? Or explain me what is possible to safe the adruino file?

---

### Post by dragonfly41 on 2014-03-21
This should help you ...

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

my bet will be on using testdisk to recover.

But first try this simple command .. n.b. takes a while to build up an index to search so be patient

```
sudo updatedb && sudo locate *.ino
```

to search for *.ino files

---

### Post by Bashing-om on 2014-03-21
Bronvu; Hi !

As it is but a single file you want to retrieve, have you considered trying to mount that partition from the liveDVD environment and simply copying the file to a stable medium ? This does assume that you know the path-to-the-file and that the partition is mountable.

[INDENT][INDENT]simple things first
[/INDENT][/INDENT]

---

### Post by tgalati4 on 2014-03-21
If *testdisk* can fix the partition table, then you can navigate directories and recover files.  If *testdisk* complains, then you have to resort to *photorec*, which will simply recover files--500 to a directory with numerical names, but with extensions.  Your *.ino files will probably be classified as scripts files with extension *.sh or *.txt.  You can then use:

```
grep arduino *.sh
```

You might have to change the keyword to search for.  Choose something that is unique in an arduino script file.

---

### Post by Bronvu on 2014-03-22
Thank you very much! I've managed to recover the file. Although I follow any of the suggestions exactly, you've all put me on the right track.

The way I did it: I used photorec to recover my files from the image I created and then used grep to find the correct file (grep returned it as a .h-file).

---

### Post by Lars_Kvale on 2015-02-11
Thank you for this thread! It helped me recover my arduino sketches after I deleted my windows partition (to install ubuntu). As I had already installed ubuntu the ntfs partition could not be mounted. I used photorec to recover all files possible, then grep on all those files to find my sketches (*.ino files). My *.ino files were returned by grep as *.c files. Finally this command to copy the exact files I needed (standing in directory with tons of folders of recovered files);
```
$ cp `grep -lir "string unique to my ino files" */*.c` recovered_ino_files/
```

Thanks again!

Cheers
Lars

---

### Post by tgalati4 on 2015-02-12
As Arduinos are quite popular, perhaps a feature request needs to go the the *photorec* developers to accurately recognize *.ino files.  *.h are header files and *.c are C language source code files (in plain text), so *photorec* is close to guessing correctly.  Some unique Arduino keywords would do it.

---

