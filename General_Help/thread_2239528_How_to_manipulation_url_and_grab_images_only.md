---
title: "How to manipulation url and grab images only?"
date: 2014-08-14
forum: General Help
---

### Post by jarwobangun on 2014-08-14
i just create a simulation website that contains images. i try to fetch images only but it doesn't work.

the string that need to be manipulation is. 

***[http://z.mhcdn.net/store/manga/10375/001.0/compressed/o1.07.jpg?v=11325158350](http://z.mhcdn.net/store/manga/10375/001.0/compressed/o1.07.jpg?v=11325158350)***

to be

**[http://z.mhcdn.net/store/manga/10375/001.0/compressed/o1.07.jpg](http://z.mhcdn.net/store/manga/10375/001.0/compressed/o1.07.jpg)**

and fetch images only.

**Wget command**

[I]wget -r -nd -A jpg [http://localhost/website](http://localhost/website)
[/I]
Thank you for reading :)

---

### Post by TheFu on 2014-08-14
Try
```

wget -r -nd -Ajpg http://localhost/website
```
remove the extra space.

---

