---
title: "Time problem ( clock )"
date: 2013-05-28
forum: General Help
---

### Post by loseby on 2013-05-28
Not sure why this happens but since making my system dual boot with windows 7 the clock on Windows is out 10 hours. This happens only after booting into windows after using Ubuntu. If I boot straight into windows after using Windows last ( and adjusting the clock ) its fine, but after using Ubuntu when I go to windows the clock is always out by 10 hours. I actually have 2 dual boot systems and both have the same funny result. Now the clock on Ubuntu is always correct but I am curious as to why have Ubuntu makes the windows clock act strangely and if anyone knows how to fix this ?

---

### Post by sudodus on 2013-05-28
I think the problem is that Windows assumes the system clock is set at local time and Ubuntu assumes that it is set at UTC, and then makes an offset to your local time. There are two solutions if Windows can use UTC too for the system clock. Otherwise there is only one solution, to let Ubuntu use local time too.

I use the small GUI program ***time-admin*** for these tasks in Lubuntu, and there is a corresponding program in Ubuntu (found via System Settings -- Time and Date).

---

### Post by Impavidus on 2013-05-28
You can modify the file /etc/default/rcS. Change "UTC=yes" to "UTC=no".

---

### Post by loseby on 2013-05-28
Its hard to grasp   :-)

In Windows Sydney shows as UTC + 10 hours time zone

IIRC utc was not enabled in Linux clock ( am on windows atm ) but I selected Sydney when setting the time zone up. If this is the case if I enabled it in UTC mode it would then match Windows time ?
Anyway I cant under why the time in Linux screws with a different O/S ........ without linux installed it works correctly 


I guess it could be argued that its just a case of Windows dragging way behind Linux;)

---

### Post by sudodus on 2013-05-29
Linux does not do anything with Windows, but it does set the clock in a different way, than Windows wants it. You need to use the same setting for both operating systems (and it may be called different things in Ubuntu compared to Windows, so test different settings until it works).

---

### Post by loseby on 2013-05-29
> **sudodus said:**
> Linux does not do anything with Windows, but it does set the clock in a different way, than Windows wants it. You need to use the same setting for both operating systems (and it may be called different things in Ubuntu compared to Windows, so test different settings until it works).

Here it is, Windows clock works perfect, never gives trouble. Install Linux ( and with Windows drives disabled ) and the Linux time is correct. BUT now the Windows clock is out by 10 hours which is basically the +10 hours for Sydney. I can go and adjust the clock and it will wrok perfectly day after day boot after boot UNTIL I go into linux ( on a different drive ). Now the time in Lunux is correct and its in the Sydney timezone . Now I boot back into windows and the time is out 10 hours  .....  somehow Linux causes this in Windows.   

Now this happens on 2 separate dual boot computers , one a efi hard drive system ( a  modern mobo ) and the other about 5 years old  ... both Gigabytes

btw: the BIOS clock is correct

---

### Post by Dave_L on 2013-05-29
loseby: Did you try the fix suggested above by Impavidus?

---

### Post by sudodus on 2013-05-30
> **loseby said:**
> Here it is, Windows clock works perfect, never gives trouble. Install Linux ( and with Windows drives disabled ) and the Linux time is correct. BUT now the Windows clock is out by 10 hours which is basically the +10 hours for Sydney. I can go and adjust the clock and it will wrok perfectly day after day boot after boot UNTIL I go into linux ( on a different drive ). Now the time in Lunux is correct and its in the Sydney timezone . Now I boot back into windows and the time is out 10 hours  .....  somehow Linux causes this in Windows.   

Now this happens on 2 separate dual boot computers , one a efi hard drive system ( a  modern mobo ) and the other about 5 years old  ... both Gigabytes

btw: the BIOS clock is correct

> **Dave_L said:**
> loseby: Did you try the fix suggested above by Impavidus?

1. Did you try it?
> 
You can modify the file /etc/default/rcS. Change "UTC=yes" to "UTC=no". 		 

2. Are you hibernating Windows, or are you shutting it down completely before booting into Ubuntu?

---

### Post by Irihapeti on 2013-05-30
I've seen this problem a few times, including on one of my PCs.

The fix that impavidus mentioned solves it.

---

### Post by efflandt on 2013-05-30
Another way to straighten it out is the old fashioned way using hwclock.```
sudo hwclock --systohc --localtime
```That would write system time to the CMOS (hardware) clock/calendar and tell the kernel that the CMOS time is localtime (which is what Windows uses instead of UTC).  Although, Ubuntu usually figures that out automatically during install if you set a proper timezone and it compares time with time servers.

---

### Post by Irihapeti on 2013-05-30
If Windows is already installed, the Ubuntu installer figures that out and sets UTC=No in /etc/rcS

The problem usually arises when using external or removable drives, and Windows has been disconnected while installing Ubuntu. It has no way of knowing that Windows is ever used on that machine.

---

### Post by loseby on 2013-05-30
> **Dave_L said:**
> loseby: Did you try the fix suggested above by Impavidus?

one it comes to using whatever its called I am not really that good at

actually am going to try by using simple cut and paste method

> sudo hwclock --systohc --localtime



> **Irihapeti said:**
> If Windows is already installed, the Ubuntu installer figures that out and sets UTC=No in /etc/rcS

The problem usually arises when using external or removable drives, and Windows has been disconnected while installing Ubuntu. It has no way of knowing that Windows is ever used on that machine.

well its one and one  

one installation with Windows installed and Ubuntu seeing it and putting the boot in GRUB and the other with Windows drives disconnected

anyway...... going to reboot and see what happens

---

### Post by loseby on 2013-05-30
it didnt work

The problem persists and I turned the computer off and then booted and time was wrong

I then when to edit the file /etc/default/rcS.  but got this message :

> You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.


btw: some other comments. Windows time is  easy to fix...just go to time server and update or it will come around to a time when it automatically adjusts time ( no idea when that is ) but I still would like to fix it

---

### Post by Irihapeti on 2013-05-30
To edit that file, you need root privileges. You need to use something like
```
sudo nano /etc/default/rcS
```
if you like using a terminal editor, or
```
gksu gedit /etc/default/rcS
```
if you don't.

If you don't use gedit, substitute whatever editor you do use.

---

### Post by Dave_L on 2013-05-30
For safety, I would also make a backup of the file before editing it:
```
sudo cp -a /etc/default/rcS /etc/default/rcS.bak
```

---

### Post by Irihapeti on 2013-05-30
Dave_L:

Good point. Thanks for the reminder.

---

### Post by loseby on 2013-05-31
actually used gksu and it brought up a box that let me give root privledges  ... I found it whilst doing searches but I think I buggered somewhere along the lines

anyway am in Windows atm so when I switch back will have another go

---

### Post by loseby on 2013-05-31
thankyou for your help

just managed to apply the fix to Linux, shut down and rebooted into Windows and the time was [SIZE=7]100%[/SIZE] correct





will apply to the other PC later

once again, thanks


btw: I am still curious to how and why this thing happens, will try google again

---

### Post by Irihapeti on 2013-05-31
Good to hear. Thanks for letting us know.

---

### Post by loseby on 2013-05-31
have found something that might explain what is happening...its an old post but I finally have some grasp on what is happening

> The problem with the Windows clock being off is because the hardware clock (the one on your actual motherboard) is being set to "Universal" time, or GMT, when you shut down your MacOS bootup. When you boot Windows, Windows assumes your clock is set to your local timezone because that's what Windows does by default. This explains why the people who set their MacOS clock to GMT got the right time in Windows... If the hardware clock is being set to "GMT," when it's actually the local time, Windows will pick this setting up as local time as it did before.

To fix this, you need to add a key to your Windows system registry to tell Windows that your hardware clock will always be GMT.

---

### Post by Irihapeti on 2013-05-31
I did have that registry fix applied to my Windows, but it was causing me too many problems when I was doing install testing. This explains it a bit further. [https://bugs.launchpad.net/ubuntu/+source/clock-setup/+bug/946132](https://bugs.launchpad.net/ubuntu/+source/clock-setup/+bug/946132) So I reverted it and did the /etc/default/rcS. Much easier to edit than the Windows registry!

---

### Post by loseby on 2013-06-02
> **Irihapeti said:**
> I did have that registry fix applied to my Windows, but it was causing me too many problems when I was doing install testing. This explains it a bit further. [https://bugs.launchpad.net/ubuntu/+source/clock-setup/+bug/946132](https://bugs.launchpad.net/ubuntu/+source/clock-setup/+bug/946132) So I reverted it and did the /etc/default/rcS. Much easier to edit than the Windows registry!

thankyou for that , it looks like they dont consider it of any importance

---

### Post by Irihapeti on 2013-06-02
I can understand why they didn't fix it. It's fairly uncommon, and it's reasonable to assume that anyone who's up for editing the registry is capable of changing /etc/default/rcS The big thing is knowing that you do need to edit it!

---

