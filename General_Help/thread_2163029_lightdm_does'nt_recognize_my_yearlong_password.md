---
title: "lightdm does'nt recognize my yearlong password"
date: 2013-07-16
forum: General Help
---

### Post by sum1nil on 2013-07-16
I'm sure like most of us Ubuntu users, I enjoy trying to figure out my own problems and slaying a zombie walker on occasion...snarf. I have never ran into this problem with ubuntu however. Pulse audio died on me, not totally unheard of, however, I was also kicked back to the login screen. I entered my login and after a few seconds I hear the jungle drums and am kicked back to the lightdm login.
I went to root recovery and altered my login password then restarted lightdm. The same thing happened with the new login under lightdm. Jungle drums and a boot to the login screen. If I escape to a terminal both my username and password are acknowlgded but if I try to start Xorg/startx using sudo I get a listing of errors about X auhority. To sum up, lightdm even after a purge and re-install seems fubared but I can log in using a text terminal. Windows amazingly will boot without flaw or at least no more flaws than usual. At a loss in STL and would greatly appreciate help. I truly don't want to reinstall and I love my Ubuntu! Thank you.

---

### Post by Toz on 2013-07-16
Check the persmissions of the .Xauthority file in your home directory. If its not owned by you, you can change ownership or simply delete the file (it will be re-created). Also, check that you haven't run out of disk space.

---

### Post by sum1nil on 2013-07-16
I deleted the Xauthority to no avail and then apt-got nvidia current to reinstall the video driver which brought only further disaster. We all know there are wars of a kind between the tech companies. Nouveau, Nvidia, flash etc. We all know that the high tier providers are betraying the work a day users to the NSA via Prism. Soon we will just go back to books and await the digital dark age. I loved Mandrake and then Ubuntu but I suppose all good things come to their end, end blurp.

---

