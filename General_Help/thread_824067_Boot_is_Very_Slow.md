---
title: "Boot is Very Slow"
date: 2008-06-09
forum: General Help
---

### Post by WeEatVista on 2008-06-09
I'm not exactly sure how to word this, but I am encountering a problem with ubuntu. When it boots, grub loads, the ubuntu symbol loads with the orange loading bar, then it asks me to log in. I log in, and after I do it takes about 6 minutes for my desktop to load. Is there anyway I can make this faster?

Thanks in advance,

We Eat Vista

---

### Post by spiderbatdad on 2008-06-09
Could you run this command:```
dmesg > ~/Desktop/dmesg.txt
```right click the created file and select "create an archive." upload that archive here with the manage attachment tool below.

---

### Post by sancho panza on 2008-06-09
Go to System>Prefs>Sessions and go over the list of programs that run at startup. You can delete those programs that you dont need to run everytime you login.

You might also wish to uncheck the box in Session Options to get rid of programs that were running when u logged out.

---

### Post by WeEatVista on 2008-06-09
> Go to System>Prefs>Sessions and go over the list of programs that run at startup. You can delete those programs that you dont need to run everytime you login.


Thanks sancho panza but that didn't solve my problem.

> Could you run this command:
Code:

dmesg > ~/Desktop/dmesg.txt

right click the created file and select "create an archive." upload that archive here with the manage attachment tool below.

Thanks for your help, here is the dmesg.txt file you asked for. I didn't know what type of file you wanted it as, but i thought .tar.gz would be the best. 


Thanks for your help so far, 

We Eat Vista

---

### Post by spiderbatdad on 2008-06-09
Ok. would like you to experiment with a boot parameter or two...You should be able to boot the system in around 35 secs., not 6 minutes:)

See if this makes any sense to you, please:[http://spiderbatdad.wordpress.com/ubuntu-boot-problems/](http://spiderbatdad.wordpress.com/ubuntu-boot-problems/)

I want you to try the parameter "irqpoll"
You can try it by pressing e to edit the kernel line from the grub screen. Then use the arrow key to move to the line beginning with the word kernel. Press e again. Delete --quiet splash from the end of the line, and add irqpoll Then hit enter and then b to boot.

If this works, you will need to edit /boot/grub/menu.lst to make the change permanent.

If it does not, please try: noapic irqpoll

---

### Post by WeEatVista on 2008-06-09
> Delete --quiet splash from the end of the line, and add irqpoll Then hit enter and then b to boot.

I tried this but the boot time was the same, and it also removed the pretty ubuntu loading bar and replaced it with the script =D

Ill try the other one when I get home and I'll let you know how it goes.

Thanks,

We Eat Vista

---

