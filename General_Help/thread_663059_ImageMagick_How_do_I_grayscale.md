---
title: "ImageMagick: How do I grayscale?"
date: 2008-01-09
forum: General Help
---

### Post by newnet on 2008-01-09
If you are an ImageMagick user, would you please tell me what is the proper way to grayscale?

---

### Post by mcduck on 2008-01-09
```
convert image.jpg -monochrome image-bw.jpg
```
..or if you don't need to keep the original:
```
mogrify -monochrome image.jpg
```

---

### Post by newnet on 2008-01-09
I used the monochrome before, and it literally turns it black and white (JUST black AND white; 2 colors)!  I am looking the command that would convert it to more than just 000000 and FFFFFF.

Is there some combination or condition needed to get a grayscale?

---

### Post by mcduck on 2008-01-10
OK, then try this one: 
```
convert  image.jpg  -colorspace Gray   image-bw.jpg
```
That would consider the color brightnesses as they appear to human eye, so blue wold be darker than red, for  example.

If you want to get the pure mathematical black&white image, use this one instead:
```
convert image.jpg -fx '(r+g+b)/3' image-bw.jpg
```

---

