---
title: "Umm.. 4 small questions :)"
date: 2007-08-25
forum: General Help
---

### Post by bigboss2200 on 2007-08-25
hi there.. :)

   Well, as the title stated, i have 4 small questions:

1- how can i update my system from Terminal..? "i just want another way to update it rather than going to the GUI interface"..

2- how can i show the progress bar of a certain installation..? "example, in Fedora i used to type [rpm [COLOR="Red"]-ivh[/COLOR] PACKAGE_NAME.rpm] and i had a progress bar showing the status of the installation, but when i type [sudo dpkg -i PACKAGE_NAME.deb], i know nothing of whats happening with my installation..

3- what is the best site to search for any ,deb package? "like rpm.pbone.net"

4- my cube is not working when i enable Desktop Effects.. in fact, i see only 1 desktop in the toolbar, but when i change it to 4 nothing happens.. and if i disable and enable Desktop effects one more time i see only 1 desktop.. any solution for that..?!

thanks alot.. and sorry for asking so many questions and for my poor english :)

---

### Post by r4ik on 2007-08-25
1. Click reload and mark all upgrades if there are any click apply
4. read  [http://ubuntuforums.org/showthread.php?t=429231&highlight=cube](http://ubuntuforums.org/showthread.php?t=429231&highlight=cube)

---

### Post by apetresc on 2007-08-25
1. I think r4ik misunderstood your question. You're looking for ```
sudo apt-get update
sudo apt-get upgrade
``` (in that order)
2. The apt-get utility is a little more verbose than dpkg, but either way I don't think you can get a full "progress bar."
4. apt-cache search :)

---

### Post by r4ik on 2007-08-25
> **AdrianP said:**
> 1. I think r4ik misunderstood your question. You're looking for ```
sudo apt-get update
sudo apt-get upgrade
``` (in that order)
2. The apt-get utility is a little more verbose than dpkg, but either way I don't think you can get a full "progress bar."
4. apt-cache search :)

Yep i did my bad thanks :)

---

