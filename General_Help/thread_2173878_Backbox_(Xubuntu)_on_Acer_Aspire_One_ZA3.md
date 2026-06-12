---
title: "Backbox (Xubuntu) on Acer Aspire One ZA3"
date: 2013-09-11
forum: General Help
---

### Post by d4rk0wl on 2013-09-11
Hello, I am having a few issues with a fresh install of Blackbox. Which is built off of Ubuntu and I have yet to find a solution.

The  first issue I am having is the odd screen resolution. Which is  1366x768. Xorg seems to be getting confused on the proper display  properties. I was able to install the system just fine via text mode  installer, however when the system boots I am confronted with a blank  screen. I am able to drop down to a system shell (Ctrl+Alt+F1) and login  from there. I am required to stop the lightDM service (sudo service  lightdm stop) and then restart X (startx) once I do this the proper  resolution is achieved and everything on that end seems to work fine. I  remember encountering this problem in earlier additions of Ubuntu, I was  able to correct it via editing the grub file in /etc/default/grub.  However, I cannot remember what exact steps I took. Here is the output  of LSPCI:

```
d4rk0wl@Linuxnetbook:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
```

The next problem  is the most irritating of the two. I am encountering many problems with permissions. It seems the  user I have setup at the install does not have permission to do  anything. I am unable to adjust power management profiles, connect to  any wireless network, or mount USB drives. I have changed the user  settings in User Manager (once I restart X) and have given all proper  permissions in the advanced settings tab. I have also set the user as an  administrator account. However, upon reboot I still do not have any  permissions. When I try to do anything I am prompted with the error "Not authorized". I have even tried adding my user to the root group to still no luck. I would really like to avoid logging in as root all the time.

Any help on these matters is greatly appreciated.
Thanks in advance!

---

### Post by d4rk0wl on 2013-09-12
Anyone have any suggestions?

I have found that these problems are purely because of the XFCE desktop environment. I have intalled the LXDE desktop environment to test.
```
sudo apt-get install lubuntu-desktop
```

All of the permissions have been restored to normal. However I need the toolkits that came with the install on the XFCE interface.

Thanks in advance,

---

### Post by mastablasta on 2013-09-12
you didn't just install LXDE desktop, you installed full lubuntu with that command. all this points to one thing ->> that backbox has an issue with your hardware.

if you had to edit grub it means you probably had to use one of the boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

also backbox though based on ubuntu does have some things done differently. it likely even has a different kernel.

---

