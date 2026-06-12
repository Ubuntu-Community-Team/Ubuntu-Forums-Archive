---
title: "Setting default permissions for pseudo terminals"
date: 2008-05-30
forum: General Help
---

### Post by mfyahya on 2008-05-30
Is there a way to set default permissions for the pseudo termnals in /dev/pts. Currently they are
The reason I want to do is that my wife is usually logged in the gnome desktop, and I frequently su to myself in a terminal and restore a screen session of whatever I was doing earlier. 
When I do this now, here's what happens
```

$ su - mfyahya
$ screen -r
Cannot open your terminal '/dev/pts/2' - please check.
$ ls -l /dev/pts/2
crw--w---- 1 thewife tty 136, 2 2008-05-30 22:28 2

```
so then I have to do
```

$ sudo chown mfyahya /dev/pts/2
$ screen -r
** mutt session continues ** 

```
So I'd like to know if I can configure the terminals so that they have read and write permission for the tty group. Then I'd just add myself to the ttyp group. 

Or is there another way to do this?

Thanks!

---

### Post by ibuclaw on 2008-05-30
You may find the file **devpts** in **/etc/default** exceptionally useful...

```
nano /etc/default/devpts
```

Regards
Iain

---

### Post by ibuclaw on 2008-05-30
Just incase you get lost...

A Step-by-Step guide would be:
```

sudo usermod -a -G tty mfyaya
sudo sed -i -e '/TTYMODE/s/620/660/' /etc/default/devpts

```

Reboot and your problem should be fixed...

Regards
Iain

---

