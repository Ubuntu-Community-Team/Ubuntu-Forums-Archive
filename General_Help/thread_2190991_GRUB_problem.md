---
title: "GRUB problem"
date: 2013-11-30
forum: General Help
---

### Post by nikolapetkovic on 2013-11-30
After installing Ubuntu 10.04.1 on my IBM Thinkpad t20 laptop, i've encountered some problems.
The installation went nice through the DVD, everything installed great.
After the installation, a message came up that i need to reboot my laptop, i rebooted.
Everything booted up fine, desktop showed. After shutting it down, and booting it up again i've encountered an error
It says: No such device, GRUB rescue (or something like that). Nothing works, pressing enter just shows the same commands.
Booting from Live CD and installing boot repair doesnt work.

Update: I just noticed i posted this in a wrong forum, sorry.

---

### Post by Bucky Ball on 2013-11-30
Welcome. 10.04 is no longer supported (as of April this year). Try the current long-term release 12.04 LTS (supported until April 2017 and a good place to start) and see if you have the same issues.

---

### Post by nikolapetkovic on 2013-11-30
Although i cant, IBM thinkpad t20 is a 8 year old laptop with Intel Pentium 3 700 mhz. It can barely run 10.04.

---

### Post by Bashing-om on 2013-11-30
nikolapetkovic; Hi !

Here are much better options than running an End Of Life version !
1. Install Lubuntu

2. Or if you are up to the challenge, a minimal install and build your own:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

If you choose option 2, we can be of great assistance to help you on your way.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by nikolapetkovic on 2013-11-30
I don't really like the Lubuntu style, i've found on the internet that its something of GRUB not recocnizing grub.cfg, i would really love a explanation how to fix it, cause i have a slow internet connection, it took me about 5 days to download the ISO, so i would not like to download again.
Thanks.

---

### Post by sammiev on 2013-11-30
Not sure if this will work with OS at its end of life but worth the try.

Recommended Live CD's (Ubuntu 12.04/11.10/11.04/10.10/10.04/9.10/9.04/Mint)
Recover/Reinstall/Repair grub2 from Linux Live CD/USB after Windows 7/8/vista/xp or grub doesn't work, It is really easy to install grub.
You just have to follow simple steps after that you will see grub2 in your system again.


First of all Boot your Linux Live CD/USB then open Terminal  and enter following commands:
This command for root permissions:
Terminal Command:

```
sudo -i
```

Check the drives number in Partition Manager :
Terminal Command:
```
sudo fdisk -l
```

Now select your Linux installed drive and change the number in following commands (Only change 'x' with your drive number) and change (sda) with your hard drive it can be (sdb, sdc, etc) you can see this in Partition Manager:
Terminal Commands:
```
sudo mount /dev/sdax /mnt
sudo mount /dev/sdax /mnt/boot
sudo mount --bind /dev /mnt/dev/
```

This command will change mnt directory permissions to root permissions:
Terminal Command:

```
sudo chroot /mnt
```

Now grub install command and Change 'a' in "sda" with your hard drive where you want to install grub, check in Partition Manager:
Terminal Command:

```
grub-install /dev/sda
```

Now installation finished, Enter following commands to unmount (If these two command doesn't work, then leave them):
Terminal Commands:

```
sudo umount /mnt/dev
sudo umount /mnt
```

Now reboot your pc:
Terminal Command:

```
sudo reboot
```

Your grub is back. That's it.

---

### Post by Bucky Ball on 2013-11-30
Be aware that you will no longer be getting security updates along with anything else which could leave your system vulnerable.

Good luck with your grub fix. ;)

---

### Post by nikolapetkovic on 2013-12-01
Thanks, i'll give it a try.

---

### Post by nikolapetkovic on 2013-12-01
Works! Thanks, we'll see after the reboot if it works :)

---

### Post by nikolapetkovic on 2013-12-01
Asks me for login, it seems i have forgot my password.
I'll reinstall Ubuntu and tell you.

---

### Post by nikolapetkovic on 2013-12-01
Still not working, but found something. If i go to LiveCD and open Terminal and type sudo reboot, it will boot me right into Ubuntu OS working, but when not rebooted, just shutdown and booted, it wont work, grub rescue.
Help anyone?

---

### Post by nikolapetkovic on 2013-12-01
Fixed it. Heres how: Reinstalled ubuntu, and when it asked me for password i just checked " Log me in automatically" wich has caused grub problems to stop. Thanks for help though! :D

---

