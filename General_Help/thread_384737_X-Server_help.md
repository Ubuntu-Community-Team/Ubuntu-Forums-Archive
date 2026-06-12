---
title: "X-Server help"
date: 2007-03-14
forum: General Help
---

### Post by Lead Head on 2007-03-14
Hello all! On my Ubuntu 6.10 install on my spare computer. I changed the video card from an nVidia riva, to a Geforce 2. I installed the nVidia binary drivers, then when I restarted X, it just kept crashing over and over again. I figure I need to install the nVidia legacy drivers. But I'm not sure of the commands to uninstall the current nvidia binary drivers, and install the legacy drivers. anyhlep would be apreciated.

---

### Post by irwa82 on 2007-03-14
Hi,

When X stops trying to load you should get access to the console. Login as your user then edit the /etc/X11/xorg.conf file with sudo access and change the driver "nvidia" to be driver "nv" . The restart gdm by doing sudo /etc/init.d/gdm restart then you should be able to access x and then you will be able to work through the x environment that you are familiar with.

Kind Regards,
Anthony Irwin

---

### Post by Lead Head on 2007-03-14
How would I edit xorg.conf from the console. Gedit does not seem to function

---

### Post by irwa82 on 2007-03-14
Hi,

Personally I would use vim but it is not the most user friendly editor maybe other people can suggest a friendly editor. That being said vim is worth learning.

to install run apt-get install vim 

then to learn how to use vimtutor (just type vimtutor at command line) and it will give you a tutorial on how to use vim.

---

### Post by FuturePilot on 2007-03-14
Try
```
sudo nano -w /etc/X11/xorg.conf
```

---

### Post by Lead Head on 2007-03-21
Thanks, it worked

---

