---
title: "session startup programs"
date: 2007-01-10
forum: General Help
---

### Post by n_hendrick on 2007-01-10
Okay I have two commands set to run at session startup, but everytime I reboot or log out and in the commands aren't being run. I have no idea why they're not starting up but when I go back to the System>Preferences>Sessions window and under startup programs there is no reference to the programs even though I entered them just seconds ago. something is reseting the list and I would really like to get this solved.....

---

### Post by n_hendrick on 2007-01-10
Nevermind I have it solved, the .config/autostart directory in my home folder didn't have write permissions for the user and I had to change the owner of the directory.

---

### Post by chanders on 2007-02-01
Thanks! I was having the same exact problem..

---

