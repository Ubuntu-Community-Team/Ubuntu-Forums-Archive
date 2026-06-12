---
title: "Graphics won't start on boot with ndivia-driver-460 and -465"
date: 2021-06-20
forum: General Help
---

### Post by sigmundwalterson on 2021-06-20
Hello,
I need some help diagnosing a problem with my graphics driver.
I had nvidia-driver-460 installed and was happy with it, but a few weeks ago there was an update, and since then the boot sequence seems to complete but would stop before actually starting the graphical interface.
Switching to TTY2 also doesn't work, and the same problem happens with nvidia-driver-465.
Luckily nividia-driver-390 is still available, and with that one everything works (with the nouveau driver as well, except for some games).

I've tried a clean install, but that didn't resolve the problem.
My motherboard is an ASUS TUF X470-PLUS GAMING
My graphics card is a NVIDIA Corporation GP104 [GeForce GTX 1070]
I've attached the boot.log and dmesg from a failed boot, but I'm not knowledgable enough to notice anything wrong.
I would appreciate any help in further diagnosing/solving this problem.
Thank you in advance.

---

### Post by bradleypariah on 2021-06-20
I'm just a stupid user, so I can't help with your logs, but did you purge every mention of Nvidia on your system via the terminal?
I had a similar situation happen to me.  I was getting screen-tearing, so I tried to roll back my driver, and I could only boot into safe graphics after that.
I had to uninstall the proprietary driver, then reboot to safe graphics again.

After logging in, I followed the advice here to purge Nvidia:
[https://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely#:~:text=How%20to%20Remove%20NVIDIA%20from%20Ubuntu%20If%20you,7%20Type%3A%20apt-get%20remove%20--purge%20nvidia-%2A%20See%20More](https://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely#:~:text=How%20to%20Remove%20NVIDIA%20from%20Ubuntu%20If%20you,7%20Type%3A%20apt-get%20remove%20--purge%20nvidia-%2A%20See%20More).

IIRC, I also opened up Muon (in your case Synaptic Package Manager), and did a search for nvidia, and purged every installed entry, then followed the instructions above again.

Then I rebooted, and ran the driver tool, and let it install 460, and rebooted again.  That did it for me.  Hope it helps you.

---

### Post by sigmundwalterson on 2021-06-20
Thank you for your speedy answer.
Unfortunately, I've already tried this and it didn't work for me.

---

### Post by Autodave on 2021-06-20
Where are you getting the drivers from?  The repos or nVidia's site?  Is this a laptop or desktop?

---

### Post by sigmundwalterson on 2021-06-20
From the repo's (installed with the drivers GUI). This is on a desktop.

---

### Post by mastablasta on 2021-06-22
have you tried uninstalling the driver and then reinstalling it using same method?

it happened to my kid once. kernel was somehow patched, but the drivers didn't patch. so removing them (purge), booting into nouveau and then installing them again fixed the issue.

second answer here is less messy: [https://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](https://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

or you can try via GUI. but it is important you purge, clean and reinstall.

---

### Post by sigmundwalterson on 2021-07-11
Thank you.
Yes, I've tried that, but unfortunately this still doesn't resolve the issue.
Even after a clean install it still won't work :(

---

### Post by sigmundwalterson on 2021-07-26
It seems the new nvidia-driver-470 has resolved the issue :D

---

