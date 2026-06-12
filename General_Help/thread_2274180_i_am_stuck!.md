---
title: "i am stuck!"
date: 2015-04-18
forum: General Help
---

### Post by patrick81 on 2015-04-18
So i am pretty much at a deadline. My pc for some reason wont show the terminal (ctrl alt f1) and gives me a black screen. I heard you can fix that with the normal terminal (ctrl alt t) but i have a launcher issue that i cant do anything. All i get is a empty desktop. Please give me exact step by step instruction what i have to do since the terminal wont display on my screen.

Any help appriciated

---

### Post by uxbal on 2015-04-18
Hi there!

Maybe this will help you explore the issue further. : [http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-%3D-black-blank-screen-385376/](http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-%3D-black-blank-screen-385376/)

Regards,

---

### Post by grahammechanical on 2015-04-18
So, what is the problem? Is it that Ubuntu is loading to a desktop with wallpaper but without a top panel and the launcher on the left side? Do you want access to the terminal so that you can run some commands to fix this problem?

What happens when you right click the desktop? Does it bring up a menu? On new versions of Ubuntu the menu should include an Open Terminal option. Do you get that option? Does it work?

The main problem might be due to conflict with video drivers. If we are getting the menu from right clicking the wallpaper we can select Change Desktop Background. That will open System Settings at the Appearance utility. From there we can get to the main system settings window and go to Software & Updates>Additional Drivers tab. And there we can experiment with another video driver. We will need to restart each time.

When you switch to tty1 (Crtl+Alt+f1) you should get an invitation to log in. Do you not get that? What happens if you use Ctrl+Alt+F2 (tty2) or any F number up to F6? By the way Ubun tu is running on tty7. So, when you are finished with the Linux console (tty) log out and switch back to the desktop by Ctrl+Alt+F7

Regards.

---

### Post by patrick81 on 2015-04-18
Fixed. Reinstalled ubuntu after that. But then i had other problems. So now i reinstalled again. This is the 5th time already. Why ubuntu why u do this!!

---

### Post by oldos2er on 2015-04-18
When asking technical questions, please provide basic information such as Ubuntu version and hardware specs. Since your problem sounds as though it might be graphics related, knowing what video card you have and which drivers it's using (if known) would help others to help you.

---

