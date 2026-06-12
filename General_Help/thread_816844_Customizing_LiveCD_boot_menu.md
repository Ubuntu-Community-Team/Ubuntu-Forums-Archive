---
title: "Customizing LiveCD boot menu"
date: 2008-06-03
forum: General Help
---

### Post by jeyaprabhuj on 2008-06-03
Hi ,

I am customizing Ubuntu using Reconstructor but till I get "Start or Install Ubuntu" as menu , i need to remove ubuntu from that and add my own name in it .

Also does ubuntu have a tool to replace the splash screen .

---

### Post by Forlong on 2008-06-03
> **jeyaprabhuj said:**
> Also does ubuntu have a tool to replace the splash screen .
Generally speaking? Yes, Startup-Manager -- it's in the repos:
```
sudo apt-get install startupmanager
```

---

### Post by Burbruee on 2008-06-03
> **jeyaprabhuj said:**
> Hi ,

I am customizing Ubuntu using Reconstructor but till I get "Start or Install Ubuntu" as menu , i need to remove ubuntu from that and add my own name in it .

Also does ubuntu have a tool to replace the splash screen .
I'm trying to do the same, I don't know how to remove the ubuntu menu from the live cd, but reconstructor has an option for splash screen. Just prepare a .png file 640x400 px and 256 colors and hit generate and it will be fine.

But, did you test your customized live cd yet? If so can you tell me if your "install ubuntu" option from the menu is also broken? The live option works fine, but install just takes me to a terminal. I could do 'startx' and it works, but that would just take me to the same place where I get by selecting the live option from the menu at the beginning. No installer is present.

---

### Post by jeyaprabhuj on 2008-06-09
Once I come to what you have mentioned I will respond how my Live CD works

---

