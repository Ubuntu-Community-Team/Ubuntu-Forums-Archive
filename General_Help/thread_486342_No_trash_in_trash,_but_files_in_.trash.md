---
title: "No trash in trash, but files in .trash"
date: 2007-06-27
forum: General Help
---

### Post by okoaomo on 2007-06-27
When I send files to trash, they do not appear when I open the trash icon. If I open the .trash folders on each drive I have mounted, there are many files I have deleted (sent to trash) in the past. How do I get every file I send the trash to show up in the trash?

---

### Post by Digitallysick on 2007-06-27
I know once i had to delete some files in the trash as root in order to get it to work again, try that, then remove it from the panel and then add it back, see if corrects the problem

---

### Post by Anzan on 2007-06-28
Sorry I don't have a solution but I had the same problem and it corrected itself a few hours later.

No idea how or why.

---

### Post by Qu4k3R on 2007-06-28
try to clear first what you got on your trash folder.
It happens (few times) with me.

In a terminal just type
> 
cd ~/.Trash
sudo rm -r *

And run.

This will clean everything you have in your trash folder (folders, files and even root files\folders)

---

