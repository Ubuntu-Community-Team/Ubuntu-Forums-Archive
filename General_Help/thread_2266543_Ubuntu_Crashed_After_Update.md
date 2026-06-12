---
title: "Ubuntu Crashed After Update"
date: 2015-02-23
forum: General Help
---

### Post by Billy_Martinez on 2015-02-23
Last night when I was using my Ubuntu machine, the little update icon popped saying that there were updates for my machine. I installed them and continued to use my computer and shut it down when I was finished with it. Now whenever I try to log into my account I get a blank desktop, there are no icons and the unity bar is missing. 

Please help

---

### Post by sammiev on 2015-02-23
You did not leave much info like the desktop version been used and flavor. 

Have you tried pressing "Ctrl + Alt + F1" you may get an login screen. If so add user-id and password. Next at the prompt type startx to see if you get your GUI back.

If all is good at this point, run software updater and reboot after.

Be sure to post back with all your computer specs as well as graphic card.

---

### Post by Billy_Martinez on 2015-02-23
> **sammiev said:**
> You did not leave much info like the desktop version been used and flavor. 

Have you tried pressing "Ctrl + Alt + F1" you may get an login screen. If so add user-id and password. Next at the prompt type startx to see if you get your GUI back.

If all is good at this point, run software updater and reboot after.

Be sure to post back with all your computer specs as well as graphic card.

Sorry I'm using Ubuntu 14, when I first discovered the problem I tried doing the "Ctrl + Alt + F1" command and for some reason it lead me to a black screen with no terminal. Then I rebooted the machine into the grub menu and used the "file system checker" in the Ubuntu recovery tools and that remedied the problem with the black screen. Then I did the "Ctrl + Alt + F1" command and logged into my machine and tried the apt-get update command and the apt-get upgrade command and then I did a reboot and, that didn't fix the problem.

---

### Post by Billy_Martinez on 2015-02-23
I was able to figure out the solution to my problem. It was an issue with the driver for my NVIDIA video card (GeForce GTX 750 Ti). I uninstalled the drivers that were currently installed and installed the latest ones from the terminal and I was able to log in.

How to uninstall your NVIDIA video card drivers.
[http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

How to install the latest drivers for your NVIDIA card.
[http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/)

I hope that this post helps anyone that's having the same issues with Unity.


  	 	**[[COLOR=#000000]sammiev[/COLOR]]("http://ubuntuforums.org/member.php?u=628319")**  	even though I was able to figure out the solution to my problem, 	thanks for trying to help me.

---

### Post by sammiev on 2015-02-23
NVIDIA video cards are well known for this problem, that's why I asked for the specs of your computer as well as graphic card.

Glad it all worked out for you.

---

