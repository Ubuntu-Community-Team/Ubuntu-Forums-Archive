---
title: "Dual Boot Problem"
date: 2014-08-18
forum: General Help
---

### Post by jfloydb on 2014-08-18
I have Xubuntu 14.04 and Lubuntu 14.04 installed on the same box, a dual boot. After the latest Xubuntu updates, Xubuntu will not boot. Lubuntu will. The grub menu shows up, Both Xubuntu and Lubuntu show up, but when I choose Xubuntu, it defaults to Lubuntu. Again, Xubuntu will not boot. I have had a lot of fun with both OSs on the same box, so I would like to fix this problem. Please tell me how to fix this problem. Thanks.

---

### Post by user1397 on 2014-08-18
Which partition did you install grub on, aka which one did you install first, xubuntu or lubuntu?

---

### Post by ajgreeny on 2014-08-18
Have you had a grub update which could have caused this to happen?

---

### Post by jfloydb on 2014-08-18
I'm pretty sure I installed Lubuntu first. I think it's on a earlier partition than Xubuntu. I'm also pretty sure that it's a grub issue. I simply do not know how to fix it. I'm at work, so I don't have my laptop with me right now. If there is any specific info that you need, let me know, and I will post it this evening. Thanks

---

### Post by markodd on 2014-08-18
As *ajgreeny* asked, did you update the grub?

```
sudo update-grub
```

---

### Post by yancek on 2014-08-18
All the information requested above and more can be obtained by running the bootinfocscript which you can download at the link below.  It just outputs information (results.txt file) and doesn't try to make repairs.  It is extremely useful to have and save any time you make changes to the boot files or partitions.  Instructions are in the link in the Description box at the site below so run it tonight and post the output here. 

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

