---
title: "First time Ubuntu user"
date: 2008-04-11
forum: General Help
---

### Post by johnnyxxxcakes on 2008-04-11
Just recently, I went on a job shadow visit to a company called Summit Digital Networking. The day was fun and great, and me and the guy I shadowed had a wonderful time. But while we ate lunch, we got on the subject of Linux. I knew what Linux was and that there were different distributions or "flavors" and he mentioned a very easy and popular one to me called Ubuntu. He told me I could install the Ubunutu operating system from within Windows Vista and run it basically like an emulator and ROM image.

Later that night, I went home and Googled Ubuntu and found out that they have the new version (8.04, I believe) coming out soon. I decided to wait those two weeks for the new program to come out, because I wouldn't want to download version 7.10 and have the new one arrive two weeks later.

So, here is my problem. I'm wondering if Ubuntu will run okay on my laptop, and how I would go about setting it up, so I won't mess up my current installation of Windows Vista. It's an Acer Extensa 4620 series with the following specs:

-Windows Vista Home Premium
-2 GB DDR2 RAM
-160GB Hard drive
-Intel Pentium Core Duo processor running @ 1.46GHz
-Mobile Intel® GL960 Express chipset video card

Here's the laptop from it's parent website: [Acer Extensa 4620](http://us.acer.com/public/page4.do?link=oln56.redirect&dau22.oid=36061&UserCtxParam=0&GroupCtxParam=0&dctx1=25&CountryISOCtxParam=US&LanguageISOCtxParam=en&ctx3=-1&ctx4=United+States&crc=1730318441#inu57_50457)

---

### Post by Het Irv on 2008-04-11
When you pop in the LiveCD you can change you partition tables using Gparted (or partition editor as it is called on the CD).  Just make sure that you Defrag Vista a few times so that you do not lose any data.
Or you could just run from the Live CD if you do not want to change your computer, but it will be slower.

---

### Post by sancho panza on 2008-04-11
Try running the 8.04 beta LiveCD which is already out there. That should give you a fair idea as to whether the actual install would work or not. The LiveCD runs just like a full install, without actually changing anything on your hard drive.

---

### Post by GoodPanos on 2008-04-11
Ubuntu is going to rock 'n' roll on your laptop. :guitar:

Your wireless card will work right off the box as pretty much everything else will, maybe not your modem.  You might find out Ubuntu is the way to go and scrap Windows; I know I did.

As far as installing it just follow Het Irv suggestion.

Enjoy!

---

### Post by johnnyxxxcakes on 2008-04-12
> **Het Irv said:**
> When you pop in the LiveCD you can change you partition tables using Gparted (or partition editor as it is called on the CD).  Just make sure that you Defrag Vista a few times so that you do not lose any data.
Or you could just run from the Live CD if you do not want to change your computer, but it will be slower.

See, that's where I get scared. I have no idea how to partition things and I'm afraid of messing something up when something is already running fine the way it is.

But I guess I could go ahead and download the beta of Ubuntu 8.04 and see how it would run on my computer.

What's this you talk about it running slower if I just run it from the LiveCD? Is the LiveCD the 700MB program you can download from right off their site?

---

### Post by sumguy231 on 2008-04-12
The LiveCD is called the Desktop CD on the website, and also allows you to install from the LiveCD. And yes, due to the nature of the medium, the LiveCD will run slower because that's just how CDs roll. As an added bonus, if you start the Ubuntu 8.04 CD it will offer to install Ubuntu inside of Windows like a standard Windows application so you can try it out, no partitioning needed.

Your laptop is up to par on specs, though the graphics card may or may not support the 3d effects. The only part you might have trouble with is the wireless card, but everything else is probably going to work fine. You can use the LiveCD to find out how well your hardware works with it.

---

### Post by Tyke91 on 2008-04-12
basically, the live cd will boot the entire operating system from the cd, no hard drive. since the cd is a slower medium than the hard drive, it will lead to an overall slower result. AND you will not be able to save settings if you quit.

partitioning is actually quite simple... just make sure to back up ALL your important data before you partition, just in case.

---

### Post by iaculallad on 2008-04-12
Just an advise, before venturing/installing Ubuntu (8.04) in your laptop, just be sure to backup all your important data from your vista drive. gParted could be a little tricky sometime. I had lost data from using it on my first hand with this application, but surely, you'll  love using Ubuntu.

---

### Post by johnnyxxxcakes on 2008-04-12
> **iaculallad said:**
> Just an advise, before venturing/installing Ubuntu (8.04) in your laptop, just be sure to backup all your important data from your vista drive. gParted could be a little tricky sometime. I had lost data from using it on my first hand with this application, but surely, you'll  love using Ubuntu.

How would I go about backing up all of my current Windows data on my computer?

---

### Post by Tyke91 on 2008-04-12
take all the important files that you need, documents, music, pics, etc... and put them all on a flash drive or a dvd... something that you can pull them back from in case your current system gets fried... but there's a 95% chance that, if you've done your research, you will do it flawlessly. If you have an IRC client you can even have somebody talk you through it while you do it

---

### Post by HunterThomson on 2008-04-12
Your, laptop should run grate on ubuntu 8.04. I have the intel x3100 GPU and yes there are some work around to use the desk top effects. But they are simple. Check out the lenovo ideapad thread for details. Yes run the live cd first to make sure it will work but don't think that's how the os runs. It will be way way slower and just not the gig but it will show you if everything will work i.e. WiFi card and stuff like that. If you have the intel wierless card it will work out of box. 

As far as partitioning. I would just wipe your hard dive of the Windo$ virus and jump into Linux. Then click on the custom partitioning at the first partitioning screen you come to setup 

one primary partition of 150Mb format ext2 and label it   /boot
One Primary Swap partition of 4GB format swap and no need to label it knows what it is
One Logical partition of 20GB format ext3 and label it just     /     this is the root partition

Put all of these at the beginning of the free space by checking that box but the next one check the box to put it at the end of the free space

One Primary Partition of 60GB format it ext3 and label it     /home   This the where all your vidios and muzak will be stored.

With this set up you can reinstall the OS or install a new one latter a lot ez'er because all you will have to do is reformat the  /boot partition the" / " root partition and then leave the home partition alone so you don't loose all your pic's/vid's/MP3's. You will also have a zone of free space in the middle so you can expand your root partition or your home partition as needed or install a new OS in there. You also don't really have a 160GB hard drive the Windo$ virus as stolen a good 15 or 20GB of it for Recovery partition and is hidden form the OS.

---

### Post by johnnyxxxcakes on 2008-04-12
> **Tyke91 said:**
> take all the important files that you need, documents, music, pics, etc... and put them all on a flash drive or a dvd... something that you can pull them back from in case your current system gets fried... but there's a 95% chance that, if you've done your research, you will do it flawlessly. If you have an IRC client you can even have somebody talk you through it while you do it

Okay sweet, thank you guys. I'm probably going to try and download Ubuntu 8.04 beta from my friend's computer because he has very, very fast high speed internet, then I'll just burn it to a CD and report back to you guys if I have any problems. :)

---

### Post by harrybazeegar on 2008-04-12
The simplest way is:
1.  empty out a partition (about 20-30GB in size) - that is to say copy all data from that partition into a different partition
2. delete that partition so that it becomes 'free space' on your hard drive
3. insert the live CD into the CDROM and reboot the computer
4. boot into ubuntu from the LiveCD
5. select the 'Install' option from the desktop
6. when you are asked to select the partitions you want to use for ubuntu, select "largest continuous free space". This way you will be using the partition that you just emptied out and deleted.
7. go on with the installation - let it complete. This will automatically give you a dual boot.
8. reboot after it completes.
9. Voila! You have a computer with Ubuntu and Vista (or any number of other OSes) all together!!

Cheers
Happy Ubuntu-ing :)

PS: this way you can avoid all the partitioning details. BUT BE SURE TO :
1. have an empty AND deleted partition ( that means FREE SPACE ) on your HDD
2. select the "largest continuous free space". If you leave this option to default, ALL YOUR DATA WILL BE ERASED!!! AND THAT IS BAAAAAAAAAAAAAAAAAD!!!!!!!!!!

---

### Post by johnnyxxxcakes on 2008-04-13
Well I installed the beta and I now have Ubuntu and Windows Vista next to each other. I guess they're partitioned because when I start up my computer, I have the option to boot in either Windows Vista or Ubuntu.

My current problem is:
I don't know how to get the network working. Like how can I connect to the internet with Ubuntu? I know one of you told me I may have a problem with my current network adapter, but I hope there's a way to get it up and working.

Thanks :)

---

### Post by HunterThomson on 2008-04-14
What wireless card do you have??

---

### Post by GCoffee on 2008-04-14
Does your wireless use WPA encryption or WEP? It shouldn't make a difference whichever but try switching the encryption. Or turning it off. Although that's not recommended.

---

### Post by HunterThomson on 2008-04-14
turn off the encryption it is worthless any way. Just don't broadcast the SSID. Anybody that knows how to find your SSID can also brake you WPA or WEP.

---

### Post by johnnyxxxcakes on 2008-04-14
> **HunterThomson said:**
> What wireless card do you have??

I have a Broadcom 802.11/g Gigabit Ethernet network adapter I believe.

---

### Post by Het Irv on 2008-04-14
System->Administration->Hardware Drivers
Is anything listed here? If so can you connect your computer in some other way? It only has to be temporarily to download the drivers.

---

### Post by johnnyxxxcakes on 2008-04-14
> **Het Irv said:**
> System->Administration->Hardware Drivers
Is anything listed here? If so can you connect your computer in some other way? It only has to be temporarily to download the drivers.

I can hook up the network cable from one of the computers in the basement and access the Internet that way.

I've been looking in to [this]("http://ubuntuforums.org/showthread.php?t=25683") HOWTO, and can't seem to get anything to work.

---

### Post by HunterThomson on 2008-04-15
You know..... Don't take my word for it but I "think" I remember reading a post that said ndswraper didn't work in Hardy or there were some problems..... maybe look into it or wait until someone with more experience can help you. I have never used ndswraper. Also,  there seems to be a live chat set up to get help from people if you don't want to wait.

---

### Post by johnnyxxxcakes on 2008-04-15
> **HunterThomson said:**
> You know..... Don't take my word for it but I "think" I remember reading a post that said ndswraper didn't work in Hardy or there were some problems..... maybe look into it or wait until someone with more experience can help you. I have never used ndswraper. Also,  there seems to be a live chat set up to get help from people if you don't want to wait.

Okay thanks, I could try that out. Do you have the name of this chatroom and what channel it's in? But if ndiswrapper doesn't work, am I screwed with trying to connect to the Internet wirelessly?

---

### Post by Het Irv on 2008-04-15
Did you check the restricted drivers, or Hardware Drivers as it is called?  I am almost positive that broadcom is supported there.  

I have heard that the absoulte begginers room in IRC is pretty active, but don't remember the actual channel name.

---

### Post by HunterThomson on 2008-04-17
NO, You can still connect wireless. try and check system/administration/hardware drivers and see if the driver you installed is there and what you can do with it. If it becomes a problem that you are following all the instructions and it is still not working try Ubuntu 7.10. You should not have any problem installing the drivers with 7.10.

---

### Post by HunterThomson on 2008-04-19
Ya, check out system/administration/hardware drivers and see if you broadcom driver was installed and see what you can do with it. Again I have no restricted drivers and have not use ndswraper so I have limited knowledge on the subject but will do what I can. If you followed all the instructions to install the drivers and still no luck then install ubuntu 7.10 and try that.

---

