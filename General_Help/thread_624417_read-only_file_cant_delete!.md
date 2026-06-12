---
title: "read-only file cant delete?!?"
date: 2007-11-26
forum: General Help
---

### Post by floydjunkie8 on 2007-11-26
ok so i was going through a bunch a folders on my cousins external hardrive and copied a few folders to my desktop.  one of them i cannot delete! :(  

somehow i got it in the trash can i have no idea how because whenever i try to move it now it says i am not allowed.  and when i try to empty my trash it says there is an error while deleting because i do not have rights to do so.

so know i have this folder with a few files in it stuck on my desktop and in my trash can.

plz help!:confused::(

---

### Post by superwad on 2007-11-26
First of all, is there only one hard drive or partition on your setup?

---

### Post by teryowen on 2007-11-26
you can delete it through terminal with root privliges:

WARNING THIS WILL DELETE FILES - so be careful

sudo rm FILENAME

that should do it to remove it. 

and to delete the files in your trash in terminal change directory to your trash so:

cd ~/.Trash 

~ --> means /home/yourusername/

now to delete the stuff here do the same thing

or if u want to do it all at once do:

AGAIN WARNING WITH THE COMMAND YOU WILL BE DELETING FILES

sudo rm -r *

---

### Post by dpar on 2007-11-27
Or try > gksudo nautilus


P.S.: Be carefull. You are now root!

---

### Post by floydjunkie8 on 2007-11-27
thanx teryowen the sudo rm -r* worked :)

---

### Post by teryowen on 2007-11-27
No problem, glad to see it worked, if you could please mark the thread as solved, its up top under the menu thread tools.

---

