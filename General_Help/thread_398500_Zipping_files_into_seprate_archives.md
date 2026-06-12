---
title: "Zipping files into seprate archives"
date: 2007-04-01
forum: General Help
---

### Post by evilgold on 2007-04-01
I have a VERY large amount of ROMS for old game systems from N64 on back. I'm talking large as in thousands if not hundreds of thousands of files. Currently they take up near 100gb of space. However most of them are uncompressed (all except mame actually), which means that they take up about 2x as much space as they could if they where in zip files. Since almost every emulator out there supports reading roms if they are in individual zip files, I'd like to go that route and compress each rom into a separate zip file. 

So aside from typing in 1,000s of file names one at a time, how can i instruct zip to compress every file in a directory to a separate .zip file. If at all possible i'd like to use the command line, just for simplicity. But if not, then are there any GUI front ends that can do such a thing?

---

### Post by djrosen on 2007-04-01
This should do it for you

$ for x in `ls /path/to/roms/`;do zip "$x" "$x";done

note the backticks around the ls command, they are not quotes.

I tested this in a small folder and it seemed to work fine. Do test a few zips before you go and delete the orignal files.

---

### Post by evilgold on 2007-04-01
I think what i need. But it seems to not work because the filenames contain spaces, It tries to zip each word instead, how can i get around this?

Thank you very much for your help.

---

