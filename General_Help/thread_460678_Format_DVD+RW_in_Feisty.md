---
title: "Format DVD+RW in Feisty?"
date: 2007-05-31
forum: General Help
---

### Post by PilotJLR on 2007-05-31
Hello all,
I've been unable to format a used DVD+RW disc in Feisty (though this has worked on previous ubuntus and fedoras).
I have a disc now that is in Restricted Overwrite mode; it was burned by K3b under Edgy about 6 months ago.

Both k3b and Gnomebaker are unable to format the disc; simply trying to write onto it using K3b also fails.

So... at a terminal, I tried:
```

sudo dvd+rw-format -blank /dev/dvdrw

```
and then
```

sudo dvd+rw-format -force /dev/dvdrw

```

And both had the same error:
```

4.7GB DVD-RW media in Restricted Overwrite mode detected.
formatting 0.0 |:- [PERFORM OPC failed with SK=2h/ASC=30h/ACQ=11h]: Wrong medium type

```


My googling is unsuccessful so far... any ideas?!?

---

### Post by phidia on 2007-05-31
Take a look at the thread from the following link [http://forum.freespire.org/archive/index.php/t-2118.html](http://forum.freespire.org/archive/index.php/t-2118.html)
It seems to apply to your situation.

---

### Post by PilotJLR on 2007-06-01
Thanks for the reply, but this unfortunately didn't work... I tried manually umounting media, also tried running k3b as root, also tried rebooting too.

---

### Post by db260179 on 2007-06-07
You could try and upgrade your firmware of your drive.

This solved my problem on my sony dvdrw drive.

---

