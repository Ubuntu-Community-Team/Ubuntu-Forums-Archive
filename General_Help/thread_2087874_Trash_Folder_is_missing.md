---
title: "Trash Folder is missing"
date: 2012-11-24
forum: General Help
---

### Post by BSG Fan on 2012-11-24
I can not find the trasb folder in Ubuntu 11.10
It's the first time this happen.

Where is it?

Any code in the terminal to find it? I tried with the terminal but did not work.

I tried to find it here: : /home/username/.local/share/Trash but It is missing.

---

### Post by llamabr on 2012-11-24
I'd be interested to see what you tried with the terminal.

[https://www.google.com/search?q=ubuntu+show+trash+desktop&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](https://www.google.com/search?q=ubuntu+show+trash+desktop&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by BSG Fan on 2012-11-24
> **llamabr said:**
> I'd be interested to see what you tried with the terminal.

[https://www.google.com/search?q=ubuntu+show+trash+desktop&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](https://www.google.com/search?q=ubuntu+show+trash+desktop&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

In the terminal I tried this: gconf-editor

see the pic
but nothing happens...

---

### Post by stevedude on 2012-11-24
Try typing this in terminal: find `pwd` -iname *Trash* -type d

You may get a few listings especially if a program has a trash feature (ie: Evolution and others). See if *home/username/.local/share/Trash* shows up in that list.

Is this a fresh install of 11.10?

If it is, the trash directory won't be created until you delete your first file. Also that is a hidden location so try CTRL-H to reveal hidden files/folders in Nautilus.

If the above doesn't apply to you, then try installing "Ubuntu Tweak" and under the "Tweaks" tab select "Desktop Icons" and select the Trash Can. Create and/or delete a file to see if that works.  Also recheck "find `pwd` -iname *Trash* -type d"

Lastly, the Trash directory is split into three folders (-expunged - files - info). The files that you see when open the trash are in this "files" directory. If you are now able to see/access that folder, deleting the contents of the files folder sometimes will bring back the icon within Nautilus in some cases.

Good luck

---

### Post by Wim Sturkenboom on 2012-11-24
The trash is in /home/username/.local/share/Trash

```

wim@aa0:~$ tree -f /home/wim/.local/share/Trash
/home/wim/.local/share/Trash
&#9500;&#9472;&#9472; /home/wim/.local/share/Trash/files
&#9492;&#9472;&#9472; /home/wim/.local/share/Trash/info

2 directories, 0 files
wim@aa0:~$ 

```

---

