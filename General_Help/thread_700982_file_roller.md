---
title: "file roller"
date: 2008-02-18
forum: General Help
---

### Post by ladybluballs on 2008-02-18
I have a rar file loaded on my desk top and cant figure out what to do with it my os is ubuntu the file is as follows,[win4lin pro desktop 3.5 rar] the download tool said its achieve is default file-roller I am very new to linux and just now giving it a new try after rest of a few weeks,how can I get the mentioned file to install and thanks for any help

---

### Post by lil_malcolmx2 on 2008-02-18
mmnn.. i'm guessing your problem is your not able to open you rar file..

try

```
sudo apt-get install unrar
```

hope it helps

---

### Post by Yellow Pasque on 2008-02-18
If I'm not mistaken, unrar is a command-line utility. I think the proprietary GUI version is also available through (System -> Administration -> Synaptic). In general, if you need a program to do something, your first stop should be the Synaptic package manager. It's one of the best parts about Debian/Ubuntu: a huge software repository.

---

### Post by sisco311 on 2008-02-18
> **Temüjin said:**
> If I'm not mistaken, unrar is a command-line utility. I think the proprietary GUI version is also available through (System -> Administration -> Synaptic). In general, if you need a program to do something, your first stop should be the Synaptic package manager. It's one of the best parts about Debian/Ubuntu: a huge software repository.

after you install unrar you can unrar files with the default file roller.

---

### Post by Yellow Pasque on 2008-02-18
Ah, thanks for correction

---

### Post by ladybluballs on 2008-02-18
> **sisco311 said:**
> after you install unrar you can unrar files with the default file roller.

thanks I got it unzipped but I need it installed on my system

---

### Post by ladybluballs on 2008-02-20
> **ladybluballs said:**
> thanks I got it unzipped but I need it installed on my system

I now have file unzipped but don't know the command to put in termnal to install it

---

### Post by Yellow Pasque on 2008-02-20
What are you trying to install, unrar?
```
sudo apt-get install unrar
```
Then:
```
cd /<directory with the rar file>
unrar e filename
```

```
UNRAR 3.71 beta 1 freeware      Copyright (c) 1993-2007 Alexander Roshal

Usage:     unrar <command> -<switch 1> -<switch N> <archive> <files...>
               <@listfiles...> <path_to_extract\>

<Commands>
  e             Extract files to current directory
  l[t,b]        List archive [technical, bare]
  p             Print file to stdout
  t             Test archive files
  v[t,b]        Verbosely list archive [technical,bare]
  x             Extract files with full path

<Switches>
  -             Stop switches scanning
  ad            Append archive name to destination path
  ap<path>      Set path inside archive
  av-           Disable authenticity verification check
  c-            Disable comments show
  cfg-          Disable read configuration
  cl            Convert names to lower case
  cu            Convert names to upper case
  dh            Open shared files
  ep            Exclude paths from names
  ep3           Expand paths to full including the drive letter
  f             Freshen files
  id[c,d,p,q]   Disable messages
  ierr          Send all messages to stderr
  inul          Disable all messages
  kb            Keep broken extracted files
  n<file>       Include only specified file
  n@            Read file names to include from stdin
  n@<list>      Include files in specified list file
  o+            Overwrite existing files
  o-            Do not overwrite existing files
  or            Rename files automatically
  ow            Save or restore file owner and group
  p[password]   Set password
  p-            Do not query password
  r             Recurse subdirectories
  sl<size>      Process files with size less than specified
  sm<size>      Process files with size more than specified
  ta<date>      Process files modified after <date> in YYYYMMDDHHMMSS format
  tb<date>      Process files modified before <date> in YYYYMMDDHHMMSS format
  tn<time>      Process files newer than <time>
  to<time>      Process files older than <time>
  ts<m,c,a>[N]  Save or restore file time (modification, creation, access)
  u             Update files
  v             List all volumes
  ver[n]        File version control
  vp            Pause before each volume
  x<file>       Exclude specified file
  x@            Read file names to exclude from stdin
  x@<list>      Exclude files in specified list file
  y             Assume Yes on all queries
```

---

