---
title: "programs not exiting on close"
date: 2008-06-18
forum: General Help
---

### Post by jessika-kaos on 2008-06-18
I have two programs whose processes do not die after I exit out of them, and I have to manually kill them (which has been really annoying). I tested these on my other computer and they both work fine. Both computers are running Hardy. I'd rather have both working properly on my main computer - any suggestions on how to figure out what is causing the problem? I've already reinstalled the apps several times and deleted their directories in my home directory.

They are both written in python too, which may just be coincidental. Thanks.

---

### Post by nikgare on 2008-06-18
Which two programs are giving you trouble?

---

### Post by jessika-kaos on 2008-06-18
Anki & mnemosyne. They are spaced repetition programs. I thought Anki had a bug but it works splendidly on a different computer. I don't get any output when I run these from a terminal and exit - I just don't get a command prompt back until I kill them.

---

### Post by nikgare on 2008-06-19
If you start either of these programs in a terminal, what output do you get wehn you quit them?

---

### Post by jessika-kaos on 2008-06-19
There is no output when I quit, but the command prompt doesn't return until I hit cntrl + c.

---

### Post by VMC on 2008-06-19
From Terminal exactly how do you run them. Like so: Anki && mnemosyne, or on seperate lines.
Display how you type them into the Terminal.

---

### Post by jessika-kaos on 2008-06-19
Cut & pasted below with comments added:

```
sonne@HIVE:~$ mnemosyne
!----after exiting I only get a cursor, and process still runs
sonne@HIVE:~$ !----control+C brings back the prompt
```


If I run either from a shortcut I get the same thing, process doesn't die after exiting. Both work fine on another PC.

---

### Post by VMC on 2008-06-19
> **jessika-kaos said:**
> Cut & pasted below with comments added:

```
sonne@HIVE:~$ mnemosyne
!----after exiting I only get a cursor, and process still runs
sonne@HIVE:~$ !----control+C brings back the prompt
```


If I run either from a shortcut I get the same thing, process doesn't die after exiting. Both work fine on another PC.

I don't know what mnemosyne is. It appears it wainting for further input. If you type mnemosyne --help, what do you get?

---

### Post by jessika-kaos on 2008-06-19
mnemosyne is just a small flashcard app.

```
sonne@HIVE:~$ mnemosyne
mnemosyne --help 
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/mnemosyne/pyqt_ui/sound.py", line 34, in update
    def update(self):
KeyboardInterrupt

sonne@HIVE:~$ mnemosyne --help
Usage: mnemosyne [<database.mem>]

Options:
  -h, --help            show this help message and exit
  -d DATADIR, --datadir=DATADIR
                        data directory
sonne@HIVE:~$
```

---

