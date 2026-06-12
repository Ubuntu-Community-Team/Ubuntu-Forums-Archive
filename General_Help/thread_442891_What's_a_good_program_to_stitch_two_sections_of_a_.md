---
title: "What's a good program to stitch two sections of a movie together?"
date: 2007-05-14
forum: General Help
---

### Post by rainwalker on 2007-05-14
I have two halves of a movie that I want to combine into one film, but I don't know what I should use to do it. I know I can use Audacity for sound files, but is there a good movie editing program for Linux?

---

### Post by 454redhawk on 2007-05-14
> **rainwalker said:**
> I have two halves of a movie that I want to combine into one film, but I don't know what I should use to do it. I know I can use Audacity for sound files, but is there a good movie editing program for Linux?


What format is the movie in?

DVD, AVI, FLASH....?

---

### Post by rainwalker on 2007-05-14
They're .avi files

---

### Post by aysiu on 2007-05-14
You could try *kino* or *mpgtx*.

This page may also help:
[http://linuxappfinder.com/multimedia/videoeditors](http://linuxappfinder.com/multimedia/videoeditors)

---

### Post by 454redhawk on 2007-05-14
You can install transcode and use avimerge -i file1 file2  -o one_big_movie.avi

or

mencoder -oac copy -ovc copy file1 file2 -o one_big_movie.avi

---

### Post by fragos on 2007-05-14
pitivi works well for me and it even is a flash .flv player.

---

### Post by hessiess on 2007-05-14
blender has a secwence editor for joining stiles into a film, dont see why you carnt use it to join 2 bits of film together

---

### Post by rainwalker on 2007-05-14
Okay, thanks everyone, I'll check those out  :)

---

### Post by rainwalker on 2007-05-15
Okay, so Kino looks like exactly what I need, but it's not loading the .avi files correctly. When I try to open them, it says:
> This is not a DV file. Do you want to import it?
and if I choose "OK" then it says 
> The playlist is empty and the default preferences for video creation have not been specified - aborting.
with the only option being to clik "OK".

Any Ideas?

---

### Post by altonbr on 2008-01-08
What about using mencoder to do this? Kino and all the other video editors will more than likely convert them into their own format, where as with mencoder, you might be able to literally stitch them together...

I don't know how, but I'd sure be interested in learning...

---

### Post by altonbr on 2008-01-08
joining two files together via mencoder: [http://ubuntuforums.org/showthread.php?t=337234](http://ubuntuforums.org/showthread.php?t=337234)

---

### Post by ~LoKe on 2008-01-08
Easy.

```
sudo apt-get install mencoder
```
```
cat file1.avi file2.avi > complete.avi
mencoder -o complete.avi -noidx -oac pcm -ovc copy resynced.avi
```

**resynced.avi** will be your complete file.

If that produces audio/video sync problems, try this instead:
```
avimerge -c -o output.avi -i file1.avi file2.avi
```

---

### Post by fragos on 2008-01-08
I've had good luck with a GUI package called "Lives".  It let's me use what ever formats I want.  It even saves and loads animated gifs.  I even started with a single jpeg image and created an animated sequence simulating an explosion.  The latest deb is at [http://www.getdeb.net/](http://www.getdeb.net/).  There is also a GUI frontend for mencoder, gmencoder, that makes mencoder much easier to use.

---

### Post by altonbr on 2008-01-08
> **~LoKe said:**
> Easy.

```
sudo apt-get install mencoder
```
```
cat file1.avi file2.avi > complete.avi
mencoder -o complete.avi -noidx -oac pcm -ovc copy resynced.avi
```

**resynced.avi** will be your complete file.

If that produces audio/video sync problems, try this instead:
```
avimerge -c -o output.avi -i file1.avi file2.avi
```

That thread said it was easy as:
```
mencoder -forceidx -ovc copy -oac copy -o output.avi fragment1.avi fragment2.avi
```

---

