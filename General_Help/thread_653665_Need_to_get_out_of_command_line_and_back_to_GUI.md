---
title: "Need to get out of command line and back to GUI"
date: 2007-12-30
forum: General Help
---

### Post by galenanderson on 2007-12-30
I have a HP Pavilion laptop and was running only Ubuntu 7.10, no dual boot. I decided to hook another monitor up to the computer, it did not work. When i restarted my computer, i was in command line mode. I  gave it up as a lost cause because i have been so busy, but since I know nothing about command line OS's, (I got my first computer after DOS), my laptop is sitting unusable.
How can I put my computer back into GUI mode.

---

### Post by TidusBlade on 2007-12-30
Try those:
1. become root (su / password) and then type "/etc/init.d/xdm restart" - That's one way.
2. As a normal user, type "startx", and that will do the same thing.

---

### Post by meindian523 on 2007-12-30
or press Ctrl+Alt+F7 to check whether you already have a GUI running!If not,then use the above commands.

---

### Post by .nedberg on 2007-12-30
try this command:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

It reconfigures your xorg.conf file

---

### Post by galenanderson on 2007-12-30
> **TidusBlade said:**
> 
1. become root (su / password) and then type "/etc/init.d/xdm restart" - That's one way.
2. As a normal user, type "startx", and that will do the same thing.

The first did not work, "sudo /ect/init.d/xdm restart" returned "command not found"

The second, "startx" returned "Fatal Server Error: Requested Entity already in use!"
The next line says "fatal IO error 104"

Thanks though, any other ideas?

---

### Post by TidusBlade on 2007-12-30
Try:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the things and then
```
sudo dpkg-reconfigure gdm
```
Hope it works!

---

### Post by galenanderson on 2007-12-30
> **.nedberg said:**
> try this command:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

It reconfigures your xorg.conf file

Tried this, returned ```
"xserver-xorg postisnt warning: overwriting possibly-costomized configureation file; backup in /etc/x11/xorg.conf.20071230080003"
```

How do i do this backup?

Thanks

---

### Post by LaRoza on 2007-12-30
> **galenanderson said:**
> The first did not work, "sudo /ect/init.d/xdm restart" returned "command not found"


It is "etc" not "ect".

---

### Post by TidusBlade on 2007-12-30
To back that up, I think you gotta do this:
```
sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf.backup
```
Basically, copies the Xorg.conf file and renames it Xorg.conf.backup which you can rename it to xorg.conf if anything goes wrong.

---

### Post by .nedberg on 2007-12-30
The command in my previous post created a backup in /etc/x11/xorg.conf.20071230080003

After issuing the command you should be able to start X with above commands, or the easies would be to reboot with ```
sudo reboot
```

---

### Post by galenanderson on 2007-12-30
> **TidusBlade said:**
> To back that up, I think you gotta do this:
```
sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf.backup
```
Basically, copies the Xorg.conf file and renames it Xorg.conf.backup which you can rename it to xorg.conf if anything goes wrong.

No such file or directory.

I think that  this is my main problem. 

I will probably try and use a CD to reinstall. Any help would be appreciated, but i will be posting a new thread later.

Thanks for all of your time and help.
Galen

---

### Post by galenanderson on 2007-12-30
Never mind. I typed something in wrong, although i did get etc right. 

Finally after reviewing everything, i found that i misspelled some code from nedberg's original post.

Again, thank you all so much, im glad to have my computer back to a state where i can use it.

Thanks especially to nedberg, for giving me the help that did it.

Galen :KS

---

### Post by .nedberg on 2007-12-30
Glad it worked out right!

---

