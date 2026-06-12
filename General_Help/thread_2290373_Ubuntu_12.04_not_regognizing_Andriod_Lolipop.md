---
title: "Ubuntu 12.04 not regognizing Andriod Lolipop"
date: 2015-08-11
forum: General Help
---

### Post by Bill Dubinski on 2015-08-11
Good Day, 
I am having a weird issue with my version of Ubuntu 12.04. 

It has been a couple of weeks, but I recently upgraded my smartphone from Gingerbread to Lolipop and from Samsung phone to an LG. (Latter should not make a difference).

But been using Ubuntu 12.04 for sometime even when I had my Samsung phone running Gingerbread. 
With my Samsung/Gingerbread phone, when I would want to access my SD card where all my music, videos and pictures are stored, alls I had to do was simply plug my phone into a USB cable to my PC. 

When I tried doing this same this same thing after getting a new phone (LG Stylo G), at best what would come up is a dialog box with nothing it under MTP or PTP. 
At first I blames LG and spoke w/ them also. They had blamed it on that phone is so new, patches are not available yet. That answer did not sit right with me because Andriod is Linux and Ubuntu is Linux as is Mint. 

Fastforward about two weeks (today), when I switched to my HDD running Linux Mint 17.2 Cinnamon, plugged my phone in and recognized my phone/SD card no problem. 
I also have Mint 17.2 Mate on that same HDD, booted up in that to double check and Mate did NOT recognize it either, just Mint Cinnamon did.
 
Then logged back into Ubuntu 12.04 and still not recognizing it, and neither is Mint Mate. 


Any advice on this is greatly appreciated. 

Bill

---

### Post by cogier2 on 2015-08-12
[FONT=arial]You could update to 14.04 that should be OK with Android or you could install the following that worked for me some years ago. Run the following in Terminal then try again.

[COLOR=#000000]sudo apt-get -y install mtp-tools mtpfs gmtp[/COLOR][/FONT]

---

### Post by efflandt on 2015-08-12
MTP should work automatically in Ubuntu 14.04, at least it does for my Samsung S3 with Android 4.3. You just may not be able to "open" files on the phone remotely, you may need to copy them to Linux first.

I never could get it to work properly in Ubuntu 12.04, regardless of trying all suggestions. So at that time I resorted to putting ConnectBot (ssh client), AndFTP (sftp) and SSHServer apps on my phone, so I could sftp files to/from my phone over WiFi from my phone or Linux. I used my Linux openssh keys (with pass phrase) on Android and Ubuntu (not passwords).

---

### Post by Bill Dubinski on 2015-08-16
Good Day cogier2 and thanks for reply. 
I already have mtpft tools installed. Had it when I was running Gingerbread but I rendered an update command in the terminal and it happened to have been already the latest version.

I am not ready to "upgrade" to 14.04 and I do not think I ever will. 
I am testing Mint again as I have not used Mint since mint 8 and Ubuntu is getting too commercial for me. 
Stated disliking Ubuntu with 12.04 and Unity.
But I am a LTS guy, I have so many things to do if I "upgraded" for my business that I only do it when EOL comes. 

But this issue is very strange because it doe not work under Ubuntu 12.04, it does not work under Mint 17.2 Mate but it DOES work under Mint Cinnamon which I have all three installed on my HDD. 

So now all I have to do (which is a pain a little) but restart the computer under my other HDD running the Mint family, choose Cinnamon in the grub screen and there I am able to access my SD card. 

Very strange.......

---

### Post by Bill Dubinski on 2015-08-16
Good Day efflandt and thanks for replying. 
Can you give me more info about this ConnectBot and does that option only work under wireless? I have a wired LAN

---

### Post by cogier2 on 2015-08-26
Hi Bill, 

All I can add is that by using Mint 17.2 Cinnamon, my favoured distro, it should work as it is based on Ubuntu 14.04, but why it doesn't work on with Mate is a mistery.

---

