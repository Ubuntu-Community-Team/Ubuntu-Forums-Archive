---
title: "Does grub disk/partition numbers change? How do I find them?"
date: 2022-09-03
forum: General Help
---

### Post by sofasurfer on 2022-09-03
Sometimes I use operating system on drive #2 with drive #1 still connected. Sometimes I use drive #2 with drive #1 DISconnected.
Does the grub drive/partition number on drive #2 change with drive #1 disconnected or connected? In SDA numbers drive #2 is always drive #2. Is it the same in grub hd numbers? What command will tell me the hd(x) number of the partition I want to use identify?

---

### Post by oldfred on 2022-09-03
UEFI/BIOS assigns drive order.
My systems regularly change order in grub when I reboot with a USB flash drive plugged in,  but that is before partitions are mounted.

In grub menu you can use the commands to go to grub's limited terminal and list drives.
grub> ls
grub> ls (hd0,1)/

Once booted drives are mounted normally by UUID or label which normally keeps them the same. 
Older instructions still used a device like /dev/sda1 to mount  partition. Then it is important to know if drive changed.

---

### Post by sofasurfer on 2022-09-03
[QUOTE=oldfred;14110928
In grub menu you can use the commands to go to grub's limited terminal and list drives.
grub> ls
grub> ls (hd0,1)/
[/QUOTE]

I suspected that those commands would help but when I run them I get errors.
```
  $ grub> ls

Command 'grub' not found, did you mean:

  command 'grun' from deb grun (0.9.3-2)

Try: sudo apt install <deb name>
 
```
Do I have to install 'grub command tools' or something?

BTW, I appreciate your fast answer.

---

### Post by sofasurfer on 2022-09-03
I am new to working with grub commands. I read the following...
```
Go to your grub command line type:

  set root=ls     ; Hit enter

```
Does this indicate that I need to set something up to be able to use grub commands?

---

### Post by ajgreeny on 2022-09-04
At the grub menu hit C to go to the grub command line; there is nothing extra to install.

---

### Post by yancek on 2022-09-04
Your post of the grub> ls and its output indicates you are doing it while booted into an installed system.  As stated in the above post, you need to do it on boot when you get the grub> prompt or by entering c and then enter at the Grub boot menu.

---

### Post by VMC on 2022-09-04
At the grub prompt, your typing "grub> ls". You should type "ls" only from the grub prompt. Also from grub prompt, type "set" to find what partition is in control.
After "set" output, look for prefix= and/or root= to see what partition assigned to grub

---

