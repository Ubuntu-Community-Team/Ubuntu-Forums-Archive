---
title: "Sudo - Editing menu.lst"
date: 2008-06-22
forum: General Help
---

### Post by johnbradbury on 2008-06-22
Hi Guys,
I've just installed Gobuntu on my dell xps M1530. I'm having a problem with my touchpad going crazy. This seems to be a common problem with a simple fix. Sadly I'm also simple ....

I'm in a terminal windows... 

```
sudo john /boot/grub/menu.lst
```

and I get an unkown command: john

Please help....

---

### Post by drs305 on 2008-06-22
> **johnbradbury said:**
> Hi Guys,
I've just installed Gobuntu on my dell xps M1530. I'm having a problem with my touchpad going crazy. This seems to be a common problem with a simple fix. Sadly I'm also simple ....

I'm in a terminal windows... 

```
sudo john /boot/grub/menu.lst
```

and I get an unkown command: john

Please help....

```
sudo gedit /boot/grub/menu.lst
```

Change *gedit* to your favorite text editor. By the way, you will be asked for your password but won't see it as you type.

If you are in an ubuntu environment, may I suggest StartUp-Manager as a safer alternative to editing menu.lst manually?

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by sdennie on 2008-06-22
Out of curiosity, what is the simple fix you are talking about?  I have an XPS m1330 and the tap clicking was so annoying that I turned it off via System->Preferences->Mouse->Touchpad and everything works fine now.

---

### Post by johnbradbury on 2008-06-23
[http://ubuntuforums.org/showthread.php?t=808164&highlight=m1530]("http://ubuntuforums.org/showthread.php?t=808164&highlight=m1530")

Worked at treat once I was able to edit the menu.lst file

Thanks drs305 ...

---

