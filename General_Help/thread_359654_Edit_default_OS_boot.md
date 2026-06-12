---
title: "Edit default OS boot"
date: 2007-02-12
forum: General Help
---

### Post by saximus on 2007-02-12
Hey,

I just installed ubuntu, and I am going to try to learn how to use it. In the mean time, I will be using xp the most. The problem is that ubuntu made itself the default OS, which is inconvenient when I have to change from ubunto to xp within ten seconds when I start the computer.. How do I set xp to be the default OS to boot from? Hope someone can help me. 

Thanks.

-saximus

---

### Post by Tomosaur on 2007-02-12
You need to edit the menu.lst file in the text editor of your choice. Here's how to do it using gedit:

Click Applications > Accessories > Terminal

Type:
```

gksudo gedit /boot/grub/menu.lst

```

And input **your** password. The file will open up, and you need to find the line which says 'default 0'. You need to change the 0 to the number of the OS you want to boot into by default. Grub counts from 0, and you need to include the 'Other Operating Systems' line in the count. So, first menu item is 0, second is 1, third is 2, etc etc. Just use whichever number corresponds to Windows XP.

Alternatively, check the link in my sig for a gui program to make this easier.

---

### Post by saximus on 2007-02-12
All right - thank you very much for the quick reply! Have a nice day then:)

---

### Post by saximus on 2007-07-18
Hello again!

I have run into the same problem again.. I installed ubuntu studio and was going to use the command posted here earlier. But my ubuntu studio OS does not start - some trouble during start-up. My question is: is it possible to edit the GRUB boot menu from windows? I need to boot XP by default..

PS. I'll get back to fixing my ubuntu installation later:)

---

### Post by Spudgun on 2007-07-19
Unfortunately, you can't edit the grub config files from Windows.

---

### Post by saximus on 2007-07-19
All right,

How about editing from the GRUB screen? I notice that it is possible to press 'e' for edit. Is it possible to edit boot order (and preferably also count-down time) from there?

---

