---
title: "How to change boot sequence selection"
date: 2008-04-25
forum: General Help
---

### Post by DMBoricua on 2008-04-25
Hi, I just upgraded Ubuntu to 8.04 hardy. Looks like when I upgraded, my boot selection changed. I've had a friend who has helped me on this, he would tell me what line of code to put on terminal to bring up the boot log and edit to put the default selection to where I want it to be.

I want to know where he gets this help. What is the code to open up the boot sequence so I dont need to be repeatedly asking this?

---

### Post by dnzz on 2008-04-25
```
sudo gedit /boot/grub/menu.lst
```

At bottom you can change the boot list order.

---

### Post by natrixgli on 2008-04-25
Keep in mind that when you get kernel updates the menu.lst file gets overwritten (either that or you have to manually add entries to load the new kernel at boot)

There's probably more to it, I'd do a search for 'edit menu.lst' on the forums.

-n8

---

### Post by Anduu on 2008-04-26
If you prefer a GUI you can install startupmanager from the repos.

It will let you change numerous aspects of the boot menu.

---

