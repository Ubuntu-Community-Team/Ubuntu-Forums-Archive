---
title: "Ubuntu 12.10 login failure"
date: 2013-02-23
forum: General Help
---

### Post by omerderi on 2013-02-23
Yesterday Ubuntu 12.10 (32 bit) -the distro which worked best for me- gave me the lesson of my life. I was suddenly faced with the Log-in screen in spite of the 'auto login', and all my attempts at login falied even as a guest. I could only login via the command line after "Alt-Ctrl-F1" which meant there was nothing wrong with my password. I tried almost every suggested solution available but to no avail. The problem appeared after the latest package update which included 'Firefox'.
So, I am waiting for a miracle to bring life back to my dead PC.

---

### Post by carl4926 on 2013-02-23
At the grub boot menu
Try selecting the previous kernel
Can you login with that?

---

### Post by omerderi on 2013-02-23
> **carl4926 said:**
> At the grub boot menu
Try selecting the previous kernel
Can you login with that?

Thanks carl4926 ..
The problem is that I already have deleted all old kernels using Ubuntu Tweak tool!
I am currently booting from a Live Ubuntu 12.10 usb. Is there anything I can do to repair my installed -but dead- OS from this live usb?

---

### Post by carl4926 on 2013-02-23
Go back to the install and login with command line

and try

```
sudo apt-get update && upgrade
```

Just to see if it helps
Then reboot

-------------------

FYI
You can chroot the system from the live usb
But try above first

---

### Post by carl4926 on 2013-02-23
> **carl4926 said:**
> Go back to the install and login with command line

and try

```
sudo apt-get update && upgrade
```

Just to see if it helps
Then reboot

-------------------

FYI
You can chroot the system from the live usb
But try above first

You might need a wired connection, not sure...

---

### Post by omerderi on 2013-02-23
> **carl4926 said:**
> Go back to the install and login with command line

and try

```
sudo apt-get update && upgrade
```

Just to see if it helps
Then reboot

-------------------

FYI
You can chroot the system from the live usb
But try above first

Thanks..
But that also didn't work!

---

### Post by fdrake on 2013-02-23
1)
> **omerderi said:**
> 
The problem is that I already have deleted all old kernels using Ubuntu Tweak tool!
Never do that! Always leave an old working/stable kernel behind , id doesn't use that much memory!

2)is this a laptop or a pc/desktop?
if it's a laptop plugin an ethernet cable and follow this:
   -boot the computer normally and use the console to login (ctrl+alt f1/f2/..)
    - type this commands in the console:
```

sudo apt-get install --reinstall gdm gnome

```
logout > reboot or press ctrl+alt+f7

---

### Post by omerderi on 2013-02-23
> **fdrake said:**
> 1)

Never do that! Always leave an old working/stable kernel behind , id doesn't use that much memory!

2)is this a laptop or a pc/desktop?
if it's a laptop plugin an ethernet cable and follow this:
   -boot the computer normally and use the console to login (ctrl+alt f1/f2/..)
    - type this commands in the console:
```

sudo apt-get install --reinstall gdm gnome

```
logout > reboot or press ctrl+alt+f7

I am using a desktop PC but was able to connect to the internet from the login screen. I downloaded both gnome & gdm. I reconfigured gdm but when I rebooted the screen went blank. I had to go back to 'lightdm' before the login screen came back.

---

### Post by carl4926 on 2013-02-23
What graphics device do you have?

Did you try 'nomodeset' boot argument ?

---

### Post by omerderi on 2013-02-23
> **carl4926 said:**
> What graphics device do you have?

Did you try 'nomodeset' boot argument ?

My graphics card is Intel 'built-in'
I haven't used 'nomodeset' yet and don't know how to use it..

---

### Post by carl4926 on 2013-02-23
Intel should just work

---

### Post by omerderi on 2013-02-24
Thanks carl4926 for all your suggestions..
I ultimately have wiped out and re-installed the system today.

---

### Post by carl4926 on 2013-02-24
> **omerderi said:**
> Thanks carl4926 for all your suggestions..
I ultimately have wiped out and re-installed the system today.

Umm..
Sorry to hear that was necessary

---

