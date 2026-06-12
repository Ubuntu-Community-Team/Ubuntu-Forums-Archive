---
title: "Linux compatibility with new tech and hardware"
date: 2013-03-04
forum: General Help
---

### Post by WesternRyno on 2013-03-04
Hello all, I've recently had quite an eye-opener attempting to run a stable system on a new Lenovo Ideapad U410 i7 8GB Nvidia GE 610M.  I'm new to installing Ubunutu but have successfully been enjoying two machines with 12.04 that my friend put on for me.  All my reading and research of late has shown that I'm not alone in experiencing difficulties with some of the new tech out there including Optimus, Intel SRT and SSDs.  I'm going to take my U410 back and am now looking into a new laptop with more foresight, and honestly a little hestiation.  My questions to the community:

  In your opinions, are many of these new laptops and their techs, as mentioned, causing issues with Linux or is it more a combination of my particular model coupled with my experience.

---

### Post by ManamiVixen on 2013-03-04
From what I heard, Intel Sandy Bridge graphics are still poor performing, Nvidia Ion dosen't work, and some wireless cards are nonfunctioning. But for the most part, Linux is better off than it was a few years ago and is compatible with most new hardware.

---

### Post by oldfred on 2013-03-04
You have one of the most complex systems to try to dual boot. The entire UEFI secure boot is new and both vendors & Linux are working around all the new issues. Linux is often 6 months or  more behind new systems as it has to figure out how to make it work without much or any help from the vendor. And Windows never does anything to make it easy for competitors.

Then you added the new Intel SRT which is designed just for Windows and somehow uses RAID. Standard desktop Ubuntu does not include the RAID drivers as normally RAID is not used a lot on desktops. So you had to work around the RAID. Those that made that work best seemed to just un-install it and use the SSD as a Ubuntu boot drive. Some vendors have larger SSDs than others but I normally suggest 10 to 25GB for / (root) so most SSD will work as a Linux system partition. 

Then you added the major issue of video. Since they added video to kernel we all have some issues. I have to add nomodeset to use my nVidia card. 
But nVidia has refused to support Optimus in Linux to date. But bumblebee seems to work.
       Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)

    
 NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

Or a new fully loaded Windows system with all the new bells & whistles is not easy to install Linux to. Not really for a new user.

---

### Post by 3Miro on 2013-03-04
If you want to use Linux only, then get a system with Linux pre-installed. System76, ZaReason or others. There is no point in buying a system with an OS that you will not use and a bunch of hardware that will probably be incompatible.

I would stay away from Optiums. Intel's performance is sufficient for work, I can run external 1920x1080 monitors on Intel HD 3000 graphics with Unity and a few extra effects.

Stay away from secure-boot non-sense. Right now, it may work, it is safer to assume that it simply doesn't work.

---

### Post by WesternRyno on 2013-03-04
Thanks for all these replies.  They confirm my experience and make me feel a little better about it too.  I was having trouble fathoming why it was so difficult to get things going.

Thread tools doesn't give me an option for solved?

---

### Post by oldfred on 2013-03-05
See my new signature for a work around.

---

