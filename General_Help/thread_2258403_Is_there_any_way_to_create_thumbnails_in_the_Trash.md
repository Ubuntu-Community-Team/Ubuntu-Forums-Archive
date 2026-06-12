---
title: "Is there any way to create thumbnails in the Trash folder?"
date: 2014-12-27
forum: General Help
---

### Post by eundas on 2014-12-27
By default these do not seem to be generated. I don't know if I can force the system to do it.

Eduardo

---

### Post by TheFu on 2014-12-28
[http://www.cyberciti.biz/tips/howto-linux-creating-a-image-thumbnails-from-shell-prompt.html](http://www.cyberciti.biz/tips/howto-linux-creating-a-image-thumbnails-from-shell-prompt.html)

ImageMagick rocks.
```

#!/bin/bash
FILES="$@"
for i in $FILES
do
echo "Prcoessing image $i ..."
/usr/bin/convert -thumbnail 200 $i thumb.$i
done
```
Filenames cannot have spaces and other strange characters might screw the script too.

---

