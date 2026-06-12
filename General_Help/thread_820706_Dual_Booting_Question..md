---
title: "Dual Booting Question."
date: 2008-06-06
forum: General Help
---

### Post by dcruwys on 2008-06-06
So here is my question.

I been using ubuntu and I LOVE it. but one tiny problem.

My games wont work!

I have tried wine, it won't work for them.

So Ubuntu is all I have installed on my comp, but in the near future, I would like to put Windows on it dual booting. So how can I do this?
Could I just install Windows on it's own partion (I can make one)? Or do I need to install something to dual boot it?

---

### Post by Titan8990 on 2008-06-06
After installing Windows you will need reinstall the GRUB bootloader in order to boot both OS because the Windows MBR (which will only boot MS operating systems) will overwrite GRUB.

You can reinstall GRUB easily via the Ubuntu alternate CD in rescue a broken system mode.

Typically, it saves a lot of hassle to just install Windows first, then there is nothing that needs to be done outside of installing both operating systems.

---

### Post by rraj.be on 2008-06-06
Nothing to be installed new to dual boot.

Just you can formate a partition that you want and install windows as you do usually.


But at the end your windows boot loader will over write your GRUB [Ubuntu boot loader]

After installing windows you have to reinstall your GRUB alone.[not ubuntu]

Its a simple 15 minutes job to reinstall GRUB.

so you can go ahed with installing windows without any fear.

---

### Post by babylon2233 on 2008-06-06
What version of Windows will you install? Windows installer will overwrite your boot sector without taking care of your existing operating system except it is another Windows installation. So, you need to reinstall GRUB or just use EasyBCD on Windows(Vista-only) later.

---

### Post by rraj.be on 2008-06-06
HOW TO REINSTALL GRUB:

There are already a lot of tutorials available for that.

Hope this will help you fine.


Boot into live cd.

open in terminal as 

Applications-->system-->Terminal

and type 


```
sudo grub

find /boot/grub/stage1
```

if it returned like hd(x,y)

then type


```

root (x,y)
setup (x)

quit

sudo reboot


```

Now your boot loader is restored and you can boot into both your windows and Ubuntu

---

### Post by FTBPrimeEvil on 2008-06-06
My situation is a little bit different, I have Vista ultimate installed and running Ubuntu Workstation in VMWare, VMware is ok for other windows os's but not Linux, so I would like to shrink my partition and install Ubuntu to this second partition, while leaving vista in place on the first partition.
Could someone one give me pointer on the best way to do this?

Also here is another option for me, i have another HD which goes into my smart bay on my Alienware m15x which takes the place of my CD ROM, could i install Ubuntu on this drive? but how would i install without the CD ROM? I would prefer to run Ubuntu from the second hd but if you think it can't be done then the above first option would be fine.

Let me know,

First time Ubuntu user as of today! 
I am an network engineer for 18 yrs, have my MCSE. I know it's pathetic that i am just now getting into Ubuntu.(But MS just pissed me off)

---

### Post by rraj.be on 2008-06-06
Hello Mr professional.MCSE,A warm welcome to ubuntu community

Could you just give me the partition details of your vistal installed hard disk.

Then i could guid you to install ubuntu in that.

---

### Post by FTBPrimeEvil on 2008-06-06
Single HD Hitachi 16mbCache 200gb, 
Disk:0
Type: Basic
Status:Online
Partition style:MBR
Capacity:190781 MB
Drive:"C"

Vista will not let me shrik the volume, will have to move the page file elsewhere, but i will alow 16gb for Ubuntu, is this enough? for the 2 partition disk:"1"

---

### Post by rraj.be on 2008-06-07
You can use Ubuntu in 15 GiB if you dont need to store any huge data in ubuntu partition.

You will get only 3-4 GiB if you install as much application's you want.

Then you need to create a swap partition about 1 GiB.

As you dual boot you can also make it to be a swap file [without any need to partition your hard disk]

Hence you may need a max of 5 GiB of disk space to install ubuntu.

and my question is do you have only one partition in that 190 GiB of h/d.

Ok.

then just create a partition for ubuntu of about 15 GiB or more

You may do this with your windows or using the boot cd itself.

After this you will just need 20-30 minuets to install Ubuntu, and another 1 hour to customize according to your needs.

Be ready.

---

### Post by dcruwys on 2008-06-08
So in the post you posted, what should i enter in x and on the y spot?

---

### Post by dcruwys on 2008-06-09
Fixed x ,y thing now i get the

<windowsroot>system32/hal.dll is missing error!!!

I'm out on the road (well kinda) so I cant use my windows disk. ubuntu works fine, but when i select windows i get that error.

I have access to blank disks so if there is some kind of free alterative to the Spotmau PowerSuite that would rock my socks off.

Thanks!

---

### Post by dcruwys on 2008-06-10
bump

---

### Post by MariusSilverwolf on 2008-06-10
The error C:\Windows\System32\hal.ddl is missing means Windows lost the configuration for the Hardware Abstraction Layer.

I'm going to assume/hope you're using Windows XP and that you have an installation CD.  The site with step-by-step instructions can be found here: [http://icrontic.com/articles/repair_windows_xp](http://icrontic.com/articles/repair_windows_xp)

A word of caution:  By following these steps, you will likely overwrite GRUB.  Follow the steps given by rraj earlier in this thread to reinstall and regain access to your Ubuntu installation.

---

### Post by dcruwys on 2008-06-10
thanks!

but oh well, I guess i'll be waiting a few weeks till I fix it,

Thanks again!

---

### Post by YMS_1975 on 2008-07-01
I could not get WINE or VMWARE to work when it came to running my Windows program. I only had 1 program that I had to run via Windows (so I could update my portable GPS), so I had no choice but to dual boot.

Not knowing much about this, I searched high and low for the answer (but nothing worked). Then, I came across this video by chance. Since then, I've been enjoying a **problem-free** dual boot with Ubuntu 8.04 & Windows Vista Ultimate.

Hope this helps you, like it helped me.

[Click Here.]("http://www.youtube.com/watch?v=JBfl3oViny8")

---

