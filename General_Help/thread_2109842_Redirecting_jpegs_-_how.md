---
title: "Redirecting jpegs - how ?"
date: 2013-01-28
forum: General Help
---

### Post by grey1beard on 2013-01-28
I'm creating a series of jpegs through streamer software using a Terminal command line.
What do I add to the line
> **streamer -o 0000.jpeg -s 300x200 -j 100 -t 2000 -r 1**

in order to get the jpegs redirected to a folder *Capture* on the Desktop ?

John

---

### Post by tgalati4 on 2013-01-28
You could try adding a complete file reference:

streamer -o /home/user/grey1beard/Desktop/Capture/0000.jpeg

or

streamer -o ~/Desktop/Capture/0000.jpeg

Or create a script:

#!/bin/bash
cd ~/Desktop/Capture
streamer -o 0000.jpeg

---

### Post by grey1beard on 2013-01-28
> **tgalati4 said:**
> You could try adding a complete file reference:

streamer -o /home/user/grey1beard/Desktop/Capture/0000.jpeg



Thanks for coming back so quickly. I'm hoping to set it up tonight !

Would that add all the output of streamer to the folder ?

John

---

### Post by grey1beard on 2013-01-28
Yes, I've now got it working so far - had to adjust the address to 
**streamer -o ~/Desktop/Capture/0000.jpeg -s 300x200 -j 100 -t 10 -r 1**

- but they're safely there.

Next job is to find out why I get a time out signal after a few seconds, and it stops !

Regards
John

---

### Post by tgalati4 on 2013-01-28
Can't help you there, I have never used streamer.  Check in /var/log for any log files that may be created.

---

