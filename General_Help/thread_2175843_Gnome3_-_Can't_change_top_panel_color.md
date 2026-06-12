---
title: "Gnome3 - Can't change top panel color"
date: 2013-09-21
forum: General Help
---

### Post by _0R10N on 2013-09-21
Hi everyone!

I have Ubuntu 13.04 + gnome3.8 and I can't change the color of the top panel, which is always black (with some themes only the font changes).

- Yes, I have installed gnome-tweak-tool
- Yes, I have installed the User Themes extension.
- Yes, I have tried with different themes (that are supposed to have a transparent panel, like Nord and Zukitwo-Shell).
- Yes, the themes previously mentioned are gnome3.8 compatible.

Please, advice!

Thanks!

---

### Post by Frogs Hair on 2013-09-21
You can try restarting the theme per the link. [http://askubuntu.com/questions/214856/how-to-reload-gnome-shell-theme-via-a-command](http://askubuntu.com/questions/214856/how-to-reload-gnome-shell-theme-via-a-command)

---

### Post by _0R10N on 2013-09-21
> **Frogs Hair said:**
> You can try restarting the theme per the link. [http://askubuntu.com/questions/214856/how-to-reload-gnome-shell-theme-via-a-command](http://askubuntu.com/questions/214856/how-to-reload-gnome-shell-theme-via-a-command)

Thanks for your reply. Unfortunately it didn't work.

Something I noticed when I started my system is that the panel appeared transparent, and then, when it completed loading everything, it went black.

---

### Post by buzzingrobot on 2013-09-21
Much of gnome-shell is config'd by CSS and Javascript.  /usr/share/gnome-shell might be worth rummaging in.

---

### Post by _0R10N on 2013-09-21
> **buzzingrobot said:**
> Much of gnome-shell is config'd by CSS and Javascript.  /usr/share/gnome-shell might be worth rummaging in.

Yes, I changed #panel options with this

#panel {
    color: #ffffff;
    /*background-color: black;*/
    background-color: rgba(0,0,0,0.6);
    /*border-image: url("panel-border.svg") 1;*/
}

Now, some themes have a transparent panel. Problem is that applications take over that space, so I'm back to the black panel.

---

