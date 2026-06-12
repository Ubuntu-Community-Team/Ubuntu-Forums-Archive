---
title: "Commands to reboot dont work properly"
date: 2016-03-24
forum: General Help
---

### Post by Uinthe on 2016-03-24
Hello. 
Have a problem on my Ubuntu 14.04.4 amd64 (up-to-date). 
Commands:
```
shutdown -r X
reboot (-f)
init 6
Alt+SysRq+REISUB
```
dont work properly. The system goes to messagses:
```
reboot: restarting system
reboot: machine restart
```
and then nothing happens. No errors or fails of some kind in syslog/kernlog/dmesg around reboot time except this:
```
sp5100_tco: unexpected close, not stopping watchdog!
``` Dont know if this bug connected with my problem.
What did i try:
1. In /etc/default/grub [FONT=arial]GRUB_CMDLINE_LINUX_DEFAULT add boot parametres:
[/FONT][FONT=arial]```
reboot=warm(cold,bios,smp,triple.kdb,efi,acpi,pci,force)
```.
[/FONT][FONT=arial]Also used:
[/FONT][FONT=arial]```
acpi=force reboot=acpi
```[/FONT]
In this case PC turns off.
 2. Run memtest twice time. No errors.
3. Switch between proprietary and oss video drivers (ATI).
4. Reinstall system.
Im done. Googling for hours and get nothing usefull to solve this annoying problem. 
My last system (a half year ago) was Mint. With Mint i feel no problems with rebooting. Now i love Ubuntu and have to deal with this...
You are my last hope. 
Thanks in advance.

P.S. Screen with reboot log
[[IMG]http://storage8.static.itmages.ru/i/16/0324/s_1458829278_8344522_f444756286.jpg[/IMG]]("http://itmages.ru/image/view/4045075/f4447562")

---

### Post by efflandt on 2016-03-24
Normally you would do one of these to reboot from the shell (since you should be running as a normal user and need to shutdown or reboot as root)```
sudo shutdown -r now
sudo reboot
```If you don't want to have to enter your password for sudo, you can use sudo with an editor (**sudo nano** in terminal or **gksu gedit** for gui) to edit /etc/sudoers, adding a line like the last line below (with your username instead of mine):```
# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
efflandt ALL=NOPASSWD: /sbin/shutdown, /sbin/reboot
```PS: Although, I have an older HP PC that never did seem to want to reboot properly, especially if rebooting between operating systems. So for that PC I made a habit of never trying to reboot. When I did updates I would shut it down completely, then cold boot.

---

### Post by Bucky Ball on 2016-03-24
Yea, I use:

> sudo reboot -h now

... myself, or replace reboot with shutdown. Never heard of those other commands you're using, which doesn't mean a lot. ;)

---

### Post by Uinthe on 2016-03-25
[B]Buck Ball, efflandt
[/B]I appreciate your help**. **Unfortunately, you didnt suggest any real solutions. As for me its not an option to humble this issue. So im still trying to find any solutions.

---

### Post by Uinthe on 2016-03-25
Finaly, i solved the problem. Don't know what is the reason, but halt and reboot daemons was turned off on all levels. 
I instlled sysv-rc-conf and turn them on lvl6. So all commands work fine.
Thx for trying to help me.

---

