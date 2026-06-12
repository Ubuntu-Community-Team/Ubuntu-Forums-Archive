---
title: "Speaker Sound"
date: 2007-08-15
forum: General Help
---

### Post by Desigen on 2007-08-15
Hi, 

I installed Ubuntu 7.04 on my Dell Laptop. When I work in the terminal or Bash Shell and press tab to fill the filename I get a very loud sound coming from the speaker. 

How can I make this sound stop or reduce it. 

Thanks

---

### Post by notwen on 2007-08-15
Is this coming from different terminal application or are you using the same one in both instances of it beeping?  If you're using the default gnome terminal look under your Current Profile settings and there should be an option to disable this.  Post back and let us know if this resolved your issue.

---

### Post by Desigen on 2007-08-15
Hi, thanks for answering. 

I mean the " ALT + CONTROL + F1 .... F6 " terminals 

Also, I will check your suggestion. 

Thanks

---

### Post by notwen on 2007-08-15
Hmm, my real console tty1-6 all have the system beep, but I think you're referring to something other than the system beep.  Maybe someone who works more within the real CLI and no inside a terminal will come along and shed some light on your situation.  Good luck w/ this. =]

---

### Post by Desigen on 2007-08-15
Okay, what should I do? rewrite the post in another forums ??

---

### Post by notwen on 2007-08-16
This seems as good as a sub-forum as any other you may classify this issue as.  I'd simply bump this thread every day or two to keep it from getting 4-5 pages back.  Wish I could have been more help, but lets hope someone more experienced will come along and help your situation out.

---

### Post by techstop on 2007-08-19
I think I can help here. Try;

```
sudo rmmod pcspkr
```

---

### Post by vlado on 2007-08-30
Eventually, to make that beep removal permanent, other users suggested to modify file
/etc/modprobe.d/blacklist
add line to the end saying
blacklist pcspkr

So pc speaker driver will no be loaded after boot and beeping will disappear.
Hopefuly.

---

### Post by Desigen on 2007-09-07
Sorrry for answring lately 

Thanks techstop, it's work very gooooood.

---

