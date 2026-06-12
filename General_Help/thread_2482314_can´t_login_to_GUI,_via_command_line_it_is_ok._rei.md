---
title: "can´t login to GUI, via command line it is ok. reinstall?"
date: 2022-12-28
forum: General Help
---

### Post by honzulal on 2022-12-28
Hi everybody, I am new one here. And absolutelly beginner with Ubuntu. But happened, that on one of my ntb Ubuntu is installed. Ver 18.04. Still woring ok, but few days ago, on login page to GUI, when I put my passwd inside..ntb seems.. working on progress but result is ..re-login. In a leap. When I try to login via command line, it is ok. I tried to change my passwd via recovedy mode..it´s done, but can´t get into GUI. Shall I reinstall that? I would like to save home directory and save this version 18.04. CPU is old celeron. Can somebody help me which image shall i download to reinstall the system?  Thanks in deep. Best regard @ alll. Jan

---

### Post by tea for one on 2022-12-28
> **honzulal said:**
> I would like to save home directory 
This is your first priority.
Are you familiar with booting into a live Ubuntu session and saving your data to another external device?

---

### Post by honzulal on 2022-12-28
i am not sure. i´ve never done it...

---

### Post by tea for one on 2022-12-28
Do you still have your original installation USB?
If not, here is a guide [https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview)
I would suggest that you use a lighter flavour such as Xubuntu (given that your CPU is an older Celeron)

Boot the PC in a live session via the PC boot menu (using the dedicated key to access the menu)
Select "Try Ubuntu"
Open the File manager.
Navigate to your /home/user/ directory.
Copy the data you need to another USB drive.

---

### Post by Impavidus on 2022-12-28
You're an absolute beginner running Ubuntu 18.04. Three possibilities: A: you installed an old version of Ubuntu; B: you installed Ubuntu at least 3 years ago and are a bit more experienced than an absolute beginner (but if you don't actively explore your system, you can still be a beginner after 3 years); C: you got the computer from someone else with Ubuntu already installed. Which of the three?

In any case, it appears that the GUI session crashes as soon as it starts. One of the possible reasons is that you don't have write permission on some vital files needed for login. Sudo misuse maybe? Make sure all files in your home directory (/home/username) are owned by you.

---

