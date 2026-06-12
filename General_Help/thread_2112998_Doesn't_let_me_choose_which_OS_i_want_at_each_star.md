---
title: "Doesn't let me choose which OS i want at each start"
date: 2013-02-06
forum: General Help
---

### Post by LioRiX on 2013-02-06
Hello guys,
About 5 days ago, I installed Ubuntu 12.10. For some reason, it didn't detect my Windows XP so I chose 'something else' and manually install it. Unfortunately, I just realised I installed it on a different partition than the windows one, which means its not on the boot partition. 
The problem is that now it goes directly in Ubuntu without asking me if I prefer Windows or Ubuntu.

I tried to use those guides with the grub2 fix but when I type "sudo grub-update" on the LiveCD it gives me this error:
"usr/sbin/grub-probe: error: failed to get canonical path of /cow."

I also tried to use Boot Repair (both on LiveCD and the installed Linux) and it's stuck on "Scanning Systems"

Any ideas? thank you!

---

### Post by mike555 on 2013-02-06
Use the live dvd and try, open gparted and send us a screenshot .....

---

### Post by LioRiX on 2013-02-06
> **mike555 said:**
> Use the live dvd and try, open gparted and send us a screenshot .....
I'm here at the liveCD "try" Ubuntu. 
I opened the gparted and its about 10 minutes that it loads and says "scanning all devices.." what do i do?
are you sure that scan shouldn't be made with the installed ubuntu?

---

### Post by howefield on 2013-02-06
> **LioRiX said:**
> I'm here at the liveCD "try" Ubuntu. 
I opened the gparted and its about 10 minutes that it loads and says "scanning all devices.." what do i do?
are you sure that scan shouldn't be made with the installed ubuntu?

Gparted isn't part of a default install of Ubuntu, you would have to manually install it (which isn't difficult and takes only a few minutes), but it is included with the Live CD. You could load gparted from the installed Ubuntu which would be fine for the purposes of getting a screen shot.

---

### Post by LioRiX on 2013-02-06
> **howefield said:**
> Gparted isn't part of a default install of Ubuntu, you would have to manually install it (which isn't difficult and takes only a few minutes), but it is included with the Live CD. You could load gparted from the installed Ubuntu which would be fine for the purposes of getting a screen shot.

On both LiveCD "try" option Ubuntu and the installed Ubuntu it gets stuck at "Scanning all devices", the program is still running, I can still see this bar moving back and forth but no change and about 20 minutes passed.. (Same as it went with Boot Repair)..
What shall I do?

---

### Post by howefield on 2013-02-06
I doubt that you will get a result after 20 minutes, do you have any external drives plugged into the computer, eg USB drives ?

If you have, you might try unplugging them and trying again.

---

### Post by LioRiX on 2013-02-06
> **howefield said:**
> I doubt that you will get a result after 20 minutes, do you have any external drives plugged into the computer, eg USB drives ?

If you have, you might try unplugging them and trying again.

I don't have any plugged in..
Will it help you to know the output in terminal when i say "sudo fdisk -l" ?
If not, what do I do to solve this..>?

---

### Post by howefield on 2013-02-06
You could try running from the terminal..

```
gksudo gparted /dev/sda
``` 

assuming that your disk is sda.

The output of fdisk would probably be useful.

---

### Post by LioRiX on 2013-02-06
> **howefield said:**
> You could try running from the terminal..

```
gksudo gparted /dev/sda
``` 

assuming that your disk is sda.

The output of fdisk would probably be useful.

Your code opened gparted and its still at "Scanning all devices", I brought a screenshot:

[[IMG]http://img854.imageshack.us/img854/1676/screenshotfrom201302061.png[/IMG]](http://imageshack.us/photo/my-images/854/screenshotfrom201302061.png/)


____________________________________________

fdisk -l code gives:

[[IMG]http://img189.imageshack.us/img189/1676/screenshotfrom201302061.png[/IMG]](http://imageshack.us/photo/my-images/189/screenshotfrom201302061.png/)



Ideas?

---

### Post by travalon on 2013-02-07
Try to install grub customizer. I don't know much about it but I've looked it over just in case.

---

### Post by grahammechanical on 2013-02-07
> Unfortunately, I just realised I installed it on a different partition than the windows one, which means its not on the boot partition. 

Ubuntu does not need to be on the boot partition, as you call it. What do you mean by boot partition? And this proves it

> The problem is that now it goes directly in Ubuntu without asking me if I prefer Windows or Ubuntu.

so, Ubuntu is booting. In the Ubuntu on the hard disk open a terminal and run

```
sudo update-grub
```

It will give a printout that should tell you if it sees Windows on sda1. If it shows Windows as well as Ubuntu run this command

```
sudo grub-install /dev/sda
```

Personally I think that the problem has to do with the partitions not being in disk order. In my opinion

Sda2 is an extended partition with sda5, sda6 and sda7 inside it. That should not be a problem. But I also see that

sda7 begins just after sda5 ends but sda6 begins just after sda7 ends. Is this what this causing a problem when it comes to having the disk/partitions scanned? I do not know.

Regards.

---

### Post by Joao Lacerda on 2013-02-07
Friend, take a look on this link.
[http://www.lancelhoff.com/restore-grub2-after-installing-windows/](http://www.lancelhoff.com/restore-grub2-after-installing-windows/)

Good luck

---

