---
title: "I've changed the GRUB nonintentonally, how to change that back?"
date: 2014-07-28
forum: General Help
---

### Post by Thorgils on 2014-07-28
Hi everyone!

I've tried to install the GNOME GUI to my Ubuntu 12.04 instead of Unity. That successed, but something crashed in my GRUB and now i can't use that normally. It changed it's background to something debian stuff, but i've never ever installed debians to my laptop. I cant choose any other operating system in the GRUB, just the default, and when I'm starting that, it allways send me an error massage. I've deleted the GNOME, but nothing changed. 
Any advice? Thank you.

---

### Post by oldfred on 2014-07-28
Lets see details on install. Post link to BootInfo report.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If a image file was copied into a directly that grub expects it will use that as a background image or theme.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by ibjsb4 on 2014-07-28
How did you install the gnome gui?

Did you change your display manager from lightdm to gdm?  Open a terminal and enter:
```
cat /etc/X11/default-display-manager
```
And what did this error message say?

---

### Post by Thorgils on 2014-07-28
Thank you for the answers, i have solved the problem today, my USB mouse was the guilt. :) When i plugd that out i could control the grub.
By the way, i still get those error massages after the booting, but when i've Canceld them they disappeared totally. The text is simply: "System program problem detected" And it asked if i wanted to report it.
I don't know why did the grub changed its background, but it doesn't hurts me, i like debian too, just looks a bit strange in a fully not debian computer. :)

---

### Post by Thorgils on 2014-07-28
Oh, and i still have the lightdm

---

### Post by ibjsb4 on 2014-07-28
> **Thorgils said:**
> By the way, i still get those error massages after the booting, but when i've Canceld them they disappeared totally. The text is simply: "System program problem detected" And it asked if i wanted to report it.
That is Apport giving you that message, you can reset Apport in terminal with the command:
```
sudo rm /var/crash/*
```

---

### Post by Thorgils on 2014-07-30
> That is Apport giving you that message, you can reset Apport in terminal

Thank you :)

---

### Post by ibjsb4 on 2014-07-30
I would also consider disabling apport.
> Apport collects potentially sensitive data, such as core dumps, stack traces, and log files. They can contain passwords, credit card numbers, serial numbers, and other private material.
[https://wiki.ubuntu.com/Apport#How_to_enable_apport](https://wiki.ubuntu.com/Apport#How_to_enable_apport)

To disable apport
```
echo 'manual' | sudo tee /etc/init/apport.override
```
And now if your problems are resolved
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums :)

---

