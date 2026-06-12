---
title: "Chinese input on an English system"
date: 2007-05-20
forum: General Help
---

### Post by wanchai on 2007-05-20
I followed the instructions given in [https://help.ubuntu.com/community/SCIM]("https://help.ubuntu.com/community/SCIM"). When I select Chinese as the session language everything works fine, Chinese and English input are possible and CTRL-Space allows me to switch between the two. But when I run the system (feisty) in English, which is what I normally do, CTRL-Space does nothing and I'm stuck with Latin characters. Can switching input methods be enabled somehow when a non-Chinese language is selected for the session?

Some configuration:

```

$>cat ~/.scim/global 
/DefaultKeyboardLayout = US_Default
/SupportedUnicodeLocales = en_US.UTF-8,de_DE.UTF-8,zh_HK.UTF8

$>ls -ogl ~/.xinput.d/
total 0
lrwxrwxrwx 1 28 2007-05-20 20:58 en_GB -> /etc/X11/xinit/xinput.d/scim
lrwxrwxrwx 1 28 2007-05-20 21:21 zh-HK -> /etc/X11/xinit/xinput.d/scim

```

---

