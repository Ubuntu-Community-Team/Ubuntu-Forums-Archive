---
title: "Can't play .wma files with audacious"
date: 2007-10-25
forum: General Help
---

### Post by peromalosutra on 2007-10-25
I'm using ubuntu 7.10. I installed audacious, but it now can't play .wma files (mp3 works ok), altough i installed all codecs, as well as ubuntu-restricted-extras. On ubuntu 6.10 it all worked ok,

when i start audacious from terminal and drag and drop .wma file into it it puts the folowing error in the terminal:
```

ivan@ivan-desktop:~$ audacious
du: cannot access `file:///media/hda5/My%20Documents/My%20Music/S.O.A.D/Toxicity/07%20Track%207.wma': No such file or directory

```
Btw, i can play .wma files normaly with bulit in movie player.

Any suggestions?

---

### Post by peromalosutra on 2007-10-25
Anyone? I really don't know what's the issue here :S I have all the codecs required.. Or maby i don't? As I said, movie player plays wma without a problem, but I would like to use audacious becouse of bether sound..

---

### Post by gcrussell1 on 2007-10-27
Bumping this . . . I'm having the same problem trying to run WMA's on Audacious. I've got about 10 gigs of WMA's, and I don't really want to bother switching them over to mp3 . . . not to mention that I've always gotten better audio quality with WMA's of the same size as mp3's.

Anyone have this working? I'm assuming the answer is yes, or there would be more threads like this one floating around, but a quick search shows that that's not the case. I would really appreciate the help, and I'm certain that peromalosutra would as well. Any help or points in the right direction would be fantastic.

---

### Post by lanchongzi on 2007-11-15
you can try this

[http://rpm.pbone.net/index.php3/stat/4/idpl/5370951/com/audacious-input-wma-1.4.0-2.i486.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/5370951/com/audacious-input-wma-1.4.0-2.i486.rpm.html)

and if it works tell me how to install a rpm :)
cause i don't know - yet - but having the same issue on 7.04, but it is late now so I will go to bed
will have look at this tomorrow

good luck

:guitar:

---

### Post by JonasLJ on 2007-11-26
I had the same problem, but then I removed the package audacious-plugins-ugly, and then it worked. There are still a few .wma-files audacious won't play, but I think it has something to do with some weird filenames and that they are on a drive using fat.

---

### Post by Ditbenik on 2007-12-06
I had the same problem, but I found somewhere that Audacious uses Mplayer to play wma and other files, so I installed Mplayer and that works

---

### Post by radiobuzzer on 2008-02-05
Ok. This solved the problem. But still doesn't work sometimes. This happens when...

the path or the filename contains non-standard ASCII characters. (eg Greek Unicode characters). Mp3s play fine, just WMA has this problem

---

