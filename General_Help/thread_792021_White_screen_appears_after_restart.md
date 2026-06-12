---
title: "White screen appears after restart"
date: 2008-05-12
forum: General Help
---

### Post by tbuht_1 on 2008-05-12
I just recently installed Ubuntu 8.04 and I enabled all the latest repositories and such and was restarting. However, I get a white screen when I am about to login. I can hear the login sounds and everything but the white screen continues to appear. Ctrl + alt + F7 gave me a message that there was something wrong with my B43 driver or some wireless problem.

Dell Inspiron 1520
NVidia GeForce 8600M GT
Vista/Ubuntu Dual-boot

Please help!!!
Thanks

---

### Post by TeoBigusGeekus on 2008-05-12
Reboot, enter recovery mode through grub and type
```
sudo dpkg-reconfigure xserver-xorg
```
This might able you to log on...

---

### Post by tbuht_1 on 2008-05-12
I restarted once and it worked fine but the second them I restarted after I made some more updates, I got the white screen again. Each time I enter what you told me to type is when it goes away. It keeps giving me some error with my ethernet adapter. It is trying to upgrade the B43 driver but gives me errors. Any ideas?

---

### Post by tbuht_1 on 2008-05-16
Should I try reinstalling once again? I have no idea what else to do...Any other suggestions?

---

### Post by strabes on 2008-05-16
This is a shot in the dark, but are you using desktop effects? If so, the white screen is a common bug while using the vesa (I believe) driver. Anyway, once you log in and get the white screen, try hitting Alt+F2 and typing in this command:```
killall compiz.real
```

Hit enter once you're done typing this out. Keep in mind that you'll have no visual feedback the entire time. If this works, let me know.

---

### Post by tbuht_1 on 2008-05-17
Thanks for the response but I don't have any desktop effects enabled yet, but I tried it anyway and it didn't change much. Still get the blank screen.

---

### Post by tbuht_1 on 2008-05-17
I also cannot get my graphic card to be enabled properly because I keep having to enable it through 'System -> Administration -> Hardware Drivers' after each logon. This is of course only through safe mode in which I have to follow TeoBigusGeekus' instructions. I tried installing Envy for nVidida but I still am having problems. I  cannot get the white screen to go away.

---

### Post by strabes on 2008-05-17
Well, your first mistake was using envy. It seems that you haven't had much luck with this install; would it be too much of a problem to reinstall? It only takes 30 minutes or so. Please use the restricted drivers manager next time.

---

### Post by tbuht_1 on 2008-05-17
Actually I started with the restricted drivers manager first but didn't have much success, but I think I'm gonna go ahead with the reinstallation.

---

### Post by tbuht_1 on 2008-05-17
Something is seriously terribly wrong. Even after reinstallation, I got everything to work normally at first, but after making a few updates and having to restart, the white screen of death came back to haunt me!!! Is there any program I can use to completely remove my Ubuntu partition, and have it reallot it to my Vista partition, so that I can try from scratch all over again? I don't know why I'm having such a hard time with this... 
:(

---

### Post by ertw1 on 2008-09-11
FIXED!

Go to [http://ph.ubuntuforums.com/showthread.php?t=712479&page=4](http://ph.ubuntuforums.com/showthread.php?t=712479&page=4)

Credit goes to OlaNordmann

Download and install the nvidia beta driver [http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

---

