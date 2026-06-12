---
title: "Any used inkscape software?"
date: 2014-11-26
forum: General Help
---

### Post by afrohippie82 on 2014-11-26
Has anyone used inkscape if so what was your experience?

---

### Post by sudodus on 2014-11-26
I have used Incscape, but not very much. It works, I could do what I wanted and needed (vector graphics).

I used the version, that is installed from the repositories in 12.04.5

---

### Post by afrohippie82 on 2014-11-26
what is the proper forum to find out how to edit a Jepg. logo in inkscape

---

### Post by sudodus on 2014-11-26
Simply enter the following command from a terminal window (where you would use the actual file name instead of test.jpg)

```
inkscape test.jpg
```

Select **Embed image** and save it as an **svg** image.

It will be stored as 'xlink:href="data:image/jpeg;base64' which you will see if you look at the svg file with an editor. If you want to create a truly scalable image, I think you have to create it as vector graphics from the beginning.

-o-

If you want to I can move your thread to the [Art & Design]("http://ubuntuforums.org/forumdisplay.php?f=16") Forum, where you can get more and better advice (at least I think so).

---

