---
title: "2 Hard Drives - 1 WinXP, 1 Ubuntu - Help"
date: 2006-08-02
forum: General Help
---

### Post by v8YKxgHe on 2006-08-02
Hey,

I've convinced my boss at work to Install Ubuntu on my PC for Web Dev, he'd still like to keep WinXP though. I told him I have a spare hard drive at home, which I could bring in and install Ubuntu on. 

I'm fine with installing Ubuntu, done it many times - but i've never really played around with GRUB and the cabel setup that will be needed for the hard drives ( Master/Slave etc ). I'd like it if Ubuntu was the first option selected, then it will ask you which to load either Ubuntu or WinXP - then it will select the correct hard drive and carry on loading the selected OS. 

Anyhelp would be great =)

---

### Post by Ramses de Norre on 2006-08-02
Set the jumper of the drive containing windows as master and set the one you want to install ubuntu on as slave or sec master. Windows wont boot if you set the drive it's on to slave.

Then install ubuntu and pick the right device to partition when asked. Grub will be installed and normally windows should be found without any problem and it will be in your grub menu.

By default ubuntu will be the first option but you can change this afterwards if you want.

---

### Post by v8YKxgHe on 2006-08-02
Thanks very much =) Easier than I thought then, cool thanks

---

