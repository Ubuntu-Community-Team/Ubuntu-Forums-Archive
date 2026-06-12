---
title: "How to install the mouse?"
date: 2006-10-15
forum: General Help
---

### Post by Nazzy on 2006-10-15
Hi,
I am after installing Ubuntu 5.10 tonight. Last time I used SuSE for about two weeks and before I was Microsoft user. After installing Ubuntu I don't know why my mouse cursor isn't working. I think its not installed. So, I tried to browse through my Ubuntu to configure it like the way I did on SuSE. I am using Genius IntelliPro Serial Mouse.

Please please could anyone help me how can I configure my mouse. This is so annoying to use your keyboard instead of mouse. :( 
I also tried to find the YaST thingy which was in SuSE but I couldn't found on Ubuntu 'cuz if I could found it I could configure the mouse. Is there any adminstrative panel on Ubuntu to configure mouse or any alternative option???

I am dying to setup it. Please help me!!!

[email]-pna2792@gmail.com[/email]

---

### Post by Nazzy on 2006-10-15
Sorry there, the mouse type is Genius EasyMouse Pro Serial.

---

### Post by Dr. Nick on 2006-10-15
The mouse is usually set in xorg.conf

yast is a suse thing, I am not sure if their is a mouse config in ubuntu, I have never needed it.

I would look at the file 

/etc/X11/xorg.conf and look for the mouse setting. should see a line like /dev/input/mouse somewhere

---

### Post by NeoLithium on 2006-10-15
I haven't used GNOME in a while but there should be something under SYSTEM -> PREFERENCES or somewhere around there in the GUI as well.

---

### Post by katalyst23 on 2006-10-15
The Ubuntu equivalent of Yast is the Synaptic package manager.  If you are in Gnome, it is located under System --> Administration --> Synaptic Package manager.

---

### Post by Dr. Nick on 2006-10-16
> **katalyst23 said:**
> The Ubuntu equivalent of Yast is the Synaptic package manager.  If you are in Gnome, it is located under System --> Administration --> Synaptic Package manager.

Synaptic is good for installing packages, but I think yast installs packages and allows other system configuration like display and other settings.

---

