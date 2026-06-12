---
title: "deleted file to trash"
date: 2016-12-07
forum: General Help
---

### Post by paulofeastman on 2016-12-07
I deleted a flash drive file to trash by mistake...is there any way I can locate it.

Thank you for your help


paulofeastman

---

### Post by &amp;KyT$0P# on 2016-12-07
Enter in a Terminal -
```
id
```
The output will start like this -
```
uid=<number>(<yourusername>) 
```

Notice the <number>.  Your file is likely buried inside a folder named [FONT=Courier New].Trash-<number>[/FONT] which is located directly in the flash drive - as in, the root of the flash drive, i.e. not in a subfolder.

If you don't see any such folder in your file manager, make sure you've selected to show hidden files.

---

