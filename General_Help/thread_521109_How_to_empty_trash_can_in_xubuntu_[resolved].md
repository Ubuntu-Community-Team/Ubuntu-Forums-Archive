---
title: "How to empty trash can in xubuntu [resolved]"
date: 2007-08-09
forum: General Help
---

### Post by dak-AD on 2007-08-09
took me ages to figure out this, so on the off-chance someone else looks for the solution:

if you don't have permission to empty some files from the trash-can in xubuntu, use the command line like this:

cd ~/.local/share/Trash/files

sudo rm -rf *

ta-da! I was looking for ~/.Trash, and getting grumpy when i couldn't find it :-/

---

### Post by draikxox on 2007-08-09
thx so much i have had the same problem

---

### Post by zazen666 on 2007-08-10
Wow!!! That worked when other tricks didnt....thanks!

---

