---
title: "Booting into windows after reinstalling ubuntu"
date: 2016-03-31
forum: General Help
---

### Post by nauris2 on 2016-03-31
Hello. So I had windows 10 and Ubuntu 15.10 both installed on my machine and on the start up I was able to choose which one to boot in to. But I ran into some problems with my ubuntu and needed to reinstall it. So I did using the same flash drive than before. I chose the option to replace the old ubuntu with the new one (reinstall). All worked fine, ubuntu is installed + I can see my windows partition from the Ubuntu OS, but how can I boot windows now? After the reinstall there is no longer a start up screen with these choices.

---

### Post by X-RED_Tech on 2016-03-31
Boot Ubuntu and ```
sudo update-grub
```

---

### Post by ajgreeny on 2016-03-31
Sounds like a candidate for the boot-info-script which you will find if you run Boot-repair as shown in my signature.

Post the pastebin link you get from the script and do not, at this stage, accept the default repair until we can see what is wrong at present.

---

