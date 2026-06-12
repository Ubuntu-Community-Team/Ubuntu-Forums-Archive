---
title: "Cannot execute file while on second hard drive"
date: 2012-10-24
forum: General Help
---

### Post by Chris_huh on 2012-10-24
I've trying to run the following script:

```
#!/bin/bash
# Written by MKZA from customerhelp.co.za
find . -type f | while read file;
do
    f=$(basename "$file")
    f1=${f%.*}
    mkdir "$f1"
    mv "$f" "$f1"
done
```

to move all my movie files into individual folders. I can get it working fine when it is on my desktop, but i can't run it when it is in the necessary folder on a second hard drive. 

I have added executable permissions to the file (chmod +x) but all i get back is:

bash: ./file2folder: Permission denied

I am the owner of the folder. Any ideas?

---

### Post by lukeiamyourfather on 2012-10-24
Chances are you are not the owner of the folder. Anything outside of the home folder for the current user is automatically owned by root. Either run it as root (probably not a good idea) or sort out permissions before you try to run the script.

---

### Post by Chris_huh on 2012-10-24
Yep, that was it. I used WorMzy's guide here [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251) to get it working.

Thanks

---

