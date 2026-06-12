---
title: "Ubuntu/Windows7"
date: 2019-05-28
forum: General Help
---

### Post by aligator88 on 2019-05-28
Hello!

I need a help. I'm new in Linux, I wanted to install ubuntu and installed successfully with the Universal USB installer. My notebook has frozen and I was forced to shutdown.
When I started notebook again, appeared boot only for Ubuntu.
I wanted to have both of OS windows and Ubuntu and to have possibility to select during the boot.
But unfortunately I can select only Ubuntu. 
Now I would like to delete Ubuntu in order to recover all the information  that I had on windows.

If you can help me, please explain like for a noob.

---

### Post by oldfred on 2019-05-28
May be best to see details, use ppa version (2nd option) with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by aligator88 on 2019-05-28
And if I don't have internet what should I do?
attached 2 photos

---

### Post by LwIh%*7 on 2019-05-28
> **aligator88 said:**
> And if I don't have internet what should I do?
attached 2 photos

If you can't get Wi-Fi for some unknown reason could you try following this guide and see what happens afterwords? 

Link:
[https://www.maketecheasier.com/fix-wi-fi-not-working-ubuntu/](https://www.maketecheasier.com/fix-wi-fi-not-working-ubuntu/)

It should try and fix the Wi-fi issue not detected etc. 

Also as for the Grub not finding Windows 7 do you have the os-prober component installed? Once that is installed and the command update-grub issued then grub should have no issue in finding the Windows partition thus if it does find it then you should be able to then boot into Windows on the selection menu.

---

### Post by aligator88 on 2019-05-28
Unfortunately the link is not working

---

### Post by oldfred on 2019-05-28
If wireless not working use a cable and hardwired connection. Then you can update drivers from Internet and get WiFi working and potentially fix other issues. 
Hardwired always best for initial install as faster & fewer issues.

---

### Post by aligator88 on 2019-05-30
@oldfred Thank you for the help. I just needed a wire internet connection and with help of this link [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) managed to boot normally to windows. Have a great day.

---

### Post by HermanAB on 2019-05-30
If you dabble with Linux/BSD a lot and you don't have a convenient wired connection, then get a Wifi Extender with an ethernet port.  You can then plug into that until you get the on-board WiFi to work.

---

