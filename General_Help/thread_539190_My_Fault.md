---
title: "My Fault"
date: 2007-08-30
forum: General Help
---

### Post by wireddad on 2007-08-30
I mis-spelled something in my xorg.conf.  Now X will not boot.  How can I get to the file from the command line?  Can I?

---

### Post by southernman on 2007-08-30
If your at a root command prompt just do

> nano /etc/fstab

If not, just add "sudo" to the front of the line

---

### Post by strabes on 2007-08-30
He said xorg.conf not fstab. ```
sudo nano /etc/X11/xorg.conf
```

Edit what you need to, then Ctrl+O to save, Ctrl+x to exit.

---

### Post by wireddad on 2007-08-30
Then what?  How do I open/edit the xorg.conf?

---

### Post by southernman on 2007-08-30
> **strabes said:**
> He said xorg.conf not fstab. ```
sudo nano /etc/X11/xorg.conf
```

Edit what you need to, then Ctrl+O to save, Ctrl+x to exit.

Thanks strabes... I was preoccupied and not paying attention very well.

You use the arrow keys to move about in the document to get where you need to edit. Make your edit and do as strabes instructed.

---

### Post by wireddad on 2007-08-30
I'd opened fstab before and tried to type the nano...  but did not save.  Ya think it had messed up anything?

---

### Post by wireddad on 2007-08-30
BTW, thank you.  I can get in X now.  Hopefully did not mess up fstab.

---

### Post by southernman on 2007-08-30
In hindsight, any time you edit a file Ubuntu will auto backup the file. Say you edit the xorg.conf file. Ubuntu will save the file and backup the old one to look like xorg.conf~ and you can verify it's there by doing this at the command line:

> sudo ls -la /etc/X11

If you see both files, now do this:

> sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf

now do 

> sudo shutdown -r now

You should be back to square one again.
sorry for the earlier confusion...

---

### Post by southernman on 2007-08-30
> **wireddad said:**
> I'd opened fstab before and tried to type the nano...  but did not save.  Ya think it had messed up anything?
Should be ok wireddad... sorry again!

zigged instead of zagging!

---

### Post by wireddad on 2007-08-30
> **southernman said:**
> Should be ok wireddad... sorry again!

zigged instead of zagging!

Hey thanks for your help.  I was gonna reload if you had not replied.  You saved me some serious re-customization time. :)

---

