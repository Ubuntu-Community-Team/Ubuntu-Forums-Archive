---
title: "Synaptic Package Manager Questions...."
date: 2007-08-04
forum: General Help
---

### Post by ReaderRat on 2007-08-04
I was browsing SPM and decided to install a games package....Ace of Penguins. I installed it, but cannot find it. It is not in the "Games" menu. How do I start the package up?

Also, while browsing, I noticed some packages denoted as "Dummy Packages", and some of these were installed. What is the purpose of these?

RR

---

### Post by be4truth on 2007-08-04
THE DUMMY PACKAGES ARE THERE FOR COMPATIBILITY REASONS. LEAVE THEM WHERE THEY ARE. DELETING THEM CAN CUASE PROGRAMS TO GET STUCK OR CRASH.

Look in the folder /usr/bin if you find a file that resembles your game. Then open a terminal and type the name of this file in it and see if your game starts.

If that is successful go to Applications with a right click and 'Edit Menu" and enter a new item. You have to enter the path of the program which in your case would be "/usr/bin/yourfile" .

---

### Post by strabes on 2007-08-05
To find the command for a package run the "which" command, like this: ```
which <packagename>
```

---

