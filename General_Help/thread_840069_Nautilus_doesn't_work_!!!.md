---
title: "Nautilus doesn't work !!!"
date: 2008-06-25
forum: General Help
---

### Post by ellobo82 on 2008-06-25
Hello everybody!

I installed UBUNTU HARDY few weeks ago and it was working perfectly...until...NAUTILUS STOPPED WORKING!

On the desktop I can see the icons but can't click on them (the same for the icons of mounted drives on the panel) and when I run "nautilus" on the terminal this is what I get :

ellobo@ElLobo:~$ nautilus
/home/ellobo/.themes/Toxig/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/ellobo/.themes/Toxig/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/ellobo/.themes/Toxig/gtk-2.0/gtkrc:58: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

I changed from Clearlooks to Human but nothing changed (except that this error message doesn't appear) and nautilus still doesn't work!

I tried to reinstall it and still it doesn't work... ](*,)

On the opposite "sudo nautilus" works greatly...

HELP! I have no idea of what to do!

---

### Post by iaculallad on 2008-06-25
What about doing a desktop re-installation:

Press Ctrl+Alt+F1

Stop GDM:

```
sudo /etc/init.d/gdm stop
```

Reinstall Gnome:

```
sudo apt-get --reinstall install ubuntu-desktop
```

Try activating GUI again and test Nautilus

```
startx
```

---

### Post by ellobo82 on 2008-06-25
Thanks...but it doesn't work!
I even tried to change theme (I used the clearlooks theme) and tried back to open nautilus on terminal...
and nothing!!!

The icons on destop disappeared!

I can't believe it appened without doing nothing at all...the day before it was working perfectly and then...

---

