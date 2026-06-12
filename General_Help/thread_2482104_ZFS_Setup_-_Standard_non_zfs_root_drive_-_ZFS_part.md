---
title: "ZFS Setup - Standard non zfs root drive - ZFS partiion not responding - service lag"
date: 2022-12-19
forum: General Help
---

### Post by computer0freek on 2022-12-19
Hey Folks, 

I'm trying to solve a problem here and I've been trying to figure it out. But running in to road blocks. I posted this on the ZFS subreddit over on Reddit but I'm not getting anywhere. Not complaining, just looking to solve the issue. I thank what ever help anyone can provide or insight that I'm missing. I'm going to provide as much detail as I can in one post. This might get long. So thank you for baring with me. 

Hey Folks,
This is a long one sorry... But I feel that it is needed to have all the information. Or it could be me just spitting fire.
I  have an interesting one on my hands here. I have Ubuntu Mate installed,  22.04 LTS, and ZFS installed. I work IT for a living so I've been  messing with NFR licensing from Veeam. Learning the product and trying  out syncs. I installed Veeam's Linux Agent within Ubuntu, which is  running my ZFS, BigPool pool. Everything was fine... Until this morning.  I installed the agent, and mlocate and plocate, and continued using the  system. I did not reboot. It did however update the Ubuntu System to  require a key be entered in to bios - secure boot. It had me enter a  password and use it during the next reboot. Which did not happen for 2-3  weeks later. At this point, my pool is still alive and I can access it  from a live CD. But my base OS on the SSD just hangs when you open CAJA  and try to go to /BigPool.
When I  run zpool list - it states the pool is healthy. I just can't access it. I  already removed the Veeam Agent, mlocate, plocate by using apt remove  --purge NAME - while also running apt autoremove, apt autoclean and then  apt update, apt upgrade -y.
The  system runs fine within the gui, but I can't access the zfs pool. Also  shut downs get stuck at the screen saying - waiting for stop action  /BigPool/NAME1, /BigPool/Name2, etc. While the system is booting, it  takes forever to get past the boot screen. But it does load after 5 -10  mins.


I  rather not reinstall Ubuntu at this point as this is also my Plex Media  Server. It takes alot to rebuild this. Does anyone have any ideas to  help me fix this. I thank all thoughts and suggestions.

Kyle


**Top Services from the command  "systemd-analyze blame"**

35.418s zfs-import-cache.service
20.651s snapd.service
8.934s NetworkManager-wait-online.service
5.016s apt-daily.service
3.895s systemd-udev-settle.service
1.594s udisks2.service
1.271s xrdp.service
989ms zfs-mount.service

Installed Software by date: 
[https://photos.app.goo.gl/6ATzo5nGpjoDFg897](https://photos.app.goo.gl/6ATzo5nGpjoDFg897)


Scrub Started. But its been sitting here for almost 50 mins.
When perform a scrub at the terminal. It simply sits there with a blinking cursor.

Image 1: [https://photos.app.goo.gl/1ZUQa1xunaSH6FmH8](https://photos.app.goo.gl/1ZUQa1xunaSH6FmH8)
Image 2: [https://photos.app.goo.gl/qxuj9XTtRdbo8Kjz8](https://photos.app.goo.gl/qxuj9XTtRdbo8Kjz8)

I can't copy and paste images or include them here. No idea why. 



Now the system is slowly loosing services. The system appears to be slowly dying the longer it is running.

I have tested the system to confirm its not a hardware issue by doing the following: 

1) Grabbing a ISO and putting it on a flash drive. Importing the pool and setting up a temp Samba share. Moving data around for 30 mins. No issues with the Pool or the hardware as I can see. 
2) Tested Memory - Pushed a RAM test, took a couple of hours, but it passed. 


Thanks for your help everyone. Kyle

---

### Post by MAFoElffen on 2022-12-20
Please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") on it... But use "-d" as a startup option to the script.

The reason it takes a while to shutdown and startup is that Ubuntu uses zfs caches at /etc/zfs/zfscache/ for both bpool and rpool. It takes a while for it to shut down, especially if there is a problem going on... On the next boot, since you shutdown prematurely, if you were looking at  the system messages, while it is booting, it's probably having troubles while trying to read the zfs.cache's and I'm suprrized it didn't sump you out to a initramfs prompt, which sometimes happens when that cache is corrupted...

Yes, run that report, upload it to a pastebin... So me and others can look at it and get an idea of what is going on. Please post the URL of the pastebin, so we know where to look.

At the least, it's probably going to need to force import the problem pools, then export the pools to close down the filesystem gracefully... Maybe re-init the zfs.caches... We'll see.

Edit1: Scrub and or resliver processes will take forever. Forewarned. And i just noticed you said "NON" ZFS root drive, even easier.

---

### Post by computer0freek on 2022-12-20
> **MAFoElffen said:**
> Please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") on it... But use "-d" as a startup option to the script.

The reason it takes a while to shutdown and startup is that Ubuntu uses zfs caches at /etc/zfs/zfscache/ for both bpool and rpool. It takes a while for it to shut down, especially if there is a problem going on... On the next boot, since you shutdown prematurely, if you were looking at  the system messages, while it is booting, it's probably having troubles while trying to read the zfs.cache's and I'm suprrized it didn't sump you out to a initramfs prompt, which sometimes happens when that cache is corrupted...

Yes, run that report, upload it to a pastebin... So me and others can look at it and get an idea of what is going on. Please post the URL of the pastebin, so we know where to look.

At the least, it's probably going to need to force import the problem pools, then export the pools to close down the filesystem gracefully... Maybe re-init the zfs.caches... We'll see.

Edit1: Scrub and or resliver processes will take forever. Forewarned. And i just noticed you said "NON" ZFS root drive, even easier.

Good Morning and thank you for the reply. 

As you noticed, my root drive is not ZFS. Only BigPool which is mounted to /BigPool is zfs. I'm attempting to run the script that you requested, but I'm having issues. The system will boot and take forever to boot - I'm able to log in and even using SSH and RDP (XRDP) for a few mins. After the system sits for about 10 mins, services start to go offline and hang. This is the result of running the script request you sent: 

[https://photos.app.goo.gl/PKdvB33iuGDKgF7o8](https://photos.app.goo.gl/PKdvB33iuGDKgF7o8)

I've ran scrub's before on this big of pool but I keep getting stuck at the 0.00% mark. The Speed in which the scrub is going will just start to run down to 0.0Kb/s. It usually takes 24 hrs for this to happen. It got to 100GB, and then started to stall. Very weird behavior.

---

### Post by MAFoElffen on 2022-12-20
A few tips... please post output as text within code tags. Pictures are hard to scan and read. Text I can put into my program editor and process/analyse. Your result (picture) tells me nothing about what happened and why you didn't run it. 

2nd) It did not say to use 'sudo" to download the script in the instructions. What I do is create a Scripts directory, change to it, then download it. now that you have it, manuaver were the script resides and do
```

./system-info -d

```
The way I see you edit data, it generates an eye's only version for "you" to review... When it generates the report for download, all sensitive data is editted and masked from the report before upload. Please post the URL of where it gets uploaded, otherwise we do not know were to look. Based on the utilities you have, it may post it to 3 different pastebins.

How much data are we talking about. A few terabytes of data may take days to scrub. I know it's multiple disks. I guess I could look up the disks by their model numbers, but I have other things to do... Such as doing quality control on daily builds.

---

### Post by computer0freek on 2022-12-20
> **MAFoElffen said:**
> A few tips... please post output as text within code tags. Pictures are hard to scan and read. Text I can put into my program editor and process/analyse. Your result (picture) tells me nothing about what happened and why you didn't run it. 

2nd) It did not say to use 'sudo" to download the script in the instructions. What I do is create a Scripts directory, change to it, then download it. now that you have it, manuaver were the script resides and do
```

./system-info -d

```
The way I see you edit data, it generates an eye's only version for "you" to review... When it generates the report for download, all sensitive data is editted and masked from the report before upload. Please post the URL of where it gets uploaded, otherwise we do not know were to look. Based on the utilities you have, it may post it to 3 different pastebins.

How much data are we talking about. A few terabytes of data may take days to scrub. I know it's multiple disks. I guess I could look up the disks by their model numbers, but I have other things to do... Such as doing quality control on daily builds.

In total is about 30 TB's. I have run scrubs before by hand using zpool scrub BigPool and it has never brought the entire system down like this. This all started after installing the Veeam Back up Agent. Like I said above, I did remove it... But it didn't' fix the problem. 

I can't copy data in or out of the system after 10 mins. I cannot copy and paste every space and enter to show what it is doing completely. The system has become unstable. Simply logging in to the system from a locked state now takes 10 mins. The wget part of the code does not download, it is simply sitting at a blinking cursor. I cannot run ./system-info as I can't download it. I will attempt to put it on a flash drive and run it from there.

I'm almost to the point of backing up my configs for NFS, Samba, and wiping the drive... Then I will just import BigPool

---

### Post by computer0freek on 2022-12-20
> **computer0freek said:**
> In total is about 30 TB's. I have run scrubs before by hand using zpool scrub BigPool and it has never brought the entire system down like this. This all started after installing the Veeam Back up Agent. Like I said above, I did remove it... But it didn't' fix the problem. 

I can't copy data in or out of the system after 10 mins. I cannot copy and paste every space and enter to show what it is doing completely. The system has become unstable. Simply logging in to the system from a locked state now takes 10 mins. The wget part of the code does not download, it is simply sitting at a blinking cursor. I cannot run ./system-info as I can't download it. I will attempt to put it on a flash drive and run it from there.

I'm almost to the point of backing up my configs for NFS, Samba, and wiping the drive... Then I will just import BigPool

Inserting a flash drive does not help- it doesn't load. So what ever Veeam agent did, some how damaged the OS... I'm guessing

---

### Post by MAFoElffen on 2022-12-20
You can dl and run the syste-info script from a LiveCD USB, But... Yes, I get the idea that your system itself is compromised.

What you said sound like the plan to follow. Back off your configs, and shutdown the pool gracefully. Migrate, and import the pool to a new install.

That way you are sure that you have a healthy system. It doesn't sound like your pools are the problem. They are just there affected by what is going on with your system.

EDIT1:
If your system itself will not let you export it, I was thinking you could import it from a LiveCD... But then thought it's going to firs say to use the "-f" flag to import it, then you just export it and go from there... But since you are going to a fresh system, you can just do that preemptively, before adding it to your new system permanently with zfs mount...

---

