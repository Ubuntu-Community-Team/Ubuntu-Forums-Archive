---
title: "Disabling gdm/lightdm?"
date: 2013-01-29
forum: General Help
---

### Post by Gotti on 2013-01-29
How can I disable the whole login-ui? I want the computer to boot directly to command line, like a server install, so i can start fluxbox whenever i need to.

Secondly...if I wanted to just purge the whole gnome install...what packages would I have to remove?

Thanks!

---

### Post by matt_symes on 2013-01-29
Hi
 
Open a terminal and type
 
```
echo  "manual" | sudo tee /etc/init/lightdm.override
```
 
Enter your password. It will not be echoed to the screen.
 
That should overide light dm and stop it booting automatically.
 
Kind regards

---

### Post by sudodus on 2013-01-29
Add the boot option text after "quiet splash" in the file
/etc/default/grub

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
```
and run ```
sudo update-grub
```

---

