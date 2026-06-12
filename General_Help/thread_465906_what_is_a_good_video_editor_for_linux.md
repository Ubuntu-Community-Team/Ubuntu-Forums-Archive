---
title: "what is a good video editor for linux"
date: 2007-06-06
forum: General Help
---

### Post by kdarkentity on 2007-06-06
i need a video editor for linux that is good ...or i need a video editing program from windows that will run in wine

---

### Post by kelvin spratt on 2007-06-06
try Cinelerra  this site gives an overview of it, mainactor is no longer supported
[http://flavor8.com/index.php/category/scitech/software/video-production/](http://flavor8.com/index.php/category/scitech/software/video-production/)   i use Cinelerra its daunting at first but quite good when you start using it and is free. I spent a lot of time installing Cinelerra so i wrote down step by step instruction for myself to follow and posted to threads on how i installed Cinelerra
[http://ubuntuforums.org/showthread.php?t=464223](http://ubuntuforums.org/showthread.php?t=464223)
[http://ubuntuforums.org/showthread.php?t=463275](http://ubuntuforums.org/showthread.php?t=463275)
i cant guaranty this will work for other people but certainly works for me

---

### Post by eggdeng on 2007-06-06
For basic dv capture and export to mpeg or dvd, kino is eas to use and does an excellent job.```
sudo apt-get install kino
```

---

### Post by scott_g on 2007-06-06
I second the kino/cinelerra combination; works really well.

Here are some steps for installing cinelerra (worked like a charm for me):

    > 1. Make sure you have universe, multiverse and restricted repositories enabled
    2. Add the following repository to your sources.list file, according to your CPU type:

    - i686:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./
    - athlonxp:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/) ./
    - pentium4:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./

    3. apt-get update ; apt-get install cinelerra 

(from [http://www.kiberpipa.org/~gandalf/blog/?p=77](http://www.kiberpipa.org/~gandalf/blog/?p=77)).

Scott

---

