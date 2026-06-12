---
title: "firefox collapses when using facebook"
date: 2022-05-28
forum: General Help
---

### Post by ronjjjg8885 on 2022-05-28
my firefox has a weird behavior.

very often when i use facebook in a private window my whole firefox collapses at once without any message shown.....

is there a log file that can show what happens? can you assist?

it's very annoying as you can guess..

tnx in advance

---

### Post by Holger_Gehrke on 2022-05-28
Have you tried starting Firefox from a terminal ? Programs that crash usually send some information to standard output ...

Holger

---

### Post by ronjjjg8885 on 2022-05-29
i guess i can start it from the terminal but i don't know how to do the rest.....
and also it is not always happens when using facebook in private mode

---

### Post by ronjjjg8885 on 2022-05-30
update

it's not only in private mode
and it's not only when using facebook

---

### Post by exploder on 2022-05-30
Are you using Wayland? I had the exact same problem! Switched the session to X11 and no more crashes.

---

### Post by ronjjjg8885 on 2022-06-03
tnx
i will try to figure out how to switch to x11.
is that the window manager or something?

---

### Post by ronjjjg8885 on 2022-06-03
did the switch from the login page.

i hope it will solve it.

will have to check for a few days.

the problem is so much annoying..

---

### Post by ronjjjg8885 on 2022-06-08
happened again today......

---

### Post by yancek on 2022-06-08
When you open firefox from a terminal, you should see some output after it closes or crashes, check that first.  There are numerous log files in /var/log which you could check,  Not sure which one would be best to check but you might take a look at the log files in that directory.

---

### Post by ronjjjg8885 on 2022-06-18
i see
for now it's ok
if there is a need i will update you

---

### Post by mIk3_08 on 2022-06-18
> **ronjjjg8885 said:**
> happened again today......

> **ronjjjg8885 said:**
> i see
for now it's ok
if there is a need i will update you
If the issue persist then do the following below. 
Please run the script below and post the information or pastebin link in this thread. Regards and cheers.
```
https://github.com/UbuntuForums/system-info
```

---

### Post by ronjjjg8885 on 2022-06-23
hasn't happened for a while

---

### Post by kurt18947 on 2022-06-23
There is an add-on for Firefox that runs Facebook in a container (I think). I don't know if that would help your problem or not but it may be a way to contain Facebook's 'curiosity'.

---

