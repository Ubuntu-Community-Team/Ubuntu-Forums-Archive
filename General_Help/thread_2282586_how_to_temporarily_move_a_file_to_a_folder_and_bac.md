---
title: "how to temporarily move a file to a folder and back using the command line"
date: 2015-06-15
forum: General Help
---

### Post by sohlinux on 2015-06-15
Hello, How can I temporarily move a file to a folder and move it back again using the command line

eg, folder1 has a file inside it called 001.txt I want to move 001.txt to a folder called folder0 for 5 mins then move it back to folder1, then move 001.txt from folder2 to folder0 for 5 mins then move it back and so on. I have many folders so I would like to automate the way its done. I am aware it could be done by mv and sleep but I have to write out each folder name but I have 100. is there a way it could be done automatically for all folders folder1, folder2, folder3 up to folder100. thanks

---

### Post by Vaphell on 2015-06-15
```
#!/bin/bash

interval=300
f=001.txt
dest=folder0
dirs=( folder{1..100} )

for d in "${dirs[@]}"
do
    echo mv -t "$dest" "$d/$f"
    echo sleep "$interval"
    echo mv -t "$d" "$dest/$f"
    echo
done
```

---

### Post by sohlinux on 2015-06-15
perfect. thanks :)

---

