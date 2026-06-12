---
title: "GUI completely gone after updating ubuntu 12.04"
date: 2013-02-25
forum: General Help
---

### Post by zomgwhat on 2013-02-25
Hi, I'm new to ubuntu so I need a little help. I've dual booted using wubi and installed ubuntu 12.04, 64 bit. Since then I installed lubuntu-desktop and I really like it. Everything has been working fine for a while. Every now and then I'm prompted to update packages for security reasons etc, and I usually just install all the updates. The latest set seems to have knackered my GUI and I can't get it back. After the update it just starts a text-based login instead of the graphical one. I'm sure some of the updates were to x-server and Xorg but I don't know enough about ubuntu to know if that is relevant! 

I've tried googling around for a solution, and other people suggest to do 'sudo apt-get update' and 'sudo apt-get upgrade' which I've done without achieving anything. I still can't start lightdm: if i do 'sudo start lightdm' or 'sudo service lightdm restart' I just get a screen with a bunch of statements, the last 3 of which are:

stopping system V run level compatibility  [ OK ] 
starting lightdm display manager   [OK ]
stopping userspace bootsplash    [ OK ] 

and then simply a flashing underscore, and nothing happens. All I can do from there is hit the power button which reboots the pc. I've also tried sudo startx, which leads to 'no screens found' and installing gdm but the same thing happens. It was running fine before the update with nvidia display drivers 304.xx. I've tried doing something like dpkg reconfigure lightdm, and this completes fine but doesn't change anything. 

Pretty annoying that all I've done to cause this is do the recommended updates ... is this generally not a good idea? :S Any advice on how to get my desktop back is welcome! I don't want to do a fresh install as I've finally got all my packages and GUI configured the way I like. Thanks

---

### Post by humpty88 on 2013-02-27
See if there's a xorg.conf in /etc/X11.
If there is, rename it to something else and reboot.
Xorg should auto-detect without it.

You should really do a system backup before installing any new updates.

---

