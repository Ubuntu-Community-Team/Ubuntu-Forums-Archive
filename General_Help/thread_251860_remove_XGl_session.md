---
title: "remove XGl session"
date: 2006-09-06
forum: General Help
---

### Post by crag277 on 2006-09-06
After several updates and some system tinkering my XGl session doesn't work anymore.  I don't really care, as it was always somewhat buggy and unstable for true everyday use.  Now I would like to remove it, and possibly try to get it working again, better this time.  How can I go about removing a session?  Thanks.

---

### Post by John.Michael.Kane on 2006-09-06
If you used a start up srcipt find it remove it. also go to system > Preferences > Sessions remove anything related to starting compiz. remove the packages using synaptic. 

reboot.

---

### Post by zaziork on 2006-11-15
If you installed your xgl session following the instructions [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL"), this removed the xgl session for me:

```
sudo apt-get remove xserver-xgl
```

Then:

```
sudo rm /usr/local/bin/startxgl.sh
```

Then: ```
sudo rm /usr/share/xsessions/xgl.desktop
```

Note: The above does not remove Beryl or Emerald (I wanted to switch to AIGLX). To do this, you need to remove everything you installed, for example:

```
sudo apt-get remove beryl emerald-themes
```

Hope this helps someone.

---

