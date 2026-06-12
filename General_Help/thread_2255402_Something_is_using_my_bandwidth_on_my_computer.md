---
title: "Something is using my bandwidth on my computer"
date: 2014-12-04
forum: General Help
---

### Post by full-rah on 2014-12-04
So a program or something is using my bandwidth to download (receive).
So my internet seemed a bit sluggish (bear in mind I don't have the best internet). So I randomly checked the "System Monitor tool" 
and I am seeing a constant stream of receiving date. Even if I am not loading anything, even right after a reboot. (see attachment)

Tried looking around the internet if there was a way to isolate it,  with no luck.
Let's hope I find a solution.

*Edit*
Just used Nethogs to see what program was using my bandwidth. Unfortunately with no success.

---

### Post by nerdtron on 2014-12-04
Probably the update manager is working?

Try to use iftop:
```
 sudo apt-get install iftop
```

To use it, run as sudo:
```
 sudo iftop
```

Just leave it running for a few minutes while you see that your internet is in use. Then post the screenshot here.

---

### Post by full-rah on 2014-12-05
So I ran "Iftop" and all I can gather is that it is talking with my router.
I also had a look at my netbook to see if that was also receiving an excessive amount. 
But no, it receives around 40kbs compared to 300 on my main pc.

---

### Post by nerdtron on 2014-12-05
All I'm seeing is the 224.0.0.251 address. What did you do or install before this happened?
[http://stackoverflow.com/questions/12483717/what-is-the-multicast-doing-on-224-0-0-251](http://stackoverflow.com/questions/12483717/what-is-the-multicast-doing-on-224-0-0-251)

---

### Post by full-rah on 2014-12-05
Last thing I did... No idea. The last prog that I may have installed was "Shotwell" which was a couple of months ago.
Apart from that Don't remember installing anything.
Btw I am running 12.04 LTS. Still havent updated to 14.04. (just haven't found the time to...)

---

