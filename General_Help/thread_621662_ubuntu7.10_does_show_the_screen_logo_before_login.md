---
title: "ubuntu7.10 does show the screen logo before login"
date: 2007-11-23
forum: General Help
---

### Post by astomi on 2007-11-23
I installed the ubuntu 7.10 on my laptop .
The notebook is HP nx6330 with the ATI X1300 graphics card, I have intalled the drive for it which version is 8.42.3.
My problem is before the login screen there no ubuntu logo.I used the ubuntu 7.04 in my desktop, it will show the ubuntu logo normally. Another problem is I can't login in the tty using the key "Ctrl +ALt+F1"

Thanks for help me.

---

### Post by astomi on 2007-11-24
Can anybody help me?

---

### Post by mozetti on 2007-11-24
This thread should sort it out for you:

[http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash+resolution](http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash+resolution)

---

### Post by astomi on 2007-11-24
chang the /etc/usplash.conf

xres=1280
yres=1024

to

[COLOR="Red"]xres=1280
yres=800[/COLOR]

then I run the command 

"sudo update-usplash-theme usplash-theme-ubuntu"

There is a panic for kernel, so I can't login in the system even recovery mode 

So I edit the grub using the backup initrd.img-2.6.22-14-generic.bak can login in the system. Then change the initrd.img-2.6.22-14-generic.bak to recover the old one.

Now can login the tty also .Thanks all the same.

---

### Post by mozetti on 2007-11-27
Where did you get that resolution? 1280x800 isn't a standard resolution.

You should have changed it to
```
xres=1024
yres=768
```

---

### Post by PlantHead on 2007-11-28
> **astomi said:**
> chang the /etc/usplash.conf

xres=1280
yres=1024

to

[COLOR="Red"]xres=1280
yres=800[/COLOR]

then I run the command 

"sudo update-usplash-theme usplash-theme-ubuntu"

There is a panic for kernel, so I can't login in the system even recovery mode 

So I edit the grub using the backup initrd.img-2.6.22-14-generic.bak can login in the system. Then change the initrd.img-2.6.22-14-generic.bak to recover the old one.

Now can login the tty also .Thanks all the same.


Can someone explain this for me...in exactly the same situation and have no idea how to fix the Kernel panic problem.

---

### Post by mozetti on 2007-11-28
To fix the kernel panic problem, run the Ubuntu LiveCD and mount your root filesystem so you can access the /etc/usplash.conf file.

Update that file to use 1024x768 instead of 1280x800 -- a quick google search showed some problems with running that resolution. Perhaps it works once Ubuntu get's loaded, but I don't think Usplash is able to draw that resolution.

**Edit** Just realized that you need to be able to run the command: ```
sudo update-usplash-theme usplash-theme-ubuntu
```

I'm not sure if you can fix Usplash without getting the kernel loaded. Someone a little more knowledgeable may come by to help you, but I'm at a loss.

---

