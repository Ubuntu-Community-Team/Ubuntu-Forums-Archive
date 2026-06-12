---
title: "hercules rmx on mixxx"
date: 2020-08-27
forum: General Help
---

### Post by djskylite on 2020-08-27
i have a hercules rmx dj controller and have trying to get it to work with mixxx 2.2.4 in ubuntu 20.04.1 i have looked on the mixxx forum and i can across this and needs to be installed into the etc folder  /udev /rules.d/69-mixxx-usb-uaccess.rules i don't know how to install it does anybody know how it is done and i don't know why mixxx does not include this when it is installed.

---

### Post by djskylite on 2020-08-27
Come on somebody knows how to to do this please as it driving me potty

---

### Post by QIII on 2020-08-27
Please bear in mind that the Forums are populated by volunteers, end users all as are you.  We are not employees of Canonical.  We offer our help as we have time.  We have real lives, jobs, spouses, children, dogs, cats and the need for meals and sleep on occasion.  Your question may not yet have come to the attention of anyone who has just the right answer for you.  Please be patient and allow about 12 hours before you bump your thread, lest you should appear impatient and demanding.

---

### Post by Yellow Pasque on 2020-08-27
Please give a link to the relevant thread/post on the mixxx forum.

---

### Post by djskylite on 2020-08-28
it say in order to use a hid device in linux you must have read and write permission to the hid devices see details at this this page [http://www.mixxx.org/wiki/doku.php/troubleshooting](http://www.mixxx.org/wiki/doku.php/troubleshooting) i clicked on it and scrolled down the page hopefully you help me and it is apreceated thanks

---

### Post by Yellow Pasque on 2020-08-28
So you have the file and want to put it in rules.d?
```
cd ~/     #or wherever you have the file
sudo mv 69-mixxx-usb-uaccess.rules  /etc/udev/rules.d/
```

---

### Post by djskylite on 2020-08-29
Thanks i will give it a try

---

### Post by djskylite on 2020-08-29
i have tried it and does not work it says package not found when i tried to install it so it looks like i have not got the file required thanks for your help where do you get this file?

---

### Post by Yellow Pasque on 2020-08-30
> **djskylite said:**
> i have tried it and does not work it says package not found when i tried to install it so it looks like i have not got the file required thanks for your help where do you get this file?

The commands I gave just copy a file. They have nothing to do with packages, so you completely lost me about what gave you an error involving package not found.
Let's try again. Open a terminal and run these commands. If you get an error, please copy/paste the output

```
cd ~/
wget https://raw.githubusercontent.com/mixxxdj/mixxx/master/res/linux/mixxx-usb-uaccess.rules
sudo cp mixxx-usb-uaccess.rules /etc/udev/rules.d/69-mixxx-usb-uaccess.rules
```

---

### Post by djskylite on 2020-09-01
sorted thanks for your help

---

### Post by Yellow Pasque on 2020-09-01
You're welcome. If everything's working with the rmx, please mark the thread solved ('thread tools' menu above first post).

---

