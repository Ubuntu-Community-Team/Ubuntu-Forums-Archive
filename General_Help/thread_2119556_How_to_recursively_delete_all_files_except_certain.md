---
title: "How to recursively delete all files except certain types?"
date: 2013-02-24
forum: General Help
---

### Post by acrocephalus on 2013-02-24
Hello,
I know this may have been posted many times, but I'm a little bit lost with bash and any help will be much appreciated. I have thousands of files in the /Music directory and its subdirectories. How can I recursively delete everything which isn't and mp3 or flac file? I'd like to get rid of anything which isn't and mp3 or flac file
Thank you so much!

Dani

---

### Post by matt_symes on 2013-02-24
Hi

Use find.

```
find . -type f  \( -not -iname "*.mp3" -not -iname "*.flac" \) -exec rm {} \;
```

Test it first though using echo.

```
find . -type f  \( -not -iname "*.mp3" -not -iname "*.flac" \) -exec echo {} \;
```

Kind regards

---

### Post by acrocephalus on 2013-02-25
Thanks Matt. I run the code and it worked perfectly.
Cheers,

Dani

---

### Post by matt_symes on 2013-02-25
Hi

No problem. I'm glad it's fixed for you.

I just thought i would mention that find does have a --delete option and a --deletedir option but at the start it always best to check by  -exec echo {}  the file the filter has found.

That way you can see if your command is correct.

Kind regards

---

