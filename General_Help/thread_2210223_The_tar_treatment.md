---
title: "The tar treatment"
date: 2014-03-09
forum: General Help
---

### Post by Langstracht on 2014-03-09
I have a bunch of pretty big video files ... and I thought I w/could save a fair bit of space by tar-ing and zip-ping them.  So

```
tar cvzf movie.tar.gz 1stmovie.m4v
```

To my astonishment the .qz file is the same size (1.9 Gig) - well a few Mb less - as the original file.

Is this "normal"?  Or have I perhaps missed something?

---

### Post by sudodus on 2014-03-09
Yes it is normal, because those files are already compressed with an efficient method.

You can compare the audio formats wav which I think is not compressed with mp3. It is a factor of 10 or more. The compression is not only loss-less (as with zip, gzip, xz etc), but lossy, using algoritms that try to reduce the size as much as possible at a certain level of quality for the human perception of sounds. Similar methods are used for video.

---

### Post by Langstracht on 2014-03-10
Well so much for that.   Guess, yet another, ext HD is in my immediate future.

That said I never fail to be amazed at how much I don't know.

Thanks for taking the time to respond.

---

### Post by sudodus on 2014-03-10
You are welcome :-)

---

