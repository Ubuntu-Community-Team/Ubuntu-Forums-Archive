---
title: "Err how is this even possible (TRASH IS WIERD)..."
date: 2008-05-05
forum: General Help
---

### Post by varnil on 2008-05-05
Just installed hardy heron (been away from the linux scene from a while) ever since debian etch (saw no reason to bother with it again until now...). Anyways, i recently deleted something and then tried to empty the recycle bin. Oddly however there were objects in it that were property of root and i did not have permisions to modify (err how the hell did they even get into my trash). So i opened nautilus as root went to trash and guess what its not there... Moreover i cannot find a .Trash-"user" folder on my home partition root, not does rm -rfv ~/.Trash/* help as there is apparently no .trash folder as in previous versions of ubuntu/dabien. Anyways i tried finding the path of trash but all i've found is a wierd url-like string "trash:///" at the addressbar of nautilus. I know that somehow the trash must be tied into the filesystem (and if i'm wrong there must still be a terminal backend to accessing it) and as such i tried searching for "trash"... found nothin, then a2 (the deleted folder)... found nothing). Now this seems too large an oversight to be made by so many people so i can guess there's something i'm missing. sooo: HOW DOES ONE CHANGE PERMISSIONS OF FILES IN TRASH OR GET TO TRASH IN TERMINAL...
(Also am i supposed to be allowed to delete parents of dierectories that are owned by root and say are 000 for others?)

---

### Post by macaholic on 2008-05-05
The trash folder is now located in ~/.local/share/Trash/files.
You can get there via cd ~/.local/share/Trash/files

---

### Post by varnil on 2008-05-08
thnx, but how come despite home being a seperate partision theres a .Trash-root there but no .Trash-"user"
edit:nvm stupid question

---

