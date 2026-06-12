---
title: "slow boot in feisty"
date: 2007-04-21
forum: General Help
---

### Post by louistan3 on 2007-04-21
hey guys... uhmm why is my bootup on feisty really slow...

my edgy setup used to take like 26 secs to boot.. but in feisty.. it takes almost 2 mins...

i just installed feisty clean today.. i dont know how to translate the bootchart very well.. so 

i would appreciate some help..

heres my bootchart...

thanks in advance...

---

### Post by pthanos on 2007-04-21
For me I think it is the fsck that increases the boot process. I had to look into this problem in edgy. It seems it was not fixed...

Fsck seems to be triggered in every boot.

---

### Post by chrisccoulson on 2007-04-21
I also have a problem with slow boot, although not as bad as this. My boot is definately slower than Dapper. I posted in the Feisty development forums just before it was locked [here]("http://ubuntuforums.org/showthread.php?t=413504")

There are 2 periods where my system just seems to sit and do nothing. One of these is when starting networking. I've eliminated this by commenting out every interface except for lo in my /etc/network/interfaces file so it looks like this:

```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

Your bootchart seems to show long periods of waiting when bringing up networking. It definately doesn't appear to be caused by fsck. What sort of network are you on? Is it statically configured, DHCP or wireless?

For me, there appears to be a second pause after starting hal, and I don't know whats causing this. In fact, on several instances now, usplash has timed out and switched to a console during the last part of the boot process. It's a little frustrating because except for this, Feisty is running a peach on my machine.

---

### Post by louistan3 on 2007-04-22
thanks for the replies..

my bootup also waits at "configuring network sumthn sumthn"

im on a wireless network with DHCP..  il try commenting out all of them and see if it improves..

hope someone in the forums can figure this out.. im totally stumped...

---

### Post by louistan3 on 2007-04-22
you were right chrisccoulson! thanks!!

come to think of it.. maybe NM-gnome might have been having conflicts with the normal ubuntu networking because both of them would be trying to configure the devices.. 

anyway thanks again guys! commenting out everything except lo fixed it! 

now i have a normal bootup speed

heres my new bootchart..

---

### Post by FuturePilot on 2007-04-22
Are you sure you installed the final version of Feisty? This happened during testing where it ended up taking forever on the Configuring Network Interfaces during boot up. You might want to make sure you're using the final version and not one of the testing versions.

---

### Post by chrisccoulson on 2007-04-22
Your bootup does look normal now which is good :) I've noticed you don't get the pause for 6 - 7 seconds after starting HAL like I do on my machine. I don't really know what is causing that 

In response to FuturePilot, mine wasn't a straightforward install because I'm using DMRAID. I actually debootstrapped and built a minimal Feisty system in a chroot from within Dapper a couple of weeks before final, just to see if I could boot Feisty using its DMRAID. Then I installed the rest of the system a couple of days before final.

```
chr1s@chris-desktop:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"

```

---

### Post by louistan3 on 2007-04-22
im almost sure that i installed final...

i downloaded it a day after it was released and did a clean install..

how do i make sure that im using final? whats the command to check for that?

---

### Post by Xummoner on 2007-04-27
Here's my bootchart image, 165 seconds to boot... Dunno what process might be the one causing this, hope someone can help me since I don't even understand what that chart means.

I'm also having a problem with something called DBUS, I can't rename/move/delete/edit/change properties to several files, but I think I should post that somewhere else.

Thanks in advance.

---

### Post by carlton on 2007-04-28
hi all i have the same problem where ubuntu boot up slow too. Hey do i go about getting to my bootup chart and where is it located.

---

### Post by Bashed on 2007-04-28
Same problem here, slow boot (2 minutes) on a 100% freshly installed Ubuntu 7.0.4 downloaded TODAY.  

**  Specs:**
  Sony Vaio Centrino / Core 2 Duo / 2GB Memory
  Intel PRO/Wireless 3945ABG Network Connection
  Intel PRO/100 VE Network Connection
[COLOR=Red]Belkin Pre-N Router[/COLOR]: firmware version 2.01.02

Also, (I'm a linux newbie) how would I check to see if I have the latest video/network drivers?

---

### Post by Bashed on 2007-04-30
Can someone explain the fix for this?

---

### Post by kelvin spratt on 2007-04-30
come on somebody please answer these people

---

### Post by chrisccoulson on 2007-04-30
Could you remove the 'quiet' option from your boot parameters to see where the boot process is stalling. Also try installing bootchart.

```
sudo apt-get install bootchart
```

---

### Post by jondecker76 on 2007-04-30
I was able to fix my slow boot -

I'm at work right now, but it is as simple as adding irqpoll in grubs menu.lst

When i get home in the morning I'll try to do a step-by-step

---

### Post by jondecker76 on 2007-04-30
Ok, this worked for me - hopefully it will help some of you other people out..


in /boot/grub/menu.lst I added irqpoll to the kernel line

so...
sudo gedit /boot/grub/menu.lst

then find your kernel entry... mine was...
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash

now just add irqpoll to the end of it:
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash irqpoll 

save it, and hopefully you will enjoy a nice fast bootup!

---

### Post by Bashed on 2007-04-30
I'd like to remind the kind people helping us out, that not all of us are linux gurus. I'm new to linux, so please keep that in mind. Basically put, I understand zero of what your telling me/us because you speak as if I'm automatically experienced with linux.

---

### Post by jondecker76 on 2007-04-30
Sorry - i'll try to break it down better

First, Open the terminal..  (Applications->Accessories)

next, in the terminal type:
```
sudo gedit /boot/grub/menu.lst
```

you will be prompted for your password.

At this point you will have a text editor open with grubs boot list. Now all you have to do is find the first line that starts with "kernel" - this is what tells grub which kernel to boot. On my installation, it looks like:
```
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash
```

now just add "irqpoll" to the end of it so it looks like this:
```
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash irqpoll 
```

Now all you have to do is hit save in the text editor and reboot.

---

### Post by Bashed on 2007-04-30
Thank you John. Appreciate the breakdown :)

I will try this out.

---

### Post by Bashed on 2007-04-30
Sorry John, that did not work unfortunately. Still took nearly 3 minutes to boot. It locks about 40% on the progress bar for about a minute before proceeding through.

---

### Post by jondecker76 on 2007-04-30
Sorry I can't help you more, hopefully someone else has the answers. I know it was frustrating when mine was booting that slow. Still, this might help others...

---

### Post by jondecker76 on 2007-04-30
Just did a little looking around..
The irqpoll thing i suggested is for people with slow boots because of certain cd/dvd drives.

It appears that there is a second slow boot bug relating to networking. Please see the following link and check out post# 16. This might fix your problem, it seems to have worked for a lot of people

[http://ubuntuforums.org/showthread.php?t=402452&page=2]("http://ubuntuforums.org/showthread.php?t=402452&page=2")

---

### Post by huffy318 on 2007-05-20
The slow boot on mine wasn't helped by the irqpoll or the network edit.  My bootchart (attached) shows the same problem as  Xummoner's:  scsi_eh_1 and modprobe both have long wait times.

What is the difference in shades of pink for those two?

It seemed like it might be a dvd problem, since in dmesg it usu happens near the ata section (see bottom).  I switched to a users kernel that  has 'USB selective suspend/resume and wakeup' disabled (since my scanner was having problems) and the boot lag moved a little.  Now it happens just after the usb lines,  It has occasionally moved around before, so i don't think this is significant.

Regarding modprob, here is what is in my /etc/modules:

lp
#fglrx
fuse

Hopefully this will help someone understand better the problem.

[   22.982224] ata1.00: limited to UDMA/33 due to 40-wire cable
[   23.002733] ata1.00: ata_hpa_resize 1: sectors = 39876480, hpa_sectors = 39876480
[   23.015009] ata1.00: configured for UDMA/33
[   23.027127] scsi1 : ata_piix
[   23.257830] usb 4-6: new high speed USB device using ehci_hcd and address 3
[   23.438530] usb 4-6: configuration #1 chosen from 1 choice
[   23.689223] usb 2-1: new low speed USB device using uhci_hcd and address 3
[   23.877614] usb 2-1: configuration #1 chosen from 1 choice
[   53.527627] ata2.00: ATAPI, max UDMA/66
[   53.539681] ata2.01: ATAPI, max MWDMA2
[   53.551697] ata2.00: limited to UDMA/33 due to 40-wire cable
[   53.727346] ata2.00: configured for UDMA/33

Thanks for any help,
Eric

---

### Post by huffy318 on 2007-05-21
**This post is related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/115915/](https://bugs.launchpad.net/ubuntu/+bug/115915/).

I submitted a bug report since there seems to be a cause for slow boots other than the drive and network issues.

---

### Post by rcoconnell on 2007-08-26
I had a similar problem (scsi_eh_2 instead of scsi_eh_1) and traced it to a "Dazzle" PCMCIA flash card reader.  Once I removed the reader, my boot time got about 35s shorter.

---

### Post by njknight on 2007-09-03
Just a quick note to say that adding "irqpoll" into my boot/grub/menu.1st caused the CD/DVD drive not to be mounted at all.

computer is as listed below..........just thought I'd mention it:)

---

### Post by R_U_Q_R_U on 2007-09-14
Thanks for the great advice in this thread. My old Dell D600 with Compiz Fusuion and Aironet wireless not boots MUCH faster. What used to happen is it hung looking for the wireless connection. Now the WAP login screen pops right up after the desktop loads. This forum is great
:popcorn:

---

### Post by mcduck on 2007-09-14
> **pthanos said:**
> For me I think it is the fsck that increases the boot process. I had to look into this problem in edgy. It seems it was not fixed...

Fsck seems to be triggered in every boot.
I can probably fix that for you (I bet you are dual booting with Windows and have some FAT or NTFS partitions on your disk?), but as it's a completely different issue you should make another thread for that..

---

