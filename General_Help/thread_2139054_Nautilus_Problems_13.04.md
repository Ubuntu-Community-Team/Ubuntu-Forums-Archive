---
title: "Nautilus Problems 13.04"
date: 2013-04-25
forum: General Help
---

### Post by Geothermal123 on 2013-04-25
I am running 13.04, and I am having 2 nautilus issues. 

First, I like having delete without moving to trash being an option for both my user and root. I can edit the preferences in my account, but when I get root access of nautilus through gksu nautilus and I go to edit the preferences, the "files" menu does not fully drop down, so I cannot edit the prefences from the menu.

Second, I use the nautilus scripts and I put them in the new standard /home/$user/.local/share/nautilus/scripts. I can access my scripts when I right click on a file or folder, but not right clicking on my iconless desktop. Any suggestions?
.
Thanks

---

### Post by mc4man on 2013-04-25
> **Geothermal123 said:**
> I am running 13.04, and I am having 2 nautilus issues. 

First, I like having delete without moving to trash being an option for both my user and root. I can edit the preferences in my account, but when I get root access of nautilus through gksu nautilus and I go to edit the preferences, the "files" menu does not fully drop down, so I cannot edit the prefences from the menu.
.
You will need to either open dconf-editor as root & enable it there for root nautilus or run a dconf or gsettings command as root
Ex.
```
sudo gsettings set  org.gnome.nautilus.preferences enable-delete true
```

---

### Post by Geothermal123 on 2013-04-26
I opened dconf as root and when I went to check the enable-delete, it nothing happened. It wouldn't check the box. I guess maybe this feature is locked down?

---

### Post by mc4man on 2013-04-26
> **Geothermal123 said:**
> I opened dconf as root and when I went to check the enable-delete, it nothing happened. It wouldn't check the box. I guess maybe this feature is locked down?
Not sure how you opened dconf-editor as root, if done properly you'd be able to check the box.

Anyway because of the removal of gksu I'd not bother with ^, just do from command line as I posted.

---

### Post by Geothermal123 on 2013-04-26
I ran your command first and then used gksu (which I have installed) when your command didn't work for me.

---

