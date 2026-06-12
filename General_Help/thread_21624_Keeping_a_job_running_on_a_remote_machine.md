---
title: "Keeping a job running on a remote machine"
date: 2005-03-23
forum: General Help
---

### Post by Sham on 2005-03-23
Hi all,

I have jobs running on 2 servers in the background, so:

> R CMD BATCH xxx.R &

but I need to log off my machine locally. If I close the terminal down I will kill the jobs. Is there any way of shutting down the local machine without losing my processes?

Cheers

---

### Post by IdoMcFly on 2005-03-23
when I want this I do a ```
nohup <my command>
```

but I don't know how to do this on existing job.

Have a look at man nohup

---

### Post by Sham on 2005-03-23
[QUOTE=IdoMcFly]when I want this I do a ```
nohup <my command>
```

but I don't know how to do this on existing job.

Have a look at man nohup[/QUOTE]


Cheers buddy. There doesn't appear to be much on the man page, but I'll keep plugging away.

---

### Post by chrisw on 2005-03-23
I had forgotten about *nohup* but my trick would be:

(R CMD BATCH xxx.R &)&

this runs stuff in the background and allows me to log off

---

### Post by TjaBBe on 2005-03-23
I have allways used a tool called screen or screens for it (you would pobably have to manually install this). You can open a "new" terminal in your terminal with screen, run your command and exit with a key combination. The screen keeps running after logging of, and you can get it back later with screen -r or something like that.

Anyway, reading above posts I'm afraid my method is a bit not-straight to the point, plus I either don't know if you can use it on an excisting process.

---

### Post by Sham on 2005-03-23
Thanks for all your suggestions guys. In the end I killed the processes, rejigged the code to resume from the saved file, and then nohupped them. All appears to be working well.

Thanks again

---

### Post by MiG on 2005-04-06
If you are using bash as a shell, you can do:

disown -h *jobspec*

to have the child process (your batch job) not be killed when its father (your terminal) is closed.

Hope this helps!

---

