---
title: "wget Resume"
date: 2013-08-10
forum: General Help
---

### Post by Geoff_Lane on 2013-08-10
I have a small web server running on my Pi (apache) and occasionally serve some video files to my daughter.

Annoying if it fails during download so I am experimenting with the wget -c option.

Tried  it on my local network using Ubuntu terminal, start a download with wget then Ctrl-C to  abort. The partial file is there in the directory so reissue wget with  -c option.

Starts from the beginning renaming the output with .1 suffix as obviously the original patial exists.

Any clues guys?

Geffers

---

### Post by oldos2er on 2013-08-10
Moved to General Help.

---

### Post by VMC on 2013-08-10
Does the server your downloading from support resume?

---

### Post by papibe on 2013-08-10
Hi Geoff_Lane.

You may need a little script in order to fully recover from fails. This would be the general idea:
```
#!/bin/bash

link="http://www.podtrac.com/pts/redirect.mp4/201307.jb-dl.cdn.scaleengine.net/techsnap/2013/techsnap-0119-432p.mp4"

output="./TechSNAP.S01E119.mp4"


wget -c "$link" -O "$output"
until [ $? = 0 ]
do
    wget -c "$link" -O "$output"
done
```
Hope it helps. Let us know how it goes.
Regards.

---

