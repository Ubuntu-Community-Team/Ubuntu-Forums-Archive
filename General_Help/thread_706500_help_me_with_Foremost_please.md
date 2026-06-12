---
title: "help me with Foremost please"
date: 2008-02-24
forum: General Help
---

### Post by korkless on 2008-02-24
hi, i have a partition  with ntfs mounted on /media/HDD and i want to use Foremost on it.
my problem is that i try to call "foremost -i /media/HDD2 or "foremost /media/hDD", then foremost starts but it stays waiting on the standard input without do nothing (the process is in sleeping state).
when i calls the application i use a custom -o outputdir where the rights directories are built but are ever empty.
i thinks that the cause it's that i use the application arguments in a bad way but i don't understand why..

with the -v argument (verbose output) appears

foremost -i /media/HDD -o /home/***/Desktop/recovery -v

Foremost version 1.5 by Jesse Kornblum, Kris Kendall, and Nick Mikus
Audit File

Foremost started at Sun Feb 24 14:27:18 2008
Invocation: foremost -i /media/HDD -o /home***/Desktop/recovery -v
Output directory: /home/***/Desktop/recovery
Configuration file: /etc/foremost.conf
Processing: stdin
|------------------------------------------------------------------
File: stdin
Start: Sun Feb 24 14:27:18 2008
Length: Unknown
 
Num      Name (bs=512)         Size      File Offset     Comment

and then the application sleep infinitly.
As configuration i use the default foremost.config wiht only the rows for image formats without #
thanks for every helps.

---

