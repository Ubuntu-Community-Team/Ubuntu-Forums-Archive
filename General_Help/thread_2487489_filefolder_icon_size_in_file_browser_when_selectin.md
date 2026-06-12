---
title: "file/folder icon size in file browser when selecting a file"
date: 2023-06-06
forum: General Help
---

### Post by rekurzionkwesi on 2023-06-06
using ubuntu 22. when i open the file browser manually i can change the size of the icons making viewing image files much easier, for instance.

however, when the file browser is opened because of a "select file" request from another program like a web browser all of my file icons are tiny and i do not see a way to change their size. in addition image files do not show a preview. if i'm trying to select an image file to upload to a website this becomes annoying really quick. 

is there a way to change the icon size of files when the file browser is initiated by another program to select a file to upload?

thanks in advance.

---

### Post by rekurzionkwesi on 2023-06-11
no one has seen this behavior before?

---

### Post by Holger_Gehrke on 2023-06-11
You labour under the false impression that these are the same thing. They aren't. One is a full program, the other is just a form or dialog. Most programs just use the one from one of the big libraries on which most desktop environments are based - either QT or GTK - but quite a few programs have their own, one example being GiMP which has a large preview area to the right of the file selection area. I know of no way of influencing the behaviour of the file chooser form through any settings. It might be possible to influence it through CSS for GTK based programs, but I haven't tried this and don't know of anyone who has done so.

Holger

---

### Post by douglas.e.ryan on 2023-06-11
At the minimum, because of those libraries (GTK and QT) a universal way change the appearance of the file pickers to match Nautilus is all but impossible. You didn't specify which DE you're using nor give any specific programs as examples but it might even be possible to get bigger icons through the settings in those programs.

---

