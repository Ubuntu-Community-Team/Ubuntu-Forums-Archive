---
title: "Installed Vista, Ubuntu Cannot Be Booted"
date: 2007-05-14
forum: General Help
---

### Post by baibbas on 2007-05-14
I installed Vista Business over my XP partition and now when I boot the machine I don't get the menu that gives me the option to get to Ubuntu or XP (now Vista)...

Ubuntu is still there, how can I get it back so I can boot to it???

---

### Post by jbro on 2007-05-14
Generally when this happens it is because the new OS has overwritten grub in your master boot record (MBR) with its own boot loader. You can solve this problem by booting from a LiveCD or other type of rescue CD with grub and its related utilities and running ```
grub-install <device>
``` where <device> is the partition where you want to install grub or the device name (e.g. /dev/sda) if you want grub on the master boot record. You may then have to set up a boot entry for Windows Vista if it is not picked up automatically. To boot my windows I have the following stanza in my /boot/grub/menu.lst ```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

One warning: As you can see, I do not have Vista, and I am assuming it doesn't play any nasty tricks with the boot record. You may want to verify this with someone who is double booting Linux and Vista.

Regards,
jbro

---

### Post by m.musashi on 2007-05-14
Yes, this is a nice trick from MS. They seem to be under the impression that no one would ever dual boot so they just overwrite the MBR without even asking. Very rude in my opinion. /rant

Anyway, the fix is easy. Boot your live CD and open a terminal
```
sudo grub
grub> find /boot/grub/stage1
```
This will produce output similar to (hd0,3) depending on your setup. Next type
```
grub> root (hd0,3)
grub> setup (hd0)
```
being sure to substitute the right numbers for your setup.

Some how-tos suggest writing grub to your linux root but in my experience that doesn't work. You will want grub on the mbr to be able to use it.

---

### Post by baibbas on 2007-05-16
Thanks for the advice, I'll try it out and get back with what the result is.

---

### Post by baibbas on 2007-05-16
> **m.musashi said:**
> Yes, this is a nice trick from MS. They seem to be under the impression that no one would ever dual boot so they just overwrite the MBR without even asking. Very rude in my opinion. /rant

Anyway, the fix is easy. Boot your live CD and open a terminal
```
sudo grub
grub> find /boot/grub/stage1
```
This will produce output similar to (hd0,3) depending on your setup. Next type
```
grub> root (hd0,3)
grub> setup (hd0)
```
being sure to substitute the right numbers for your setup.

Some how-tos suggest writing grub to your linux root but in my experience that doesn't work. You will want grub on the mbr to be able to use it.

Ok, I did as you asked, and now when I boot I get this

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device...

HELP!!!

---

### Post by baibbas on 2007-05-16
Bump....

Cmon guys I need help here!!

---

### Post by brim4brim on 2007-05-16
You should be able to restore the MBR with Vista install disc using repair option (assuming its the same as XP).

Then you can use Msconfig and change the windows boot loader and add feisty into it.  That would be the way I'd do it.

---

### Post by baibbas on 2007-05-16
Tried the system restore, there is no option for restoring the MBR on the repair menu, I tried to do a system restore and when it rebooted gave me teh same boot message...

---

### Post by baibbas on 2007-05-16
BUMP...look, this is ridiculous, I follow the instructions and now I can't get to Vista or Ubuntu..SOMEONE PLEASE HELP ME...I don't want to have to totally whack my drive and reinstall Vista and Ubuntu, so could some one PLEASE tell me how to get my boot menu back that I lost installing Vista?  Now I cant get to Vista at all because I followed the second poster's instructions and it keeps asking me for the damn boot device!

HELP HELP HELP!!

---

### Post by baibbas on 2007-05-16
Bump

---

### Post by baibbas on 2007-05-16
Bump Again.

---

### Post by jbro on 2007-05-16
Have you tried booting with a LiveCD, doing grub-install, and checking your /boot/grub/menu.lst file to make sure it's got all the right stuff? I would start there. Don't despair. Perhaps if you provide some information on your partitioning scheme (like post the output of "fdisk -l <device>" where <device> is your hard drive device) I can give you some more detailed steps.

Regards,
jbro

---

### Post by m.musashi on 2007-05-16
> **baibbas said:**
> Ok, I did as you asked, and now when I boot I get this

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device...

HELP!!!

This sounds like a bios error. It is looking for a boot device and not finding one. Or it finds one but it is not properly set up. If you followed the steps I listed before about using a live CD and reinstalling grub then (assuming you put in the right information for your system) it should work.

Can you be a bit more specific about what steps you have taken, when in the startup process you get this error, how you have your drives set up in the bios (i.e. what boots first, second and so on) and the output from 
```
sudo fdisk -l
```
The last part of that is a small letter L.

You can also use the vista disk to repair the MBR which will give you access to vista again but not both.

We can solve this problem so hang in there. Not all fixes are easy and since we are not all in front of our computers 27/7 there will be delays between you post info and when we can respond.

One more thing, when you boot a live CD and set up grub, be sure you use the correct partition names for your system and not the examples I gave. For example, if your stage1 is on disk 0 and partition 5 (ie /dev/sda5 which is the same as (hd0,4)), at the grub prompt (which looks like 'grub >') you would do
```
root (hd0,4)
setup (hd0)
```
The second number in the (hd0,x) part is always one less than the number in /dev/sdax.

---

