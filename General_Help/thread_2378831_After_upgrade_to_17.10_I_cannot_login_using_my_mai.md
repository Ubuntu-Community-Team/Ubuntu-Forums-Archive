---
title: "After upgrade to 17.10 I cannot login using my main user ID"
date: 2017-11-28
forum: General Help
---

### Post by yurad on 2017-11-28
Hello,
Two days ago I carelessly accepted a distro upgrade from 16.10 to 17.10 on my laptop Asus X556U. From  somewhat point the  laptop became unresponsive on the lock screen. I forced reboot via power button, After reboot the laptop was stuck prior to getting login screen. In failsafe mode I did receive a login screen, but the login didn't go through. I re-created xorg.conf. the resolution of the login screen was improved, but I couldn't login. After I enter the password, I am getting a black screen, and then I am  back to the login screen . Then I created another user id, and with user2 I am successfully login to Unity, But with my old user I still cannot login, looping: login screen, black screen, login screen.
I gzipped all "dot" files and directories, but it didn't change anything. Then I removed (moved to another destination) the home directory /home/user1 and recreated a new /home/user1 via mkhomedir_helper, but anyway I cannot login, having the same loop: login screen-black screen-login screen.
That's a mystery for me.  The new user2 has no issue, but the old user1 cannot login. Previously I was sure that all user information is stored in the home directory, but now I am doubting.
Could someone advise please how to restore my old user id?

---

### Post by yurad on 2017-11-28
I figured it out.
The problem was that it was set a wrong default desktop environment. I attached a screen shot.. I don;t know why, but there is Ubuntu on Xorg twice. One of them was set as a default. I changed  to  Unity.

---

### Post by mörgæs on 2017-11-28
Good, please mark the thread solved.

---

