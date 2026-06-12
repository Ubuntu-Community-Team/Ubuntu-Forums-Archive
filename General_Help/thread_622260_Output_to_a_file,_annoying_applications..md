---
title: "Output to a file, annoying applications."
date: 2007-11-24
forum: General Help
---

### Post by Rizado on 2007-11-24
Running a command in a terminal using >> usually sends the output to a file but not with all applications.

```
sudo dsniff -i eth0 >> outputLog
```This should write the output to a file called outputLog but for the dsniff applications (msgsnarf etc) it doesn't work, output is still sent to the terminal.

Why is this and what can I do to make it do what I want?

Same thing goes with startx (if I remember correctly), it's extremely annoying.

---

### Post by kidders on 2007-11-26
Hi there,

Strictly speaking, '>' and '>>' only redirect stdout. Perhaps dsniff is sending output to stderr. Try **sudo dsniff -i eth0 2>> outputLog** instead ... just in case.

---

