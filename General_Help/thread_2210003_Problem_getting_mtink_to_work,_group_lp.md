---
title: "Problem getting mtink to work, group lp?"
date: 2014-03-08
forum: General Help
---

### Post by Extreedoc on 2014-03-08
Can somebody tell me how to get mtink to work: it keeps telling me I need to belong to the group lp; ok... how do I proceed?

---

### Post by Mark Phelps on 2014-03-08
Presuming your username is "bob", open a terminal and enter: > sudo adduser bob lp

To check that worked, enter > cat /etc/group | grep lp:

You should then see something like > lp:x:7:bob

---

### Post by Extreedoc on 2014-03-08
Thanks Mark, done but still can't use mtink, I get the same old group lp stuff. I did check as you suggested  and got roughly the right message but the lp:x: was in red, the rest in black. Is that to be expected? Thus: lp:x:7: bob... (I did substitute my username for bob).

Edit: Disregard the above; I have got it to recognise me as a group member but now it says There is a problem with the printer communication... I can "OK" that and get the mtink "window" up but the operation buttons are greyed out. If I click on preferences it asks "choose browser" The choices are many and are headed "Directories" and "Files" I have found and selected my printer model and there is only one choice of port which I have also selected.

---

