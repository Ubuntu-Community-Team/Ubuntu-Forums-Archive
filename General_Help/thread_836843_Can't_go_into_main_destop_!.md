---
title: "Can't go into main destop !"
date: 2008-06-21
forum: General Help
---

### Post by WILL_CHAN on 2008-06-21
Recently, my power-supply burned, so I just got a new one and one RAM and my graphics Card ( Geforce ) were broken too. I took those off and now I can log in Windows normally but for Ubuntu, I can't. It just stayed at the black-white screen, I log in with my user name and password but still. It kept stay in that annoying mode. I don't know is it involved with the problem that I have with my RAM and graphics Card or not ! I use both Windows XP and Ubuntu. And I really need help, a whole bunch of codes in C++ I stored in Ubuntu system. It drove me crazy lately. Any help would appreciated. Thanks in advance 
ps : sorry for my horrible English, if sthing is confusing, I will  put more info. as needed. Once again, thanks !   
After I typed in the user name and password, the screen display this :
> 
The program included with the Ubuntu system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.
...
****
And my user name like in terminal appear here : I don't really know what should I type here 'cause I can't see anything...
****/
...


---

### Post by smo0th on 2008-06-21
hello,

remove the 'quiet' and 'splash' settings in your menu.lst file, this will give you the command line output for every step in the boot process, this way you may be able to look where your system is getting stucked, menu.lst is located inside /boot/grub/ directory.

boot from your live cd and mount your ubuntu partition so you can access your files.

---

### Post by WILL_CHAN on 2008-06-22
Thanks Smooth, so now I have to boot from Ubuntu CD ? I'm not really familiar with hardware stuffs, so I'm a little confused.
I understand the step that you showed to access my data, but if I want to make it as before. What should I do ? Do you you know what kind of issues is it ? I want to learn programming on Linux so I used Ubuntu mostly. Can you help me one more time ? Thanks in advance !

---

### Post by smo0th on 2008-06-30
hello, sorry for the late response I'll try to join more often, my recommendation to back up your data is:

boot from live cd
mount your partition
[INDENT]```
sudo mkdir /media/disk
sudo mount /dev/sda1 /media/disk
```
in case /dev/sda1 is your ubuntu partition, type ```
sudo fdisk -l
``` to check your partitions
[/INDENT]
now you should be able to browse your ubuntu partition and grab all your files

---

