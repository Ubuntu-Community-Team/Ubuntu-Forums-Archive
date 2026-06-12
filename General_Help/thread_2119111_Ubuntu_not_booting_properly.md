---
title: "Ubuntu not booting properly"
date: 2013-02-23
forum: General Help
---

### Post by WizardlyPenguin on 2013-02-23
Hi I'm new to using Linux as a actual OS instead of using a virtual machine and there is a problem when I boot. I'll boot then after it loads, I see my mouse and a background but nothing else. It is a good job I dual booted windows 8 and Ubuntu so I could post this.
Regards.

---

### Post by carl4926 on 2013-02-23
Can we assume you are using Ubuntu? (not: Kubuntu, Edubuntu, Xubuntu and Lubuntu) And version 12.10?

Before you installed... did you try it live? And was it OK?

---

### Post by WizardlyPenguin on 2013-02-23
Yes I'm using Ubuntu 12.10, I tried it live it seemed to be ok so I installed the OS Booted it worked fine, until I did the updates. The up dates could of caused the problem, but I needed to get them because they had my graphics drivers in them and I was going to download steam.

---

### Post by carl4926 on 2013-02-23
> **WizardlyPenguin said:**
> Yes I'm using Ubuntu 12.10, I tried it live it seemed to be ok so I installed the OS Booted it worked fine, until I did the updates. The up dates could of caused the problem, but I needed to get them because they had my graphics drivers in them and I was going to download steam.

So you seem to be suggesting that it worked OK just after install, but after updates, not so good?

Just after install,  would be using the default driver for graphics.

What graphics device is it? Or is it Hybrid?

---

### Post by WizardlyPenguin on 2013-02-23
It is a AMD 6970 1GB GDDR5 dedicated card. This card has always worked with me for anything and has had no problems in the past.

---

### Post by carl4926 on 2013-02-23
At the grub boot menu
If you choose Advnaced option and then toggle down the resulting list to a older kernel, and hit enter
Will it boot with any of those?

---

### Post by WizardlyPenguin on 2013-02-23
I tried it and it did the exactly the same thing. But I realized when I do Ctrl+Alt+Del I can log out. It looks normal then, but when I log in it goes back to the thing where I only have my mouse. Also, after I updated, I think the graphics drivers worked because my monitor is at a higher resolution.

---

### Post by carl4926 on 2013-02-23
I'm not sure...
Have you tried the Guest user login
Does the same happen?

---

### Post by geekytechie on 2013-02-23
> **WizardlyPenguin said:**
> Hi I'm new to using Linux as a actual OS instead of using a virtual machine and there is a problem when I boot. I'll boot then after it loads, I see my mouse and a background but nothing else. It is a good job I dual booted windows 8 and Ubuntu so I could post this.
Regards.

 Distributions ain't an issue for now, this [[COLOR="RED"]LINK[/COLOR]]("http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html?m=1") might resolve your issue B-)

---

### Post by WizardlyPenguin on 2013-02-23
Don't worry I solved it. All I did was reinstall Ubuntu and installed the updates and works like a dream now. Thanks for the replies though :p.

---

