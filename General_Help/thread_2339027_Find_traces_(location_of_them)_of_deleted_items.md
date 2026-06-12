---
title: "Find traces (location of them) of deleted items"
date: 2016-10-04
forum: General Help
---

### Post by tonma on 2016-10-04
Hi,

I've downloaded IntelliJ Idea tar.gz and extracted it, then followed the instructions on the installation text file. it was done by typing ./idea.sh. Then it installed.
I saw that IntelliJ does not install a package, so I can just delete the folder. But, the installation process did ask me if I want to add an entry for IntelliJ so it will appear when I search for it in the "Search your computer" button

Now, even if I delete the IntelliJ Idea folder, I still see its logo when I search for it (it doesn't launch though). How do I find all its leftovers and remove them?

Ty!

---

### Post by howefield on 2016-10-04
What was the path to the folder that you removed ?

There are several that you could look at..

---

### Post by tonma on 2016-10-04
It was inside the Downloads folder, I removed that, but the entry for search is still here (I remember the installation asked me specifically if I want an entry in the search - not in these exact words of course)

---

### Post by howefield on 2016-10-04
Have a look for some hidden folders and files in your ~/home folder, the names might not be exact but if they are there you should recognise them.

```
/home/$USER/.gnome/apps/jetbrains-idea-ce.desktop
/home/$USER/.android
/home/$USER/.local/share/JetBrains
/home/$USER/.IdeaIC2016
```

---

