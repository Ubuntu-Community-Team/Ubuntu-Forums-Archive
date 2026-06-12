---
title: "Ubuntu cannot open files with accentuated character paths or file names"
date: 2017-02-13
forum: General Help
---

### Post by avidichard on 2017-02-13
I am a noob on Ubuntu. I am french Canadian and all my folders are in french. But when downloading files or trying to open files under my "Downoads" folder which is named "Téléchargements", they won't. I get a message saying that my file does not exist but when I look it is there. I also tried to change my downloads folder to a non-accentuated folder but my daughter needs to open files for her homework which also contains accentuated character and I get the same error so I can't get arround this problem. Can someone help me out as a noob user please?

---

### Post by dragonfly41 on 2017-02-13
In your terminal run the command
```
locale
```
It should show UTF-8 settings.

---

### Post by avidichard on 2017-02-13
> **dragonfly41 said:**
> In your terminal run the command
```
locale
```
It should show UTF-8 settings.

everything is en_US except the following which are fr_FR:
[LIST]
[*]LANG
[*]LANGUAGE
[*]LC_CTYPE
[*]LC_COLLATE
[*]LC_MESSAGES
[/LIST]

---

### Post by dragonfly41 on 2017-02-13
I'm afraid that as a typical Brit I have no personal experience in applying different languages
but from quick reading I believe that you will need to run something like this ..

[COLOR=#000000][FONT=Arial]```
sudo update-locale LANG=fr_CA.UTF-8 LANGUAGE=fr:en
```

[/FONT][/COLOR]Read here ... [https://help.ubuntu.com/stable/ubuntu-help/session-language.html](https://help.ubuntu.com/stable/ubuntu-help/session-language.html)
[COLOR=#333333][FONT=Consolas]


[/FONT][/COLOR]

---

### Post by avidichard on 2017-02-15
That did not work. I find that really weird that Ubuntu cannot handle characters with accents. I can save under those paths but not open them. Basically, those are `.doc`files that open with libreoffice and they don't open at all.

---

### Post by dragonfly41 on 2017-02-16
As I declared I am not the best person to address accentuated name/path issues.
My guess is that it must be something very simple and basic, but beyond my ken.
I'll try as best I can (from just reading threads)  ..

You write &#8220;but when I look it [the accentuated name file] is there&#8221;.

So you could  start by understanding what Ubuntu thinks the file path is ..

Launch a command terminal ... Ctrl + Alt + T

start by installing a small utility .. realpath

```
sudo apt-get update
sudo apt-get install realpath
```

Understand what realpath does by typing command "man realpath"

After installation of realpath type command

```
cd ~/[COLOR=#000000]Téléchargements[/COLOR]
realpath accentuatedfilename.doc
```

and take a note of the filepath to your (accentuated name) test document you can see.

Here is one discussion which seems relevant to your problem.

[https://forum.openoffice.org/en/forum/viewtopic.php?t=38713](https://forum.openoffice.org/en/forum/viewtopic.php?t=38713)

Also if still having problems you could search in here ...

[https://wiki.ubuntu.com/CanadianTeam/](https://wiki.ubuntu.com/CanadianTeam/)

I hope this thread of thought helps until someone else steps in with better advice.

===============================================

[Later edit]

Further reading from above openoffice.org thread

Launch LibreOffice > Tools  > Language Settings > Language

choose French (Canada)

---

### Post by Keith_Helms on 2017-02-16
What are you trying to open it with?  I created a test directory with that name by copying it from your post, created a test file under it and I was able to open it with a text editor without any problem.
```

$ ls -lR T*
Téléchargements:
total 4
-rw-rw-r-- 1 keith keith 11 Feb 16 07:10 text.txt


```

Please post the result of this command:
```

ls -lR Téléchargements

```

---

