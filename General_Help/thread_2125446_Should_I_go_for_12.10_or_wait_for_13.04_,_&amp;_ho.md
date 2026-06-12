---
title: "Should I go for 12.10 or wait for 13.04 , &amp; how will upgrade affect present software?"
date: 2013-03-14
forum: General Help
---

### Post by ask_ on 2013-03-14
Hello ,

I am using Lubuntu 11.10 . I have the following queries :-

1)Now this version is supported till April 2013 . So is it 1 April or 30 April ?

2)And since it is only 1.5 months till next release , should  I wait for 13.04 ? 

3)Further I had a query regarding upgrades. I have got virtualbox running Windows XP , Dropbox , Java runtime , vlc media player , flash player. Will these software become non functional if I upgrade ? And what about the data , I mean even if software goes , it would be great if data remains intact (I will make a backup in any case).

4)Also since I dont have guaranteed internet connectivity , I plan to make a Live USB by downloading the iso file.
As far as I recollect when booted , the live USB gives option of upgrading present version. Will it have same effect if upgraded from within the OS using internet ? 


Thanks.

---

### Post by VeeDubb on 2013-03-14
1. I'm not sure, but it really doesn't matter.  The number of meaningful patches and updates in that time will be extremely limited.  That said, I 'believe' that it's through the end of April.

2. I would wait.  If you want to stick with LTS releases, you'd actually want to install 12.04, but since you're not currently using an LTS, I don't see much point in that.  Likewise, I just don't see much point in updating about a month before a new version comes out.

3. Typically, any software that was installed through the main repos will function just fine, although there have been exceptions here and there.  I don't see anything in your list that would give me pause.

4. Yes.  And the easiest way to upgrade (assuming your system is running well) is usually to go to where you will have a good connection for a couple of hours and simply upgrade.  It's not actually much more work than doing regular periodic software updates.  The update manager will show that 13.04 is available, you click the button, make a sandwich, and wait.  After you reboot, you're running 13.04.  That said, if your system is not running well, you may want to consider backing up your important files, including the VM for windows, and doing a clean install.  You should also, as a matter of good housekeeping, back those things up regularly anyway to some sort of outside storage.  At a minimum, and external USB hard drive.  An NAS would be better, and offsite storage is best.  You should also go ahead and make your USB install disk before you begin so that if things do go all wahoonie shaped, you'll be able to change gears and do your fresh install.

---

### Post by claracc on 2013-03-14
I would update your lubuntu 11.10 to the lubuntu 12.04 release, which has to appear in your software sources software if you have chosen to see the notification for any new release in the update tab.

13.04 as a new release (yet not out) will have initial stability problems (as it is logical) till patches and updates make it to go stable, being tried by users who will report the problems. Lubuntu 12.04 althoug not a LTS it is a stable well proof release. From it you can update too to 12.10 (step by step updating) which is a stable lubuntu release too.

When updating through update manager your /home folder is preserved but if you make a new install you'll have to backup your data since your personal data are removed by new installation. 

I don't think your virtual box has to be damaged by an update of the release, but for this point, you will have to wait for more expertize knowledge.

---

### Post by VeeDubb on 2013-03-14
> **claracc said:**
> I don't think your virtual box has to be damaged by an update of the release, but for this point, you will have to wait for more expertize knowledge.

While we disagree about what to update to and when, you are absolutely correct about this.  Virtualbox stores your VMs in your home folder unless you've done something very non-standard.  As you rightly point out, your home folder is not touched by a regular upgrade.  That said, I still recommend backing up first in case something goes wrong and you're forced to do a clean install.  It's unlikely, but it can happen.  If replacing that VM would be a problem, you need to be sure you're backed up, but that's just good administration.

---

### Post by sudodus on 2013-03-14
I agree with most of what has been replied, but want to add my two cents.
> **ask_ said:**
> Hello ,

I am using Lubuntu 11.10 . I have the following queries :-

1)Now this version is supported till April 2013 . So is it 1 April or 30 April ?

Usually near the end of the month (but before the 30th).
> 
2)And since it is only 1.5 months till next release , should  I wait for 13.04 ? 

No, 13.04 will probably be buggy during the first two months, and you will need something before the end of life of 11.10.
> 
3)Further I had a query regarding upgrades. I have got virtualbox running Windows XP , Dropbox , Java runtime , vlc media player , flash player. Will these software become non functional if I upgrade ? And what about the data , I mean even if software goes , it would be great if data remains intact (I will make a backup in any case).

My Virtualbox has survived several upgrades to new versions :-) and the other application programs should be OK. You have some choices about the data:

1. Upgrading and taking the risk, that some program packages or applications need some tweaking (or in a bad case a lot of tweaking). It has to be done stepwise 11.10 - 12.04 - 12.10 ... and the more steps to longer time and more risk.

2. A complete fresh installation of 12.10. You need to reinstall your data files and reset your environment settings and tweaks. It is a good idea to install program packages when you need them (instead of trying to find and reinstall all your old 'extra program packages').

3. A fresh installation of 12.10 but with a separate partition for /home (copy your present /home directory to a new partition). This will keep most of your data and environment settings and tweaks. But you will probably need to re-tweak some settings anyway.

> 
4)Also since I dont have guaranteed internet connectivity , I plan to make a Live USB by downloading the iso file.
As far as I recollect when booted , the live USB gives option of upgrading present version. Will it have same effect if upgraded from within the OS using internet ? 

Thanks.

I'm not sure about this last question. It is possible but less convenient to upgrade your system without internet connectivity. I have seen threads at the Ubuntu Forums about this issue. Try to find them :-) If you can't find any of them, start a new thread with a descriptive title about that subject for example 'how can I update and upgrade my lubuntu without internet or with a bad connection'.

---

### Post by ask_ on 2013-03-14
Hi,thanks for the replies. They really helped.

By the way , update manager is telling me that 12.04.2 is available. I wonder why it is not giving any notification for 12.10 . Iis that because of the stepwise installation thing ?

My internet is usually reliable , but in 1 out of 20 times it may go down. What happens to upgrade process in such a case. Will I be able to resume it later ? And roughly how much would be data download - 700 MB to 1 GB ?

---

### Post by mörgæs on 2013-03-14
> **ask_ said:**
> 

1)Now this version is supported till April 2013 . So is it 1 April or 30 April ?


The exact end date will be posted here: [http://ubuntuforums.org/forumdisplay.php?f=13](http://ubuntuforums.org/forumdisplay.php?f=13)

Lubuntu does not offer long time support. There are simply too few people around for maintaining an old release.

You could install 13.04 now in a dual boot and only fall back to 11.10 in case some things go haywire in 13.04. Though it's formally still in development it's stable (at least on my hardware) and ready for install. Best is that you simply test it rather than asking for opinions. Stay away from upgrades.

---

### Post by sudodus on 2013-03-14
You need to upgrade stepwise, 11.10 -- 12.04 -- 12.10, so when you have 12.04.2, upgrading to 12.10 will be offered.

---

### Post by ask_ on 2013-03-15
I did something which I had not planned. I installed Ubuntu on one of my systems. There is an old one for which Lubuntu is suitable. 

But on the other system - a lenovo laptop having Intel I3 and 2 GB ram I was running Lubuntu out of habit. I did that mainly because I wanted to use battery efficiently and because I am a bit used to WindowsXP like desktop interface. 

But going by most of the feedback here,  I realised that I would have to do upgrades/fresh installs every  1.5 years if I carried on with Lubuntu. 

Hence I did a fresh install of Ubuntu 12.04.2 on it. Now I can be relaxed till April 2017 . :) 

And to save battery I installed LXDE on it. I hope it will have same effect as installing Lubuntu ? 


On the other system which is rather an old one I am sticking with LUbuntu and will follow advice given here.

---

### Post by sudodus on 2013-03-15
It is not exactly the same thing. The same desktop environment LXDE, but it is tweaked in a different way, and it is not bundled with the same software as Lubuntu. But it is OK.

The sad thing is that LXDE has not long time support (LTS), so you are in the same situation as if you had installed Lubuntu at the start. 12.04 is good until this October (2013), but then you need to decide what to do:

- upgrade to 12.10 or

- remove LXDE and install another desktop environment, for example XFCE (or the full xubuntu-desktop). This will give you long time support until April 2015.

- remove LXDE and use standard Ubuntu with Unity or gnome shell. This will give you long time support until April 2017.

---

### Post by ask_ on 2013-03-15
Thanks again, for replying. 
I suppose I will remove LXDE from October 2013 onwards and stick with Unity or go for GNOME shell.
The idea of LTS till 2017 is pretty appealing.

---

### Post by sudodus on 2013-03-15
> **ask_ said:**
> Thanks again, for replying. 
I suppose I will remove LXDE from October 2013 onwards and stick with Unity or go for GNOME shell.
The idea of LTS till 2017 is pretty appealing.

Then you may find this link useful [[COLOR=#ff0000]https://help.ubuntu.com/community/PreciseGnomeClassicTweaks[/COLOR]]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks")

Good luck :-)

---

