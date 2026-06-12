---
title: "Missing elements after update..."
date: 2007-08-13
forum: General Help
---

### Post by ljkwesi on 2007-08-13
Hello...

I'm here again for yet another problem... I've just done a clean install of Ubuntu with the mini.iso installer, and I ended up with Edgy (or it might have been Dapper, not too sure on this one)... So straight to the Update Manager I went, to upgrade the system to Feisty... So far, so good, or at least, seems so good.

The trouble comes up when I reboot after the update is complete. 

I get a nifty little "The NetworkManager applet could not find some required ressources. It cannot continue." Fortunately it doesn't impair my internet access, but hey, do I really wanna click "Ok" every time I boot up...

Next up, because one lonely problem wouldn't be cool enough, I get a bunch of error messages when loading nautilus as root... Here's a little preview :
```
kwesi@ubuntu:/media$ gksudo nautilus
Initializing gnome-mount extension

** (nautilus:10122): CRITICAL **: failed to load icon 'lpi-help': Icon 'lpi-help' not present in theme

(nautilus:10122): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed

** (nautilus:10122): CRITICAL **: failed to load icon 'lpi-translate': Icon 'lpi-help' not present in theme

(nautilus:10122): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed

** (nautilus:10122): CRITICAL **: failed to load icon 'lpi-bug': Icon 'lpi-help' not present in theme
```

Sure it's only icons missing, sure the nautilus runs fine, but hey, do I wanna have to read all this everytime I boot nautilus in command line as a root user ? Not that I care, but it's sign o' trouble to me... I did all the updates on my clean install without installing any programs or libs, so I only see two options :

- My computer smokes too much crack (or it might be me, who knows, and who cares ?)
- The update process is going wrong at some point...

Any ideas on how to get rid of these error messages/actually solve the problem would be nice... Thanks

PS. My configuration is : AMD Athlon 64 3000+, 512 Mb DRAM, on a MSI K8N Neo 2 Platinum board, some crappy ATI video card, 3 IDE Hard drives (160GB NTFS, 80GB NTFS, 6GB EXT3)... running Feisty 32 bits...

---

### Post by PaulFr on 2007-08-13
I think you might want to look at **[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/95833](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/95833)**.

---

### Post by ljkwesi on 2007-08-13
Seems like it's working, thanks for the link :)

Now for the NetworkManager applet, it stopped showing up after a third reboot... I'm not too sure what's going on, but it seems fixed for now...

---

