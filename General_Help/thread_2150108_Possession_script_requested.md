---
title: "Possession script requested"
date: 2013-05-31
forum: General Help
---

### Post by Fred Doolie on 2013-05-31
I'm sorry. I don't know all the Linux commands. Could somebody please make a script for me that does:

Delete Thatfolder and everything in it
Create Thatfolder
Copy Thisfolder/everything to Thatfolder
Make me the full permissions owner of Thatfolder

Why? Because I want to transfer stuff from Puppy to Ubuntu and Puppy makes everything belong to ROOT.
I want the folder to belong to me in Ubuntu so I can use it.

Thank you

---

### Post by Impavidus on 2013-05-31
```

#!/bin/bash
rm -rf thatfolder/
mkdir thatfolder/
cp -r thisfolder/* thatfolder/
chown -R you:you thatfolder/

```

---

### Post by Fred Doolie on 2013-05-31
Thank you

---

