---
title: "Where can I find the program commands?"
date: 2018-11-29
forum: General Help
---

### Post by aneblanc on 2018-11-29
Where can I find the commands to launch the following programs "chromium", "audio recorder", "sound", "SD card files" with the "startup applications preferences" in Ubuntu 16.04?

---

### Post by robert48 on 2018-11-29
If you look to the left (default) icon panel you will see an orange suitcase icon. Left click and it will open ubuntu-software. Using the search at the very top of the window left click on the spy-glass icon then type in the name of the program required. Select your programme and you will be offered the option to install.

You can also evoke the application by typing the following code into the terminal:-

```
ubuntu-software
```

---

### Post by logix2 on 2018-11-29
From what I understand, you're trying to find the command used to run an installed application, right? To easily find an application's executable, open your file manager, navigate to /usr/share/applications/, then open the application file from there with a text editor, and look on the "Exec" line. That's the application executable (the command you can type to run it). You can ignore parameters like %U or %F, you only need the command part, for example "chromium-browser".

---

