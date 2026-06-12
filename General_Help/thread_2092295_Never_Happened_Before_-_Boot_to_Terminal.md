---
title: "Never Happened Before - Boot to Terminal"
date: 2012-12-07
forum: General Help
---

### Post by Quarkrad on 2012-12-07
Running 12.04 Unity on 64 bit machine.  Everything has been 100% until recent update to 3.2.0-35 - PC boots to terminal.  I've googled and run a few terminal commands like startx, sudo service lightdm restart, sudo service gdm start but so far nothing works.  I can go 'recovery mode' at the grub screen and go back to 3.2.0-34 and I'm back to 100% but only terminal command with 3.2.0-35.  Any suggestions most appreciated.

---

### Post by Quarkrad on 2012-12-07
Now it's booting to terminal on 3.2.0-34 and 3.2.0-33 so I'm completely locked out.  When I ran **startx** I ended up with a message **no screens found**.  Looking back through the text I saw:

Error: API mismatch the nvidia kernal module has version 310.14, but this driver component has version 295.40

---

### Post by forestG on 2012-12-07
try to uninstall the nvidia-drivers. 

[http://askubuntu.com/questions/189347/how-can-i-uninstall-nvidia-proprietary-drivers](http://askubuntu.com/questions/189347/how-can-i-uninstall-nvidia-proprietary-drivers)

---

### Post by Habitual on 2012-12-07
> **Quarkrad said:**
> ...PC boots to terminal...

Terminal is a Desktop Application.
"known as an X terminal emulator, often referred to as terminal or shell"

I believe you are referring to the console which is what commands like ```
startx, sudo service lightdm restart, sudo service gdm start
``` are run from after grub, of course.


Edit0: N/M.
More info posted during reply composition. Doh!

Have a Great Day!

---

### Post by Quarkrad on 2012-12-07
Thanks - sorted it by following commands:

sudo apt-get --purge remove nvidia-*

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings

---

### Post by IrishAdam on 2012-12-20
I had the same problem today with 64 bit 12.04.

I removed the AMD catalyst 12.11 beta drivers that I was using for steam, rebooted and then reinstalled them. Everything is fine again.

The commands I used to remove the drivers where


sudo sh /usr/share/ati/fglrx-uninstall.sh 

sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

---

