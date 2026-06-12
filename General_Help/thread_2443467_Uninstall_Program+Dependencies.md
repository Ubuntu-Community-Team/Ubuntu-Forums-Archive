---
title: "Uninstall Program+Dependencies"
date: 2020-05-16
forum: General Help
---

### Post by bionic3epl on 2020-05-16
How do I uninstall a program plus all it's Dependencies w/out hunting for all of them?

---

### Post by monkeybrain20122 on 2020-05-16
Depends on how you installed it. If you installed it with apt or synaptic, then 
```

sudo apt remove packagename && sudo autoremove
```

autoremove uninstalls the dependencies.

---

### Post by bionic3epl on 2020-05-16
Is there any other way to remove the program dependencies?

---

### Post by monkeybrain20122 on 2020-05-16
Why do you want other ways? All other ways involving finding them manually.

---

### Post by Impavidus on 2020-05-16
In addition to terminal commands, you can use synaptic, which will have a list of autoremovable packages, or you can use the update manager, which will offer to remove them. Under the hood it's all the same.

BTW, it's **sudo apt autoremove**.

---

### Post by ajgreeny on 2020-05-16
If it was installed using apt or one of the GUI package managers run command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` and you will see a list, arranged by date, of all installed packages which may allow you to figure out what else was installed at the same time.

---

