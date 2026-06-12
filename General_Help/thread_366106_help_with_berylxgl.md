---
title: "help with beryl/xgl"
date: 2007-02-20
forum: General Help
---

### Post by Somenoob on 2007-02-20
I followed this tutorial [link]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL") and everything went well I think. but I have 3 problems with it.

1. Not important but I named the the login entry "Xgl-Beryl" but it's named "foo" in the login window. I accidentally  forgot the = character first, but apparently the change didn't apply so how do I remove a login entry? 

2. Xgl runs slowly, but I managed to run my preferred font and theme.

3. When I switch the window manager to Beryl it fails to load.

---

### Post by strabes on 2007-02-20
I have noticed a big performance hit with XGL as well.

To remove the session you created you can simply delete the file that you created. In that guide, it's /etc/X11/sessions/xgl.desktop. So, just run ```
sudo rm /etc/X11/sessions/xgl.desktop
```

Run beryl-manager from a terminal, and paste the output when you try to switch the window manager to beryl.

---

