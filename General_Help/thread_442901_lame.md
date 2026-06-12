---
title: "lame"
date: 2007-05-14
forum: General Help
---

### Post by merlinus on 2007-05-14
I need to have a file for audacity called libmp3lame.so in order to export mp3s.

I have downloaded lame-3.97.tar.gz, but do not know what I need to do with it to get that file.  

Many thanks!

-merlin

---

### Post by dunedust on 2007-05-14
Heres a simpler way
 ```

     sudo apt-get install lame
```

once it has installed you will find a the file in
/usr/lib/


note: Audacity will ask for a file named* libmp3lame.so* 
          However the file i found under /usr/lib  was* libmp3lame.so.0*
          But it works just fine.

---

### Post by merlinus on 2007-05-14
I did as you suggested, but cannot find the file in usr/lib.

Perhaps it is different with Ubuntu 7.04?

Thanks.

-merlin

---

### Post by jocko on 2007-05-14
It looks like that file is in the package liblame-dev.

---

### Post by dunedust on 2007-05-14
well try this then 

```
sudo locate libmp3lame.so
```

That should show you where the file is located 
Also if you are searching through audacity enable hidden files and enable  "show  all files" option
I don't think it should be located elsewhere in feisty

---

### Post by zvacet on 2007-05-14
You can find it in synaptic and after install it will be in usr/bin.

---

