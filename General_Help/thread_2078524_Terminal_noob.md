---
title: "Terminal noob"
date: 2012-10-31
forum: General Help
---

### Post by 2d2f on 2012-10-31
What am I doing wrong? Why can't I access "Biblioteka" folder?
[[img]http://www.freeimagehosting.net/t/8gowu.jpg[/img]](http://www.freeimagehosting.net/8gowu)

[http://img593.imageshack.us/img593/2994/screenshotfrom201210310e.png](http://img593.imageshack.us/img593/2994/screenshotfrom201210310e.png)

---

### Post by steeldriver on 2012-10-31
Hello and welcome

Your pic is a little bit hard to read but it looks like you have specified an absolute path (which looks for a folder called Biblioteka in the filesystem root directory [COLOR=Red]/[/COLOR] )

```
cd [COLOR=Red]/[/COLOR]Biblioteka
```If you are trying to access a folder in the [COLOR=Red]current[/COLOR] directory then the command would be

```
cd Biblioteka
```

---

### Post by 2d2f on 2012-10-31
thanks! Solved ! :)

---

