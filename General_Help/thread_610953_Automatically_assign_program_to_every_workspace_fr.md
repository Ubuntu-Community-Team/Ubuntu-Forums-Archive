---
title: "Automatically assign program to every workspace from startup?"
date: 2007-11-12
forum: General Help
---

### Post by TonySmash on 2007-11-12
Alright, so I have my sessions set to run my Windows XP virtual machine with VirtualBox automatically at startup using this code:

```
VBoxManage startvm "Windows XP Professional"
```

This starts the virtual machine automatically in the first workspace. However, since I have seamless virtualization running, I like having the Windows taskbar at the bottom of every desktop, so I right-click on the virtual machine window in the Ubuntu taskbar and select the "Always on visible workspace" option, so the Windows taskbar follows me between workspaces. 

Is there a command I can add to the startup command that automatically assigns the virtual machine to always be on the visible workspace?

---

