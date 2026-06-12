---
title: "I want to Move files; Ubunut *copies* them instead!"
date: 2017-11-05
forum: General Help
---

### Post by sterator on 2017-11-05
I simply need to move files from one spot to another, but Ubuntu seems to insist on copying those files instead...how can I instruct it that I want only to ***move*** the files?

Both folders are at the same level...have the same parent folder. I'm not dragging across drives, etc..

Thank you!

---

### Post by yancek on 2017-11-05
It would help if you were more specific about exactly what steps you have taken to move the files and exactly what happens.

If you have a main folder named Main and two folder in it; folder1, folder2 and you want to copy all from folder1 to folder2, change to the Main folder and do:

> mv folder1/* folder2/.

---

### Post by coldraven on 2017-11-06
From the Nautilus help page:
> 
[LIST]
[*]Open the file manager and go to the folder which contains the file you want to copy. 
[*]Click [COLOR=#6C6C6C]Files[/COLOR] in the top bar, select [COLOR=#6C6C6C]New Window[/COLOR] (or press [COLOR=#6C6C6C]Ctrl+N[/COLOR]) to open a second window. In the new window, navigate to the folder where you want to move or copy the file. 
[*]Click and drag the file from one window to another. This will *move it* if the destination is on the *same* device, or *copy it* if the destination is on a *different* device.

For example, if you drag a file from a USB memory stick to your Home folder, it will be copied because you're dragging from one device to another.
You can force the file to be copied by holding down the Ctrl key while dragging, **or force it to be moved **by holding down the Shift key while dragging. 
[/LIST]


Or select the files, right click and select "Move to".

---

### Post by sterator on 2017-11-10
> **yancek said:**
> It would help if you were more specific about exactly what steps you have taken to move the files and exactly what happens.

If you have a main folder named Main and two folder in it; folder1, folder2 and you want to copy all from folder1 to folder2, change to the Main folder and do:

.

I've simply dragged files from one folder to another...the other night, the cursor had a plus sign, and only copied the files in question.

thank you!

---

