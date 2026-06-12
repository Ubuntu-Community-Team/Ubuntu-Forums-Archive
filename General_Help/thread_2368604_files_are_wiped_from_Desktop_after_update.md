---
title: "files are wiped from Desktop after update"
date: 2017-08-12
forum: General Help
---

### Post by Matrix01 on 2017-08-12
Two files, which have writing, are wiped from Desktop
after recent Update is completed,
And unable to make desktop short cut of Apps.

Any fix?

---

### Post by again? on 2017-08-12
Are you sure the files are wiped or pcmanfm is no longer drawing the desktop.
```
ls -al ~/Desktop
```
What happens if you run
```
pcmanfm --desktop
```

---

### Post by Matrix01 on 2017-08-13
here's output:

taro@taro-HP-Mini-110-3000:~$ ls -al ~/Desktop
ls: cannot access '/home/taro/Desktop': No such file or directory
taro@taro-HP-Mini-110-3000:~$ pcmanfm --desktop
taro@taro-HP-Mini-110-3000:~$

---

### Post by again? on 2017-08-13
You have no ~/Desktop directory to draw the desktop.
I doubt an update would remove ~/Desktop. Accidentally delete possibly????

Recreate directory
```
mkdir ~/Desktop
```

Then check **~/.config/user-dirs.dirs** for the correct entry.
Should have a line
```
XDG_DESKTOP_DIR="$HOME/**Desktop**"
```

Edit if necessary, save and log out.

I don't use Lubuntu, but I tested in a live Lubuntu 16.04 usb and after deleting ~/Desktop, the above method worked to restore.

---

### Post by sotiris2 on 2017-08-15
Before that you should check if Ubuntu is installed in English.

---

