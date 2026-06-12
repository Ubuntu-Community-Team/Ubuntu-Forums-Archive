---
title: "ddrescue on Ubuntu Rescue Remix working?"
date: 2014-11-02
forum: General Help
---

### Post by don28 on 2014-11-02
Hello,  I'm using ddrescue to clone a 1Tb drive and I'm not sure if it's working or, if it is, how long it will take.  Below is a screen shot:
[ATTACH=CONFIG]257699[/ATTACH]

Is ddrescue running OK?  How long do you think it will take to finish cloning?  

Thanks in advance for your consideration and help!!

---

### Post by don28 on 2014-11-04
'Sorry for my newbie question, but can anyone help?

---

### Post by sudodus on 2014-11-04
I'll try. I have used ddrescue and it has worked for me. I used the info page (which is better than the man page)

```
info ddrescue
```

The small tutorial with examples is good. I'll have a look at your attached picture and come back ...

---

### Post by sudodus on 2014-11-04
If you are booting from a third drive (and write the log file to a directory in that drive), it looks good (like the first step of Example 1.)

It can take several hours, depending on the drive size and the copying speed. The second step can take different amount of time, depending on how many bad or almost bad sectors there are, that must be read and re-read trying to rescue as much data as possible.

---

