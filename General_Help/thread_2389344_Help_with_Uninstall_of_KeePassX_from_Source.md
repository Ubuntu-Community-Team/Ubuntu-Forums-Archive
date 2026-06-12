---
title: "Help with Uninstall of KeePassX from Source"
date: 2018-04-15
forum: General Help
---

### Post by KenUBF on 2018-04-15
Hi everyone. I've only installed a few pieces of software from source, and have never tried to uninstall anything yet, and I'm not sure how to go about it. I looked at the websites for the program at [https://github.com/keepassx/keepassx](https://github.com/keepassx/keepassx) and keepassx.org but I haven't found anything from the developers on how to uninstall the program. Can anyone help with this? I looked at the forums but none of the solutions seemed to work for me. If it might help, when I first installed it, I followed the install instructions on the github website. Thanks!

---

### Post by dragonfly41 on 2018-04-15
If you install Synaptic Package Manager ... synaptic ..
you have a GUI which you can launch, search for "keepass" and find entries
keepass2

Mark for removal and then apply.

---

### Post by KenUBF on 2018-04-16
Thanks for the reply. I just looked for the entry a second time and it tells me there isn't any KeepPass versions installed. This is one of the methods I tried originally, but tried again just in case I missed something, but I'm not sure that's the correct method. If I'm not mistaken Synaptic is only a graphical interface for the Ubuntu package repository, but I installed this version of KeePass from the developer, from source code, directly. There aren't any connections to any repositories that enables me to uninstall it by that method. I was hoping I could find the commands to reverse the changes I made by installing it.

---

### Post by oldos2er on 2018-04-16
Go back into the source folder and run  ```
sudo make uninstall 
```

---

