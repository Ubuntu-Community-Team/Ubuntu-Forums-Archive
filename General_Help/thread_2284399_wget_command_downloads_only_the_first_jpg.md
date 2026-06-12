---
title: "wget command downloads only the first jpg"
date: 2015-06-29
forum: General Help
---

### Post by andfree on 2015-06-29
I try to use wget command to download jpg files from a website. In the address line of firefox, a different ending of the form "&pg=*" appears for every jpg file, eg "&pg=1", "&pg=2" etc. Whatever I test, only jpg from page 1 is downloaded.

```
wget -r -l 16 --accept=jpg www.website&pg=*
```

Page 1 is downloaded even if i put "2" instead of "*".

 Any idea what I should do?

---

### Post by dino99 on 2015-06-29
[http://askubuntu.com/questions/240702/wget-a-series-of-files-in-order](http://askubuntu.com/questions/240702/wget-a-series-of-files-in-order)

---

### Post by andfree on 2015-06-29
Thank you, but it didn't help. It downloaded only first page again. And it's not curious, if you think that it downloads always page 1, even if I ask to download page 2 or 3 or any.

---

