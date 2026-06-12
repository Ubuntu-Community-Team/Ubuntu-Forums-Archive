---
title: "Checking .rar files with a .par2 file"
date: 2008-01-02
forum: General Help
---

### Post by Peregrine88 on 2008-01-02
Keep in mind I know very little about anything :)  I'm running Ubuntu 7.10 - the Gutsy Gibbon on a dell Inspiron E1705.

I'm trying to unpack a series of .rar files. Normally I just right click on it and say "extract here". Sometimes that does not work and I open a terminal and use this code to unpack the files.

unrar e -kb "filename.r01"

This seems to force the extraction to take place even when there are some damaged or missing files. There is usually a part of the file I extract that is corrupt but I've dealt with them.

The .rar files I get usually come with parity files and I've seen a friend use a program to repair the .rar archive. He's using windows and I can't seem to find a linux program for it. I know there must be something out there, what should I use? Also any explanation about .rar files and especially parity files would be helpful, I don't really understand what they are and what they're used for. Thanks in advance.

---

### Post by yabbadabbadont on 2008-01-02
par2cmd (or something close to that) is the name of the package you want.  Search for par2 in synaptic.  System->Administration->Synaptic Package Manager.  You may have to go to the Settings->Repositories menu to enable the extra repositories before it will show up.  Then you would run, in a terminal window
```
par2repair filename.par2
``` to validate, and repair if required, your file.

---

### Post by yabbadabbadont on 2008-01-02
By the way, if you use the "x" option with unrar instead of "e", it will recreate the stored directory tree in the rar file (if any).

---

### Post by Peregrine88 on 2008-01-02
It worked perfectly! Thanks a bunch. The program was simply named par2. There are also skins to install for a gui but they normally make things more complicated... Thanks a million!

---

