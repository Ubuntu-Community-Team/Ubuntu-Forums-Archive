---
title: "Ubuntu 16.04 LTS does not start anymore in VMWare Player"
date: 2018-11-07
forum: General Help
---

### Post by torben545 on 2018-11-07
Hello everyone, 

I have been using Ubuntu in a VM (VMWare Player 14) for a long time now. The host for this system is Win10. I tried to start PyCharm in the Ubuntu guest and it crashed with multiple Java errors. I rebooted to fix this error. However, from that on it does not boot, but opens a shell. Text:

[FONT=courier new]Gave up waiting for root device.   Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT!   UUID=06c1882f-5487-4294-bada-8767adf6d10e does not exists.   Dropping to a shell!

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfd)[/FONT]_

[FONT=arial][FONT=lucida sans unicode][/FONT][/FONT][FONT=verdana]I have a nearly identical virtual machine that works. The only thing I am really concerned about is the files on it from a project for my computer science class. So either way to get to the files is all I really need. So either by getting the system to work again or by somehow extracting the files from the VMWare vmdk files. 

Can anyone help me with this? Thanks a lot!
[/FONT]

---

### Post by ajgreeny on 2018-11-07
Can't help with your inability to boot the vmdk VM but you should at least be able to mount the VM file and retrieve you needed files from it by following the info in [https://askubuntu.com/questions/202571/how-to-mount-a-virtual-hard-disk](https://askubuntu.com/questions/202571/how-to-mount-a-virtual-hard-disk)

---

