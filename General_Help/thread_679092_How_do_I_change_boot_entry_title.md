---
title: "How do I change boot entry title?"
date: 2008-01-26
forum: General Help
---

### Post by espressopigeon on 2008-01-26
I want to dual boot Xubuntu and Ubuntu. I currently have Xubuntu installed, but the GRUB menu shows the name as Ubuntu. Can I change this so I don't get confused when I have both?

---

### Post by taurus on 2008-01-26
Just edit /boot/grub/menu.lst and change it to whatever you want for the _title_ entry.

```
gksudo mousepad /boot/grub/menu.lst
```

---

### Post by seventhc on 2008-01-26
You know, you don't really need to dual boot between the two. You can just install the extra desktop to one system and choose which one you want at login. for example I used to choose between kubuntu, xfce, or gnome. The default install was ubuntu with gnome and I just added the desktops to ubuntu. I now only use gnome but I think if you do it that way its easy to choose. :)
So if you were to boot into ubuntu you could run this command
```
 sudo aptitude update && sudo aptitude install xubuntu-desktop
```
and then you can choose at login.
heres a link [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)
Then again you already have you partitions so need to change anything if you don't want to, I'm just letting you know for future reference. :)

---

