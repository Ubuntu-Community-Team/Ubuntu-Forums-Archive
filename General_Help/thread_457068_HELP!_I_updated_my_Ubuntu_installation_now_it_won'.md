---
title: "HELP! I updated my Ubuntu installation now it won't boot"
date: 2007-05-28
forum: General Help
---

### Post by BuckoA51 on 2007-05-28
I had not used my Ubuntu installation in a while, so I used the update manager to update it. When it had finished downloading and installing it said a reboot was required... Now all I get when I try to reboot is

"Error 17 - Cannot mount selected partition"

I thought Linux was supposed to be robust? Windows hasn't done this to me since the 98 days, yet I've had a SUSE linux installation fall over on me when I changed screen res, now Ubuntu dies after an update! :(

---

### Post by louieb on 2007-05-28
Error 17 claims that the partition that you're attempting to boot is of a format that GRUB does not recognize.

Using a livecd such as Knoppix or Mepis, could you post the contents of your  /boot/grub/menu.lst and the result of "sudo fdisk -lu".

Now for my cafe rant: With windows I have to protect my computer for viruses, maul ware, and spy ware.  With Linux I don't worry about those things. The one thing that can and has trashed a Linux install is me.

---

### Post by Famicommie on 2007-05-28
Whoa, slow down there. If you want us to help, then you have to provide us with information first. In every help thread you create, you should tell us which version of Ubuntu you are using. You can also set up your profile so that it will list said version.

Now, the other pieces of information are a little trickier to get. Have you installed the necessary drivers in Windows that will allow you to read from your GNU/Linux partition? If not, then you will have to boot up the LiveCD and run the terminal command
```
sudo mkdir /media/Ubuntu && sudo mount -t ext3 /dev/<partition> /media/Ubuntu
```
Insert the proper location of <partition> (mine is hdb1, for instance). If you don't know what it is, you can bring it up on a terminal with the command ```
sudo fdisk -l
``` It will be the listing with the type "Linux".

Having mounted your hard drive, navigate to /boot/grub/ and paste the contents of the file "menu.lst". That is our first necessary ingredient.

The other thing we need is the contents of your fstab, located in the file /etc/fstab

It would also be helpful if you listed the output of ```
sudo fdisk -l
```

---

### Post by yabbadabbadont on 2007-05-28
It is probably related to the security update to the kernel.  It appears to be breaking things for many people.

[http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)

---

### Post by Nehvrook on 2007-05-28
I doubt this will help much, but the other day I got that error. It turned out my SATA cable into the hard drive was a little loose. I plugged it in properly and re-booted and it worked again.
I realise this probably won't be the case but I thought I may as well let you try it.

---

### Post by BuckoA51 on 2007-05-28
Okay, I'm running Ubuntu 7.04 the Feisty Fawn one... I tried Knoppix but all I get is a black screen when I boot the DVD, can't I just use the Ubuntu DVD to do what you ask?

I don't think this is a hardware problem as all the drives on my machine were working fine until I applied the updates.

You're right about Linux being much better against spyware/viruses etc but I hardly think that what I did was stupid or even wrong or should have broken the OS, so I'm a little disappointed in it to be honest. Usually keeping things up to date is sensible not stupid. There are people who will probably say they had far more problems running Windows than they did Linux, but so far that has not been my experience at all, even taking into account my lack of experience with Linux compared to Windows.

---

### Post by BuckoA51 on 2007-05-28
sussed, thanks for the hints I was able to go into the grub menu and change the boot drive, as you suspected the menu.lst file was overwritten. I have absolutely no idea why this would happen. I am 100% sure I did not change it myself. I was able to change it temporarily then boot into ubuntu and use sudo to edit the file back to how it was.

Panic over, for now.

---

