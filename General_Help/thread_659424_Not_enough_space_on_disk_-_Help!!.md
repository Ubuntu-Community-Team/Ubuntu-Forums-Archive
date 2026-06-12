---
title: "Not enough space on disk - Help!!"
date: 2008-01-05
forum: General Help
---

### Post by tatianam on 2008-01-05
I just found out that I have only 4.6GB of space capacity (im running on ubuntu) - and, obviously, with only a few files I have reached 94.9% of usage. How do I either delete unnecessary files or get more space?

Thanks

---

### Post by taurus on 2008-01-05
You can clean out the cache to give you some more space but you need to start deleting programs that you don't need or files that you have saved to your $HOME.

Applications -> Accessories -> Terminal
```
sudo apt-get clean
df -h
```

---

### Post by tatianam on 2008-01-05
I didn't add any programmes, all I have basically are some Word files and pictures. Are there any programmes that are already on Ubuntu that I don't use and can delete? How so?

---

### Post by taurus on 2008-01-05
Look in your Applications to see which ones you don't need or use.  Then, you can Search for them in synaptic, System -> Administration -> Synaptic Package Manager -> Search, and remove them.  

Or you can remove them from a terminal if you wish, assuming you know the name of the apps.

```
sudo apt-get remove *program*
```

---

### Post by tatianam on 2008-01-05
Thank you!!

---

### Post by jamaisvu on 2008-01-05
[FONT=Franklin Gothic Medium]You can always check that the following files/directories aren't ginormous:

/home/joebloggs/.mozilla/firefox/randomalphanumericnonsense/cache/
/home/joebloggs/.xsession-errors

(And if you're a total control freak, use the file size view of Konqueror (yes, this is a hint to control freaks) to identify anything else unnecessarily massive.)[/FONT]

---

