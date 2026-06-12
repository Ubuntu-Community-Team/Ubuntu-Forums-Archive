---
title: "Problems with Nvidia driver in Ubuntu 16.04 LTS"
date: 2016-06-08
forum: General Help
---

### Post by leka0024 on 2016-06-08
New computer, with a Nvidia Quadro M4000 card, and came with Ubuntu 16.04 LTS loaded.

The default driver was Nouveau. I'm certain that I've correctly disabled it, because now running 'lshw -c video' shows me that there is no driver! In fact, I can't get past the login screen. When I login, it just crashes back to the login screen.


I was (finally) able to figure out how to stop lightdm from the tty console. I then ran the nvidia driver installer. It complained A LOT. A lot of the problems were due to security and keys.

I think the problem is related to "secure boot". For example, this thread: [http://askubuntu.com/questions/761136/ubuntu-16-04-nvidia-drivers-dont-work](http://askubuntu.com/questions/761136/ubuntu-16-04-nvidia-drivers-dont-work)


I can't reinstall the OS on this computer. I have to try to make it work, as is. Is it possible to turn off Secure Boot, so that Ubuntu can load the installed driver without asking for a key?

---

### Post by leka0024 on 2016-06-08
Anyone have any ideas on this? If I can't do anything about Secure Boot, does anyone know how I can put the keys used to sign the Nvidia Kernel into the trusted key database??

The Nvidia driver installer said that the driver kernel wouldn't load because the keys weren't trusted. Something like that.

I'm more than happy to just make this Secure Boot boot stuff go away, if that can be done without re-installing the entire OS.

---

### Post by Bucky Ball on 2016-06-09
Have you looked in 'Additional Drivers' when you're at the Ubuntu desktop??? That is how the NVidia driver is generally installed. The appropriate driver for you NVidia card should be suggested in there. All you need to do is tick and enable it. 

You need to go to 'Software and Updates' and in 'Other Software', make sure you have 'Canonical Partners' enabled, update, check 'Additional Drivers'.

You shouldn't need to manually disable Nouveau. In fact, not advisable, as you have found. How you gonna see the desktop to install a new driver with no graphics driver??? 

Nouveau will be replaced by the appropriate NVidia driver when you install it so I suggest you either install Nouveau until you get this figured out or install the NVidia driver from Additional Drivers directly. You may, though, need to clean up the mess and uninstall any NVidia driver you have installed to this point and start fresh.

PS: Secure Boot is the stuff of another thread and suggest you start one for that to improve your chances of support with it as it is unrelated to this support request and the title of the thread. Good luck. ;)

---

### Post by leka0024 on 2016-06-09
Bucky,

Thanks for the reply. While I'm sure you meant well, I don't think your suggested path is advisable. I'm following the path suggested by the Nvidia drivers readme. Nouveau must be disabled, by writing several lines of code to a blacklist configuration file and then running a sudo initramfs -u command. Yes, this means that there is no graphics driver, and one would then be unable to get past the greeter login screen. It's at that point you're supposed to use the tty console (Ctrl+Alt+F1 at the login screen) and run the Nvidia installer. That would normally have taken care of everything, including updating the X config file.


**However, the issue was indeed secure boot. Going into BIOS of the computer and disabling it immediately allowed the installed Nvidia driver kernel to load and start driving the graphics card.**


But it might be nice if the other solution was found too, for people who can't/aren't allowed to disable secure boot on their system. In that case, I'm certain if they key(s) that are used to sign the Nvidia driver kernel are just placed in the right location, then secure boot would trust the driver and allow it to load. Just didn't figure out how to do that.



In any case, if you want to close this thread, that is fine with me. Hope it can help someone else! And if you want to change the thread title to something like "Problems with Nvidia driver *being able to load* in Ubuntu 16.04 LTS", that would also be fine. I don't see an option for editing the thread title when editing the original post.

---

### Post by Bucky Ball on 2016-06-09
Odd. I installed 16.04 and I guess it must have been using Nouveau. Whacked in the NVidia driver from Additional Drivers and worked without issues. Maybe the Additional Drivers app takes care of Nouveau ...

Anyway, glad you got it solved and thanks for marking it that way.

---

