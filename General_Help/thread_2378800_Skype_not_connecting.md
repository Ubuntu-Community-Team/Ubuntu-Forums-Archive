---
title: "Skype not connecting"
date: 2017-11-27
forum: General Help
---

### Post by lumaja2 on 2017-11-27
Ubuntu 16.04 LTS
  Skype 4.3
  
 
  Working with this Skype for years but now stop connecting.
  Enter User name then correct password and Skype off from the screen with no error.
 Contact Skype.com I enter user name and password and was connect to my account.
  How to fix this please.
 Thank you

---

### Post by ajgreeny on 2017-11-27
That version of Skype is no longer supported by Microsoft/Skype so you will now have to uninstall it and then use the new version from [https://go.skype.com/skypeforlinux-64.deb](https://go.skype.com/skypeforlinux-64.deb) and install it with ```
sudo apt install /Downloads/skypeforlinux-64.deb
```assuming the .deb file is in your Downloads folder, the default for browsers.

It is very different from the previous version and many users have had problems of empty, inactive windows when started minimised to the icon at boot time.
See my thread at [https://ubuntuforums.org/showthread.php?t=2376306](https://ubuntuforums.org/showthread.php?t=2376306) and the Microsoft Skype page at [https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_startms-skype_installms/upgraded-to-the-latest-skype-linux-version-but/34553112-f42c-4740-a435-a64ddf3ad89f](https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_startms-skype_installms/upgraded-to-the-latest-skype-linux-version-but/34553112-f42c-4740-a435-a64ddf3ad89f) 
You will find quite a lot of unsatisfied Skypeforlinux users at the Microsoft forum area.

---

### Post by lumaja2 on 2017-11-27
My Ubuntu is 32 bit not 64, can I still work with it or there is other way

---

### Post by ajgreeny on 2017-11-28
If your OS is 32 bit you can no longer install Skype as it is not available in that format any more; all you can do is use the skype for web as shown above.

---

