---
title: "How to open shell script graphically"
date: 2020-03-29
forum: General Help
---

### Post by lesliek2 on 2020-03-29
I have a file x.sh that's supposed to run the application x. If I open the terminal, navigate to the directory the file's in and run the command ./x.sh, x opens. If, on the other hand, I navigate to the file graphically and left-click on it, the file opens in gedit for editing. If I right-click on it and look at "opens with", it says that files ending in .sh are to be opened in gedit. Should I be changing gedit to something else? If so, what? Is there something I should be doing instead in order to get x to run when I left-click on x.sh?

Leslie

---

### Post by dragonfly41 on 2020-03-29
Make it executable in x.sh file properties.

---

### Post by deadflowr on 2020-03-29
In Files you need to reset the executable preferences.
it defaults to display, you need to set to to run or ask.
Unfortunately you haven't provided any information about which release this relates to, but for Ubuntu 18.04 the help page for it is here:
[https://help.ubuntu.com/lts/ubuntu-help/nautilus-behavior.html.en]("https://help.ubuntu.com/lts/ubuntu-help/nautilus-behavior.html.en")

---

### Post by TheFu on 2020-03-29
Linux doesn't care about extensions.  Some GUI programs do care about extensions.
All files have "permissions." As dragonfly41 says above, changing the permissions to include "eXecute" probably will fix it, but you'll need to double-click the file, not single-click.

The contents of the *x.sh* file may not be sufficient for it to be run through a GUI. Can you please post the first line? If that line doesn't provide an interpreter in the correct format, it probably won't run. Which interpreter should be used depends on the language the script is written in.

There are some settings which might prevent running programs on a specific file system. This is a security setting and not enabled by default on Ubuntu systems to my knowledge.  However, as Linux desktops become more popular, we are being attacked and it might be time to prevent the execute permission bit from working on all mounts.  That's a very different discussion, however.

---

