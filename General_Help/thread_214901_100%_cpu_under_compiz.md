---
title: "100% cpu under compiz"
date: 2006-07-13
forum: General Help
---

### Post by matoxxx on 2006-07-13
I am ATi x1600xt user and iam experiencing 100% cpu usage issue on scrolling and moving windows under xgl/compiz

What i have is fresh install of dapper LTS and latest fglrx deb's
when i switch to metacity -non xgl/compiz- desktop the 100% cpu usage scrolling and moving windows disappears

its like these pluging on xgl/compiz arent takeing resources from GPU via fglrx, as they should, but instead using mesa and cpu resources

all other effects working fine, minimum cpu usage
__________________

---

### Post by Rackerz on 2006-07-13
Type in the terminal 'fglrxinfo' and post what you get back here.

---

### Post by Bagnaj97 on 2006-07-13
I'm not certain but I don't think either that ATI or NVIDIA have implemented the GL_EXT_TEXTURE_FROM_PIXMAP extension in their drivers, so it defaults to the software to do it causing the cpu usage.

---

