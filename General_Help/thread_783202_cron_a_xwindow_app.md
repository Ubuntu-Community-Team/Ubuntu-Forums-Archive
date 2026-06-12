---
title: "cron a xwindow app"
date: 2008-05-05
forum: General Help
---

### Post by JayeD on 2008-05-05
I'm having a bit of trouble with starting an app that has a GUI using cron. I've tried things like:

* * * * * DISPLAY=:0.0 /usr/bin/transmission > o.txt

and nothing happens. I've tried using --display, I've tried it with xmessage too but get nothing. I've tried using a script but get nothing.

The path to transmission is correct since

* * * * * DISPLAY=:0.0 /usr/bin/transmission --help > o.txt

output the help text to o.txt

What am I doing wrong?

---

### Post by FuturePilot on 2008-05-05
Try starting it with
```
export DISPLAY=:0 && /usr/bin/transmission > /home/<USER>/o.txt
```

---

### Post by JayeD on 2008-05-05
> **FuturePilot said:**
> Try starting it with
```
export DISPLAY=:0 && /usr/bin/transmission > /home/<USER>/o.txt
```

In the crontab or in terminal?

The bit on the right of the arrow is fine. That file is created. The problem is that transmission doesn't open.

I've just tried this and it's no different. The o.txt file is created but I don't get transmission started. I'm using o.txt as a debug file really. Unfortunately it stays empty when transmission doesn't work. I don't get an error message.

---

### Post by JayeD on 2008-05-05
[This thread](http://ubuntuforums.org/showthread.php?t=105250&page=2) helped me.

I typed in "xhost local:my_name" and it fixed it.

6 months in and linux is getting better all the time :D

---

