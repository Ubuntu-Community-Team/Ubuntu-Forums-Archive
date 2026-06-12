---
title: "Need My Files..."
date: 2007-09-12
forum: General Help
---

### Post by pyromike3000 on 2007-09-12
Background:

I recently reinstalled Windows XP Professional on my computer.  Unfortunately, I accidentally disabled my graphics card (from within Windows) and now am presented with a black screen every time I boot in Windows.  Even more regrettably, I have files that I desperately need on my hard drive, but  I can't see anything in Windows.

Question:

Is it possible to use Ubuntu to recover my files and, if so, how?

---

### Post by merlinus on 2007-09-12
Mount your windows partition from ubuntu.  If it is NTFS, you may have to install the ntfs-3g driver.

If you do not know how to do this, then post output of these commands in a terminal:

```

sudo fdisk -l
cat /etc/fstab

```

---

### Post by Shazaam on 2007-09-12
Do you have  Ubuntu livecd? If you do you can use it to mount the Windows drive and get your files.
Can you boot Windows in Safe Mode? That might let you get in to change Device Manager.

---

### Post by tyggna1 on 2007-09-12
For the non-Linux oriented user--yes, you can, I had to do so myself.

Since you're a windows user, I'll assume that you prefer using the windows/graphical interface.

From windows, press F8 on boot-up and select "safe mode with command prompt."

When the command prompt comes up, simply type in
```
chkdsk /f
```

and reboot your computer twice--that will make sure installing something on Linux won't damage any of your files.

Then install from the live CD--setting a bare minimum of 500MB for a "swap" partition (150% the size of your RAM is optimal), and then make your primary partition:
The size of all the files you want to save +2 GB minimum (10 GB is preferred).

Resize your partition and install Ubuntu from the live-CD under those constraints.

Once it's up, make sure you have an internet connection (wired is preferred), and click on the "applications" menu, and then click, "Add/remove programs"
From that search bar type in NTFS --> and you'll find a program called "NTFS configuration tool."
Click the box next to that, and then click "ok"
It will install that program, and then click on Applications -> system tools -> NTFS configuration tool.  Select both options and then click "ok"

Now you'll be able to browse your windows partition.  It'll have the same name as in windows.  All you have to do now is drag and drop the files from the windows partition to somewhere in your "home" folder (found under places).  That'll back up everything you'd want to in Linux--but you may want to try using it for more than just that :)

---

### Post by pyromike3000 on 2007-09-12
Hooray!

Thanks for the replies.  And I love the quote:

"The best part of waking up is Ubuntu booting up."

---

