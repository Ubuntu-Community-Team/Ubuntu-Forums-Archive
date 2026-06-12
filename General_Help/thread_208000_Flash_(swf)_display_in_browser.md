---
title: "Flash (swf) display in browser"
date: 2006-07-02
forum: General Help
---

### Post by Byronious on 2006-07-02
I don't know if anyone else is having this issue, but flash files located within webpages are not displaying correctly. They are sometimes not playing, or are displaying completely wrong. Is there a way to solve this, or is it something I just have to live with?

---

### Post by jimmygoon on 2006-07-02
[QUOTE=Byronious]I don't know if anyone else is having this issue, but flash files located within webpages are not displaying correctly. They are sometimes not playing, or are displaying completely wrong. Is there a way to solve this, or is it something I just have to live with?[/QUOTE]

did you install gnash or flash macromedia non free?

---

### Post by Byronious on 2006-07-02
I installed everything I could find pertaining to flash in synaptic. libflash-mozplugin is what I believe is installed and being used to display them. If I remove it, firefox wants to install the plugin but it cannot install it through firefox.

---

### Post by Winblowz on 2006-07-02
Try this in the terminal (command prompt)...
```
sudo aptitude purge libflash-mozplugin 
sudo aptitude install flashplugin-nonfree
sudo update-flashplugin
```
Then, restart Firefox.

---

### Post by az on 2006-07-02
[QUOTE=Byronious]I installed everything I could find pertaining to flash in synaptic. libflash-mozplugin is what I believe is installed and being used to display them. If I remove it, firefox wants to install the plugin but it cannot install it through firefox.[/QUOTE]
flashplugin-nonfree is in the multiverse repository.  You just install it and you are good to go.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Byronious on 2006-07-03
Wow, I can't believe I missed that in the Wiki after looking at that page for playing movie formats. Thank you all for your help, it is working wonderfully now.

---

