---
title: "top like tool for disk access?"
date: 2008-05-06
forum: General Help
---

### Post by fadenb on 2008-05-06
Hi.

About 20 to 50 times a day i notice heavy disk access (shown by gkrellm) on my laptop (slowing down everything) while cpu usage is normal. I did not have success trying to identify the process which is causing this.

Is there any top like tool to show me which process is reading on my disk?
I tried lsof but i do not think this kind of output will help me identifying the process.

Thx for any advice!

---

### Post by fadenb on 2008-05-08
*push*

---

### Post by tribaal on 2008-05-08
My personal favorite monitoring tool is "saidar":
```
sudo aptitude install saidar
```
```
saidar -c
```

This shows you machine usage, including disk space/access, paging, network usage etc... all in a single screen.

Hope this helps.

- Trib'

**EDIT:** My bad, I didn't read your post well enough, you want to know *which process* is using your disk most... :( Try "top", then order by (using shift-O) page fault (that's "u"), this can give you an idea, although it's not strictly disk access. Sorting by swapped size can be useful too.

---

### Post by fadenb on 2008-05-08
seems like a nice tool, but does not help me to identify which process is accessing the disk.

thx anyway!

---

### Post by hyper_ch on 2008-05-08
or use htop and sort accordingly

---

### Post by pastuhoff on 2008-11-17
This is a very late reply but today I encountered the same problem. I used "cat /proc/[PID]/io" as a base for a simple python script, just to find what process was chewing on the hard drive. This is the script:

```

#!/usr/bin/env python
import os,time

dic = {}
dRead = 0
dWrite = 0
while True:
    for pid in os.listdir('/proc/'):
        try:
            FILE = open('/proc/'+pid+'/io', 'r')
            lines = FILE.readlines()
            if dic.has_key(pid):
                dRead  = int(lines[4][12:len(lines[4])-1]) - dic[pid][0]
                dWrite = int(lines[5][13:len(lines[5])-1]) - dic[pid][1]
                if not (dRead == 0 and dWrite == 0):
                    print pid, '\t', dRead, '\t', dWrite
            dic[pid] = [int(lines[4][12:len(lines[4])-1]), int(lines[5][13:len(lines[5])-1])]
            FILE.close()
        except:
            pass

    print '-----------------------------------'
    print 'PID\tRead\tWrite'
    time.sleep(0.5)

```

---

