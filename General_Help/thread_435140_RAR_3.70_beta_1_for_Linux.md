---
title: "RAR 3.70 beta 1 for Linux"
date: 2007-05-06
forum: General Help
---

### Post by fernando_lopes_jr on 2007-05-06
I would like same help to install the latest version of RAR 3.70 beta 1 for Linux. In the winrar home page this software is not available in deb it's only available in a gaz.tar file witch when I open has a bunch of files inside that I don't know what to do with them can someone please give me a  hand.

---

### Post by taurus on 2007-05-06
There should be two files that you are interested in:  rar & unrar.  Just copy them to somewhere in your path, perhaps /usr/local/bin, and run them from there.  

```
sudo cp rar /usr/local/bin
sudo cp unrar /usr/local/bin
```
Otherwise, post the output of this command from a terminal while you are in the directory that you unpacked rar.

```
ls -la
```

---

### Post by fernando_lopes_jr on 2007-05-06
The output is this

Code:
> 
cda@cda-server:~/cda-server/rarlinux-3.7.b1/rar$ ls -la
total 1592
drwxr-xr-x 2 cda cda   4096 2007-05-06 21:50 .
drwxr-xr-x 3 cda cda   4096 2007-05-06 21:50 ..
-rw-r--r-- 1 cda cda  56994 2007-01-08 16:50 default.sfx
-rw-r--r-- 1 cda cda    217 2007-01-08 16:50 file_id.diz
-rw-r--r-- 1 cda cda   4398 2007-01-08 16:50 license.txt
-rw-r--r-- 1 cda cda    428 2007-01-08 16:50 Makefile
-rw-r--r-- 1 cda cda   3183 2007-01-08 16:50 order.htm
-rw-r--r-- 1 cda cda 341152 2007-01-08 16:50 rar
-rw-r--r-- 1 cda cda   1018 2007-01-08 16:50 rarfiles.lst
-rw-r--r-- 1 cda cda 872804 2007-01-08 16:50 rar_static
-rw-r--r-- 1 cda cda  70107 2007-01-08 16:50 rar.txt
-rw-r--r-- 1 cda cda   1050 2007-01-08 16:50 readme.txt
-rw-r--r-- 1 cda cda   8957 2007-01-08 16:50 technote.txt
-rw-r--r-- 1 cda cda 196720 2007-01-08 16:50 unrar
-rw-r--r-- 1 cda cda   6018 2007-01-08 16:50 whatsnew.txt
cda@cda-server:~/cda-server/rarlinux-3.7.b1/rar$


---

### Post by taurus on 2007-05-06
Try

```
chmod 755 rar unrar
file rar unrar
```
Post the output of the second command.

---

### Post by fernando_lopes_jr on 2007-05-06
This is the output

> 
cda@cda-server:~/cda-server/rarlinux-3.7.b1/rar$ file rar unrar
rar:   ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), for GNU/Linux 2.6.0, stripped
unrar: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), for GNU/Linux 2.6.0, stripped
cda@cda-server:~/cda-server/rarlinux-3.7.b1/rar$


---

### Post by taurus on 2007-05-06
Just copy them to /usr/local/bin and you can run them anytime.

```
sudo cp rar /usr/local/bin
sudo cp unrar /usr/local/bin
```
Then, log out and back in again.  Now, run

```
unrar
```
and you will see a list of options that you can use with unrar command.

---

### Post by fernando_lopes_jr on 2007-05-06
The rar varsion is still the same it's still not the 3.7 version

> cda@cda-server:~$ unrar

UNRAR 3.51 freeware      Copyright (c) 1993-2005 Alexander Roshal

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
  ow            Save or restore file owner and group
  p[password]   Set password
  p-            Do not query password
  r             Recurse subdirectories
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
cda@cda-server:~$


---

### Post by TheMono on 2007-05-06
Did you uninstall the rar and unrar from the repositories first? You probably have rar and unrar already installed from the repositories, so it is defaulting to them first rather than your new versions.

---

### Post by fernando_lopes_jr on 2007-05-06
No I did not what do I have to do then?

---

### Post by TheMono on 2007-05-06
OK, depending how you installed them in the first place, this should probably work.

Start the synaptic package manager - I use Kubuntu rather than Ubuntu, but I think you can find it in settings -> administration.

Then, search for any package with rar in it.

The ones that are installed have a green box next to them. You want to right click on them, and select "mark for complete removal". Then go apply, and it is done.

---

### Post by taurus on 2007-05-06
Open synaptic and Search for it.  Then, remove it.  

Or try

```
sudo aptitude remove unrar
locate unrar
```

---

### Post by fernando_lopes_jr on 2007-05-06
Still not working :(  one more thing I'am using Ubuntu 6.06 LTS server version sow everything was to be with comands.

---

