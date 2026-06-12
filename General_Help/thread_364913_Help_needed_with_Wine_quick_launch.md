---
title: "Help needed with Wine quick launch"
date: 2007-02-18
forum: General Help
---

### Post by kamaboko on 2007-02-18
Hello,

I just installed Wine and will be using it with SwishMax.  I've tried to create a quick launch from the control panel, w/o any luck.  Swish was installed to the following:

/home/username/.wine/drive_c/program files/swishmax/swishmax.exe

I also have a swishmax.lnk on my desktop, but honestly have no idea why it's there.  

So...how do I create a link that will fire up Wine and SwishMax?

Thanks,
K

---

### Post by erwinquita on 2007-02-18
> **kamaboko said:**
> Hello,

I just installed Wine and will be using it with SwishMax.  I've tried to create a quick launch from the control panel, w/o any luck.  Swish was installed to the following:

/home/username/.wine/drive_c/program files/swishmax/swishmax.exe

I also have a swishmax.lnk on my desktop, but honestly have no idea why it's there.  

So...how do I create a link that will fire up Wine and SwishMax?

Thanks,
K

You can create a launcher

type: application
Name: SwishMax
Command: wine "/home/winter/.wine/drive_c/Program Files/swishmax/swishmax.exe"
Comment: anything you want to say...

Note: the directory is case sensitive so just make it sure you have the right case for the swishmax directory.

Hope this helps.

---

### Post by WW on 2007-02-18
Be sure you use capital letters correctly, and be sure to either put a backslash in front of any spaces in the file name, or put the file name in quotes.

I think this is the command that you want for your launcher:
> wine /home/username/.wine/drive_c/Program\ Files/swishmax/swishmax.exe
(If swishmax is actually SwishMax, change the file name to match.)

Edit: Or you can follow the advice of erwinquita, who is much faster than me :)

---

### Post by kamaboko on 2007-02-18
thanks.  i tried EVERYTHING except the bloody quotation marks.  lol.

---

