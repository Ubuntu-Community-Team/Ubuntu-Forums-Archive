---
title: "Grub Error, can't go to bios"
date: 2014-02-16
forum: General Help
---

### Post by bigmonty on 2014-02-16
Whenever I power up the computer, it types a little message "system resuming". Then it comes up with the following message. 


```
error: unknown filesystem 
grub rescue >  
```


I tried to pull out the battery to see whether the computer restarts or not but to no avail. At the bottom, there is a message: "system resuming" no matter what I do.


I followed the instruction from the following link:
[https://help.ubuntu.com/community/Grub2/Troubleshooting#Search_.26_Set](https://help.ubuntu.com/community/Grub2/Troubleshooting#Search_.26_Set)


Following are the steps I followed:


In the grub rescue prompt. I typed:


```
 set prefix=(hd0,6)/boot/grub
 set root=(hd0,6) 
```


Then if I type  
 ```
ls (hd0,6)/boot/grub/ 
```
 I see all the mod files but when I do 


 ```
insmod normal 
```


it says ```
'/boot/grub/i386-pc/normal.mod not found 
```


Then I typed the full path 

```
insmod /boot/grub/normal 
```

 but I end up with the same message. What is confounding is that why reference of 'i386-pc' is coming up. Does it have anything to do with  grub.cfg file? I don't seem to find that file.


This has left me stumped for days now. Any suggestions will be highly appreciated.

---

### Post by jeanjd63 on 2014-02-17
Hello
Il your install is on /dev/sda6, you can try to réinstall grub with à LiveCD/USB :
[COLOR=#000000][FONT=Arial]**sudo  mount   /dev/sda6   /mnt**  
**sudo  mount  --bind  /dev  /mnt/dev**
**sudo  mount  --bind  /proc  /mnt/proc**
**sudo  mount  --bind  /sys  /mnt/sys**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]**sudo  chroot  /mnt**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][B]update-grub
grub-install  /dev/sda
reboot

[/B][/FONT][/COLOR]

---

### Post by bigmonty on 2014-02-19
Thanks for your reply. The problem is that my system goes straight to grub rescue prompt. In the grub rescue prompt sudo command does not work. As I mentioned in my first post, when I power up, "system resuming...." message comes up and it straight goes to the grub rescue prompt. No pre-session button is working!

---

### Post by bigmonty on 2014-02-19
I tried the following also: 

[COLOR=#000000][FONT=Comic Sans MS]set prefix=(hd0,6)/usr/lib/grub

[/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]Then if I do [/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]insmod normal[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]then I get the completely new error:[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]'grub_divmod64_full' not found

I have no idea what's that. 
[/FONT][/COLOR]

[COLOR=#000000][FONT=Comic Sans MS]
[/FONT][/COLOR]

---

### Post by oldfred on 2014-02-19
The commands from jeanjd63 are a chroot (CHangeROOT) into your system using your liveDVD or flashd drive to run repairs from inside your install.

May be best to see details.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

