---
title: "How to record terminal output log"
date: 2012-12-10
forum: General Help
---

### Post by pellyhawk on 2012-12-10
While logging on some server, I used to use xmanager or secureCRT which both provide feature recording all the output log automatically(Windows platform). Now, I switch to Ubuntu and found cannot record the output log by terminal.

Any suggestion is welcome:)

---

### Post by Sazhen86 on 2012-12-10
There is a command, 'script', that logs all terminal output to a file.  Hope that helps.

---

### Post by CaptainMark on 2012-12-10
or the command 'tee' if you want to direct output for one command onto the terminal and also to a text file or elsewhere

---

### Post by pellyhawk on 2012-12-10
Thanks you all. Would you please list some examples? I them but cannot succeed:confused:.

---

### Post by drmrgd on 2012-12-10
What you are describing looks more like you might want to use 'script' as suggested above.  Have a look at the man page for how it works:

```
man script
```

In short, just run:

```
script -a <file_to_capture_log>
```

When you're done, you can just type 'exit'.

---

