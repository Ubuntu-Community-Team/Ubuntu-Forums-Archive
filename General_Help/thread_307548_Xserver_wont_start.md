---
title: "Xserver wont start"
date: 2006-11-26
forum: General Help
---

### Post by elsebasbe on 2006-11-26
Hi all!
I've got a big problem starting X.
When I boot everything it´s normal till it comes to the x server,
I get this message:

> 
[I](EE) No Devices Detected.

Fatal Server Error:
no screens found
XI0:  fatal I0 error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaning.
xauth: error in locking authority file /home/elias/.Xauthority
[/I]


I have tried to chmod the .Xauthority file and also set me as the owner of it (I had that problem with another file a while ago.), but nothing works.

I preformed a few searches on google and on this forum, but problem not solved.. And another thing, for some reason the internet connection doesn´t work either, so I can make any apt-get installs and stuff.

A thought, is there some recovery tool or something anywhere? (Except the one when you boot, because that didn´t work)

Oh, and yeah, here is my system:
X Window System Version 7.0.0
Linux 2.6.15.7 i686
Ubuntu 6.0.6

I would *really* appriciate help, as is now I can´t use my compyter at all  :(

---

### Post by taurus on 2006-11-26
There is a problem with your /etc/X11/xorg.conf so you need to reconfigure it again.  From a prompt, type

```
sudo dpkg-reconfigure xserver-xorg
```
And if you don't know the answer, just hit the Return or take the default setting...

---

### Post by elsebasbe on 2006-11-26
Okey, I tried that before too, but I might not managed to get it right.

A simple question, I got Connect3D Radeon x800GTO 256Mb DDR grafic card, what "X server driver" should I select (there is no Radeon or anything similar to the card in the list)?

---

### Post by taurus on 2006-11-26
You can use ATI if it's on the list.  Otherwise, pick vesa and once you have X running again, then install a driver for your graphic card...

---

### Post by elsebasbe on 2006-11-26
It didn´t work :(
Same problem as before, after the re-configuration.

You have any other ideas?

---

### Post by taurus on 2006-11-26
Can you boot your machine using the LiveCD?

---

### Post by elsebasbe on 2006-11-26
Unfortunately I don´t have it here, but I probably will be able to download and burn a new one tomorrow.
Is there some utulity there I can use? Reinstall?

Thanks for your help btw, I really appriciate it!

---

### Post by taurus on 2006-11-26
If the LiveCD boots up fine with your machine, then you can copy the /etc/X11/xorg.conf from the CD to your harddrive...

---

### Post by elsebasbe on 2006-11-26
Ah, okey. I´ll try that as fast as I can, back later.

---

### Post by elsebasbe on 2006-11-27
I´ve got the LiveCD now and its running. But how do I access the hard drive to copy over the .Xauthority file?
When I do /home/elias it says that it couldn´t find it.

Edit:
When I go to root and double click the hdd (a partion), I get this error mesage:

> Unable to mount the selected device
error: device /dev/sda1 is not removable
error: could not execute pmount


---

### Post by darrenm on 2006-11-27
Sorry for pursuing 2 different routes but are you able to post your /etc/X11/xorg.conf file here and your /var/log/Xorg.0.log?

---

### Post by taurus on 2006-11-27
Now, I need to know the location, partition, where you installed Ubuntu on!  If not sure, open a terminal and paste the output of this command here...

```
sudo fdisk -l
```

---

### Post by elsebasbe on 2006-11-27
> **taurus said:**
> Now, I need to know the location, partition, where you installed Ubuntu on!  If not sure, open a terminal and paste the output of this command here...

```
sudo fdisk -l
```

I get this:
```

Devide Boot, Start, End, Blocks, Id, System
/dev/sda1, 1, 1275, 10241406, 83, Linux
/dev/sda2, 1276, 1416, 1132582+, 82 Linux swap / solaris
/dev/sda3, 1417, 36483, 281675477+, 83, Linux

```

---

### Post by elsebasbe on 2006-11-27
> **darrenm said:**
> Sorry for pursuing 2 different routes but are you able to post your /etc/X11/xorg.conf file here and your /var/log/Xorg.0.log?
Yes, I will. And I'm not sorry, just happy that you guys want to help me :).
But I try this with taurus first, since I have to shut down the LiveCD to get the logs as is now.

---

### Post by taurus on 2006-11-27
From the LiveCD, open a terminal and type

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1  /mnt/ubuntu
sudo cp /etc/X11/xorg.conf  /mnt/ubuntu/etc/X11/xorg.conf
sudo umount  /mnt/ubuntu
```
Reboot and see if X is working again...

---

### Post by elsebasbe on 2006-11-27
> **taurus said:**
> From the LiveCD, open a terminal and type

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1  /mnt/ubuntu
sudo cp /etc/X11/xorg.conf  /mnt/ubuntu/etc/X11/xorg.conf
sudo umount  /mnt/ubuntu
```
Reboot and see if X is working again...

Wow, thanks a bunch!
It works like a charm, thank you very much!

The commands simply copyed the original xorg.conf over my old not working one, right?

---

### Post by taurus on 2006-11-27
> **elsebasbe said:**
> Wow, thanks a bunch!
It works like a charm, thank you very much!

Good job.  :mrgreen: 

> The commands simply copyed the original xorg.conf over my old not working one, right?

It copied the X config file from the LiveCD over to your harddrive, replacing the broken one on your computer...  ;) 

Now, enjoy Ubuntu.

---

### Post by elsebasbe on 2006-11-27
Hmm, first problem solved, however - now I can't login.
Is the password stored in the config file, and thereby its now changed?

---

### Post by taurus on 2006-11-27
It shouldn't change!  Are you sure you get the right password (check for cap lock)?  Otherwise, you can change your password by booting into recovery mode from GRUB menu.  Then at the prompt, type

```
passwd elsebasbe
(assuming elsebasbe is your login name...
```
Reboot and see if you can log in with the new password.

---

### Post by elsebasbe on 2006-11-27
Hehe :D
The thing that messed up the login was my keyboard, the characters doesn't match to the keyboard totaly :). But I guess I can fix that myself! *Edit: fixed :)*
Thanks again for all the help!

/Posting from the Ubuntu machine *happy again*

---

### Post by taurus on 2006-11-27
So everything is all good now!  ;)

---

### Post by elsebasbe on 2006-11-27
> **taurus said:**
> So everything is all good now!  ;)
Yup! Thanks a bunch!

---

### Post by nowadays who knows on 2006-11-28
Hello all .
 Just wanted you to know I had a problem adding a video card to my desktop and had a botched up](*,)  xserver config file and by following your post i got my machine back to original working condition. One of these days when I have time ill work on using the new card. 
 So thanks for posting your problem for others to follow :KS

---

