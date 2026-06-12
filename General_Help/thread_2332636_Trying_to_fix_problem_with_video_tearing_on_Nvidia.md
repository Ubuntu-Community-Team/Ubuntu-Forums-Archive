---
title: "Trying to fix problem with video tearing on Nvidia, but instructions aren't working"
date: 2016-08-02
forum: General Help
---

### Post by gamelord122 on 2016-08-02
I know I'm not the first person to have trouble with tearing on Nvidia cards, but I've been following [these instructions]("http://www.iwillfolo.com/finally-nvidia-tearing-issue-fix-found/") and I'm not getting the same results.  I'm running Ubuntu 16.04 and Nvidia drivers 367.35 on a GTX 660M in an old Lenovo laptop.  Since installing Ubuntu on this machine, I've mostly just used it for playing games like Medieval II: Total War and Robocraft, and I haven't noticed any tearing there, so I figured my settings were perfectly fine.  However, I've recently been using it as a portable Netflix machine (and soon HBO, once I get Flash installed), and it turns out that the video playback settings are different from the OpenGL settings.  Following the above instructions, it tells me to modify my xorg.conf file and to check some boxes in my nvidia-settings such as "sync to Vblank".  I added those changes into my xorg.conf, but I don't have those checkboxes in the OpenGL settings of my nvidia-settings application.  I rebooted in spite of not being able to find those options, and not only did it not fix the problem, but it also seemed to wipe out my changes in my xorg.conf file (which I confirmed had saved before rebooting).  I booted up Robocraft again and confirmed that my 3D gaming performance is still good, so I know I haven't completely screwed over my machine, but I'd rather get rid of the guess work here.  Can anyone shine insight into why X saw fit to wipe out my changes or why the Nvidia settings application is missing settings like "sync to Vblank" and any kind of option to set refresh rates for my screen?  I found both of these in compiz settings, but I'm trying to follow these directions exactly.

---

### Post by ajgreeny on 2016-08-02
How did you install the nvidia driver?

The recommended way is to use the Additional Drivers from the dash or menu, not go to nvidia direct, which is what I suspect you may have done as the latest driver in the repos for nvidia cards is 361, not the newer version you have.

Newer is not always better, particularly with these older graphics cards, so try using the driver offered to you from the repos, using Additional Drivers, and see if you get better performance.

---

### Post by gamelord122 on 2016-08-02
I added the Nvidia repository to my repository list, and I installed from there so that it's kept up to date.

---

### Post by mc4man on 2016-08-02
>  I'm running Ubuntu 16.04 and Nvidia drivers 367.35 on a GTX 660M 
Those instructions are likely for a desktop gpu not a mobile/optimus one. The best/default method to using  nvidia drivers on these laptop gpus is thru nvidia-prime which has not a shred of vsync. 

Additionally, due to a so-called mesa bug  while using the nvidia drivers thru nvidia-prime,  Intel,  (which handles the actual display),  is set to modesetting so 'tear-free' cannot be set.

---

