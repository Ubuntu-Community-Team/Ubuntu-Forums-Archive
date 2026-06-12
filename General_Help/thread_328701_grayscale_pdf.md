---
title: "grayscale pdf"
date: 2006-12-31
forum: General Help
---

### Post by Skeletonix on 2006-12-31
**Hello ...  **

How can I convert colour pdf to grayscales pdf ? On my Ubuntu  computer with Gnome (Evince & AcroRead). 

Thank you a lot !

---

### Post by Skeletonix on 2006-12-31
hou,hou ... small Nautilus script ..

```
#/bin/sh
#color pdf to grayscale pdf

filepath=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

pdftops -level1 $filepath  /tmp/grayscale.ps 
ps2pdf   /tmp/grayscale.ps ./grayscale.pdf
rm /tmp/grayscale.ps 
```

---

