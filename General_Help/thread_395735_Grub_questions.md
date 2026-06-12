---
title: "Grub questions"
date: 2007-03-28
forum: General Help
---

### Post by Biffy on 2007-03-28
Hi, i have a couple of Grub questions:

1) After some searching, i understand that grubconf is no longer an active project and therefore not in the repos anymore. On the project homepage, there says that a grub editor should exist in the Gnome System Tools package. I can't find this editor anywhere tough, what's the command to start it? Using Fluxbox, so gnome directions won't help.

2) When booting the kernel, it seems that the system isnt printing wich services it is starting. Normally you get something like "Starting DBUS    ok" when you boot. This is not happening on my computer at all. The system is working fine tough so im pretty sure they are being loaded. I bet this is a option you can edit in grub when booting the kernel. What is it called? Or any other ideas?

---

### Post by jerryrw on 2007-03-28
you can edit the grub kernel options in /boot/grub/menu.lst with any text editor

sudo gedit /boot/grub/menu.lst

---

### Post by Biffy on 2007-03-28
> **jerryrw said:**
> you can edit the grub kernel options in /boot/grub/menu.lst with any text editor

sudo gedit /boot/grub/menu.lst

Yes, but what shall i type when im editing menu.lst? I am looking for an option wich i dont know the name of.

---

### Post by Repabil on 2007-03-28
> **Biffy said:**
> Yes, but what shall i type when im editing menu.lst? I am looking for an option wich i dont know the name of.
I'm not wholly understood with grub but if you're looking to have it spit out the messages as it boots and loads I think you'll have to leave out the parameter *quiet* from the *kernel* command of the posts you want this feature from. Note that you'll have to edit this configuration file as administrator. Like ```
sudo nano /boot/grub/menu.lst
```

Remember to backup this file before you edit it to have something to fall back on if all goes haywire.

For example if there's a line like this:```
title           Ubuntu, kernel 2.6.17-11-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=2bf30ef3-e946-4d2b-b83b-2b53be83a5fe ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot
```
Leave out the *quiet* like:```
title           Ubuntu, kernel 2.6.17-11-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=2bf30ef3-e946-4d2b-b83b-2b53be83a5fe ro splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot
```
And I bet this post in your grub will boot showing what's loaded and so on.

---

### Post by Biffy on 2007-03-29
> **Repabil said:**
> I'm not wholly understood with grub but if you're looking to have it spit out the messages as it boots and loads I think you'll have to leave out the parameter *quiet* from the *kernel* command of the posts you want this feature from. Note that you'll have to edit this configuration file as administrator. Like ```
sudo nano /boot/grub/menu.lst
```

Remember to backup this file before you edit it to have something to fall back on if all goes haywire.

For example if there's a line like this:```
title           Ubuntu, kernel 2.6.17-11-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=2bf30ef3-e946-4d2b-b83b-2b53be83a5fe ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot
```
Leave out the *quiet* like:```
title           Ubuntu, kernel 2.6.17-11-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=2bf30ef3-e946-4d2b-b83b-2b53be83a5fe ro splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot
```
And I bet this post in your grub will boot showing what's loaded and so on.

Thanks! That was exactly what i was looking for! :)

Now, when the menu.lst file has been edited, what do i type to write the changens to MBR?

And oh, do you know anything about the replacement for grubconf?

---

### Post by Repabil on 2007-03-29
> **Biffy said:**
> Now, when the menu.lst file has been edited, what do i type to write the changens to MBR?You don't have to write anything to MBR for it to work. If you already got grub installed in MBR it will read your configuration file from where it's at.
> **Biffy said:**
> And oh, do you know anything about the replacement for grubconf?Afraid not, dunno if I even tried grubconf.

---

### Post by Biffy on 2007-03-29
> **Repabil said:**
> You don't have to write anything to MBR for it to work. If you already got grub installed in MBR it will read your configuration file from where it's at.
Afraid not, dunno if I even tried grubconf.

Neat! Thanks for your help dude! I'll try this tomorrow. :popcorn:

---

