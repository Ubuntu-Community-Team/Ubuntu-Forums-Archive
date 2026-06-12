---
title: "[SOLVED] how do you figure out gtk version"
date: 2008-06-26
forum: General Help
---

### Post by suicidejack on 2008-06-26
I'm trying to figure out what GTK version I am running.  I can't find anything online for this.

---

### Post by ibutho on 2008-06-26
If you installed gtk via the package manager, you can use Add/Remove software or Synaptic to check the gtk version.

---

### Post by Forlong on 2008-06-27
> **suicidejack said:**
> I'm trying to figure out what GTK version I am running.  I can't find anything online for this.
What do you mean by "GTK version" and why do you need to know that?

---

### Post by suicidejack on 2008-06-27
as in what version number i am running on my comp.  i know i have 2.something but i'm not sure which one i have.  mostly interested in this for possible theme creation. plus i figured its a good thing to know.  a shell command should work for this - i just can't figured out what command to use.

as to synaptic it only tells me that i have the 2.x gtk engine, etc. no relaly detailed info unless i am looking in the wrong place...

---

### Post by ibutho on 2008-06-27
Search for libgtk2.0. You should see version 2.12.9.

---

### Post by unutbu on 2008-06-27
```
% COLUMNS=150 dpkg --list libgtk2.0-0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                            Version                         Description
+++-===============================-===============================-==============================================================================
ii  libgtk2.0-0                     **2.12.0**-1ubuntu3                 The GTK+ graphical user interface library
```


```
% COLUMNS=150 dpkg --list libgtk2.0-0 | egrep '^ii' | awk '{print $3}'
2.12.0-1ubuntu3
```

---

