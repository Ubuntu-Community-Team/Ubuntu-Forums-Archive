---
title: "Grub"
date: 2007-08-08
forum: General Help
---

### Post by Hickler on 2007-08-08
I tried posting my problem in the Sabayon Linux forums but the community there isn't exactly top-notch and a couple of my posts there have gone unanswered for a while. So, here it is:

I'm using the Ubuntu bootloader to dual boot Ubuntu and Sabayon. When I choose Sabayon it then takes me to the Sabayon bootloader. So my question is can I remove the Sabayon bootloader? Thank you.

---

### Post by Wiebelhaus on 2007-08-08
Isn't that what it's supposed to do? or am I misunderstanding your question?

---

### Post by Hickler on 2007-08-08
Well, it shows the Ubuntu bootloader with the ubuntu selections and Sabayon, when I choose Sabayon, it takes me to another bootloader that I had before with the choices of Feisty and Sabayon... I feel this second bootloader is unnecessary and when I choose Sabayon in the first bootloader I would like it to boot into Sabayon.

---

### Post by Wiebelhaus on 2007-08-08
> **Hickler said:**
> Well, it shows the Ubuntu bootloader with the ubuntu selections and Sabayon, when I choose Sabayon, it takes me to another bootloader that I had before with the choices of Feisty and Sabayon... I feel this second bootloader is unnecessary and when I choose Sabayon in the first bootloader I would like it to boot into Sabayon.



Post the output of "/boot/grub/menu.lst" Please.

---

### Post by DagMan on 2007-08-08
You'lle need the output of both the files for ubuntu and sabyons bootloader menu files preferably.

---

### Post by confused57 on 2007-08-08
> **Hickler said:**
> I tried posting my problem in the Sabayon Linux forums but the community there isn't exactly top-notch and a couple of my posts there have gone unanswered for a while. So, here it is:

I'm using the Ubuntu bootloader to dual boot Ubuntu and Sabayon. When I choose Sabayon it then takes me to the Sabayon bootloader. So my question is can I remove the Sabayon bootloader? Thank you.
What you can do is boot into Sabayon, post your Sabayon boot entries in your /boot/grub/grub.conf in this thread.

Once you've posted your Sabayon boot entries here...boot into Ubuntu, open your /boot/grub/menu.lst, then copy & paste the Sabayon boot entries into your Ubuntu  menu.lst...This may be the easiest way for you to do this, and  it "should" boot directly into Sabayon.  If it works, you still might want to leave your configfile entry at the very bottom of your menu.lst, just in case you need it.

---

