---
title: "funpidgin broke pidgin"
date: 2008-05-05
forum: General Help
---

### Post by adredz on 2008-05-05
ok its my fault i installed funpidgin without taking precautionary actions...i thought it would install just fine. so i right clicked and opened it using gdebi. the process of installation was smooth but to my surprise, after the installation, gdebi prompted me to "install package"..again? it was supposed to say "package successfully installed" or whatever right? however, when i checked the dpkg.log..

> 2008-05-04 10:09:38 install funpidgin <none> 2.4.1-0ubuntu1
2008-05-04 10:09:38 status half-installed funpidgin 2.4.1-0ubuntu1
2008-05-04 10:09:38 status not-installed funpidgin <none> 

what does the log file above mean?
the problem is pidgin keeps crashing after i installed funpidgin. i tried to uninstall pidgin and remove the .purple folder in my home folder then reinstalled it back...no luck.. yes uninstalling funpidgin might be the solution but i don't know which package i should remove. i "sudo ap-get remove funpdigin" but it says it's not installed. i don't know how to completely remove it..help please...

---

### Post by edythemighty on 2008-05-05
Did you uninstall pidgin-data and libpurpl along with pidgin?

---

### Post by QCompson on 2008-05-05
> **adredz said:**
> ok its my fault i installed funpidgin without taking precautionary actions...i thought it would install just fine. so i right clicked and opened it using gdebi. the process of installation was smooth but to my surprise, after the installation, gdebi prompted me to "install package"..again? it was supposed to say "package successfully installed" or whatever right? however, when i checked the dpkg.log..

 

what does the log file above mean?
the problem is pidgin keeps crashing after i installed funpidgin. i tried to uninstall pidgin and remove the .purple folder in my home folder then reinstalled it back...no luck.. yes uninstalling funpidgin might be the solution but i don't know which package i should remove. i "sudo ap-get remove funpdigin" but it says it's not installed. i don't know how to completely remove it..help please...

Funpidgin is the same as pidgin but with two or three extra plugins included.  

I would suggest removing everything pidgin and funpidgin related (including .purple) and starting over.  Also, if the only functionality you need is to resize the text input box, try installing regular pidgin and adding the plugin found [here]("http://developer.pidgin.im/ticket/5296") ([http://developer.pidgin.im/ticket/5296](http://developer.pidgin.im/ticket/5296)).  

To uninstall funpidgin, try:
```
sudo dpkg -r funpidgin
```

---

