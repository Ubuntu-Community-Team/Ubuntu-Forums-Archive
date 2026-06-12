---
title: "Problems with chmod"
date: 2007-05-11
forum: General Help
---

### Post by Mark Haysom on 2007-05-11
HI,

Well I am new to linux and I guess this will prove it!
I was attempting to make firestarter run on startup for all users. Part of the instructions were to add a line to the /etc/sudoers. To do this i used chmod 777 sudoers and made the change. Once completed I needed to change it back but no joy, I typed the following.

mark@Serenity:/etc$ sudo chmod 0440 sudoers
sudo: /etc/sudoers is mode 0777, should be 0440
mark@Serenity:/etc$ 

I have learnt to copy files I am going to play with first, but really need to change it back, can anyone help?

---

### Post by carlosqueso on 2007-05-11
I think you're going to have to boot into recovery mode (should be an option in your grub menu) and then run ```
chmod  0440 /etc/sudoers
``` to change your sudoers file back to the proper permissions. 
 In the future, don't chmod the things you're going to edit, edit sudo with ```
sudo visudo
``` or for other files ```
gksudo gedit <filename>
```

---

### Post by Mark Haysom on 2007-05-11
Thanks for your help, appreciated. All back to normal now :)

---

