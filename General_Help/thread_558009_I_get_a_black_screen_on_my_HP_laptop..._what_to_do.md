---
title: "I get a black screen on my HP laptop... what to do ??"
date: 2007-09-23
forum: General Help
---

### Post by rahul_s on 2007-09-23
I am a kinda beginner with Ubuntu installation.

I have installed Wubi Ubuntu on my HP dv6000 laptop... downloaded it... had it download and install Ubuntu on my external drive... after the install it loads all stuff and then shows a blank or a black screen... but the laptop is on.

BTW the HP laptop has an NVidia GeForce Go 6150 card which I suspect can be the problem

I found a command by pressing Ctrl+Alt+F2 and then typing 
lspci | grep -i nvidia 

But when do I do this... when it is loading the drivers ? Also does this command really work

---

### Post by ddrichardson on 2007-09-24
Its not the nVidia card  - its HP's power saving implementation. Specify the noapic option at boot time and all should be well.

---

### Post by rahul_s on 2007-09-24
> **ddrichardson said:**
> Its not the nVidia card  - its HP's power saving implementation. Specify the noapic option at boot time and all should be well.

How do I do that ... please... I am a noob with Wubi Instaler :oops:

I just need to know how when to press what key & enter what where

---

### Post by ago on 2007-09-25
> **rahul_s said:**
> How do I do that ... please... I am a noob with Wubi Instaler :oops:

I just need to know how when to press what key & enter what where

Edit the menu.lst file in /wubi/boot/grub
There is a line that start with "kernel", append "noapic", save and reboot

It might also be that you need to install the appropriate driver within ubuntu, there are several guides on how to do that on ubuntuforums

---

### Post by rahul_s on 2007-09-25
> **ago said:**
> Edit the menu.lst file in /wubi/boot/grub
There is a line that start with "kernel", append "noapic", save and reboot

It might also be that you need to install the appropriate driver within ubuntu, there are several guides on how to do that on ubuntuforums

Thank you sir... :D
I did the above and I was able to start Ubuntu... 
I have joined the Ubuntu family now :)

:guitar:

---

### Post by ddrichardson on 2007-10-20
Can you mark this thread solved to help others?

---

### Post by rahul_s on 2007-10-20
> **ddrichardson said:**
> Can you mark this thread solved to help others?

Yes Sir... thanks for your assistance !! :)

:guitar:

---

### Post by ddrichardson on 2007-10-20
No worries - was just trawling through tracked posts to clear!

---

