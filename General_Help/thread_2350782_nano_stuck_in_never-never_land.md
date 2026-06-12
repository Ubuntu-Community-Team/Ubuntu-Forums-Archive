---
title: "nano stuck in never-never land"
date: 2017-01-27
forum: General Help
---

### Post by jmill00 on 2017-01-27
I was editing smb.conf via PUTTY when I lost power on the machine I was using PUTTY on. Now when I try to get back into the file it tells me it is currently open by root. I've tried restarting the server, but no luck. 16.04 Server 32bit.

---

### Post by QIII on 2017-01-27
Are you working from a Linux machine?

If so, could you post the exact results of attempting to open the file with nano from the command line?

Thanks.

---

### Post by cariboo on 2017-01-27
Try:

```
ps ax | grep nano
```

The result should look something like this:

```
ps ax | grep nano
14427 pts/1    S+     0:00 nano blame.txt
14457 pts/2    S+     0:00 grep --color=auto nano
```

as you can see the in the first instance I have a file called blame.txt open, and the PID is 14427. If nano is unresponsive kill it using:

```
sudo kill 14427
```

the PID on your system will be different, but the principle is the same.

---

### Post by jmill00 on 2017-01-27
I just tried the method described by cariboo with no success 
here is the message I get when trying to open smb.conf with nano from the main terminal
"file smb.conf is being edited (by root with nano 2.5.3 PID 2169)

---

### Post by jmill00 on 2017-01-28
I don't have any data on this install, so I'll just reinstall.

---

### Post by nothingspecial on 2017-01-28
Did you try ```
 sudo kill 2169
```

---

