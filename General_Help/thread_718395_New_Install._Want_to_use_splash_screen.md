---
title: "New Install. Want to use splash screen"
date: 2008-03-08
forum: General Help
---

### Post by Laughed on 2008-03-08
I am reinstalling gutsy because of to many issues with the last run. Anyway, the only way I could get the last install to boot up correctly was to delete "splash" from menu.lst and the boot line after "ro quiet" 

Hopefully someone knows what I am talking about. The thing is, I kinda want the splash screen to be there (though I have never actually seen it on any install to date). Is there a fix???

---

### Post by dcstar on 2008-03-08
> **Laughed said:**
> I am reinstalling gutsy because of to many issues with the last run. Anyway, the only way I could get the last install to boot up correctly was to delete "splash" from menu.lst and the boot line after "ro quiet" 

Hopefully someone knows what I am talking about. The thing is, I kinda want the splash screen to be there (though I have never actually seen it on any install to date). Is there a fix???

Open a terminal and edit the first file to be 1024 768, then add "vga=791" to the end of your grub boot string:

```
gksudo gedit /etc/usplash
sudo update-initramfs -u
gksudo gedit /boot/grub/menu.lst
```

---

