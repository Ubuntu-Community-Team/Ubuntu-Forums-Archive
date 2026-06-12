---
title: "How to hide an application from the application list"
date: 2014-11-02
forum: General Help
---

### Post by miceagol on 2014-11-02
I have replaced Nautilus with Nemo. Although I've made Nemo the default file manager, Nautilus still shows up in the application list when searching for either Nautilus or Files. I'd like to hide Nautilus completely from the search (*), so that the less tech-savvy in the family do not use it. How?

(*) The reason I want to disable Nautilus is a bug after installing the Gnome Desktop Environment, which makes it impossible to resize the Nautilus window.

[ATTACH=CONFIG]257700[/ATTACH]
Which one is Nemo?

---

### Post by miceagol on 2014-11-02
This must be my record in time solving something myself after posting. :)

Applications can be removed from the applications list by renaming or removing the associated file from **/usr/share/applications** or **~/.local/share/applications**

I removed Nautilus by running this in the /usr/share/applications folder:
```

sudo mv nautilus.desktop nautilus.desktop.hidden

```

---

