---
title: "vmware kills all special keys on keyboard"
date: 2008-06-11
forum: General Help
---

### Post by SpaceTeddy on 2008-06-11
Hi Folks,

i am encountering a very strange behavior. I have a vm running (windows mainly - sometimes i need it) which is usually somewhere where i can reach it. Sometimes, when i am jumping between the host system and the vm, all my functions keys die one of them is pressed continuously. 

This means **Capslock, shift (left and right), ctrl, alt and both windows keys (which control compiz) go dead. **

I am not entirely sure yet if the vm is actually involved or not in this, but so far it only happened whenever i had the vm running. So here is my question:
1.) how can i figure out what is causing this ?
2.) has anyone else ever had a similar problem
3.) how to do i reset the x-servers keyboard short of rebooting or loging out ?

any help is appreciated...

PS: if you need any futher clarification, just ask. I will provide all and any information that is asked.

---

### Post by simonasambler on 2008-06-11
I have quite similar problem with Sun VirtualBox. Solved by install scim-bridge-client-qt
```
sudo apt-get install scim-bridge-client-qt
```

---

### Post by SpaceTeddy on 2008-06-11
thanks, i'll try it and post my results.

---

