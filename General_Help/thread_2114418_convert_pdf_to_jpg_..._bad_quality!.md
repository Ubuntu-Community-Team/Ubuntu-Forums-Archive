---
title: "convert pdf to jpg ... bad quality!"
date: 2013-02-10
forum: General Help
---

### Post by quickk on 2013-02-10
Hi everyone, 

    I'm trying to convert a pdf image to a jpg.  My file is called "friction_A.pdf."  I read that this should work:

```
convert friction_A.pdf -quality 100 friction_A.jpg 
```

however, when I do this, the resulting image is still of terrible quality.   I've tried playing with the -quality, -geometry, -density tags, but still the jpg is completely useless.   

Here's a before/after example produced with the following command:
```
convert friction_A.pdf -quality 100 -geometry 300 -density 300 friction_A.jpg

```

Before:
[IMG]http://s9.postimage.org/qp9j51fzz/friction_A_page_1.jpg[/IMG]

After:
[IMG]http://s9.postimage.org/lbfcb8fnj/friction_A.jpg[/IMG]

What's wrong?

---

### Post by meteorrock on 2013-02-10
I use an online converter to convert images online. Here is one of my favorites. There are different online image converters you can use that might up the quality on your picture. It does .pdf and has online tools to sharpen up that image.

[http://image.online-convert.com/convert-to-jpg](http://image.online-convert.com/convert-to-jpg)

---

### Post by sudodus on 2013-02-10
Obviously ***convert*** imports the pdf file with low resolution. It can probably be changed, but I don't know how.

When I try with ***gimp*** I can get higher resolution. Try

```
gimp friction_A.pdf
```

---

### Post by quickk on 2013-02-10
Thank you for the replies everyone.   I spent another 45 minutes searching the internet and found that you have to be careful with the order of options.   Basically, the file names should be last otherwise the quality options seem to be ignored!

**Good:**
```
convert -quality 100 -geometry 300 -density 300 friction_A.pdf friction_A.jpg
```

[B]
Bad:[/B]
```
convert friction_A.pdf -quality 100 -geometry 300 -density 300 friction_A.jpg
```

---

### Post by sudodus on 2013-02-10
Congratulations :KS

And thanks for sharing your result with the Ubuntu Forums :-)

---

