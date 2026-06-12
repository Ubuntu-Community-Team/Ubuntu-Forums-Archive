---
title: "Mass rename of files replacing '_' with space"
date: 2006-08-31
forum: General Help
---

### Post by jessexoc on 2006-08-31
How do you mass rename files from the command line? I have a bunch of mp3's with filenames like:
Artist_-_Album_-_TrackNumber_-_Track_name.mp3

I want to convert all the "_"(underscore) to " "(space). I tried:
$ for i in *; do mv "$i" `echo $i | tr '_' ' '`; done

but it complains that:
mv: target `name.mp3' is not a directory.

What am i doing wrong?

---

### Post by pyros on 2006-08-31
dunno... maybe an escape character (\) before the space?

---

### Post by jessexoc on 2006-08-31
I tried that and got the same error.

---

### Post by ayoli on 2006-08-31
works with double quotes:
```
[09:03:54@ayoli.zone]:~/test >$ touch artist_-_trak_name.mp3
[09:04:24@ayoli.zone]:~/test >$ for i in *; do mv "$i" [COLOR="Red"]"[/COLOR]`echo $i | tr '_' ' '`[COLOR="Red"]"[/COLOR]; done
[09:06:01@ayoli.zone]:~/test >$ ls
artist - trak name.mp3
```

---

### Post by yota on 2006-08-31
Hi,

just:
```

rename 's/_/ /' *.mp3

```

should do it.
Hope this helps!

---

### Post by ayoli on 2006-08-31
> **yota said:**
> Hi,

just:
```

rename 's/_/ /' *.mp3

```

should do it.
Hope this helps!

won't work, it takes only the frst '_' :
```
[09:31:11@ayoli.zone]:~/test >$ touch artist_-_trak_name_2.mp3
[11:01:59@ayoli.zone]:~/test >$ rename 's/_/ /' *.mp3
[11:02:32@ayoli.zone]:~/test >$ ls
artist -_trak_name_2.mp3
```

---

### Post by yota on 2006-08-31
Oh, you're right:
```

rename 's/_/ /g' *.mp3

```
will replace every occurrence of _

---

### Post by ayoli on 2006-08-31
btw, i just wanted to point the error in jessexoc script (missing double quotes), but in fact i agree that rename used with sed is more efficient in this case.
regards.

---

