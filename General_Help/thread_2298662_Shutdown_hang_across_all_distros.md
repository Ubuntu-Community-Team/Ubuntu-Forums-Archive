---
title: "Shutdown hang across all distros"
date: 2015-10-13
forum: General Help
---

### Post by willy9 on 2015-10-13
First and foremost; if this is not in the right area, I am sorry as I am totally new to these forums.

So, my problem is that the only shutdown option I have is to force the shutdown by holding my power button down. I cannot pin-point the problem although I can tell that something is causing my CPU to stall and the shutdown hangs. This happens on Ubuntu 14.04 LTS as well as Kali 2.0 (don't remember exact version number), but the peculiar part is that my Windows 7 still shuts down and reboots fine and that this problem only came about after I reinstalled Ubuntu 14.04 LTS (prior to my Kali installation). No matter the command to shutdown or reboot, it never fails that it hangs without forcing the shutdown by holding the power button. Any help or suggestions would be appreciated considering it was shutting down fine before re-installation of Ubuntu and that both Linux installations are hanging on shutdown/reboot. Thanks in advance!


[IMG]https://scontent-lax3-1.xx.fbcdn.net/hphotos-xtf1/v/t34.0-12/12168014_1033279373369392_940231484_n.jpg?oh=4046e65f116f28f1c36082d1302e6396&oe=561E7A9D[/IMG]

---

### Post by oldfred on 2015-10-13
I see mention of nouveau.
What video card/chip(s) do you have?

Did you install nVidia driver from repository before when system worked ok?

       ubuntu-drivers devices | grep recommended 

   #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA

---

### Post by willy9 on 2015-10-15
Sorry about the late reply!

I have an Nvidia GeForce GTX 765m so it was automatically using the Noveau driver.

It appears as though that the latest driver update for Noveau forces some sort of hang/stall on the CPU that persists into shutdown which caused the hang. I swear that I had changed drivers to an Nvidia driver, but it appears as though it has switched back somehow. Now my Ubuntu reboots properly and it has stayed using the Nvidia driver through reboot. Now I need to figure out how to properly install an Nvidia driver onto Kali 2 since it also uses this recent Noveau driver that causes this hang on my GTX 765m lol

---

