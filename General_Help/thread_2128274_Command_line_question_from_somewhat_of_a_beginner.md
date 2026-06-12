---
title: "Command line question from somewhat of a beginner"
date: 2013-03-22
forum: General Help
---

### Post by Original Chaos on 2013-03-22
I searched goog and this forum to no avail so now I ask simply why
Terminal doesn’t want to understand spaces in file names.
[COLOR=#0000ff]/media/Storage HD/[/COLOR][COLOR=#000080]other folder[/COLOR]/ and so on look correct or am i missing something.
It stops at storage:file not found, do i need underscore or something _ - / \ * "" ???
I can install and run programs and stuff, but other than that I’ve had no luck.
Hopefully my question as well as the answer are simple enough.
so thanks in advance.

---

### Post by steeldriver on 2013-03-22
You can either enclose the filename with quotes

```
"/media/Storage HD/other folder/"
```

or escape the spaces with backslashes

```
/media/Storage\ HD/other\ folder/
```

---

### Post by oldos2er on 2013-03-22
Use the Tab key and have the shell complete file or folder names for you, including ones with spaces.

---

### Post by andrew.46 on 2013-03-22
...and avoid spaces in filenames.

---

### Post by CaptainMark on 2013-03-22
As to why, its because the terminal uses 'white space' (meaning any empty space or spaces) as a way to separate input into fields to be handled separately (called arguements), its a standard convention that is used because otherwise the terminal wouldn't know what bit you typed is the command name and what bit is telling it what you want to do etc.

---

### Post by GameX2 on 2013-03-22
You can also drag and drop the file you want to launch in the Terminal.  It will automatically add single-quote caracters ( ' ).

---

### Post by Original Chaos on 2013-03-22
Wow quotation marks, now i feel dumb. All works now,so i can work off external hard drives instead of moving to the desktop.
thanks all and extra thanks for the scientific answer, it helps every thing make a bit more sense.

---

