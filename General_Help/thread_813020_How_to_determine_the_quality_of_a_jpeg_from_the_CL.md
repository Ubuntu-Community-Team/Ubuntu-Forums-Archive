---
title: "How to determine the quality of a jpeg from the CLI"
date: 2008-05-30
forum: General Help
---

### Post by unutbu on 2008-05-30
I'm looking for a faster CLI command to determine the quality of a jpeg.

The only method that I know of at the moment uses the identify program (part of imagemagick): 

```
stop@intersection:~% identify -verbose IMG_1681.JPG | grep -i Quality | awk '{print $2}'
98
```

But this command is dog-slow:

```
stop@intersection:~% time identify -verbose IMG_1681.JPG | grep -i Quality | awk '{print $2}'
98

real	0m8.769s
user	0m8.661s
sys	0m0.100s
```

Do you know of a better (quicker) way?

---

### Post by disturbedite on 2008-05-30
i found two packages in the repo that look like they might be what you're looking for:
imageinfo
&
jpeginfo

---

### Post by unutbu on 2008-05-30
Thanks for that disturbedite, but unfortunately, neither give info on the compression quality.

---

### Post by disturbedite on 2008-06-01
there is a new package that just hit the repo today for intrepid, it is called libimage-metadata-jpeg-perl.  but it seems as if it is only for metadata, but i just thought i'd mention it...
here is the description:
This package provides an interface for reading and interpreting the
content of JPEG segments, in particular of those segments containing
metadata (like TIFF headers, thumbnails, Exif info, IPTC info, comments,
etc.). Some segments can even be modified and rewritten to disk.

The author claims that this module is still EXPERIMENTAL: use it at your
own risk.

---

### Post by unutbu on 2008-06-01
Thanks for the tip!

---

### Post by disturbedite on 2008-06-01
no prob.  that is what we're here for.

but sorry, i know it prolly isn't exactly what you're looking for...

---

### Post by Avelino Rego on 2008-09-20
Did you find a faster solution?

I has reach the same method and here is also very slow.
I have a lot of photos to check and this way ...

---

