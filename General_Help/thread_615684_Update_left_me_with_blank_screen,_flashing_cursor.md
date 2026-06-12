---
title: "Update left me with blank screen, flashing cursor"
date: 2007-11-17
forum: General Help
---

### Post by ageilers on 2007-11-17
I have Kubuntu Feisty. I did an update the day before yesterday that I think included the kernel. Now I boot into a bank screen with a flashing cursor. I was able to boot into the old kernel, and in trying to fix with 

```
sudo dpkg --configure -a
```

I broke that kernel as well. How can I get back to a working GUI??

Desperate!

---

### Post by overdrank on 2007-11-17
> **ageilers said:**
> I have Kubuntu Feisty. I did an update the day before yesterday that I think included the kernel. Now I boot into a bank screen with a flashing cursor. I was able to boot into the old kernel, and in trying to fix with 

```
sudo dpkg --configure -a
```

I broke that kernel as well. How can I get back to a working GUI??

Desperate!

HI what graphics card does the system have? Have you tried to reconfigure your xorg? 
 From recovery mode. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
```

---

### Post by ageilers on 2007-11-19
I have a Nvidia 7800GS. I think the nvidia-glx package was updated as well.I will try that when I get home.

Thanks.

---

