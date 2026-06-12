---
title: "an Home folder too small"
date: 2007-06-20
forum: General Help
---

### Post by giocarra on 2007-06-20
Hi to all of you!
I don't know why but Ubuntu, installed via Wubi has chosed to let me use a too small home folder : only 1,7GB. 
So I cannot resume in such a folder my previous backup, which is greater.
How can I solve this problem?
I tried to use gparted but I thinks it is impossible since Ubuntu is installed inside WindowsXP.
Anyone has a suggestion?
Thanks in advance.
giocarra

---

### Post by ago on 2007-06-20
You can put large files in the windows disks

---

### Post by giocarra on 2007-06-20
Thanks for your kind answer, ago
but, since I'm a newbye, I'm not sure how to do what you suggest.
May I have your help again?
Thanks in advance.
Have a nice day.
giocarra

---

### Post by ago on 2007-06-21
You can put your files in any other folder in any other partition, and if you want them available within your home folder, you can create a link with the command:

ln -s /path/to/folder /home/yourname/foldername

---

### Post by vanadium on 2007-06-21
You can also use Nautilus to create these symbolic links. that is available from the right-click menu ("Make link"). After creating the link, move that to your home directory. then you will be able to access the directory from within your home directory. Linux links work perfectly: they will just behave as a regular folder under your home folder, although the actual data are elsewhere on another partition (can even be over the network).

---

