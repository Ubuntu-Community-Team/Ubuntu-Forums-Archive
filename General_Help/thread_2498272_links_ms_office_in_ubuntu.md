---
title: "links ms office in ubuntu"
date: 2024-06-06
forum: General Help
---

### Post by franvalles on 2024-06-06
Hi! 
A while ago I installed MS Office on Ubuntu and the application icons from the Office package appeared. How can I delete it? I remember that I installed it through the console but not with wine.
thank you.

---

### Post by currentshaft on 2024-06-06
"dpkg --list" will show you installed packages, then you can use apt to remove them.

---

### Post by ActionParsnip on 2024-06-07
You may find then in your home folder somewhere

---

### Post by franvalles on 2024-06-08
Thank you. I had listed the packages before the consultation but I did not write because I could not solve it, it is already solved as you have indicated

---

### Post by deadflowr on 2024-06-08
Could you post how you solved it? It's not very clear on how it was solved.
And to help others who might have a similar issue, [please mark this thread as solved.]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by franvalles on 2024-06-09
You can install links to the MS Office suite on Ubuntu.
If you want to delete it and don't remember what the installation package is called, follow these steps

dpkg --list (Search page to imagine the name of the package, in this case it is simple because it contains the word microsoft)
sudo dpkg --remove microsoft-online-apps (remove links)

that's all

---

