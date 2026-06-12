---
title: "Backup"
date: 2014-02-06
forum: General Help
---

### Post by mark103 on 2014-02-06
Hey everyone just looking for a bit of advice on backing up my data, i have installed Ubuntu server 12.04 in RAID 1 and have everything working thanks to this site as well :)
 
I'm using 2 3TB drives for my RAID 1, the question i have is i want to backup the RAID 1  with an external 3TB drive from my gaming pc as i was thinking what happens if make my backup locally and the whole system crashes i have my backup on a 
network drive. I'm just looking for advice on how to go about doing this 

I have looked on the forums and on google but doesn't clear everything up for me and a lot of people are saying to use Rsync as the backup tool
So this is why i am here is it a good idea to backup my server from my gaming pc with a 3TB drive installed there ? or do you recommend it locally ? and how would i go about installing hopefully somebody can help
me i would really appreciate that :) thanks

---

### Post by mastablasta on 2014-02-06
so you have it in RAID and now you want to backup that raid? to have backup of backup? then what about backup of backup of backup? :-)

i am a bit unclear as to what you actually want.

what part of server oyu want to backup? the system part? or the data? or both? if you have #TB on your raid1 and they are full (actually it will be a bit less and you want to backup that) then maybe the 3TB drive might not be big enough especially if you have something else already on it.

you can use rsync or some cloning tool like clonezila to create image.

---

### Post by mark103 on 2014-02-06
hows it going and thanks for replying to my thread :) i just wanted to backup my media movies pictures music to be honest I'm new to linux so this is all new to me sorry if i didnt explain it properly
but thats all i want to do is use a external drive to backup my media on the Raid drive thats all cheers

---

### Post by mark103 on 2014-02-09
anybody know cheers

---

### Post by prasys on 2014-02-09
Just to be clear , you want to backup your data files and not the OS , or do you wish to have 1:1 copy

1:1 copy which means in an event of your RAID fails or what-so-ever , you could completely restore the backup and the system along with the data would be functional

---

### Post by mark103 on 2014-02-09
ye id like to have a 1:1 copy and have this 3Tb on another pc doing it is it possible to do that thanks

---

### Post by prasys on 2014-02-09
> **mark103 said:**
> ye id like to have a 1:1 copy and have this 3Tb on another pc doing it is it possible to do that thanks

Yep entirely possible , you would need to use CloneZilla. You would have to download and run it on a cd.


You may connect your external HD via USB or even do it via Samba/Windows Sharing (a bit slower but it works)

[http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php)

---

### Post by mark103 on 2014-02-09
ok cool thanks so when i download this as an iso image and burn it to a dvd do i just put it into my server and run it ? and then i would have to mount the 3Tb drive from my pc. I do have samba installed 
alright but ill have to figure that out as well im new to linux never mounted a hdd before

---

### Post by prasys on 2014-02-09
Yes mark

Burn the iso , boot it up from CD/DVD and then either plug your external HD or make sure you have sharing enabled in your Windows PC. Follow the steps in CloneZilla , it guides you step-by-step and it would start backing up your entire HD :)

---

### Post by mark103 on 2014-02-09
cool ill give that a shot and try that out once i have that configured with clonezilla will it backup everyday from the external drive ? and thanks for all your help i really appreciate it

---

