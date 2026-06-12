---
title: "Gimp questions"
date: 2007-10-06
forum: General Help
---

### Post by oldcpu on 2007-10-06
1. Gimp saves every image opened as thumbnails and stores it in ~/.thumbnails, which never expires.  How do I disable this?

2. Gimp logs recently opened images in ~/.recently-used.  How do I disable this?

---

### Post by conehead77 on 2007-10-06
i think you can delete the ~/.recently-used file and then make a directory with the same name. this will result in a error, cos gimp cannot write in a directory.
i did that with the recently-used.xbel and it works good. no clue about the thumbs though

---

### Post by bodhi.zazen on 2007-10-06
you could make ~/.recently-used and .thumbnails to ro (read only)

chmod 500 ~/.recently-used file # or 400 if you prefer

---

