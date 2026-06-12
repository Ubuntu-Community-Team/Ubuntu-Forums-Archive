---
title: "Delete folders in /usr/share"
date: 2007-10-06
forum: General Help
---

### Post by cuervo_jones_85 on 2007-10-06
I've been recently exploring trough linux folders, and i noticed that in /usr/share there's some stuff wich i think could be removed... but i wanted to know that if do this it will be harmless. this is the stuff
- an AbiSuite folder (i unninstalled AbiWord) from my ubuntu, that folder is still there
- games folder (no games installed, removed what came)
- gnibbles, gnobots
- sudoku
-gnumeric (removed)
- some icons and themes not all of them
-ubuntudocs

can i remove them without prejudice?

thank you!

---

### Post by Caffeine_Junky on 2007-10-06
What I would suggest, in the interests of learning/understanding how to use the system safely, would be to open Synaptic Package Manager and down on the Left you will see a Button that says "Status" ...click on that and you will be presented with catigories in the colmn above, ..one of those options will be "Not installed (residual config)"...
 
Note: if there is nothing that falls under that catigory, (i.e left-overs from a programme that has been uninstalled)  ..the option will not appear in the "Status" list.

Now if you select to "mark for complete removal" > [apply] , you will recieve a dialog box in which you can check to see if removing selected item will impact on any other packages in the system,  ...and it is at that point that you can make an informed decision on removing that item.

As for empty folders in /usr/share , ...the above action "complete removal" should take care of most unused config files and the like...

---

