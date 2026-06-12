---
title: "Create ISO file From Hard Drive"
date: 2007-02-23
forum: General Help
---

### Post by killerkhatiby009 on 2007-02-23
Alright so i have some video files on my computer and i would like to put them into an .iso file so that i can burn them to a dvd. How can i do that in Ubuntu Edgy without using terminal, is there a program to do it like in windows. Because right now i have to switch to my windows dual boot create the iso then switch back and burn it in ubuntu i would like to do it all in ubuntu. Any help is appreciated, thanks. BTW im a complete noob to linux and all that so if you could please explain things very well.

---

### Post by po0f on 2007-02-23
killerkhatiby009,

```
[font="Courier New"]$ mkisofs /path/to/direcorty/with/movies -o my.iso[/font]
```

Why don't you try just burning a data DVD?  There's no need to create an ISO just to burn data.

[EDIT]

Forgot to specify output.

---

### Post by killerkhatiby009 on 2007-02-23
I thought that if i did data it would not work well with my dvd player? i thought that somehow burning an .iso would make it play better, but i dont know i just read that somewhere i think. So your saying if i just burn it as a Data DVD using K3b it should work fine to play in a dvd player?

---

### Post by ramjet_1953 on 2007-02-23
Why not try qdvdauthor?

Regards,
Roger :cool:

---

### Post by po0f on 2007-02-24
killerkhatiby009,

As hinted in the above post, you'll have to author a DVD to play it in a DVD player.  I don't have any experience authoring DVDs, but there are a couple HOWTOs in the [Tutorials & Tips](http://ubuntuforums.org/forumdisplay.php?f=100) forum.

You might be lucky and can just burn MPGs to DVD as a data DVD and have your player recognize them.  I've come across a couple DVD players that behaved like this.

---

