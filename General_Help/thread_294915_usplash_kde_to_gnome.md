---
title: "usplash kde to gnome"
date: 2006-11-07
forum: General Help
---

### Post by heathenx on 2006-11-07
i'm having a heck of a time changing my usplash back to the default gnome theme instead of the kubuntu theme. can anyone help?

i typically use gnome on ubuntu edgy and just installed kde yesterday to check it out. now when i boot-down and boot-up, i get the kubuntu usplash. 

i have installed gnome-splashscreen-manager but it doesn't seem to work. in my /usr/lib/usplash dir i have the following:

usplash-artwork.so
usplash-theme-kubuntu.so
usplash-theme-ubuntu.so

---

### Post by Ramses de Norre on 2006-11-07
```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by heathenx on 2006-11-07
ahh! well, that tip got me half way there. now when i re-boot i no longer see the kubuntu usplash and see the ubuntu usplash instead. great! however, after i pass the bios on booting up i still get the kubuntu usplash.

perhaps there is a bug in edgy or do i need to run a different command. i ran your command several times, btw.

thanks for your help, Ramses de Norre

---

### Post by Ramses de Norre on 2006-11-07
What about these: ```
sudo dpkg-reconfigure linux-image-`uname -r`
sudo dpkg-reconfigure usplash
```

---

### Post by heathenx on 2006-11-07
sweet! it worked.

**sudo dpkg-reconfigure linux-image-`uname -r`** did not work. :(  

**sudo dpkg-reconfigure usplash** worked. :-D 

i really appreciate your help. thank-you, Ramses de Norre.

---

### Post by Audimage on 2006-11-07
It happens to me too, I only get the ubu spash when shuting down, not booting up.

---

