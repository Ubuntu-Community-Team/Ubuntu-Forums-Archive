---
title: "help, somehow ubuntu switched to eduubuntu"
date: 2007-04-20
forum: General Help
---

### Post by !@#$% on 2007-04-20
^see the topic

i don't know what i did,and it just happened. 
anyone knows how to switch it back to ubuntu? thanks

---

### Post by johnc4510 on 2007-04-20
Did you have the gnome ubuntu desktop to start with? If you did, at the log in screen choose sessions, choose gnome and then make it the default desktop.

---

### Post by !@#$% on 2007-04-20
i just unistalled everything related to eduubuntu from sync pack,  and it seems to solve the problems, but you know when starting up, you got a black screen saying ubuntu and a bar loading.
i still have the word EDUUbuntu...how do i change it?

another question, when i switch the workspaces using ctrl+alt+f1~6, and then i want to come bakc to the grahpic interface, and it freezes... is that becuase i have beryl install?

---

### Post by jiminycricket on 2007-04-20
Try typing dpkg-reconfigure usplash in a terminal.

Or [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

The second problem is due to fglrx.  Only ATI (I guess you're using XGL as well) can even fix that problem because it's a binary driver.  If you have a card supported by r300 I would try that.

---

### Post by arijarot on 2007-06-02
I'm trying to change the loading screen back to "ubuntu." I installed the ubuntustudio desktop theme and now it's taken over the loading screen, splash screen and shut down screen. I tried setting the sessions as default "gnome;" didn't work. I tried dpkg-reconfigure usplash, error message follows

```

sudo dpkg-reconfigure usplash
Password:
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
cp: cannot stat `/etc/udev/rules.d/25-dmsetup.rules': No such file or directory

```

---

