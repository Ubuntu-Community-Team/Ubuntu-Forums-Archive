---
title: "Title bars"
date: 2007-12-17
forum: General Help
---

### Post by enc on 2007-12-17
Hi everyone. I've been having problems with Gutsy. My title bars are extremely large in the GDM, and the Gnome desktop. I know there are fixes for both issues, the popular GDM fix works fine. 

However, turning the Compiz effects off and then on again to restore proper title bar size isn't going to work. I'm on a laptop, so I'm constantly rebooting; and turning the effects off and then back on doesn't actually fix the issue. 

A couple of weeks ago I found another fix for the desktop title bar problem, if I remember correctly it involved setting a screen size in the xorg.conf. However, I'm unable to find that particular fix again. I've spent quite a bit of time searching for it. I was wondering does anyone know exactly what the fix entails, or does someone know where that particular thread is? 

Thanks in advance.

---

### Post by pointone on 2007-12-17
I don't have the information you're looking for, but I had this same problem. My workaround was to have the following script run each session:

```
sleep 15
gtk-window-decorator --replace
```

---

