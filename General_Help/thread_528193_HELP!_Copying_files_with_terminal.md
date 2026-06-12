---
title: "HELP! Copying files with terminal"
date: 2007-08-17
forum: General Help
---

### Post by SmartRoss on 2007-08-17
HELP!

I am trying to copy a file into my mounted hard drive (hda1). Does anyone have any idea how to go about doing this with terminal? I have tried

```
sudo cp /home/Desktop/vcssetup.exe /media/hda1/Documents and Settings/<my_username>/My Documents/Downloads/
```

and that hasn't worked. Any ideas?

---

### Post by Seisen on 2007-08-17
What kind of errors are you getting?

---

### Post by merlinus on 2007-08-17
Do not believe you can use spaces in folder and filenames in a terminal.

Look at output of dir for /media/hda1.

Probably:

Documents\ and\ Settings

-merlin

---

### Post by ajgreeny on 2007-08-17
Or just put the whole of the location in hda1 in quotes.
"/media/hda1/Documents and Settings/<my_username>/My Documents/Downloads/"
 Presumably you are trying to do this into a fat32 windows partition, or a ntfs partition with the appropriate ntfs tools available.  The ntfs tools needed are in feisty by default, but not, I think in earlier versions of ubuntu.

---

### Post by kerry_s on 2007-08-17
You can always make it easy & use "mc".
sudo apt-update
sudo apt-get install mc

type> mc
or
sudo mc <if you need root

---

### Post by SmartRoss on 2007-08-18
Can you tell me how to use mc? I can't work it out.

Edit: I need to be able to access read only files.

---

### Post by kerry_s on 2007-08-20
> **SmartRoss said:**
> Can you tell me how to use mc? I can't work it out.

Edit: I need to be able to access read only files.

okay, on the left side move to the folder that has what you want to copy(arrow up & down keys, enter to go into folders) tab key, to get to the right side and go where you want to copy to, then tab back to the left and move to what you want copied and press F5 for copy. the bottom of mc shows you what the short cut key is F1->F10

[http://linuxgazette.net/issue23/wkndmech_dec97/mc_article.html](http://linuxgazette.net/issue23/wkndmech_dec97/mc_article.html)

---

