---
title: "how do i add repositorys"
date: 2007-02-24
forum: General Help
---

### Post by hempa on 2007-02-24
Hello i am trying to install beryl everything is going well until i get to the part when i am supposed to add the beryl repository to the /etc/apt/sources.list
 
 how do i do this, need exact commands to write in the terminal. this is the repository that i want to add
 
 deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

---

### Post by altaaa on 2007-02-24
- Open up a terminal (Applications > Accessories > Terminal)

- Type the following: [FONT="Courier New"]sudo gedit /etc/apt/sources.list[/FONT]

- Add your repo at the end of the file

- Save the file and exit Gedit

- Type the following: [FONT="Courier New"]sudo apt-get update[/FONT]

That's it!

---

### Post by sisco311 on 2007-02-24
sudo su
echo "deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main" | cat >>/etc/apt/sources.list
apt-get update

---

