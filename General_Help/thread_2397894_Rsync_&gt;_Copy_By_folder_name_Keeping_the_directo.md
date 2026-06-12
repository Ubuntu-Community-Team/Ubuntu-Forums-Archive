---
title: "Rsync &gt; Copy By folder name Keeping the directory structure"
date: 2018-08-04
forum: General Help
---

### Post by gnubielearning on 2018-08-04
Okay so i have

/home/user/gnubiedirectory


I want to rsync every change in real time(or every 1 min) thath happens in thath directory to my raspberry.

But i want to copy just folders thath are named "logs" and all the files inside those folders obv.


Also i need to maintain the folder structure. For example

/home/user/gnubiedirectory/ubuntu/random/logs/(9 text files inside)


in my raspberry should copy

gnubiedirectory/ubuntu/random/logs/


i mean, each logs folder in each random named folder inside each ubuntu named folder. just copy logs+what is inside logs but copying all folders thath are above.

---

### Post by TheFu on 2018-08-05
Welcome to  the forums?
Ok.  What have you tried?   
When is the homework due?
[https://www.tecmint.com/rsync-local-remote-file-synchronization-commands/](https://www.tecmint.com/rsync-local-remote-file-synchronization-commands/) should get you started.  Don't forget that rsync supports regex patterns matching anywhere in the source.

---

### Post by oldfred on 2018-08-05
Are you sure you want that much data on a Raspberry pi?
Log files can be very large when an issue occurs and the memory card on a pi is not large.
Or do you have a large drive attached to the pi?

---

### Post by HermanAB on 2018-08-06
Hmm, I have a terabyte of solid state storage on a RPi.

Anyhoo, the rsync man page is quite good and it includes examples at the bottom.  I always get it wrong at first, so the trick is to do a 'dry run' with '-n' before doing the real thing.

---

