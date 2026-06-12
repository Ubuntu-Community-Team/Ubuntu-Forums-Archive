---
title: "Firestarter Priv. Problems."
date: 2005-05-27
forum: General Help
---

### Post by dmccarney on 2005-05-27
Hello,

I'm not too sure if a solution to this has been posted before but I did a quick search fo firestarter in this sub-forum and couldn't find one. Anyway, my problem is that when I restart my ubuntu box I get an error when Firestarter attempts to load about needing root privileges to run.

Of course I can start it again manually after the boot process has finished with sudo but I was wondering if their is a secure and safe way to get it to start with those sudo privliges automatically.

I believe I may have to do some hack and slash with visudo but I'm not quite sure how to go about it and it seems like that file is very important so I'd prefer to not totally FUBAR it up. 

Thanks for any and all help

---

### Post by bored2k on 2005-05-27
1) Tip 1: edit your file with gedit:
```
export EDITOR=gedit && sudo visudo
```

2) [http://www.ubuntuforums.org/showthread.php?t=26483&highlight=firestarter](http://www.ubuntuforums.org/showthread.php?t=26483&highlight=firestarter)

---

