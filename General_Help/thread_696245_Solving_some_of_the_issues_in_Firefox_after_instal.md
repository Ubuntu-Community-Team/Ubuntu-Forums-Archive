---
title: "Solving some of the issues in Firefox after install of the Ubuntu SE theme"
date: 2008-02-13
forum: General Help
---

### Post by Jaz_knos on 2008-02-13
Lo! All
Have spent half a day trying to figure this out, so thought i would share it, to hopefully save some other people some more time. 
As said in the "Ubuntu; Dark Them Tips", once SE is installed, it integrates some of the system theme colors into its own workings; resulting in dark colored text entry boxes, drop down menus, radio buttons (the lil ones where you can only select one option) and tick boxes. (all i've found so far.
While re-coloring the entire browser with you're new dark theme is nice, it tends to become a pain in the backside after a while, with webpages not displaying as they were meant too.
Solution:
in file-system browser go too :-
   /home/jaz/.mozilla/firefox
from there, navigate to the folder that is there, then to the chrome folder
(alternatly, in terminal type :-
   cd ~/.mozilla/firefox/*/chrome
   pwd
the printed line will be the full extension to your user-specific browser formatting file
open the file userContent-example.css and at the bottom add :-
input, textarea {
  background-color: inherit !important;
  color: inherit !important;
  background: inherit;
}

select, option {
  background-color: inherit !important;
  color: inherit !important;
  background: inherit !important;
}
Save the edited version as userContent.css and then re-start Firefox. This solves the issues with the text boxes, both single line and textArea's along with some of the issues of the dropdown boxes (the drop-down background area is still dark when its dropped down, but they're more usable at least!). Have not had much luck working out how to solve the radio-buttons and tickboxes. If anyone has any figurings please let me know
A quite good Firefox theme to use with SE is  ["NASA Night Launch"]("https://addons.mozilla.org/en-US/firefox/addon/4908"), Looks in keeping with the rest of the SE theme, while still being usable.
Enjoy
Jaz_knos
Hope this helps at least a lil bit, and if anyone has any thoughts on the leftovers...

---

### Post by K.Mandla on 2008-02-13
Moved to General Help.

---

