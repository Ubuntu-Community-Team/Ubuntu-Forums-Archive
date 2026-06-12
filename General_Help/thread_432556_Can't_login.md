---
title: "Can't login"
date: 2007-05-04
forum: General Help
---

### Post by slink on 2007-05-04
Hello, 

I've installed ubuntu 7.04 i386 two days ago. I've updated via Update Manager. I've browsed the internet and installed Flash. Everything's just fine. 

This morning I've started the computer, seen the orange progress bar reach the end, and then there's a black screen with the 'spinning wheel' cursor for about a quarter of hour. 

I've tried ctrl+alt+F1 but nothing happens.

What can I do?

Thank you

---

### Post by coxy on 2007-05-04
Try Ctrl+Alt+F2

If not then select recovery mode from your Grub menu. Once your into the system go to the X11 folder.

```

cd /etc/X11/

```

List the contents

```

ls

```

You should see some files which include xorg.conf and xorg.conf.1 Make a backup of xorg.conf

```

sudo cp xorg.conf xorg.conf.bak

```

Now there should also be some existing backups or xorg.conf named something like xorg.conf.1 You can change one of these to replace your existing xorg.conf file.

```

sudo rm xorg.conf
sudo mv xorg.conf.1 xorg.conf

```

When you restart, xorg should use the last configuration in use before whatever broke it. If you need or want to restore the xorg.conf file you started with then do the following.

```

sudo rm xorg.conf
sudo mv xorg.conf.bak xorg.conf

```

---

### Post by slink on 2007-05-04
Thank you. I'll try that.

---

### Post by slink on 2007-05-04
Do you believe that I must delete the "splash quiet" instances as in :


[http://ubuntuforums.org/showthread.php?t=429653](http://ubuntuforums.org/showthread.php?t=429653)

---

### Post by coxy on 2007-05-04
I do that on my boxes, especially my laptop because the splash screen never worked and took an age to load. It may help and won't harm if you give it a try.

It might also allow you to see the issue at boot as without the splash screen everything is printed to the screen.

---

### Post by slink on 2007-05-07
I did not find any xorg.conf backups made yet, and I did not manage to edit Grub, so I decided to reinstall since I still had not any valuable data. 

Now the first thing I've done is a xorg.conf.backup. 

I remember I changed my 'Login Window' prefs before the problem so I guess I should have restored something like a "login_window_prefs.conf" or so...

Anyway, thanks for help coxy.

---

### Post by coxy on 2007-05-07
That is one of the great things about Ubuntu, it takes less than 30 minutes to install it with a good internet connection. Good luck with the fresh install and taking backups of .conf files is always a good practice.

---

