---
title: "Logging into desktop with bypassing desktop login screen"
date: 2021-11-19
forum: General Help
---

### Post by SciGuy1872 on 2021-11-19
Hi.  I was wondering if there was a way to login to desktop and bypass the desktop login screen?  Maybe by using tty, then starting desktop?

---

### Post by grahammechanical on 2021-11-19
What does the startx command do? The answers given on AskUbuntu might help you.

[https://askubuntu.com/questions/518454/what-does-startx-command-do](https://askubuntu.com/questions/518454/what-does-startx-command-do)

Please keep in mind that the X-Server is close to being replaced by video servers based upon the Wayland protocol. Experimenting with the only install of Linux on a machine could end up breaking the installation. There are valid reasons why the X-Server should be replaced. It has taken years for a replacement to be developed to the point of satisfying all use cases. The desktop is more complicated than it was years ago. What you want to do might not be so easy to do as simply switching consoles and running the startx command.

Regards

---

