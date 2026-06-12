---
title: "First Time User: Many Questions Please Help"
date: 2007-03-06
forum: General Help
---

### Post by chunkylover21 on 2007-03-06
Hey guys this is my first time ever using linux. I have Ubuntu 6.10. Basically, I have installed only the op system, and run the system update. So now I am ready to install nVidia drivers, wireless net drivers, and audio drivers.

I am on a Gateway MX3414 Laptop. It has an nVidia Geforce 5700 Go! GPU. Realtek sound and wireless. Could you guys please start me off I cant wait to learn how linux works.

Thanks a lot!

---

### Post by aysiu on 2007-03-06
Since you want to learn something, copy and paste some commands off this page. You won't regret it.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

But if you're feeling in a rush and don't want to learn as much right now, you can also use this:
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

or this:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by chunkylover21 on 2007-03-06
I dont understand nothing is working. When I downloaded the easyubuntu thing, the .deb file does not do a thing when i double click on it. I right click and try to install but nothing moves, nothing starts or runs. Same thing for the automatrix

---

### Post by aysiu on 2007-03-06
That's weird. Usually double-clicking on the .deb will open up the installation dialogue.

Let's try the command-line to see what errors we encounter. Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post back into this thread any output (errors or otherwise)? ```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
wget -c http://easyubuntu.freecontrib.org/files/easyubuntu_latest.deb
sudo dpkg -i easyubuntu_latest.deb
```

---

### Post by CocoAUS on 2007-03-06
Can .asc keys be imported the same way .gpg keys are?  And what is the -0- option at the end of the wget command?

---

