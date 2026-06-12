---
title: "Can't send file Via bluetooth, Phone not found"
date: 2007-09-21
forum: General Help
---

### Post by BeastlyKings on 2007-09-21
Hello, I can send files from my phone to my computer but if I try to send the other direction, my phone is not found.
I can do "hcitool scan" in  a terminal and my phone is found there.


tom@tom:~$ hcitool scan
Scanning ...
        00:16:B8:26:CF:F8        BeastlyKings
tom@tom:~$ 


Is there any way that I can use my phones address to send the file directly to my phone?


Please help?

Original link
[http://ubuntuforums.org/showthread.php?t=94713&page=7](http://ubuntuforums.org/showthread.php?t=94713&page=7)

---

### Post by por100pre1 on 2007-09-23
Try using gnome-obex-server (I'm assuming you're using Gnome, let me know if you use KDE):

```
gnome-obex-send -d 00:16:B8:26:CF:F8 *a-file*
```

Sorry for the delay...

---

### Post by BeastlyKings on 2007-09-25
Oh thank you so very much!
It works now!
For some reason though I had to remove the "a-file" part becuase Ubuntu kept saying "File "a-file" not found.

But it definetly works now, thanks again!

Any idea as to why it didn't work before?

---

