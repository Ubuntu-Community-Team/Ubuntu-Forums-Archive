---
title: "bad sectors"
date: 2016-06-24
forum: General Help
---

### Post by hbw1770 on 2016-06-24
am running xenial all fine, but have a 500GB toshiba external  HDD. When I installed xenial, forgot to remove the toshiba, it now contains the root and boot file systems, gnome-disks reports "Disk is OK, 312 bad sectors", do I have a problem?

---

### Post by RobGoss on 2016-06-24
This is a indication that your hard drive may have a hardware problem or maybe failing. It also might need replacing 

I'm have a Dell 610 that has this same problem it's currently running Linux mint and runs OK but sometimes when I boot up I get a bad sector message so I won't use it as my primary work station

---

### Post by hbw1770 on 2016-06-24
Thanks Rob Goss. As I said everyrting works fine, there are no error messages or apparent problems, but because the boot and root file systems are on the external toshiba HDD I cannot boot up the system unless the toshiba is connected. I want to avoid this and have everyting on the internal HDD. Can I just re-install xenial again, this time having removed the toshiba beforehand, or might this cause corruption.

---

### Post by RobGoss on 2016-06-24
So what your saying you installed 16.04 on a external HDD correct?

Do you have another machine you want to install 16.04 on is that what you're wanting to do

---

### Post by hbw1770 on 2016-06-24
Yes, unintentionally in part only, the only part of xenial on the external HDD are the boot and root files sytems, everyting else is on my internal HDD. I don't want to install it on another machine but have all of it on the internal HDD of my existing machine (an MSI GT72 notebook) because a) I don't want to cart the external drive around wherever I go and b) because it has a lot of bad sectors, which although at present there are no apparent errors, I'd rather not have them on this important part of my system.

---

### Post by hbw1770 on 2016-06-24
It's 2.20 am here now and I'm going to bed. Thanks for your interest RobGoss, talk to you again later.

---

### Post by Geoffrey_Arndt on 2016-06-24
Just save your data from the internal drive to an external USB flashstick . . . OR to the external hdd after creating a data/backup partition on it.   Then do a complete reinstall with the external drive disconnected.   

On an LTS install - - simplest setup is just two partiitons, swap and a single / with all system directories _and home under roo_t.    Problem solved

---

### Post by RobGoss on 2016-06-24
I'm not sure how you did your installation and did not install Ubuntu all on the internal hard drive but you should just do a fresh installation on the internal drive this time.

---

### Post by hbw1770 on 2016-06-24
ThANKS


Thanks RobGoss and Geoffrey_Arndt, I'll do what you have suggested. Was thinking along those lines myself, but was worried that reinstalling 16.04 over the top of an existing installation might cause corruption.

---

### Post by RobGoss on 2016-06-25
You should be able to reinstall Ubuntu over the existing partition as you did when you first install Ubuntu. There will be a option to remove the existing Ubuntu installation and reinstall it again.

---

