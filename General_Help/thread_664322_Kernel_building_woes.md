---
title: "Kernel building woes"
date: 2008-01-11
forum: General Help
---

### Post by Washer on 2008-01-11
Ok first of all is there any way to regenerate the /boot/config.* file? I uhh.. may have deleted mine & now i'm afraid to restart.

I was trying to add reiser4.. & it worked, .. but somehow I lost truecrypt & I can't live without it. Anyone know how that could happen? I'm sure I got the correct source & did the config properly. I even repeated the entire process twice. Third time around I even tried renaming/deleting the config file to see if menuconfig would register & it did. The only anomaly was "make-kpkg" wouldn't work so I switched to "make deb-pkg"

Thanks in advance

---

### Post by danwood76 on 2008-01-11
the config.*** file does nothing for your boot up its just a copy of the config used to build each kernel.
If you still have a copy in your build folder it wont be a problem, just keep it somewhere safe like in the build folder :)

You can always re-configure your build to add true crypt, just make sure you do a make clean before you rebuild so that the changes will deffinatly update.

The make-kpkg is in the kernel-package apt package so you can install with:
```

sudo apt-get install kernel-package

```

regards,
Danny

---

### Post by Washer on 2008-01-11
> **danwood76 said:**
> the config.*** file does nothing for your boot up its just a copy of the config used to build each kernel.

If you still have a copy in your build folder it wont be a problem, just keep it somewhere safe like in the build folder :)It'll boot! Ok dodged one bullet. Now my main problem is I didn't save a copy & I have no idea what to feed to menuconfig. I emptied the entire build folder to start anew so there's no old config file.

> You can always re-configure your build to add true crypt, just make sure you do a make clean before you rebuild so that the changes will deffinatly update.Yeah I was just about to start that when I saw I didn't have a config.* file. It's supposed to be enabled on the original config.* file, right? I was kinda hesitant to start re-enabling individual things bc I didn't know what else I might have lost.

> 
The make-kpkg is in the kernel-package apt package so you can install with:
```

sudo apt-get install kernel-package

```I did install that, or I think it may already have been installed. When I tried to run it the process just stops after ~2 min. At the end it says

exec debian/rules 
nothing to be done

.. and I had no idea what to do so I just switched to deb-pkg.

---

### Post by danwood76 on 2008-01-11
what kernel version are you using?
Attached is the one for kernel version 2.6.22-14-generic which is the standard with gutsy.

Obviously you will need to enable your extra options with this.

regards,
Danny

---

### Post by Washer on 2008-01-11
> **danwood76 said:**
> what kernel version are you using?
Attached is the one for kernel version 2.6.22-14-generic which is the standard with gutsy.

Obviously you will need to enable your extra options with this.

regards,
Danny

Well that works perfectly, thanks. I guess I'll mess around with menuconfig till something works.

---

### Post by nowshining on 2008-01-11
if u used terminal - sorry it's gone, but if u used the root nautilus windows then well it's in /root/.Trash

ctrl + h to show hidden and backup files.

/ = filesystem
root folder

ur folder/ the one u save to is in /home/username/

and a howtwo build a kernel is my site. Give feedback please if u follow my guide.

---

### Post by Washer on 2008-01-11
yeahhh there isn't much there. I've gotten into a bad habit of shift-deleting everything.

---

### Post by nowshining on 2008-01-11
u can put a right-click delete in the right-click menu, it's in the nautilus prefs :/

---

### Post by Washer on 2008-01-11
re truecrypt

Still didn't work. The exact error is

```
insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.22.ko': -1 Invalid module format
FATAL: Module truecrypt not found.
truecrypt: Failed to load TrueCrypt kernel module
No volumes mapped

```
Some [googling]("http://ubuntuforums.org/archive/index.php/t-606247.html") convinced me a simple reinstall will fix it so I'm giving up on the kernel's two hour compile time.


One last problem with reiser4 I hadn't noticed. It's mounting the partition, but it can't write. Forgot to test that yesterday. Now I'm not even sure it can read because there's nothing to read. That copying file dialog stays up & won't close.

---

### Post by Washer on 2008-01-11
I'm using the 2.6.22 patch from [this site ]("http://linuxhelp.150m.com/installs/compile-kernel.htm") since namesys seems to be permanently down :(

(I think i'll head to sleep now it's way past my bedtime)

---

