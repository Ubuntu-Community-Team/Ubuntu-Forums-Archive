---
title: "Can I tell from where a program is starting e.g. Firefox"
date: 2020-06-17
forum: General Help
---

### Post by jdpitt on 2020-06-17
I am running Focal Fossa and every time it is started, Firefox opens up a window to the log in page of my Dropbox. I have checked within FF itself but it is not there as a different start up page is set. It is also not listed in startup applications so I am somewhat confused as to where else to look. I would appreciate any ideas please, thanks.

---

### Post by dragonfly41 on 2020-06-17
command:
which firefox

---

### Post by CelticWarrior on 2020-06-17
If it "opens up a window to the log in page of my Dropbox" then likely you installed Dropbox and that is the initial setup (Dropbox sync client is typically set to run in the startup by default).

Once you login and the sync client it set to your Dropbox account, Firefox will open in the homepage.

---

### Post by jdpitt on 2020-06-17
Thanks dragonfly41 will give that a try

---

### Post by jdpitt on 2020-06-17
Thanks I will remove dropbox and see if that fixes it.

---

### Post by GhX6GZMB on 2020-06-17
Another idea is to launch Htop and press F5. This will give you a tree view of which processes/programs have started other processes.

---

