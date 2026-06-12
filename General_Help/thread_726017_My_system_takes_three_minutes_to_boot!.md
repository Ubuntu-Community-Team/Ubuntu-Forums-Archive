---
title: "My system takes three minutes to boot!"
date: 2008-03-16
forum: General Help
---

### Post by endtheembargo on 2008-03-16
I've installed ubuntu v. 7.1 on my Toshiba Satellite A135, and for some reason it takes 3 whole minutes to boot (I timed it)! 

It gets past the part that says GRUB loading stage 1.5, and then, it sits at a black screen for three minutes before the Ubuntu loading graphic comes up.

Once Ubuntu loads for the most part everything runs fine but every once in a while the computer will freeze and and need to be restarted. (I think this mostly happens while I'm in firefox.)

I'm wondering if this is a software or hardware issue. The computer came to me used with windows vista on it, and at that time I don't remember it having any problem booting up.

I'm sorry if this is a little vague, I' still learning about computers. Let me know if I need to get more specific about anything.

---

### Post by jocko on 2008-03-16
If you want to see what takes time during boot, there is a program called bootchart that will log what happens and produce an image.
If you want to install it, run this in a terminal (or search for "bootchart" in synaptic):
```
sudo apt-get install bootchart
```
After this, an image will be produced in /var/log/bootchart every boot.
If you post the bootchart here, chances are someone will know how to help you speed it up.

---

