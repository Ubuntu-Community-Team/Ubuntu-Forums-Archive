---
title: "Problem with starting up from command line"
date: 2013-03-30
forum: General Help
---

### Post by MaxLinuxLover on 2013-03-30
When I start up from command line I use 'startx' to get to graphical mode. The problem is that when I get to graphics mode, there is no launcher or bar on top. Is there a way to start from command line and keep the launcher and bar on top. Is it a command in the command line, or is it something in grub, or anything. 

Thanks in advance

---

### Post by Bashing-om on 2013-03-30
MaxLinuxLover; Hi !
Later versions require:
```
sudo service lightdm start
``` to start the GUI desktop.[INDENT=3]
hth

[/INDENT]

---

### Post by MaxLinuxLover on 2013-03-30
Thanks, I will try that

---

### Post by MaxLinuxLover on 2013-03-30
Thank you Bashing-om, typing "sudo service lightdm start" worked.

---

### Post by Bashing-om on 2013-03-30
MaxLinuxLover;

You are most welcome; It is a challenge keeping up with why/what changes !
[INDENT=4]
just pass'n it on

[/INDENT]

---

