---
title: "Installing Nvidia Drivers"
date: 2007-10-05
forum: General Help
---

### Post by flower199 on 2007-10-05
Hey, 

Could someone point me in the direction of a tutorial on how to install the Nvidia display drivers or any driver because I don't know where to start, and Nvidia's driver page is too vague ([link]("http://www.nvidia.com/object/linux_display_ia32_100.14.19.html"))

Any help would be most appreciated.

---

### Post by elliotjreed on 2007-10-05
Try downloading nvidia-glx from Synaptic. Then run:

```
sudo nvidia-glx-config enable
```

If you have a newer video card, etc. try using nvidia-glx-new instead!

---

### Post by flower199 on 2007-10-05
> **elliotjreed said:**
> Try downloading nvidia-glx from Synaptic. Then run:

```
sudo nvidia-glx-config enable
```

If you have a newer video card, etc. try using nvidia-glx-new instead!

I don't get where to run it, iin the console?

---

### Post by elliotjreed on 2007-10-05
Yer!

Just run it in the terminal!

Applications > Accessories > Terminal

---

### Post by flower199 on 2007-10-05
> **elliotjreed said:**
> Yer!

Just run it in the terminal!

Applications > Accessories > Terminal

Cool, thank you. It ask for a password, but I can't type anything!! ](*,)

---

### Post by FuturePilot on 2007-10-05
That's a feature of the terminal. You are actually typing your password, but it just doesn't show up. Another way you can install the driver is to just go System>Administration>Restricted Drivers Manager

---

### Post by flower199 on 2007-10-05
> **FuturePilot said:**
> That's a feature of the terminal. You are actually typing your password, but it just doesn't show up. Another way you can install the driver is to just go System>Administration>Restricted Drivers Manager

Ok, I just enabled it, thanks for the help. It would be nice to learn how to install a .run file though!!!!!

---

### Post by elliotjreed on 2007-10-05
No Probz!

As for the .run file, I think you just click on it!

If not, try running it in the terminal:

sudo /home/**file**.run

I think...

---

### Post by FuturePilot on 2007-10-05
Installing the Nvidia driver manually is a bit tricky. You need to make sure you have all the development packages installed. I can't remember all of them right now though. Then you have to log out and drop to a tty by pressing Ctrl+Alt+F2 and then log in through the command line. Then you have to stop X by issuing this command
```
sudo /etc/init.d/gdm stop
```
Then you need to go to the directory where the installer is 
```
cd /path/to/installer
```
```
sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run
```
But if you do it this way X will break after a kernel update. It's just much easier if you use the driver in the Ubuntu repos.

---

