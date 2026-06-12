---
title: "ubuntu 16.04 stuck on login loop"
date: 2017-08-03
forum: General Help
---

### Post by offir on 2017-08-03
I have a computer With Ubuntu 16.04 that stuck on login loop


Pretty similar to what appears in this Link
[https://www.youtube.com/watch?v=OG4deLa_vK8]("https://www.youtube.com/watch?v=OG4deLa_vK8")

I tried what he recommended but did not work

I also tried what they recommended in the comments (to remove Nvidia's drivers)
Also did not worked

I do not have access to the Desktop

how do i fix this  so i will have access to my desktop

---

### Post by BenginM on 2017-08-03
Hiya , so what've tried so far is , reinstalling xorg and xorg server and then installing ubuntu-desktop for Unity .. 


when you switch to a virtual console , run 

sudo apt-get remove --purge nvidia-*


This is the equivalent of searching for "additional drivers":  sudo ubuntu-drivers list
  then use:
  sudo ubuntu-drivers autoinstall
After autoinstal , switch to another VT , Ctrl+Alt+F6

sudo service lightdm restart

now switch back to X with Ctrl+Alt+F7 , login .. did you reached the desktop ..!

if you're still unable to login, then i suppose it's time to replace lightdm display manger and try login in with GDM or Slim , or SDDM ..

again , from a VT , :

sudo apt-get install gdm

sudo service lightdm stop

sudo dpkg-reconfigure lightdm

the package configuration window will show ..

select gdm instead of lightdm, press Tab to move to OK, and press Enter.

then $ sudo reboot

---

### Post by offir on 2017-08-03
It did not work
Now I do not get to the desktop either
It keeps doing a loop as if it's trying to get to the desktop
I tried to press Ctrl + Alt + F1-6
But i can not
I do not have the time to enter a user name and password
Because it's all the time in the loop

---

### Post by BenginM on 2017-08-03
Did you install the Nvidia's driver using the .run file !

---

### Post by BenginM on 2017-08-03
You don't happen to have an xorg.conf.XXXXXXXX in use, or do you!

if you purged Nvidia-* , then nouveau is loaded to be used ..

You didn't conform , did you replaced lightdm with GDM!

---

### Post by BenginM on 2017-08-03
Are you able to boot into recovery mode ,and drop to a root shell !

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)


And for future reference , this is how one's supposed to install Nvidia's driver :

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by offir on 2017-08-03
> Did you install the Nvidia's driver using the .run file ! 
I've done all the commands you've written

> You didn't conform , did you replaced lightdm with GDM! 
yes i did


> Are you able to boot into recovery mode ,and drop to a root shell !

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

I did not know how
I'll try it

---

### Post by offir on 2017-08-04
>  Are you able to boot into recovery mode ,and drop to a root shell !

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

I just tried it
And I have a possibility

What options do I have to choose and what to do exactly

---

### Post by BenginM on 2017-08-04
I still don't know how you have installed the nvidia driver, so i can't guide you ,  did you used the additional drivers GUI section or used the nvidia installer .run file from nvidia.com!

---

### Post by offir on 2017-08-04
> I still don't know how you have installed the nvidia driver, so i can't guide you , did you used the additional drivers GUI section or used the nvidia installer .run file from nvidia.com! 

These are the steps I have taken

when in logging desk top

Ctrl + Alt + F1 
then 
```
sudo apt-get remove --purge nvidia-*
```
then
```
sudo ubuntu-drivers autoinstall
```

Ctrl+Alt+F6
```

sudo service lightdm restart
```

It did not work so I tried the second part

Ctrl + Alt + F1 
```
sudo apt-get install gdm
```

```
sudo service lightdm stop
```
```

sudo dpkg-reconfigure lightdm
```
 
i select gdm instead of lightdm

then ```
 sudo reboot 
```

That's it

---

### Post by BenginM on 2017-08-04
offir , No , am asking how did you installed nvidia driver before you got stuck in a login loop .. did you used a .run file or installed the driver from ubuntu's repo using the additional drivers .. because you have tried to remove --purge nvidia-* , and you still unable to login.

a *run file would look something like this " NVIDIA-CURRENTLY-INSTALLED-VERSION.run " ...

---

### Post by offir on 2017-08-05
i installed the driver from ubuntu's repo using the additional drivers

additional drivers had several options
I chose the one with the stable release

Something else I did not write in the first post
The computer worked fine for half a year
This problem appeared about a week ago
Since then I can not log on to the computer

---

### Post by BenginM on 2017-08-05
Ok, there is few thing we need to check at this point , since the system was working fine for a long time , and we tried to remove -- purge nvidia-* without secsuess , maybe you;re locked out because your home directory is full , or /boot or / .. so to check this boot into recover mode drop to a root shell , and run df -h and see if any of those are % full ratio .. note down the /root partition device sda1 or 2 , and if you have a separate /boot partition note that down also .. also it's a good time to check the file system ..

from recovery (safe) mode drop to a root shell , and type:



mount -o remount,rw /
df- h
fsck -f
mount -o remount,ro /
sync
reboot

---

### Post by offir on 2017-08-05
```
mount -o remount,rw /
df- h
fsck -f
mount -o remount,ro /
sync
reboot 
```

I tried to do what you wrote but it did not work
Only the first line was accepted
When I typed the second line and clicked Enter
The computer did a kind of restart
It returned to the previous screen where I had several options (where I chose "drop to a root shell")
Then the computer no longer responded to commands
Only to Ctrl Alt Del

So I tried something else
After I have reached the screen that allows the selection of recovery mode
 I chose The fourth line in the picture
Then the computer came up and I got to the desktop

There were a lot of updates
The computer worked maybe half an hour just on updates
And then demanded a restart

I clicked Restart
And I went back to the previous situation where there was no access to the desktop

It has not reached the stage of log in

---

### Post by BenginM on 2017-08-05
okay , if you're stuck now on a black screen ... switch to a VT Ctrl+Alt+F3 , login , then run # sudo reboot .. after the BIOS screen press ESC or Right shift .. this should show the GNU GRUB bootloader Menu  "like the picture you took " where you have kernel options to boot with/into .. highlight kernel 4.4 , and hit enter to boot with it .. does that take you to the display/login manager ..!

---

### Post by offir on 2017-08-05
Maybe I did not explain well
I can get to this screen that appears in the picture

But if I choose the first option

I do not get to the desktop
The computer enters a type of loop as if it is trying to load the desktop repeatedly

I would upload a video of everything
But I do not know how you can upload large files here

---

### Post by #&amp;thj^% on 2017-08-05
> **offir said:**
> Maybe I did not explain well
I can get to this screen that appears in the picture

But if I choose the first option

I do not get to the desktop
The computer enters a type of loop as if it is trying to load the desktop repeatedly

I would upload a video of everything
But I do not know how you can upload large files here

Sorry for the drive by but have you tried with "nomodeset" yet?

---

### Post by offir on 2017-08-06
what is nomodeset
I searched Google to know what it is
Not really understand

---

### Post by deadflowr on 2017-08-06
A nice explanation of nomodeset (and other settings) here:
[https://ubuntuforums.org/showthread.php?t=1613132]("https://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by BenginM on 2017-08-06
I don't think bootin' into normal mode with nomodeset is a good idea..!

---

### Post by offir on 2017-08-07
so only new install ?

---

### Post by BenginM on 2017-08-07
> **offir said:**
> ```
mount -o remount,rw /
df- h
fsck -f
mount -o remount,ro /
sync
reboot 
```

I tried to do what you wrote but it did not work
Only the first line was accepted
When I typed the second line and clicked Enter
The computer did a kind of restart
It returned to the previous screen where I had several options (where I chose "drop to a root shell")
Then the computer no longer responded to commands
Only to Ctrl Alt Del

So I tried something else
After I have reached the screen that allows the selection of recovery mode
 I chose The fourth line in the picture
Then the computer came up and I got to the desktop

There were a lot of updates
The computer worked maybe half an hour just on updates
And then demanded a restart

I clicked Restart
And I went back to the previous situation where there was no access to the desktop

It has not reached the stage of log in

well so far we're tried every possible solution to fix this , if you were able to boot and reach the desktop with an old kernel , perhaps you can try fixing broken packages with dpkg from recovery mode like this [http://imgur.com/a/jwHrB](http://imgur.com/a/jwHrB)

the only things that we haven't checked is the permissions set on $HOME , so when drop to a root shell , try 

chown user:user /home/owner/* 
chown user:user /home/owner/.*

where user is your YourUserName

then try to boot with that kernel that got you to the desktop.

---

