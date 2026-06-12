---
title: "Change Mouse Size (13.04)"
date: 2013-02-14
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-02-14
Where do i report a bug in this, i am not sure which package should file the bug report in
this issue is still present in raring, my mom needs a big mouse cursor
[http://ubuntuforums.org/showthread.php?t=2066945](http://ubuntuforums.org/showthread.php?t=2066945)

in short the mouse keeps the default size for only the main cursor icon when over panels, desktop, and title bars

---

### Post by stinkeye on 2013-02-14
> **pqwoerituytrueiwoq said:**
> Where do i report a bug in this, i am not sure which package should file the bug report in
this issue is still present in raring, my mom needs a big mouse cursor
[http://ubuntuforums.org/showthread.php?t=2066945](http://ubuntuforums.org/showthread.php?t=2066945)

in short the mouse keeps the default size for only the main cursor icon when over panels, desktop, and title bars
[**_[COLOR="DarkRed"]THIS[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12473313&postcount=11") works on my Quantal install.
Was broken in Precise and doesn't work in Raring.

---

### Post by dino99 on 2013-02-14
have you tried:

System Tools -> System Settings ->  Universal Access 

then set your preferences on each tab   ):P):P):P

---

### Post by zika on 2013-02-14
> **stinkeye said:**
> [**_[COLOR="DarkRed"]THIS[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12473313&postcount=11") works on my Quantal install.
Was broken in Precise and doesn't work in Raring.Yes, that works nicely in RR also... Thank You.
Reboot is not needed, just restart ox X or use xrdb...

---

### Post by stinkeye on 2013-02-14
> **zika said:**
> Yes, that works nicely in RR also... Thank You.
Reboot is not needed, just restart ox X or use xrdb...
Doesn't work for me in RR.
Get the same result as **pqwoerituytrueiwoq** describes.

---

### Post by zika on 2013-02-14
> **stinkeye said:**
> Doesn't work for me in RR.
Get the same result as **pqwoerituytrueiwoq** describes.Bummer...
At my place it changes as soon I change value in dconf-editor...
Did You make/edit ~/.Xresources...?

---

### Post by stinkeye on 2013-02-14
> **zika said:**
> Bummer...
At my place it changes as soon I change value in dconf-editor...
Did You make/edit ~/.Xresources...?
Is it consistently the same size?
For me it's inconsistent as it was in 12.04, as if it's not using the ~/.Xresources file.

---

### Post by zika on 2013-02-15
> **stinkeye said:**
> Is it consistently the same size?
For me it's inconsistent as it was in 12.04, as if it's not using the ~/.Xresources file.
Yes, it is consistenly the same size, as far as I saw...
If I change setting in dconf-editor (org.gnome.desktop.interface cursor-size) it changes size even though I did not change ~/.Xresources at that time... It looks like I might do not need ~/.Xresources file at all, I will investigate that as soon I get some spare time...
Update&#8321;: Yes it is consistent and Yes, ~/.Xresources is not necessary...

---

### Post by papibe on 2013-05-01
Thread moved to **General Help**.

---

