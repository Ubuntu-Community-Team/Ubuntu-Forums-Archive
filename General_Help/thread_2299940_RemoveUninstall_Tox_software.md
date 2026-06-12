---
title: "Remove/Uninstall Tox software"
date: 2015-10-22
forum: General Help
---

### Post by Afnan on 2015-10-22
I just installed this software called Tox ( [https://tox.chat/](https://tox.chat/) ) and after using it I didn't like it. now I cant find any option to remove it from my system. How do I remove it? Please help.

---

### Post by ajgreeny on 2015-10-22
What were the binaries that you downloaded from that link?

Were they (or it) static binaries that ran when you clicked on them, or did they go through an installation procedure?  It looks as if there is a .deb package that you could have installed by double clicking on it and it would then be installed by software-center.

What exactly did you do?

---

### Post by Afnan on 2015-10-23
I inputted these code as per their website instructions:

```

echo "deb https://pkg.tox.chat/debian nightly release" | sudo tee /etc/apt/sources.list.d/tox.list 
wget -qO - https://pkg.tox.chat/debian/pkg.gpg.key | sudo apt-key add - 
sudo apt-get install apt-transport-https 
sudo apt-get update
sudo apt-get install qtox-unity

```

---

### Post by Bucky Ball on 2015-10-23
Then look for 'qtox-unity' in Software Centre and it should be there. Remove. Is it there? qtox-unity?

---

### Post by Afnan on 2015-10-23
> **Bucky Ball said:**
> Then look for 'qtox-unity' in Software Centre and it should be there. Remove. Is it there? qtox-unity?
Yes it was there, thank you very much, it has been removed. Now do I have to remove any ppa or that's it?

---

### Post by ajgreeny on 2015-10-23
You can open software-sources and remove the ppa from the "Other software" tab if you want to, but as long as you don't install anything again there should be no problem.

For a cleaner system I always remove unwanted ppa repos, but it's your choice.

---

### Post by Bucky Ball on 2015-10-23
> **ajgreeny said:**
> For a cleaner system I always remove unwanted ppa repos, but it's your choice.

I'd go along with that. :)

---

