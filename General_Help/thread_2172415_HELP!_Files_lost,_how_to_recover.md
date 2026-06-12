---
title: "HELP! Files lost, how to recover?"
date: 2013-09-04
forum: General Help
---

### Post by tope_cadiz on 2013-09-04
I am a new linux user. I have installed Ubuntu Studio into my netbook. It only boots with Linux 
I transferred all my data to the netbook I have installed with Linux. It ran well for a day then (I don't know what I did but as far as I can remember, I did not do anything), all my files were lost. I have not backed up the files. These files are all my work files. I have saved it in a general folder named Work in my Desktop. I have not created any folders. The Desktop does not show my shortcuts, too.

When I checked through gparted, it showed a file system for boot as ext2, an extended file system with a sub-file system lvm2 pv with flag lvm. This sub file system shows a size of 297.85 GiB and the used space is 297.84 GiB. 

Please help me. I have to recover my files.

---

### Post by ibjsb4 on 2013-09-05
If I understand right, you have a working system with a lost folder.  Do a search for it in [terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal").

```
locate Work
```

---

