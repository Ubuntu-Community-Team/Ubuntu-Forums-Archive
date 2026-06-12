---
title: "Wubi Installing and Wireless Problems"
date: 2008-06-01
forum: General Help
---

### Post by Schpudd on 2008-06-01
Hi there,

When using Wubi to install Ubuntu 8.04 within Windows XP it downloaded the distro fine, asked me to reboot and upon selecting Ubuntu i get the error **"Error 1: Filename must be either an absolute pathname or block list"**. I have read a couple of threads, people don't seem to post their answer of how they got the fix. I am using an NTFS filesystem and I haven't edited any options in any way.

I tried installing Ubuntu a few months ago so I can't remember the exact errors I was getting at the time, but I decided to try again. My problem is that after running from a Live CD I didn't have wireless internet within Ubuntu and have no way of connecting myself to the router with an ethernet cable. Knowing this is a seemingly common error with Linux I'll give you my cards. I have an unknown model of a **Broadcom 802.11b/g** which is an internal PCI card and a **Belkin 802.11g** external USB dongle.

Any help would be greatly appreciated.

---

### Post by jualin on 2008-06-02
First let me welcome you to Linux and let me tell you that we have been there buddy, just hang in there a little longer, help is on the way!. The only thing that I can help you with is with the wireless. Broadcom is very common in Linux and therefore is widely supported. To know the specific model of your wireless card go to the terminal and type > lspci (that will give you a list of all the hardware in your computer, you should be able to find the model of your Broadcom Wireless Adapter, it should say "Broadcom" and "your-model". Post the results to continue helping you or google "how to broadcom (your model) ubuntu" that usually takes you to the right solution. 
Basically the process is installing a package called "ndiswrapper" and since you dont have an internet connection in your computer, you should use Winblows or another computer and simply download the package and its dependencies from [http://packages.ubuntu.com/hardy/]("http://packages.ubuntu.com/hardy/"). or [http://packages.ubuntu.com/hardy/misc/ndiswrapper-common]("http://packages.ubuntu.com/hardy/misc/ndiswrapper-common"). After you have this package installed you only need to look for the correct Windows Driver suggested by Linux users for your specific Broadcom Wireless Card. Hope this points you in the right direction!

---

### Post by jualin on 2008-06-02
You also need to download "ndiswrapper-utils" which you can find in [http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9]("http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9"). Good luck!!

---

### Post by Schpudd on 2008-06-02
Thanks very much for all the help based on the wireless issues; all I need now is to get Ubuntu working again and I should be able to have everything set and hopefully get rid of XP forever.

---

### Post by jualin on 2008-06-02
I found this post online [http://ubuntuforums.org/showthread.php?t=372070]("http://ubuntuforums.org/showthread.php?t=372070") (qwerkus' post) which said that removing the "savedefault" command solved the problem. To change that command you need start Ubuntu in Failsafe mode so you can get to a command line interface and from there change "true" to "false" from the "savedefault=" line. Try booting up Ubuntu in Failsafe mode and log in as root. After this type > vim /boot/grub/menu.lst, look for the line "savedefault=true" and switch it to "savedefault=false". You can usually find this line on the bottom of the file. To save simply press the "Esc" key twice and then type > ZZ and that should make the trick. I dont know if that would help you but at least thats what the other person did to solved his problem. Hope this works!

---

