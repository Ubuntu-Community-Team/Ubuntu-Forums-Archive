---
title: "Trash icon, Ubuntu 20.04"
date: 2020-05-04
forum: General Help
---

### Post by mrwaistcoat on 2020-05-04
Is it possible to remove it from the dock?  I've used tweak to remove it from the desktop, but either using the native dock or dash to dock, there is no option to remove the icon.

Thanks

---

### Post by ipv on 2020-05-04
here you go :

[https://askubuntu.com/questions/965881/how-do-i-remove-trash-icon-from-gnome-desktop](https://askubuntu.com/questions/965881/how-do-i-remove-trash-icon-from-gnome-desktop)

---

### Post by deadflowr on 2020-05-04
> **ipv said:**
> her you go :

[https://askubuntu.com/questions/965881/how-do-i-remove-trash-icon-from-gnome-desktop](https://askubuntu.com/questions/965881/how-do-i-remove-trash-icon-from-gnome-desktop)

Comically the command linked isn't what would work, but it is very close, just change out desktop-icons for dash-to-dock and you've got a winner.
The link is this command
```
gsettings set org.gnome.shell.extensions.desktop-icons show-trash false
```
but the trash icon in the dock is a dock feature, so you need to replace desktop-icons with dash-to-dock like so
```
gsettings set org.gnome.shell.extensions.dash-to-dock show-trash false
```

---

### Post by ActionParsnip on 2020-05-04
Great share. Hopefully this will help others

---

### Post by mrwaistcoat on 2020-05-05
Brilliant stuff. many thanks

---

### Post by ipv on 2020-05-05
> **deadflowr said:**
> Comically the command linked isn't what would work, but it is very close, just change out desktop-icons for dash-to-dock and you've got a winner.


my bad i overlooked the word ' dock ' in the OP. thank you for the correction.

---

### Post by deadflowr on 2020-05-05
> **ipv said:**
> my bad i overlooked the word ' dock ' in the OP. thank you for the correction.

I just thought it was funny how both commands are so similar,
of course run both and eliminate trash on the desktop completely.

---

