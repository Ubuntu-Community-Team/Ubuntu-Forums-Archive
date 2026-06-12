---
title: "Install file.run"
date: 2015-07-30
forum: General Help
---

### Post by mark236 on 2015-07-30
Hello. I have Ubuntu 14.04 
I want install .run file. I wrote command in terminal:
[B]sh /home/lord/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/Qt.run 
[/B]And i gave it:
[B]/home/lord/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/Qt.run: 1: /home/lord/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/Qt.run: Syntax error: ")" unexpected

[/B]&#8203;What did I do wrong?

---

### Post by dino99 on 2015-07-30
did you made Qt.run executable ?

[http://ubuntuforums.org/showthread.php?t=239797](http://ubuntuforums.org/showthread.php?t=239797)

if its really a syntax error, check the exact path, and remember that letters are sensitive

as your path has cyrillic letters, i hope the syntax error came from that mix cyrillic/non cyrillic

---

### Post by buzzingrobot on 2015-07-30
I'll suggest the qt.run is a script and contains an unmatched ')'.  You would see another error message, not that "Syntax error:..." message, if the file wasn't executable.

---

### Post by mark236 on 2015-07-30
I did way **home/lord/ Qt.run** and terminal wrote "syntaxerror": ')' unexpected.
Qt.run is executable.

---

### Post by steeldriver on 2015-07-30
What is the output of the command

```

file /home/lord/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/Qt.run 

```

please? if it's a binary (or even a shell script for a shell other than sh/dash) you should just run it as

```

/home/lord/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/Qt.run

```

or
```

./Qt.run

```
if you are already in the directory that contains it.

---

### Post by mark236 on 2015-07-30
Terminal wrote it:

lord@Hellraiser:~$ file '/home/lord/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/Qt.run' 
/home/lord/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/Qt.run: ELF 64-bit LSB  executable, x86-64, version 1 (GNU/Linux), dynamically linked (uses shared libs), for GNU/Linux 2.6.18, BuildID[sha1]=5cbb7ba150b6aa2669eefcc998b615419e1703bc, not stripped

Qt - it is [FONT=Arial]the installation file of [/FONT]Qt Creator

---

### Post by mark236 on 2015-07-30
All right. File for 64x. I have Ubuntu 86x. 
Thank everyone. :)

---

