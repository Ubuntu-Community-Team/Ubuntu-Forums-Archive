---
title: "Can't Install New Software Version"
date: 2013-03-30
forum: General Help
---

### Post by Tk007LwZFJW5ej on 2013-03-30
I'm trying to install the latest version of Anki (2.0.8). I downloaded the .deb from the website ([http://ankisrs.net/](http://ankisrs.net/)), clicked on it, Ubuntu software center opens up and I click install (I had to install some python dependency first). I open up Anki and see that it's still the old version (1.2.9). So I uninstalled the old version and install the .deb of the new version again (I never had to uninstall the new version; it's like the installation had absolutely no effect) with software center as I did before. I open up the newly installed program and check the version. It's still the old version! I tried uninstalling and reinstalling again; same issue. How is this even possible?! How do I fix it?

EDIT: Now I've tried to install at the command line with

sudo dpkg -i anki-2.0.8.deb

same problem.

---

### Post by ibjsb4 on 2013-03-30
Sounds like there are some leftover (1.2.9) configuration files.  Do a search and remove.

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by Tk007LwZFJW5ej on 2013-03-30
> **ibjsb4 said:**
> Sounds like there are some leftover (1.2.9) configuration files.  Do a search and remove.


I used 
```
sudo apt-get purge anki
```, then installed the .deb. It's still the old version.

---

### Post by Tk007LwZFJW5ej on 2013-04-02
Ok, I need to learn to read. I did a purge, *then* searched and deleted some python files and miscellaneous other files, now the latest version is installed. Thank you.

---

### Post by ibjsb4 on 2013-04-02
Congratulations :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

