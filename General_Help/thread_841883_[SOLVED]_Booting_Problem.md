---
title: "[SOLVED] Booting Problem"
date: 2008-06-26
forum: General Help
---

### Post by WeEatVista on 2008-06-26
I'm not sure if this has been addressed anywhere. If it has, point me in the right direction.

When I turn on my computer, Grub loads, then the pretty Ubuntu splash screen loads. Once the splash screen is finished, the boot goes:

* Reading Files Needed to Boot... [OK]
* Setting preliminary Keymap... [OK]
* Preparing Restricted Drivers... [OK]
* Setting the System Clock... [OK] 
* Starting Basic Networking... [OK]
* Starting Kernel Event Manager... [OK]
* Loading Hardware Drivers... [OK]
* Setting the System Clock... [OK]
* Loading Kernel Modules... [OK]
* Loading Manual Drivers... [OK]
* Setting Kernel Variables... [OK]
* Activating Swap... [OK]
* Checking root file systems... [OK]
* Checking File Systems... [OK]

And the list keeps going on, it's impossible to name everything that it shows. I want my Ubuntu Laptop to do a normal boot where it goes into the splash screen then right into log in screen, I don't want to see this. Any suggestions?

Thanks,

We Eat Vista

---

### Post by drs305 on 2008-06-26
> **WeEatVista said:**
> I'm not sure if this has been addressed anywhere. If it has, point me in the right direction.
And the list keeps going on, it's impossible to name everything that it shows. I want my Ubuntu Laptop to do a normal boot where it goes into the splash screen then right into log in screen, I don't want to see this. Any suggestions?

Thanks,

We Eat Vista

Install StartUp-Manager, a grub menu.lst editor.
```
sudo aptitude install startupmanager
```

Open it via System, Administration, StartUp-Manager.

In the Boot Options Tab, uncheck "Show text during boot" and optionally tick "Show Boot Splash".

StartUp-Manager is a safe and easy method of changing a variety of boot options without having to manually edit the actual file.

For more information:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by WeEatVista on 2008-06-26
Thanks for your help, but when I installed bootup-manager, show text was already unchecked and show boot splash was checked. I restarted and it still, after the splash screen, shows that writing.

any other suggestions?

Thanks,

We Eat Vista

---

### Post by drs305 on 2008-06-26
> **WeEatVista said:**
> any other suggestions?


Look at /boot/grub/menu.lst:
```
cat /boot/grub/menu.lst
```

In the main menu area, does your default boot selection look like this at the end of the kernel line and at the bottom (2 places):
```

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro splash **quiet**
initrd		/boot/initrd.img-2.6.24-19-generic
**quiet**

```

If you don't see "**quiet**" add it. Note: This will not eliminate all messages, just some.
```

cp /boot/grub/menu.lst /boot/grub/menu.lst-bak1
gksudo gedit /boot/grub/menu.lst

```

---

### Post by WeEatVista on 2008-06-26
Thanks for the fast reply :)

> In the main menu area, does your default boot selection look like this at the end of the kernel line and at the bottom (2 places):
Code:

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro splash quiet
initrd		/boot/initrd.img-2.6.24-19-generic
quiet


Yes it looks exactly like that, except in the kernel line mine says: ro splash vga=769 quiet

Any Help Would be Appreciated,

We Eat Vista

EDIT: My boot ends up being 6-7 minutes X_X

---

### Post by drs305 on 2008-06-27
WeEatVista,

I haven't been able to find a solution to the boot text. I have a 32-bit laptop that shows no text and a 64-bit desktop that shows the scrolling text on startup no matter what settings I use. The grub settings are supposed to take care of that but apparently don't in all circumstances.

Anyway, the point of the post is to mention something about your extended boot times. A few days ago I was working a boot problem with another reader on a related note. However, she also mentioned very long boot times and resolved it by using StartUp-Manager to change her boot resolution. I think she changed from 640-480 8 bit to ... had to check the options... 1024x768 16 bit. Apparently that solved her long boot problem. 

Just thought I'd mention it.

---

### Post by WeEatVista on 2008-06-27
Thanks for all your help, I guess it might just be a 64bit issue? That's what I'm also running. I'll try to change the options as you stated, maybe that would help. I guess this is as solved as it's going to get :)

Thanks for all your help,

We Eat Vista

---

