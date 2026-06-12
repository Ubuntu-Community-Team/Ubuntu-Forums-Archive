---
title: "KDE file manager problem"
date: 2017-01-07
forum: General Help
---

### Post by tushar21nov on 2017-01-07
I am using Kubuntu 16.04.1 and it is 64 bit. I am seeing this message  when I click on Dolphin file manager to browse other folders and files. I  am also unable to make any changes in Dolphin like icon size or options  in the menu. This is happening when I log in as a normal user. After  click on the OK button or the Close button I can browse Dolphin file  manager and other folders and files. How to solve the problem. But I can  do anything in root user mode when I use 'sudo dolphin' command in the  terminal. 

The Message:
Configuration file "/home/tushar/.config/dolphinrc" not writable. Please Contact your System Administrator.

---

### Post by dragonfly41 on 2017-01-07
I had a look at my Dolphin on Ubuntu 14.04 but I must admit that I do not use it.  
Instead I use Krusader File Manager (which is kde).

But when I run .. sudo dolphinrc .. I see that for my installation dolphinrc is here ..

$HOME/.kde/share/config/dolphinrc
and
/root/.kde/share/config/dolphinrc

But I'm in Ubuntu 14.04 and you are in Kubuntu 16.04 so paths might differ.

I can only suggest that you first find dolphinrc (using sudo locate) and change permissions to read/write.

Also if launching Dolphin in root mode use .. sudo -H dolphin

Krusader can launch a root session.  Tools > Start Root Mode Commander.

---

