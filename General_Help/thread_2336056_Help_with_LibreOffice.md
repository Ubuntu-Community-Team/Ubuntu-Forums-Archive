---
title: "Help with LibreOffice"
date: 2016-09-04
forum: General Help
---

### Post by sammc35 on 2016-09-04
First of all thank you for coming here.

My question, how can I assign formmating to shorcuts like Ctrl+1

For example
If I press Ctrl+1, indent is changed to 2"
Ctrl+2 Centered, indent 4"

---

### Post by Bucky Ball on 2016-09-04
Welcome. Good question, and an interesting one which I think I can answer: You create a macro and then assign a shortcut key to it. 

1/ Create a macro. Tools> Macros> Record macro. (note: you must go to Tools> Options> Advanced and tick 'Enable recording macros' to get this option in your Tools macro menu);
2/ Do the formatting you want to do then stop recording the macro and name it.

That's the macro done. The second part is assigning the shortcut key.

1/ Go to Tools> Customize> 'Keyboard' tab> Category> Libreoffice macros. Find the macro you just created.
2/ Click on the macro you just created, select a shortcut key combo from the list or create one then click 'Modify'. 

That key combo will now run the macro you recorded. Or at least should if you got it right.

Good luck and hope that helps and is along the lines of what you were after. Took me awhile to figure this out when I thought of doing it a couple of years ago. They may seem like they take a bit to set up, but its easy once you get the hang and you can create some quite complex macros then execute a lot of moves in a couple of clicks for ever more after creating the macro shortcut in 'Customise'.

(* In short, you would choose 'Record macro' then change indent to 2", stop recording and name. Go to Tools> Customize and choose the Ctl+1 as the shortcut key for the macro.)

---

