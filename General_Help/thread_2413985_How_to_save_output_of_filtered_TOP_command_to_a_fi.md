---
title: "How to save output of filtered TOP command to a file?"
date: 2019-03-04
forum: General Help
---

### Post by suaro on 2019-03-04
Hi Everyone,

I'm running the command below to extract the details of PID 99837 and every 10 seconds it produces a new line.
# top -b -d 10 | awk '/99837/ {print strftime("%Y-%m-%d-%H:%M:%S", systime()), $0}'

 (output ) 
2019-03-04-19:42:52  99837 root      20   0 1422056 354060   7032 S   0.0  2.5  65:39.84 python2.7
2019-03-04-19:43:02  99837 root      20   0 1422056 354060   7032 S   0.4  2.5  65:39.88 python2.7
2019-03-04-19:43:12  99837 root      20   0 1422056 354060   7032 S   0.4  2.5  65:39.92 python2.7
            ...

How can I take this output and send to a file ?
I've tried several ways

(top -b -d 10 | awk '/99837/ {print strftime("%Y-%m-%d-%H:%M:%S", systime()), $0}') >> /tmp/output1.log

top -b -d 10 | awk '/99837/ {print strftime("%Y-%m-%d-%H:%M:%S", systime()), $0}' | tee /tmp/output1.log 

 .... but the output never shows up there. 


Any tips greatly appreciated

---

### Post by TheFu on 2019-03-04
The output is going to stderr, not stdout.  With bash, you can redirect that using **2>$1**

I would do it all differently, using **sar** or **pidstat**. Tools designed for this stuff. For example:
```
$ pidstat -p 3312 10 1000
```
Control of all the available fields is possible too. Check the manpage.

---

### Post by suaro on 2019-03-06
Gotcha!  Thanks so much! Will use pidstat

---

### Post by TheFu on 2019-03-06
Might want to check out "The Art of the Command Line" to filling some knowledge gaps.  I re-learn or get reminded of things whenever I look at it.
[https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) - is has redirection stuff.

If this is solved, please use the "thread tools" button to help out the community.

---

