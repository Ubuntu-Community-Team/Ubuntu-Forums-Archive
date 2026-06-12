---
title: "Ram printing with sudo cat file &gt; dev/lp0 fails"
date: 2007-12-06
forum: General Help
---

### Post by thirunavukkarasu on 2007-12-06
Hi guys,

Drafting this mail with few experience with Ubuntu.

My system is connected to a parallel port printer and printer senses as /dev/lp0 device file.

When trying to a print using the below command fails
$sudo cat /boot/grub/menu.lst > /dev/lp0 ; it asks for root password, and it shows the below error
bash: /dev/lp0 : Permission denied:confused:

When the same with root shell(i.e sudo bash)
#cat /boot/grub/menu.lst > /dev/lp0 ; here it is OK and get the print out in my printer.

Why my previoud command is not working. Please help what need to be done so that i can run the command with sudo itself.

Rgds,
Thiru.S

---

### Post by lha on 2007-12-06
```
sudo cat /boot/grub/menu.lst > /dev/lp0
```
runs only the "cat /boot/grub/menu.lst" as sudo. The redirection to /dev/lp0 is done with non-root permissions. You'll need something like
```
sudo bash -c "cat /boot/grub/menu.lst > /dev/lp0"
```

---

### Post by thirunavukkarasu on 2007-12-06
Thank you lha

Now it is getting printed:)

Rgds,
Thiru.S

---

### Post by frafu on 2007-12-08
Hello,

The Accessibility Forum being intended to talk about software related to disabilities, I have moved this thread to a more appropriate forum.

Have a nice day.

Francesco

---

