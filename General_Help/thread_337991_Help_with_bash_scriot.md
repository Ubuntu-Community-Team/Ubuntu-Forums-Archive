---
title: "Help with bash scriot"
date: 2007-01-13
forum: General Help
---

### Post by rdoolen on 2007-01-13
I am new to linux and am trying my first bash script. I am trying to run the following script:

#!/bin/bash
 for i in `seq 1 2`;
 do
                echo transcode -i /dev/dvd -x dvd -T 2,$i,1 -a 0 -y mp3 -m test$i.mp3
 done

when I run the script by typing ./filename, I get this for output:

transcode -i /dev/dvd -x dvd -T 2,1,1 -a 0 -y mp3 -m test1.mp3
transcode -i /dev/dvd -x dvd -T 2,2,1 -a 0 -y mp3 -m test2.mp3

This seems like the corect output, but the commands don't run. I must be doing something silly, can someone tell me what?

---

### Post by 23meg on 2007-01-13
Remove the *echo* in front of *transcode*. It will just output the text after it to stdout.

---

### Post by po0f on 2007-01-13
rdoolen,

Remove the 'echo'.  All your script does is print to the terminal what command you want it to run.

---

### Post by Waappu on 2007-01-13
Hi

You have echo command there. Try this ```
transcode -i /dev/dvd -x dvd -T 2,$i,1 -a 0 -y mp3 -m test$i.mp3
```

---

### Post by rdoolen on 2007-01-14
Bingo!!!

Thanks to you all.

---

