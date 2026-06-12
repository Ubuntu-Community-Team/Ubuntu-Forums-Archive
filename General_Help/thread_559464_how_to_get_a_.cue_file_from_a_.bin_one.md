---
title: "how to get a .cue file from a .bin one?"
date: 2007-09-25
forum: General Help
---

### Post by obbe on 2007-09-25
hello, I've a .bin file and i need to create the related .cue, i took a look on internet and i just found an application called acetone iso2 but it seems quite complicate, i was wondering if there is another way to create a .cue file from a .bin. any help? ):P

---

### Post by vanadium on 2007-09-25
I never tried this myself, but it might be possible to mount the iso and then use cdrdao to obtain the toc file. toc2cue can then be used to convert the cdrdao toc to cue format.

---

### Post by fktt on 2007-09-27
yes, but he has a .bin not a .iso, from what i gather..


you can try bchunk search for it in the repos, iirc it was to be found there :)

do note though that it works trough the terminal but its not hard to use, if you look at the help output. :)

for an example what i did to get a .bin into .iso was:

```
 bchunk -r filename.bin > filename.iso 
```

and it did create the iso, havent tested this iso yet though, but i think i actually will right now.. :)

edit: iso didnt work as i didnt specify the fs, DOH!
edit2: got a correct iso on the secon time, no need to use the -r in there, if you have the .cue files then its easy.. :D

---

### Post by vanadium on 2007-09-28
I am not too familiar with all this myself, and I believed a bin could also be mounted. Nevertheless, a search revealed following approach to convert a bin where you do not have the cue: 

[http://paradigma.pt/ja/slog/index.php/2007/06/burn-a-bin-file-in-linux-or-convert-bin-into-iso.html](http://paradigma.pt/ja/slog/index.php/2007/06/burn-a-bin-file-in-linux-or-convert-bin-into-iso.html)

It involves creating a "default" cue then using bchunk indeed to convert to iso.

---

### Post by fktt on 2007-09-29
ooh, thanks vanadium, useful link! =D>

---

