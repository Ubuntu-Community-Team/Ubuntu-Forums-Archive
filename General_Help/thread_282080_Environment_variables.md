---
title: "Environment variables"
date: 2006-10-22
forum: General Help
---

### Post by Ariod on 2006-10-22
If I create a launcher to an application on my desktop, can this application read environment variables?

What I did was make .bashrc file and put this line into it:
```
export PATH=$PATH:/home/ariod/bin
```
In the terminal, I can read the new PATH variable just fine. However, a launcher will not find the executable file located in that /bin directory. As if it cannot read the updated PATH variable. What's the problem here?

---

### Post by Najand on 2006-10-22
Try to add your path in the suitable line in /etc/init.d/rc file...(YOU NEED ROOT PREVILAGE TO EDIT THAT FILE)

---

### Post by kwalo on 2006-10-22
Application launchers don't read your .bashrc files. Just put the full path to an executable in your launcher. No need to bother with environment variables.

---

