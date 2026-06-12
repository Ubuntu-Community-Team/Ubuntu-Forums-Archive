---
title: "Is there a way to run bash scripts every time i plug in my camera / phone?"
date: 2007-08-17
forum: General Help
---

### Post by markp1989 on 2007-08-17
Im not sure if this is the right place to make this post, tell me if its in the wrong place

I wrote a small bash script to copy my videos and photos from my phone to a folder in my home directory, and i was wondering if there is a way to make this run automatically every time i plug in my phone?

this is my bash script 

#!/bin/bash
cd /media/MM/mobile/picture
ls *jpg
cp *jpg /home/mark/Pictutres/from_phone

cd /media/MM/mobile/video
ls *3gp
cp *3gp /home/mark/Videos/from_phone
ls -alth

Also i was wondering if there is a way to get some kind of process bar so i know how many photos/Videos are reamaining?...(im nt sure if this is posible or not with bash scripting)

Thanks in advanced.

---

### Post by markp1989 on 2007-08-17
Not to worry i found out how to get it to work:

1, Rename the script to "autorun.sh" and copy it to the root of the removable drive
2.Go system>preferences>Removable Drives and Media
3. Enable the option that says "Auto-run programs on new drives and media" 

every time u plug in the device it will run the script

---

