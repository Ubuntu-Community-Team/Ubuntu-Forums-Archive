---
title: "shutdown fails to turn power off"
date: 2013-03-19
forum: General Help
---

### Post by wijit on 2013-03-19
Just updated to 3.2.0-39 few hours ago and the first effect was wrongly detected monitor type and resolution. System Settings>Displays could not change the monitor profile from being a Laptop and the resolution of 1024x768 because no other options in the dropdown. This machine was a desktop PC. Before updated the monitor type was unsure but the resolution was 1280x1024 (5:4). In System Settings>Additional Drivers the NVIDIA accelerated graphics driver (Version 96) was recommended but not activated. After the driver was activated and the system restarted, the monitor was able to be configured to the proper resolution but the type was still a laptop. And the worst, the system could only restart but not shutdown. I remembered that other updates before this update never asked me to activate the driver. Also the big Ubuntu logo at startup and shutdown that was seen only the first run of the installation now was shown every time the system boots and shuts down. If you want more information please feel free to tell me. A command line or menu sequence would be appreciate because I'm just a user.

---

### Post by gifford on 2013-03-19
Where does the shutdown stall? Is with the blinking dots?

---

### Post by wijit on 2013-03-20
At the Ubuntu logo and the row of orange and white dots which changing for a while before freezing forever. I guess all key processes were shutdown but I wasn't have a chance to do any thing. All input devices stopped. However, the mainboard led, CPU fan and NIC led still run. I also guess that the graphic card (NVIDIA MX/MX400) still functioned since the monitor stay still at the logo which mean it still received the video signal from the card. Thanks

---

### Post by c2tarun on 2013-03-20
> **wijit said:**
> At the Ubuntu logo and the row of orange and white dots which changing for a while before freezing forever. I guess all key processes were shutdown but I wasn't have a chance to do any thing. All input devices stopped. However, the mainboard led, CPU fan and NIC led still run. I also guess that the graphic card (NVIDIA MX/MX400) still functioned since the monitor stay still at the logo which mean it still received the video signal from the card. Thanks

There might be a chance that your system is shutting down but not getting halted. Try following command:

```
sudo shutdown -h now
```

If this doesn't work then I found a way to enable text mode during boot or shutdown [here]("http://askubuntu.com/questions/6101/console-text-appears-on-shutdown"). Please follow the steps and where Ubuntu logo with orange/white dots appear there you'll see some messages. See if that messages help you to understand anything. (I am not sure but pressing arrow key when Ubuntu logo is displayed will also changes to text mode, please try this).

---

### Post by wijit on 2013-03-20
Thanks c2tarun. I did almost all switches of the command. Only -r works. I agree with you that it must be the graphic accelerator who caused the problem but not that the kernel provided good driver. This was the first time of the problem and the display worked fine since first installation of 12.04. I'd like to go back to kernel 3.2.0-38 that used to work fine before updating. However, I had a bigger problem now. I removed the proprietary driver and install the similar from Synaptic Package Manager. After restart the system, I saw a warning said that the system runs in a very resolution graphic. It gave me some options to select but none of them brought a login screen up. I could login in text mode. Please guide me out of this.
<br>I forgot to tell you that shutting down failure did not harm the system but it was annoying. I could safely turn the system off by restarting instead of shutting down and unplugged the power when the system started to reboot. I tried to fix a small problem but it took me to another problem bigger.

---

### Post by wijit on 2013-03-20
Thanks c2tarun. I did almost all switches of the command. Only -r works. I agree with you that it must be the graphic accelerator who caused the problem but not that the kernel provided good driver. This was the first time of the problem and the display worked fine since first installation of 12.04. I'd like to go back to kernel 3.2.0-38 that used to work fine before updating. However, I had a bigger problem now. I removed the proprietary driver and install the similar from Synaptic Package Manager. After restart the system, I saw a warning said that the system runs in a very resolution graphic. It gave me some options to select but none of them brought a login screen up. I could login in text mode. Please guide me out of this.

I forgot to tell you that shutting down failure did not harm the system but it was annoying. I could safely turn the system off by restarting instead of shutting down and unplugged the power when the system started to reboot. I tried to fix a small problem but it took me to another problem bigger.

Yes, hitting an arrow key on the keyboard switches the graphic mode to text mode. I found no error reported. The very last line said the system halted. The problem persisted as the screen did not show no signal messages, the CPU fan spun and the NIC led did not turn off.

---

### Post by wijit on 2013-03-20
I followed the 8th answer of [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error) and got the system up again. However, shutting down problem still persists.

---

### Post by gifford on 2013-03-20
For the shutdown issue here is a link to help. [http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer](http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer)

I had the same issue at one time and the information in the link helped. After installing new kernels I do run update-grub and update-grub2.

---

### Post by wijit on 2013-03-20
Thank you very much, gifford. The link also helped me. This really surprised me as I just realized that is not only a conflict between NVIDIA and 12.04 but it related to Grub too. I also have a Dell INSPIRON N4030 driven perfectly by Lucid but never faced this problem. Another surprise was that there are so many of the same kind of problem under Related topic of the page and signigicant number of them relate 11.10. Even though my problem was solved, i'd like to investigate what really caused the problem by comparing between Lucid and 12.04. This might be just a dream for me since I am very limitted in programming.

Other information that might be useful for developers or programmers is that every time just before the system got froze I heard a small sound of parking of the HD. The sound occured roughly at the 2nd or the 3rd orange dot.

I'm finding the way to mark this thread as solved.

---

### Post by davelectronic on 2013-03-20
I have not long installed Ubuntu 12.04 LTS on my old emachine 2230 it also failed during a restart to do this, although shut down was ok, if its a similar issue the below worked for me.


WORKAROUND: Type in a terminal:
 sudo nano /etc/default/grub

find the line:
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it to:
 GRUB_CMDLINE_LINUX_DEFAULT="reboot=pci quiet splash"

save then perform via the Terminal:
 sudo update-grub

---

