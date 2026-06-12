---
title: "Configuring GRUB?"
date: 2008-06-08
forum: General Help
---

### Post by cereal killer on 2008-06-08
I'm sure I'm not the only one with this problem...I think. :)

After certain Ubuntu updates were installed, the GRUB selection menu doubled the Ubuntu options. In other words, when GRUB 1st pops up, I got the Ubuntu, I got the Ubuntu recovery mode, and something else, along with Windows option.

So a few weeks ago after installing an update, I now have SIX options for Ubuntu, basically doubles that do the same thing. Yesterday after another update, I got 3 more. So now I have NINE Ubuntu's spamming my GRUB screen.

I looked and found the GRUB text file and see all the stuff there, but when I try to delete it won't let me.

It's nothing fatal, but at this rate I may have like 27 in a month and have to scroll down for 10 secs to get to Windows.

---

### Post by leito666 on 2008-06-08
with "sudo gedit /boot/grub/menu.lst" you will be able to edit those lines.

---

### Post by cereal killer on 2008-06-09
Yep, worked like a charm. Thanks.

Anything I can do to keep this from happening again?

---

### Post by Powerman2442 on 2008-06-09
Yeah I just updated tonight and it did the same to me. I just did the "sudo gedit /boot/grub/menu.lst" command and deleted the old lines. Not sure how to prevent it though. :S I'm running 7.04.

---

### Post by p_quarles on 2008-06-09
You don't really want to prevent this behavior. When a new kernel update becomes available, Ubuntu defaults to installing the new one alongside the old one. The reason is because a kernel update can cause major havoc if something goes wrong. 

Editing out entries you don't want is the best way to take care of it. Changing the default behavior would make things much more difficult in the event of any problems.

---

### Post by Powerman2442 on 2008-06-09
> **p_quarles said:**
> You don't really want to prevent this behavior. When a new kernel update becomes available, Ubuntu defaults to installing the new one alongside the old one. The reason is because a kernel update can cause major havoc if something goes wrong. 

Editing out entries you don't want is the best way to take care of it. Changing the default behavior would make things much more difficult in the event of any problems.

Hey I was just saying... I don't know how to prevent it.

---

### Post by meierfra. on 2008-06-09
> You don't really want to prevent this behavior. When a new kernel update becomes available, Ubuntu defaults to installing the new one alongside the old one. The reason is because a kernel update can cause major havoc if something goes wrong.

But you can limit yourself to 2 sets of kernels without taking a risk. drs305 wrote a very nice howto on the subject. (Click on drs305 in my signature)

---

### Post by VMC on 2008-06-09
> **meierfra. said:**
> But you can limit yourself to 2 sets of kernel without taking a risk. drs305 wrote a very nice howto on the subject. (Click on drs305 in my signature)

That "drs305" is an excellent article! 
It helped change by boot up using Startup Manager.  That article has a lot of information in it. 

[I need to add links to my signature. Never thought of doing that until now.]

---

