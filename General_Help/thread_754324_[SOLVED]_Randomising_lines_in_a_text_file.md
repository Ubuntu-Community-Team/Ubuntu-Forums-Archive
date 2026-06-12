---
title: "[SOLVED] Randomising lines in a text file"
date: 2008-04-13
forum: General Help
---

### Post by SegaFan on 2008-04-13
I wasn't sure if I should post this here or in multimedia & video. I have a text file and what I want to do is mix up all the lines so they're in a random order. Is there any easy way to do this (in a text editor or otherwise)?

Here's exactly what I'm trying to do. I have a simple m3u playlist (in the form of a text file with the location of one music file on each line), about 30 tracks long, and I want to create a random playlist with all the tracks in random order. I *could* just use the random function on my music player, but if you do that you will inevitably end up with some tracks being played more than others (at least initially). If the playlist itself was random I could play through all 30 and each track would play exactly once, then I could play them in that same order as many times as I liked until I chose to randomise it again.

---

### Post by pointone on 2008-04-13
A simple Python script can easily accomplish this:

```
#! /usr/bin/env python

import random
import sys

f = open(sys.argv[1], "r")
lines = f.readlines()
f.close()

f = open(sys.argv[1], "w")
while len(lines) > 0:
    f.write(lines.pop(random.randrange(0, len(lines))))
f.close()
```

Make executable and run with "scriptname /path/to/playlist".

---

### Post by SegaFan on 2008-04-13
Right, thanks for that, but I'm a bit of a noob when it comes to this, would you mind explaining in more detail?

---

### Post by pointone on 2008-04-13
Not a problem.

Copy the above code into a text file using gedit or your favourite text editor, and save the file as, for example, "/home/username/randomizer.py".

Next, browse to your home directory in Nautilus (the file manager), right click, select "Properties", and under the "Permissions" tab, select "Allow executing file as program".

Alternatively, open a terminal and type "chmod +x /home/username/randomizer.py".

Now you can run the script as:

```
/home/username/randomizer.py /path/to/your/playlist.m3u
```

If your playlist is already in your home directory, you can simply run:

```
./randomizer.py playlist.m3u
``` 

... while in your home directory.

Make a backup of your playlist first just to ensure things work the way you want them to.

---

### Post by SegaFan on 2008-04-13
Excelent, it works. Thanks a lot. :)

---

### Post by mali2297 on 2008-04-13
A somewhat easier method would be to use the tool **shuf**.
```

shuf oldlist.m3u -o newlist.m3u

```
Unfortunately, this tool has just recently been added to the package coreutils, so you need Hardy (or later).

---

