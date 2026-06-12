---
title: "Xubuntu 18.04 screen tearing...."
date: 2019-08-14
forum: General Help
---

### Post by Furycd001 on 2019-08-14
HI Guys.. I'm running xubuntu 18.04 with Nvidia GM108M [GeForce 940MX] & nvidia-driver-430 (propritary, tested) installed. I have followed ["this post"]("http://ubuntuhandbook.org/index.php/2018/07/fix-screen-tearing-ubuntu-18-04-optimus-laptops/") to try and fix screen tearing, but it still persists. In the post it says that the final command should output a "Y" but I always seem to get a "N". Could someone please help....

---

### Post by &amp;wP*!) on 2019-08-14
> **jonny6 said:**
> HI Guys.. I'm running xubuntu 18.04 with Nvidia GM108M [GeForce 940MX] & nvidia-driver-430 (propritary, tested) installed. I have followed ["this post"]("http://http://ubuntuhandbook.org/index.php/2018/07/fix-screen-tearing-ubuntu-18-04-optimus-laptops/") to try and fix screen tearing, but it still persists. In the post it says that the final command should output a "Y" but I always seem to get a "N". Could someone please help....

The link you have pasted above is dead.

---

### Post by Furycd001 on 2019-08-14
> **pencuse said:**
> The link you have pasted above is dead.

Sorry.. Fixed now....

---

### Post by coffeecat on 2019-08-14
Hi.

I won't be able to help you with your screen tearing as I have no experience of that family of nvidia graphics cards, but a question for you and a comment about that linked "tutorial".

Are you sure you have Optimus? You make no mention of an Intel GPU. The tutorial is for Optimus.

Somewhat more importantly, the author of that tutorial has made an absolutely heinous and inexcusable technical error in one of the commands. This:

```
sudo gedit /etc/modprobe.d/nvidia-drm-nomodeset.conf
```

That is not far short of an abomination. One should never use bare sudo for opening graphical applications. Although there is a caveat on the [Ubuntu RootSudo community wiki page](https://help.ubuntu.com/community/RootSudo) about it containing out of date information, the section on [Graphical sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo) should be heeded. This:

> You should never use normal sudo to start graphical applications as root. Using sudo with graphical apps has the potential to corrupt your environment by allowing root to take ownership of and/or change permissions on critical files that you must own. The forums frequently see panicked requests for help from users who can no longer log in after running graphical applications under sudo. 

Personally, I would be chary of following a tutorial with such an egregious error.

Hopefully, someone here will be able to help you with the screen tearing. Good luck!

---

### Post by Furycd001 on 2019-08-14
Thanks for replying. Not sure if the card I have is a optimus or not, but most of the tutorials or post that I came across had the same commands etc. I actually don't have gedit installed so I switched that part out for nano. I had the same problem in 16.04 which someone on these forums helped me with. Tried that first, but it never worked....

---

### Post by Furycd001 on 2019-08-14
my problem appears to have solved itself. I now get a "Y" & screen tearing seems to be gone....

---

