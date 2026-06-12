---
title: "&quot;Select File&quot; Dialog does not show directories (not hidden)"
date: 2020-10-30
forum: General Help
---

### Post by ubulove89 on 2020-10-30
Hi all,

I am a happy user of different Ubuntu derivatives until now. I use Ubuntu 20.04.1 with lates updates and upgrades. Everything worked perfectly on other derivatives.

I have a NFS share located in my LAN. But when i open the app CherryTree and click on open file so the "Select File" Dialog opens. it does not show my folders that i created with mkdir in terminal. So the NFS folder doesn't show up too. The other "Open File" Dialog thats inside ubuntu called "Open File" works well. But the problem is that i use CherryTree for development solutions so i need acces to my created directories because my notes and most used codes are in there. There is a solution to copy the wile from the NFS to my local, but that is not what i need. I work on projects with more people on the same NFS. I do not now why ubuntu has two different "Open File"Dialogs, and i don't know yet which dialog belongs to what app yet, because i moved from Xubuntu to Ubuntu because of AMD GPU Failures.
Is there a way to purge one of the dialogs to force use of the other? Or other solution?

(I am sure it is not a hidden directory)
Also when i create a dummy directory, it doesn't show up. I tried to chown different user:groups without any effects, also chmod 777 has no effect.

Also i cant manage the bookmarks in the dialog "Select File", color of options is grey.

Screenshots of file manager vs dialog:
[https://imgshare.io/image/NhQ1U4](https://imgshare.io/image/NhQ1U4)
[https://imgshare.io/image/NhQgMZ](https://imgshare.io/image/NhQgMZ)

Look like its the dialog of Nautilus

Thanks in advance!

---

### Post by Holger_Gehrke on 2020-10-30
You might want to check whether you're using the snap version of CherryTree. Snap confinement makes it impossible to access directories outside of $HOME and /media/$USER/. Try 'snap list' in a terminal to find out.

Holger

---

### Post by ubulove89 on 2020-10-30
Thanks indeed, that did the trick, i did not now i had the snap version! :)
Thread can be marked as solved!

---

### Post by Impavidus on 2020-10-30
You can mark as solved yourself: Thread Tools -> Mark as solved.

Many applications outsource the creation of the open file dialogues to some widget library. There's more than one of those, the most popular are GTK and Qt. On Ubuntu and Xubuntu you'll see mostly GTK, on Kubuntu mostly Qt. That explains why there are different styles of open file dialogues. Some applications even make their own from scratch.

---

### Post by ubulove89 on 2020-10-30
Ah i see! i never used those libraries. Thanks! I do more with data analytics (databases)...

---

