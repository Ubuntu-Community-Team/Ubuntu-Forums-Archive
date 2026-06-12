---
title: "I can't boot in to E17"
date: 2007-12-20
forum: General Help
---

### Post by zach12 on 2007-12-20
Hello, 
I've installed E17 with CVS but i can't boot in to E17

I think i the issue is that E17 isn't in the right  folder
 
> [Desktop Entry]
Encoding=UTF-8
Name=E-17
Comment=
Exec=/home/zach/e17_cvs
Icon=
Type=Application


Thanks

---

### Post by worldwithoutgurus on 2007-12-21
Here is my enlightenment.desktop file (install dir is /usr/local)

[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=Beauty at your fingertips
Type=XSession
Icon=
Exec=/usr/local/bin/enlightenment_start
TryExec=/usr/local/bin/enlightenment_start 

If you installed E17 in /opt/e17:

(...)
Exec=/opt/e17/bin/enlightenment_start
TryExec=/opt/e17l/bin/enlightenment_start 

You need to give the full absolute path to the enlightenment_start executable

---

### Post by zach12 on 2007-12-21
Well it looks like i have E17 in 
/home/zach/e17_cvs/e17/
and 
/opt/e17/bin

I've tryed them and they don't work?

---

### Post by PeterJS on 2007-12-21
> **zach12 said:**
> Well it looks like i have E17 in 
/home/zach/e17_cvs/e17/
and 
/opt/e17/bin

I've tryed them and they don't work?

The paths you posted are the folders, but as WorldWithoutGurus said you need to give it the path to enlightenment_start, which should be *in* one of those folders.

---

### Post by Rui Pais on 2007-12-22
Hi,
it looks like you installed using easy_e17.sh script.

I would advise you link to original launcher to avoid issues with any possible change of bin file name:
```
sudo ln -s /opt/e17/share/xsessions/enlightenment.desktop /usr/share/xsessions/enlightenment.desktop

```

Check too if you have /opt/e17/bin on your PATH variable.

---

