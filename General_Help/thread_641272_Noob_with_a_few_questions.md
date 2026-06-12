---
title: "Noob with a few questions"
date: 2007-12-15
forum: General Help
---

### Post by natebenn on 2007-12-15
Well I finally got 7.04 installed on my system and I really like what I've seen so far but I have a few questions. 
1. Can I install wine on my setup? I have the 7.04 version that is built for A64 CPUs and when I try to download and install wine from applications-Add/Remove it tells me it can't be installed with this CPU. Am I missing something or is there no way to get wine on this system.

2. Is there a hotkey to switch between workspaces?

3. Can my resolution go any higher than 1024 x 768. So far it's the largest of 3 choices I have. 

Thanks so much for any help you can offer, it's much appreciated!

---

### Post by overdrank on 2007-12-15
> **natebenn said:**
> Well I finally got 7.04 installed on my system and I really like what I've seen so far but I have a few questions. 
1. Can I install wine on my setup? I have the 7.04 version that is built for A64 CPUs and when I try to download and install wine from applications-Add/Remove it tells me it can't be installed with this CPU. Am I missing something or is there no way to get wine on this system.

2. Is there a hotkey to switch between workspaces?

3. Can my resolution go any higher than 1024 x 768. So far it's the largest of 3 choices I have. 

Thanks so much for any help you can offer, it's much appreciated!

1. this link may help
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)
3. this link may help with  your resolution 
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by natebenn on 2007-12-15
Thanks, I 'll check those out and hopefully I can get things working here.

Another question to add to the pile though :-k, when I reboot and try to get into my XP Pro OS all I get is the words "Starting up..." across my black screen and nothing happens. Any ideas here?

---

### Post by jamesford on 2007-12-15
regarding screen resoluton, u may get more choices if u install ati/nvidia drivers (providing u got  ati or nvidia graphics card)

also wrt to resolution, ubuntu 7.10 comes with a nice gui screen/resolution tool that might be useful. afaik its not available for 7.04, the option then i thnik is to edit xorg.conf manually...why did u install and old version of ubuntu anyway?

---

### Post by natebenn on 2007-12-15
I would have installed 7.10 but for one reason or another all I could get when trying the live cd was  a black screen once Ubuntu had loaded.

---

### Post by r-mo on 2007-12-15
Don't think anyone's answered your second question yet.  You should be able to switch workspaces with ctrl+alt+left (or right) arrow.

---

### Post by knutschr on 2007-12-15
Try 
```
sudo apt-get install dist-upgrade
```
to get 7.10

---

### Post by natebenn on 2007-12-15
Thanks for all the answers and responses!

I would love to get to 7.10 but I am a noob to all of this so please bear with me but where do I enter this code you've posted to get to 7.10?

---

### Post by knutschr on 2007-12-15
Open Terminal and paste it.

---

### Post by natebenn on 2007-12-15
ok I'll do just that but before I can someone tell me what happened to my XP pro install? Is this a common problem after installing Ubuntu? Thanks again everyone for all the help!

---

### Post by Martje_001 on 2007-12-15
> **natebenn said:**
> ok I'll do just that but before I can someone tell me what happened to my XP pro install? Is this a common problem after installing Ubuntu? Thanks again everyone for all the help!
No that's not common. There is probably something wrong in '/boot/grub/menu.lst'

---

### Post by blackdragon1157 on 2007-12-15
I have XP pro on my dual boot and both Windows and Linux run just fine.  Perhaps it is a partition problem or maybe there is a genuine problem with windows that is not related to ubuntu.

---

### Post by MONODA on 2007-12-15
to answer your last question: if you did not defragement your hard drive in windows before installing ubuntu then u probably installed ubuntu over some system files. If you did defragment then I am not sure what went wrong. No I dont think it is a common problem b/c I have installed ubuntu at least 10 times on several different compouters.
Good luck

---

### Post by natebenn on 2007-12-15
Alright well I didn't defrag so maybe that's the issue. I think I am going to go ahead and move up to 7.10 anyways and use the non 64 bit version, seems like it may be a little more noob friendly. I guess I'll wipe out my whole drive and start over, seems like the easiest way to do it. Are there any suggestions before I do that? I am not sure how to put 7.10 on a cd in Ubuntu either so if somebody could give me a heads up that'd be great.

---

### Post by knutschr on 2007-12-15
Download the LiveCD .iso file.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by saving it.
It will go to your /Home/[name] directory.

You then must burn it as an image.
I don,t remember what is installed by default in Ubuntu, but I use K3b.
```
sudo apt-get install k3b
```

You must install XP first, as MS ignores any other installations on the HD.

---

### Post by natebenn on 2007-12-15
Great, thanks! The download is in progress so I am gonna go buy some cds while I wait and then give it a shot. I think I am gonna pass on installing XP as well and just go cold turkey, it will force me to learn this stuff. :) Thanks again, I'll try and update the thread with what happens.

You've got a great forum here!

---

### Post by r-mo on 2007-12-15
> **natebenn said:**
> I guess I'll wipe out my whole drive and start over, seems like the easiest way to do it. Are there any suggestions before I do that? I am not sure how to put 7.10 on a cd in Ubuntu either so if somebody could give me a heads up that'd be great.

1) Make sure you backup all your important stuff
2) If you're doing a dual boot, install xp first
3) Think about using a separate /home partition this makes upgrading (to 8.04 etc) a lot easier.

As for burning the cd you should be able to right click the iso and 'Write to Disc' or you could install k3b (kinda like nero) from add/remove apps.  (It puts it under sound and video.)

---

### Post by natebenn on 2007-12-15
so are you saying make a partition on the drive that's like 8 gb just for the 7.10 install? I would like to do that if it will make things easier but i want to be sure I understand you correctly.

---

### Post by r-mo on 2007-12-15
> **natebenn said:**
> I think I am gonna pass on installing XP as well and just go cold turkey, it will force me to learn this stuff. :) 

Good choice :)

Yes you understand correctly, I found this on ubuntu wiki:

"Having a separate partition for /home is always a good idea, since it lets you reinstall your system without losing valuable personal data. This can be especially useful in a distro like Ubuntu, where users have the chance to upgrade their install quite often (every six months) and might want to perform a clean install to avoid potential problems. Nevertheless, and while some other distros out there already do this automatically, Ubuntu doesn't."

[https://wiki.ubuntu.com/RecommendSeparateHome](https://wiki.ubuntu.com/RecommendSeparateHome)

---

### Post by natebenn on 2007-12-15
Great suggestion, I'll do just that. Is that something I can do during the install or do I need to do it previous to the install somehow?

---

### Post by knutschr on 2007-12-15
I don't know that, but I think you should make your /Home much greater than 8 GB.
That is the partition that will grow, and where everything you will have remained goes by default.

---

### Post by r-mo on 2007-12-15
You can do it in the installation.  When it asks about partitioning chose the manual option.  You'll want to delete whatever's there and set up 3 new partitions.  It's pretty easy really

1) for the system set the mount point to / in the drop down  I'd recommend 20GB personally but that depends how much extra you want to install, 4GB is enough, I just like to try out all the games and stuff :) (format as ext3) 

2) for your home set the mount point to /home in the drop down you probably want this as whatever space is left (format as ext3) less 1-2GB for

3) for the swap partition this is the 1-2GB you left out and is used as extra RAM and for hibernation (I think) so should be bigger than the amount of RAM you have.  Set mount point to swap

---

### Post by r-mo on 2007-12-15
and If you find the partitioner built into the install a bit confusing.  There's a more graphical way to do it in System->Administration->Partition Editor  

You still need to set the mount points in manual partitioning though.

---

### Post by natebenn on 2007-12-15
alright well I am not sure that I understand all of that but is probably because I'm not familiar enough yet with Ubuntu's setup; it's so different from windows. Anyways I have the 7.10 on disk now so I am gonna wipe this and give your suggestions a try. I will keep asking questions I'm sure so if you have the patience keep checking back. :) Thanks again r-mo and knutschr, you are a real help.

---

