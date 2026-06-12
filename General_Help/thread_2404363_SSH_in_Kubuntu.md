---
title: "SSH in Kubuntu"
date: 2018-10-23
forum: General Help
---

### Post by ricardosilva on 2018-10-23
Hello, I am sorry if this is a duplicate, but I could not find any answer to my question.

I am multi-booting several Linux distros, specifically: Ubuntu 18.04.1 LTS w/ Gnome 3; Ubuntu 18.04.1 LTS w/ Unity; Linux Mint 19; Kubuntu 18.04.1 LTS.
Kubuntu is my new addition to the lot, it is my first time with Plasma (or any KDE), and I am really enjoying discovering the different DE. By now, everything is working, except SSH. I need to connect to the University server by SSH. I was able to use symbolic links to make the keys I originally had in my first distro available on my second Ubuntu and on Linux MInt, but that does not seem to work on Kubuntu.
 
I am able to connect if I log into a terminal and do: 
~$ ssh-add mykey
and add the key I want to use, before I log in to the remote server.

But I will have to do it again next time I turn on my computer.

Is there any way to automate it?
Where does KDE store SSH passwords? (In Gnome / vanilla Ubuntu it is simply ~/.ssh)

---

### Post by ricardosilva on 2018-10-23
I was able to solve the problem, by creating a script and adding it to ~/.config/autostart-scripts.

---

