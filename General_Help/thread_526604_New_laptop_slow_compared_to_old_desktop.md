---
title: "New laptop slow compared to old desktop"
date: 2007-08-15
forum: General Help
---

### Post by ACGarib on 2007-08-15
Hi, about a month ago, I got a new laptop (Dell vostro core 2 duo T7300 with 2 GB of ram, 120 GB 5400 rpm HDD, and a NVIDIA 8400 GS). I installed ubuntu feisty so now I have a dual boot laptop. (vista and ubuntu). The first thing I noticed was how slow vista was on my laptop compared to XP on my old computer. (my old computer is a 3 GHz P4, 1 GB ram, windows on 80 GB 7200 rpm HDD, ubuntu on 160 GB 7200 rpm HDD, ATI Radeon 9800 pro) I just figured that vista is naturally slower than XP. (By the way, Vista eats up almost 1 GB of my ram with only firefox open!)

I also noticed that feisty on my laptop is slow compared to feisty on my desktop. Everything just seems a little more sluggish. Programs take longer to open, Compiz-fusion is a lot slower (especially with animation. Indirect rendering helps, but then I can't logout without the laptop freezing), and in particular, Firefox/Swiftfox/Swiftweasel/Opera is slow and not very responsive.

My web browsers take a few seconds to pop up (longer than in my old desktop, which is only 1 second or so), then take 20 or more seconds to re-load the webpages I had open in the last session. (my old desktop is a little faster to reload my previous session). While the webpages are loading up from my last session, the whole computer bogs down, even though my CPU usage is around 40-50%. Also, I noticed that the CPU's frequency gets scaled down to 1.6 GHz from 2 GHz when my web browsers are doing any web page loading. 

Selecting a different tab in my web browser on my laptop takes 2 seconds to bring up that page and another second for the titlebar to reflect the change in the web page's name. On my old computer, this happens almost instantaneously. 

It seems like my processor's speed gets scaled back whenever there is CPU or GPU usage over 40-50% from any other program also (not just swiftfox). 

Mplayer is just barely able to play 1080p H.264 video, and the audio in rythmbox stutters whenever I do anything processor intensive (such as launching Opera).

Compiz-fusion shows a framrate of 10 fps when I am using the 3D cube w/ transparent windows, but on my old desktop, it is around 40 fps.

Using metacity doesn't speed anything up.




So, I guess I just feel like my brand new laptop should feel faster than it is. I don't think my 3 year old desktop should feel more responsive than a 1 month old laptop.

Anybody have any suggestions?

**What about the CPU scaling down during heavy usage problem I'm having? Could that be the cause of the slowness?**





P.S. You know that splash screen that pops up during login? how do I get rid of that? It doesn't show up on my old computer because I went to system, preferences, then gnome splash screen preferences and disabled it, but on my laptop, that isn't there.

EDIT: nevermind the first P.S., but do read the second P.P.S. ...or is it P.S.S I just installed gnome-splashscreen-manager and unchecked "show spash screen".

P.P.S You know how when you open a program that requires administrative privileges, a box opens that asks for the password and the rest of the screen darkens? How do I get my laptop to stop doing the whole darkening thing? (it is very juttery and full of tearing) My old desktop doesn't do this.

---

### Post by gobbles414 on 2007-08-15
Hi ACGarib,

I'm not sure if I can help you with your P.P.S. issue. Nor can I explain your processor slowdown (this may be a power saving feature of your particular processor). However, I may be able to explain the slowness of your system in general:

(1) The RAM might be the source of your problems. First, there are different speeds of RAM available. If your RAM is one of the slower types, that might cause a general sluggishness in both Vista and Ubuntu. Also, computers today work best if the RAM is installed in pairs. That is, two 1 GB sticks of RAM will run faster than one 2 GB stick of RAM. EDIT: In addition, if there are two sticks of RAM but they are of different speeds, the system will use the slower of the two speeds.

(2) How did you install your dual-boot? If you installed Ubuntu along side an existing Vista image, then that could cause slowing. This is because Vista is AWFUL when it comes to keeping a disk defragmented. On my system, which is also a dual-boot Ubuntu/Vista, installing one game in Vista can cause massive fragmentation. Luckily, I was able to install Vista after Ubuntu, so the fragmentation of the Vista partition does not hurt my Ubuntu experience.

(3) You mention that the speed of your laptop's hard drive is 5400 RPM. I can tell you that the speed difference between a 7200 RPM drive and a 5400 RPM drive is substantial. If the drive in your desktop is 7200 RPM, then it might indeed seem to be faster than your new laptop.

(4) Some Linux programs are just slow. For example, I use Banshee as my music player in Ubuntu. I have over 3000 songs in my music library. Probably due to the fact that my collection is a mix of FLAC, Apple Lossless, and MP3s, Banshee really slows down when I type anything in the search field.

I hope that this has been helpful. Please let me know.

---

### Post by ACGarib on 2007-08-16
Thanks for the reply. 

1) My RAM is DDR 2 at 677 MHz. This is the fastest RAM available for my laptop. For some reason, the Santa Rosa platform only supports 677 MHz RAM even though the FSB is at 800 MHz. They are a matched pair of 1 GB sticks, but I don't know if they are running in dual channel or whatever it is called. How do I find out?

2) I got my laptop with vista already installed. I started installing programs that I like to use, then I defragmented the hard drive, freed up 10 GB of space for Ubuntu with the Gparted CD, then I installed Feisty. I don't know If I should have installed Ubuntu first, then installed my windows programs. How does the fragmentation of the Vista partition hurt Ubuntu's performance? Are random NTFS files scattered around the HDD and the EXT3 partition is built in chunks around the fragmented files?

3) That is one thing I wish I could have upgraded to, but the option was not available. I guess in the future I may buy a 7200 rpm HDD for my laptop, but for now, I'm using my 5400 rpm one.

I just wish I knew why my processor slows down at exactly the wrong time. It's set to performance mode in cpufreqd.conf in /etc when it's plugged in, so I don't know why it would slow down. I see a part for overheating, but I don't know how to check the temperature of my CPU.

Thanks for your help gobbles414,

Andrew

---

### Post by tgalati4 on 2007-08-16
sudo apt-get install lm-sensors

Do a search in the forums for how to set it up.

You could have a deficient heat sink.  Either not enough or too much heat paste, or the heat sink is not properly seated.  As the CPU die heats up, the thermal protect circuitry will throttle it back to keep it working.  This is better than the previous HALT due to overload, but it makes troubleshooting more difficult.

If your computer locked up everytime you tried to do something, you would toss it out the window.  Now it only slows down.

Let us know how well Dell deals with this issue.

---

### Post by ACGarib on 2007-08-16
Well, I couldn't get lm-sensors to install without freezing my computer, so I installed sensors-applet instead. (sensors-applet was also about 1000 times easier to install) It is saying that my CPU is at 45 degrees C right now (the fan is currently off), and when I select a new tab, then a new one, and a new one, etc, the temperature goes up to about 60 degrees C. (60 is the highest the applet goes to)

One question though, what should I set the sensor value multiplier to and the sensor value offset to? I saw a website [ http://www.laisseznousvivre.com/ubuntu_on_delld420.htm ]( http://www.laisseznousvivre.com/ubuntu_on_delld420.htm ) that said to set the multiplier to .75, but I have a different laptop and a different processor. Right now, I have the multiplier set to 1.

EDIT: Also, I noticed that if I load a new web page, my CPU temp instantly shoots up instead of creeping up. Is that normal? One last thing, how do I view the temps that the bios is reporting? I saw that people are comparing the bios's temps to the applet's temps and ajusting the applet's offset and multiplier accordingly. Do I just have to reboot and go into the bios or is there a way to see them in an OS so I can directly compare them?

---

### Post by gobbles414 on 2007-08-16
ACGarib

Are you running Ubuntu Feisty? 32-bit or 64-bit...? Vista 32-bit or 64-bit...?

Regarding number two in my list (how Vista could effect the Ubuntu install), it sounds like you followed the correct procedure for claiming hard drive space from Vista. I probably would have also done an error check of the disk in Vista with both boxes checked. The tool I'm talking about is directly above the defragment button. But that probably would not have done anything on a new computer.

The reason that installing Ubuntu after Vista is a bad idea: It is critical to remember that the hard drive is an actual physical device. As such, if data are stored in many different places on the drive, that can SIGNIFICANTLY increase read/write times. As I said previously, I don't trust the defragmentation tool in Vista at all. According to Wikipedia, Microsoft plans to "improve the performance" of defragmentation in Vista with Service Pack 1. Also according to Wikipedia, "Chunks of data over 64MB in size are not defragmented [in Vista]" So, let's assume that your disk was fragmented when you installed Ubuntu -- even after you ran the defragmentation utility. This means that when you partitioned your hard drive for Ubuntu, the files used by Vista were physically scattered all over your hard drive. So your Windows partition could be physically located on 100 different parts of your hard drive. Consequently, Ubuntu probably is as well. 

Did Dell provide you with a re-installation disk? I know that many companies use hidden restore partitions and factory restore disks (yuck). Here is what you might try:

* Backup your data (obvious)
* Make sure that you have the latest version of your computer's bios installed; and reset it to factory specifications.
* Use the gwscan utility to completely overwrite your hard drive with zeros. The gwscan utility is a free download from Gateway Computers. I believe that the latest version is 5.11. I haven't provided a link just in case there is a newer version. 
* Install Ubuntu and swap partition according to your needs. Make sure to leave a minimum of 40 GB free for Vista.
* Install Vista to free space. I know for a fact that this is possible with a copy of Vista purchased at a retail store. I don't know about any copy Dell included with your computer.

If your computer is still running sluggishly, it might be worth calling Dell to see if installing a 7200 RPM hard drive will void your warranty. If it will not, I recommend that you replace your hard drive with a faster one. If your computer is still running poorly, I would ask Dell to repair/replace your laptop.

---

### Post by ACGarib on 2007-08-16
Both Linux and Windows are 32 bit.

Sadly, My laptop did not come with a Vista CD. I guess I could ask for one, but they might make me buy it.

My computer did come with a recovery partition, but I have no idea how to access it. It also came with a media direct partition (stripped down version of XP that allows me to play media w/out booting up), but that doesn't work. 

Is there a program that shows physically where the partitions are located on my HDD?

I don't know if it matters, but I used Diskeeper to do the defragmenting because it is faster.

I don't think I want to wipe everything and install Ubuntu and Vista and set everything up all over again. Is there a way to re-do the partitions so they are in one continuous chunk in the HDD w/out wiping it first?

---

### Post by gobbles414 on 2007-08-16
Hello once more ACGarib,

According to Wikipedia, "The defragmenter program included with the Windows 2000, XP, and 2003 operating systems is based on the full retail (Home) version of the Diskeeper program." I have absolutely no idea if that means that your disk was defragmented correctly or not.

Dell may send you a Vista DVD -- Dell was really good about sending some XP disks to me when I used to be in charge of a school computer lab. However, it would not surprise me to learn that Microsoft has disallowed Dell from providing home users with OS disks. I know that HP will no longer provide an OS disk to a paying customer! Also, I think that Microsoft offers a program where you can purchase replacement disks for an existing license. That service costs something like 29.95 USD, I think.

The best bet for seeing a representation of the physical status of your hard drive is probably some sort of data recovery program. Or, maybe computer forensics software can help. As far as I know, "re-doing" a partition means deleting all data on that partition. Even if you did this, the physical condition of your hard drive would remain the same.

Your best bet, IMHO, is to erase your hard drive with zeros (that may or may not erase the Vista recovery partition). Then install 64-bit Feisty and test it. If you are satisfied, then you are only left with the problem of getting Vista installed again.

---

### Post by ACGarib on 2007-08-16
I just finished talking with Dell, and they said they will ship me a Vista business CD for free. (I will keep an eye on that so see if it really is free.) I asked for an OEM CD, does that mean that it will install on a wiped HDD?

How is Feisty 64 bit? Are there any driver or program problems with it? I know there are still problems with the 64 bit version of Vista, so I don't know if Feisty is just as bad.

If I do wipe my hard drive, how would I get it to dual boot? I heard that you have to install vista first, but you are saying to install Ubuntu first.

---

### Post by gobbles414 on 2007-08-16
ACGarib,

You may be correct about installing Vista first. It seems that installing Vista will erase any bootloader created by Ubuntu. Thus, installing Vista first is the quickest fix. The problem and a solution that allows you to install Ubuntu first is described with step-by-step instructions [here]("http://apcmag.com/5045/how_to_dual_boot_vista_with_linux"). Now that I look at the sizes of my own computer's partitions, I think that I may have actually installed Windows first.

**But the critical difference between your computer and mine is that I partitioned the hard drive BEFORE installing Vista or Ubuntu.** This is where the flexability of having an actual Vista DVD instead of a system restore utility comes into play. The Vista installation disk will allow you to partition your hard drive prior to installing anything. Most of the system restore utilities I've seen will just reformat your entire hard drive.

Regarding 64-bit: Using 32-bit Feisty and 32-bit Vista myself, I can only tell you what I have read and heard about 64-bit systems. There is not a correct answer here as far as I am concerned. A 64-bit OS will fully utilize the power of your laptop. Some also argue that 64-bit Vista is best for gaming due to its support for extra processor and RAM resources. I can tell you that gaming on 32-bit Vista has been an AWFUL experience for me. I will probably never install 32-bit Windows again. However, many important drivers/apps have not yet been compiled to run on 64-bit systems. Adobe Flash is an example that comes to mind for both Vista and Ubuntu. So the 64-bit experience in Vista probably won't be the greatest either -- at least for awhile. Dell my only provide you with the 32-bit version, or only with the 64-bit version, or with both. If you want a different bit-version, you may be able to order it from Microsoft for a fee. This is where Mac users have it good... 32-bit and 64-bit are on the same installation media. It would be interesting to see what happens to your system speed in 64-bit Feisty. In short, it depends upon your priorities.

---

### Post by ACGarib on 2007-08-16
I went to reboot my laptop for the first time today, and now it can't start X. 

It says that nvidia failed to initialize the nvidia kernel module. please ensure that there is a supported nvidia gpu in this system, and that the nvidia device files have been created properly. Please consult the Nvidia readme for details. Screens found, but none have a usable configuration. Fatal server error: no screens found.

HELP! what should I do?

---

### Post by ACGarib on 2007-08-16
Nevermind, I just had to reinstall the nvidia drivers from source and now I got x working again.

I don't think I will re install Vista and ubuntu now. Maybe I will when I get a faster 7200 rpm perpendicular recording hard drive (possibly with that built in memory for vista) in the future.

I went into my cpufreqd.conf file in /etc and changed the throttle back threshold to 60 degrees so now I don't get the 1.6 GHz throttleback that I used to get nearly as often.


Thanks for all of your help, 
Andrew

---

### Post by tgalati4 on 2007-08-17
To get the BIOS temperatures and voltages you need to do the following:

>sudo apt-get install lm-sensors
>sudo modprobe i2c-dev (This step may not be needed on some systems)
>sudo sensors-detect (answer yes to most questions)
>sudo sensorsd -s (to set the correct multipliers--you can change later)
>sensors

Now you can add several temperature applets on your top panel.

The sensor-applet only reports the temperature that is reported from ACPI.  Who knows where that temperature comes from?

---

### Post by ACGarib on 2007-08-17
I booted into Vista and downloaded CPU temp and it is reporting similar temps for my CPU. 

Well, after only waiting for less than 20 hours, I received my CDs (Vista 32 bit business, audigy advanced MB (?), Dell hardware drivers, roxio creator, cyberlink PowerDVD, and Dell MediaDirect) That was totally unexpected. I thought I would get them in a week or so, not less than a day!

Anyway, I did try to install lm-sensors, but doing sensors-detect takes about 1.5 hours and is constantly freezing my laptop. In the end it tells me to add some modules to /etc/modules then it asks if I want it to do it for me. I say yes, but then when I go to /etc/modules, they are not there. I add the stuff in #cut here to /etc/modules and comment out one of them because it says I can't support it. (I cant remember what, something about smartbattery) I am currently on windows to monitor the temps so I can't do some stuff right now.

I will boot into ubuntu and try the sensors-detect again and hopefully this time it won't break my NVIDIA driver.

Also, at the end of sensors-detect, it gives me a list of 3 modules to add to /etc/modules. Should I add them from the bottom of that list up or top to bottom? (the list has some commented out lines saying that smartbattery is not supported on my computer and I should comment it out)

---

### Post by ACGarib on 2007-08-17
When I do sensors-detect I get the following at the end: ```
#----cut here----
# I2C adapter drivers
i2c-i801
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
# Chip drivers
eeprom
# no driver for Smart Battery Charger yet
# Warning: the required module smartbatt is not currently installed
# on your system. For status of 2.6 kernel ports check
# http://www.lm-sensors.org/wiki/Devices. If driver is built
# into the kernel, or unavailable, comment out the following line.
smartbatt
#----cut here----
```

It then asks if I would like to automatically add this to /etc/modules, and I say yes, but when I check, etc/modules has not changed. I then do sudo modprobe eeprom then sudo modprobe i2c-i801 to add the modules. After that, I do sudo sensors -s, but I get the following:```
 ~$ sudo sensors -s
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

What should I do? I don't want to do sensors-detect again because it takes forever, it uses 100% of my cpu the whole time, and last time, it broke my graphics card driver.

I tried to look at the temps in my BIOS, but there are none. Does that mean that lm-sensors won't find anything?

---

### Post by gobbles414 on 2007-08-17
ACGarib,

I'm glad to learn that Dell was so great! I've had a mixture of good and bad experiences with Dell in the past. But especially now that it is officially supporting Ubuntu, I may very well purchase my next computer from Dell. I tried to order an OS disk from HP on behalf of a friend of mine about 6 months ago. Let's just say that experience was less than pleasant (HP will not be getting any of my business anytime soon).

Congratulations on solving your processor's throttling problem. If I can think of a way to help you with your temperature sensing problems, I'll let you know.

---

### Post by ACGarib on 2007-08-17
So do you guys think that wiping my hard drive and starting over from scratch will make ubuntu feel  significantly faster, or will it only make it a tad bit faster? I don't want to go through the trouble of wiping my HDD, partitioning it, figuring out how to set up media direct, setting up Vista then setting up Ubuntu if the performance improvement is barely noticable.

Also, does anybody know how to set up a triple boot media direct + Vista + Ubuntu system? When I installed Ubuntu, it broke my media direct. The media direct CD says to install it first, then vista. Do you think that I could install ubuntu and still have media direct, or will that not work?

And finally just to make sure I am fully understanding what will give me the best performance (without getting a perpendicular recording 3 Gbps 7200 rpm HDD), Should I wipe the HDD, then install media direct, then install Vista, making sure to only use a certain amount of space by using the partioner. (how much space should I give to vista?) 

About the partitioner, how powerful is it? can I make a windows partition, a blank partition for ubuntu, and a storage partition with the leftover HDD space, or do I have to use Gparted to do that?

After installing Vista should I then install Ubuntu on the blank partition (how big should this blank partition be?)



If any of the procedure I wrote is wrong or not as good as it could be, please tell me.


I might not even do this. I might just wait until my laptop feels too slow and upgrade to a new hard drive (which should have that built in flash memory by then) and redo everything then.

It all depends on the benefits of wiping the HDD are starting over.

---

### Post by stchman on 2007-08-17
> **ACGarib said:**
> Hi, about a month ago, I got a new laptop (Dell vostro core 2 duo T7300 with 2 GB of ram, 120 GB 5400 rpm HDD, and a NVIDIA 8400 GS). I installed ubuntu feisty so now I have a dual boot laptop. (vista and ubuntu). The first thing I noticed was how slow vista was on my laptop compared to XP on my old computer. (my old computer is a 3 GHz P4, 1 GB ram, windows on 80 GB 7200 rpm HDD, ubuntu on 160 GB 7200 rpm HDD, ATI Radeon 9800 pro) I just figured that vista is naturally slower than XP. (By the way, Vista eats up almost 1 GB of my ram with only firefox open!)

I also noticed that feisty on my laptop is slow compared to feisty on my desktop. Everything just seems a little more sluggish. Programs take longer to open, Compiz-fusion is a lot slower (especially with animation. Indirect rendering helps, but then I can't logout without the laptop freezing), and in particular, Firefox/Swiftfox/Swiftweasel/Opera is slow and not very responsive.

My web browsers take a few seconds to pop up (longer than in my old desktop, which is only 1 second or so), then take 20 or more seconds to re-load the webpages I had open in the last session. (my old desktop is a little faster to reload my previous session). While the webpages are loading up from my last session, the whole computer bogs down, even though my CPU usage is around 40-50%. Also, I noticed that the CPU's frequency gets scaled down to 1.6 GHz from 2 GHz when my web browsers are doing any web page loading. 

Selecting a different tab in my web browser on my laptop takes 2 seconds to bring up that page and another second for the titlebar to reflect the change in the web page's name. On my old computer, this happens almost instantaneously. 

It seems like my processor's speed gets scaled back whenever there is CPU or GPU usage over 40-50% from any other program also (not just swiftfox). 

Mplayer is just barely able to play 1080p H.264 video, and the audio in rythmbox stutters whenever I do anything processor intensive (such as launching Opera).

Compiz-fusion shows a framrate of 10 fps when I am using the 3D cube w/ transparent windows, but on my old desktop, it is around 40 fps.

Using metacity doesn't speed anything up.




So, I guess I just feel like my brand new laptop should feel faster than it is. I don't think my 3 year old desktop should feel more responsive than a 1 month old laptop.

Anybody have any suggestions?

**What about the CPU scaling down during heavy usage problem I'm having? Could that be the cause of the slowness?**





P.S. You know that splash screen that pops up during login? how do I get rid of that? It doesn't show up on my old computer because I went to system, preferences, then gnome splash screen preferences and disabled it, but on my laptop, that isn't there.

EDIT: nevermind the first P.S., but do read the second P.P.S. ...or is it P.S.S I just installed gnome-splashscreen-manager and unchecked "show spash screen".

P.P.S You know how when you open a program that requires administrative privileges, a box opens that asks for the password and the rest of the screen darkens? How do I get my laptop to stop doing the whole darkening thing? (it is very juttery and full of tearing) My old desktop doesn't do this.

My recommendation is to re-install Vista.  Your laptop has a WPA key so all you need to do is borrow a Vista Premium DVD.

The amount of cr@pware that PC maker put on a new system is ridiculous.  Horribly slow the system down.

If you need Vista then re-install it and make sure you nuke the existing partitions.  Seems when you have Ubuntu installed alongside of a cr@ppy Vista install Ubuntu acts slow as well.

If you don't want vista reinstall Ubuntu telling Ubuntu to wipe the entire hdd.

---

### Post by ACGarib on 2007-08-17
The nice thing about the Vostro line of laptops is it comes with absolutely NO crapware (well, it came with norton ativirus and windows defender, and I consider that unwanted-ware, but that is easily removed) So I don't think crapware affected my ubuntu install.

At what point in the future do you guys think that solid state HDDs will become mainstream? What about those hybrid ones that microsoft is always talking about? I'm wondering if I should upgrade to a 7200 rpm hard drive soon or wait a couple of years and upgrade to a solid state HDD.

Again, see my previous post and make sure the steps I listed are correct for optimal performance.

Another question: Should the temperature of my cpu go up and down so fast? It can go from 40 degrees to 60 degrees in one second if I open a program like swiftfox. My GPU's temp slowly and steadily goes up and down instead of jumping all over the place like my cpu. Both windows and ubuntu are showing the same temp changes for my CPU

---

### Post by gobbles414 on 2007-08-17
ACGarib,

I don't know about a procedure for Dell Media Direct. Frankly, upon reading more about its purpose, I think that DMD sounds like more trouble than it is worth. However, I don't require instant-on functionality in my day-to-day computer use as you may.

The partitioner that comes with Vista Ultimate is very basic. How I would approach the partitioning would be to partition the computer during the Vista install into two partitions. One of these will hold Vista, the other will start out as free space. After the Vista install, Use the partitioner in the Ubuntu installer to divide the free space in two. After installing Ubuntu, you should be able to use either Vista or the Gnome Partition Editor to format the remaining free space into a storage volume.

[This]("http://www.computerhope.com/issues/ch000687.htm") document is a bit old, but appears to be a good general discussion about processor temperatures.

---

### Post by ACGarib on 2007-08-17
Thanks for all of your help gobbles414, and I think I will axe dell media direct. I don't see myself using it enough to give up some GBs of my HDD for it. 

So just to be clear, using that program that writes all 0s on the HDD you reccomended earlier in the thread, then putting the Vista CD in will work, even without a product key? It won't ask me for a new key and give me only a 30 day trial? Don't forget they gave me a Vista CD after I asked for one (I don't know if that makes a difference or not).

---

### Post by gobbles414 on 2007-08-18
ACGarib,

No problem about the help. I've asked for more than my share of help here in the forums; so it's nice to give back from time-to-time.

You should have a product key for Vista. You should be able to find it on the bottom of you laptop, or in your product's printed documentation. If it's on the bottom of the computer, I recommend that you write it down on a piece of paper so that you don't have to lift the laptop while the Vista installation DVD is spinning in the computer. Microsoft may require you to call them toll-free to activate Vista after it's installed. Otherwise it sounds lie you're "good to go"! :)

**EDIT: Don't forget to look on the Dell website for a bios update!**

Let us know how the installation goes.

---

### Post by stchman on 2007-08-19
> **ACGarib said:**
> The nice thing about the Vostro line of laptops is it comes with absolutely NO crapware (well, it came with norton ativirus and windows defender, and I consider that unwanted-ware, but that is easily removed) So I don't think crapware affected my ubuntu install.

At what point in the future do you guys think that solid state HDDs will become mainstream? What about those hybrid ones that microsoft is always talking about? I'm wondering if I should upgrade to a 7200 rpm hard drive soon or wait a couple of years and upgrade to a solid state HDD.

Again, see my previous post and make sure the steps I listed are correct for optimal performance.

Another question: Should the temperature of my cpu go up and down so fast? It can go from 40 degrees to 60 degrees in one second if I open a program like swiftfox. My GPU's temp slowly and steadily goes up and down instead of jumping all over the place like my cpu. Both windows and ubuntu are showing the same temp changes for my CPU

My father has an HP laptop with Vista Premium and it was running like cr@p.  I was able to borrow a Vista Premium DVD (I used the WPA key on the bottom of the laptop) and the laptop runs far better now.  HP is famous for massive amounts of cr@pware.

---

### Post by gobbles414 on 2007-08-19
*My father has an HP laptop with Vista Premium and it was running like cr@p. I was able to borrow a Vista Premium DVD (I used the WPA key on the bottom of the laptop) and the laptop runs far better now. HP is famous for massive amounts of cr@pware.* Ah... So it turns out that there are more version of Windows Vista than even Microsoft will admit! Windows Vista Home Premium: Home Speed Edition & Windows Vista Home Premium: Professional Speed Edition... :lolflag:

---

### Post by ACGarib on 2007-08-19
Well, I'm done installing Vista and Ubuntu, and Vista doesn't seem any faster, but holy moly!, ubuntu is definitely faster. Firefox and compiz-fusion still seems slower on my laptop than on my desktop, but everything else is a lot faster. 

I gave Vista 40 GB of space and Ubuntu 12 GB of space and the extra is for storage.

I guess I will spend the next week re installing and re-configuring everything...


Thanks for everybody's help! Thanks to you, my Ubuntu system is like it should be!

---

### Post by gobbles414 on 2007-08-19
ACGarib,

Glad to learn that most of Ubuntu is faster. Firefox has a reputation for slow render times versus other browsers. I don't know enough about Compiz Fusion to make any suggestions other than to make sure that you have version 0.5.2 (released August, 13th 2007) or higher. 0.5.2 is considered "the first release of Compiz Fusion," according to Wikipedia. I can't say that I'm surprised about Vista. It's such a memory hog that I doubt any system can run it at an impressive speed!

---

### Post by ACGarib on 2007-08-19
Yeah, tell me about it... Vista was using 1.1 GB or RAM with just firefox open and windows media player playing some music. I guess I see why people say to get at least 2 GB or RAM for Vista!

Ubuntu uses 350 MB of RAM with Gaim, swiftfox, compizconfig, emerald theme manager, compiz-fusion, and system monitor open.

I was surprised when I noticed that cpu scaling worked out of the box. I spent days trying to get it to work before. (go figure)

Also, I forgot to install the 64 bit version. (oops) I guess I will download the live CD and try it out to see if everything works, then maybe install it.

EDIT: also, does anybody know how to set custom commands in the new compiz-fusion? I want to have gnome-system-monitor open when I do control alt delete, but I can't figure out how. I can set command 0 to open gnome-system-monitor, but I can't figure out how to set command 0 to run when I type control alt delete. Any advice?

---

### Post by stchman on 2007-08-20
> **gobbles414 said:**
> *My father has an HP laptop with Vista Premium and it was running like cr@p. I was able to borrow a Vista Premium DVD (I used the WPA key on the bottom of the laptop) and the laptop runs far better now. HP is famous for massive amounts of cr@pware.* Ah... So it turns out that there are more version of Windows Vista than even Microsoft will admit! Windows Vista Home Premium: Home Speed Edition & Windows Vista Home Premium: Professional Speed Edition... :lolflag:

There are many editions of Vista

Home Basic
Home Premium
Business
Ultimate
Enterprise

Ridiculous.

---

### Post by ACGarib on 2007-08-20
I just found out that on my new Feisty install, compiz fusion makes swiftfox slower. 

Before I reinstalled Ubuntu, swiftfox was slow in both metacity and compiz fusion, but now, swiftfox is definitely faster and more responsive in metacity than in compiz fusion. 

I have found that using the --loose-binding option in compiz fusion speeds things up a bit, but it's still pretty slow compared to my desktop computer.

---

