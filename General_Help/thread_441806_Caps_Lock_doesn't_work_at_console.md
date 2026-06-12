---
title: "Caps Lock doesn't work at console"
date: 2007-05-12
forum: General Help
---

### Post by irotas on 2007-05-12
Yesterday I installed Ubuntu Feisty 7.04 on my Dell Latitude c840 laptop. The installation went very smoothly, but (of course) there are some problems.

One problem is that the Caps Lock key doesn't work when I'm at the console. It works fine while I'm in X, but at the console everything is lowercase, regardless of whether Caps Lock is on or off.

I'm not sure how to troubleshoot this. Any suggestions?

Thanks,
Adam

---

### Post by Belathor on 2007-05-17
I hate this very much. I have had this problem since Dapper. Perhaps there is a setting wrong somewhere? If you find a way to fix it, please let me know!

Thanks!

---

### Post by GuitarRocker2562 on 2007-05-17
for kubuntu, console is bash right? If so, why would you need caps?

---

### Post by irotas on 2007-05-17
Sometimes I want to work at the console without starting X. It gets annoying that the Caps Lock doesn't work, especially when I'm editing files.

I'm sure there is some easy fix for this, but I have no idea where to start.

---

### Post by Belathor on 2007-05-18
Alright: Jordan_U_ on the #ubuntu irc channel gave me a solution:
> sudo dpkg-reconfigure console-setup
I changed the default and now I can use my caps lock key!

---

### Post by irotas on 2007-05-18
> **Belathor said:**
> Alright: Jordan_U_ on the #ubuntu irc channel gave me a solution:

I changed the default and now I can use my caps lock key!


Ah, that worked! I selected the 'Dell Latitude series laptop' option.

Thanks for the tip!

---

### Post by irotas on 2007-05-18
Hmm, it worked until I reboot, but now it's not working again. How do I make the change permanent?

---

### Post by Belathor on 2007-05-20
Yeah, I had that same problem. I'm not sure what is going on.

---

### Post by Belathor on 2007-05-22
I have noticed that the command only works if it performed in a tty* terminal. I tried adding a modified version of it to my /etc/rc.local file but it didn't change things in the tty* terminals. It is weird. All it needs is for the program to run and then it works, I don't have to change anything. For the time being, I simplified the process of setting the console-setup by using:> sudo dpkg-reconfigure --frontend=noninteractive console-setup

---

### Post by Belathor on 2007-06-07
Permanent fix: 

Disable the boot splash screen by going into /boot/grub/menu_list and deleting the word splash from the boot options.

---

### Post by irotas on 2007-06-09
> **Belathor said:**
> Permanent fix: 

Disable the boot splash screen by going into /boot/grub/menu_list and deleting the word splash from the boot options.


I have no idea how you figured that out, but it worked!

Although, the correct file to edit is  /boot/grub/menu.lst


Thanks!

---

