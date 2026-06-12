---
title: "help with graphics problem Acer aspire one za3 using 12.04LTS"
date: 2013-02-15
forum: General Help
---

### Post by aiden707 on 2013-02-15
Hi
i have a problem after installing 12.04 on my aspire one netbook . after booting the screen goes black. i have followed these instructions which work, but not fully

 Re: Acer Aspire One - Screen goes black after install.
Hello and welcome to Linux. I remember my first time trying to install Ubuntu on the same net-book as you. In face that's what i'm using right now with Ubuntu 12.04. I'll try to walk you through the steps as much as i can.
When you power on the netbook and it goes to the black screen wait a few seconds for it to fully load then press Ctrl+Alt+F1. This will switch you to a terminal like screen. Type your user name and press "Enter" then type your password. Next type this command and press Enter "sudo service lightdm restart"
This will now load your desktop but this is only temporary and will have to be done every time you boot. To make this permanent you have to edit your grub. Now that you are at your desktop press Ctrl+Alt+t to open a terminal and enter these commands
"gksudo gedit /etc/default/grub"
After entering your password a text fill will open. Find this line "GRUB_CMDLINE_DEAULT="quiet splash" and change it to look like this "GRUB_CMDLINE_LINUX_DEFAULT="quiet console=tty1 acpi_backlight=vendor acpi_osi=Linux acer_wmi.blacklist=yes mem=1920mb"
Now save and close the file. After that enter this command in the terminal "sudo update-grub"
After that is finished reboot and if you did everything exactly as said your netbook will boot perfectly. No more black screen

all works well, but does not work when i reboot i end up haveing to type it all in  again
thanks

---

### Post by Bashing-om on 2013-02-15
aiden707;
>  but does not work when i reboot i end up haveing to type it all in  againAs the above instructions should work:
a) Did you invoke the editor "gedit" with admin authority "gksudo" as directed ?
b) Did you save the file with the recommended changes ?
c) Did you run the terminal command "sudo update-grub" ? 
[INDENT]waiting to see what else is to be said
[/INDENT]

---

