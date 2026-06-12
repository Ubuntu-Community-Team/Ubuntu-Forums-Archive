---
title: "Should I remove Windows 8?"
date: 2014-02-22
forum: General Help
---

### Post by jamesp2 on 2014-02-22
I have a toshiba nb10t - full spec here - [http://www.notebookcheck.net/Review-Toshiba-Satellite-NB10t-A-101-Netbook.108374.0.html](http://www.notebookcheck.net/Review-Toshiba-Satellite-NB10t-A-101-Netbook.108374.0.html)

I have been trying for the last week to dual boot preinstalled windows 8 with Ubuntu 12.04 LTS via USB

To cut a long story short I have ended up with both Windows 8 and Ubuntu 12.04 installed on my hard drive however the boot seems to be broken (unable to fix with boot repair in Ubuntu Live) and i cannot access the recovery partition for Windows 8. . I have tried to repair windows 8 using a bootable USB from a friend however this has been unsuccessful (multiple errors - drive locked, missing partition when i have tried this). As i understand it it can only be repaired with a USB recovery made from the original Windows - the activation code for the preinstalled Windows 8 is in the BIOS and these must match for it to repair - wont do it from any other copy.

To top it all off when i installed Ubuntu through USB my laptop screen was not recognized and i had to do it using an external monitor attached via VGA. The touchscreen worked however. It succesfully installed but as before i cannot access it as i cannot boot.

ANy help on these issues would be greatly appreciated.

I am sorely tempted to boot through LIve USB and erase windows and install Ubuntu over the whole 500gb hard drive. I am very wary of doing this as i may not be able to boot into it (which i currently cant do) or see it on my laptop screen (which i cant do either). Plus i do not want to end up with a very expensive paperweight.

Sorry this post is so long but I am really really stuck!!!!

James

---

### Post by TheFu on 2014-02-22
SecureBoot enabled?
GPT and/or UEFI involved?

Should you remove Win8?  I'd say YES! But ... people who respond on this forum are likely to say that always. ;)
Or you could reset the system to the factory default using that backup you made before starting down this path.  Anytime we mess with boot and/or partitions, we risk screwing things up.  It is more true since UEFI and secure boot were mandated by Microsoft than ever before.

---

### Post by mörgæs on 2014-02-22
I guess you are the best to answer the question. 

How do you plan to use the computer? If you for example are into gaming it is a good idea to try to salvage Windows but if the main purpose is normal web surfing a Buntu-only system would do fine. 

If you do reinistall I suggest a 64 bit 13.10 and not 12.04.

---

### Post by TheFu on 2014-02-22
> **mörgæs said:**
> If you do reinistall I suggest a 64 bit 13.10 and not 12.04.

Clearly others will have a different opinion.

I disagree with this advice without providing all the caveats. Support for 13.10 will expire **before** support for 12.04 expires in 2017.  For a non-programmer, being on an LTS release is more important than almost anything else.  We want to use the system, not reinstall the entire OS every 6 months. In theory, support for UEFI and GPT has been back-ported to 12.04.

There is an upgrade path from 12.04 to 14.04 since both are LTS releases.

---

### Post by Mark Phelps on 2014-02-22
It's not clear from your post whether you have actually USED Ubuntu on this notebook or, instead, only gotten far enough to install it.

BEFORE I got rid of Win8, I would at least use the Notebook in Ubuntu for a while to confirm the following:
1) All the hardware devices work -- including the SD card reader and the VGA video out jack
2) The notebook does not run hot, neither do you have the problem of the fan running nearly all the time
3) The graphics on the notebook are able to provide real-time video without tearing, pixelation, or the notebook overheating.

You already paid for Win8 when you bought the Notebook.  You need to confirm that Ubuntu works at least as good as that before you remove Win8.

Also, since this is a Toshiba, they provide a way to create Restore media on USB or DVD.  I would use that to create USB restore media as soon as you can get Win8 booting again.

---

### Post by jamesp2 on 2014-02-22
We use it as a family laptop - web surfing, simple documents and spreadsheets,Skype, music, occaisonal video. No real gaming or developement.
Ubuntu is installed on the hard drive but since i cannot boot into it i cannot verify what does and doesn't work (although in setup the Wifi worked fine)
The main fear is for the laptop screen. As i said i had to I went through the install on an external monitor via VGA not the laptop screen itself.

Will try and get a screenshot of Gparted put up in a few minutes

---

### Post by jamesp2 on 2014-02-22
Blimey.

Since i tried to do a repair of windows 8 with my friends USB this is now the state of the computer in Ubuntu Live Gparted - 
(on the external screen via VGA)

[ATTACH=CONFIG]250567[/ATTACH][ATTACH=CONFIG]250568[/ATTACH]

Everything is gone and i cant boot into anything.
When i try booting via HDD it says - 

Checking for media presence
No Media detected......

Help!!!!

---

### Post by mörgæs on 2014-02-22
> **TheFu said:**
> Clearly others will have a different opinion.

I disagree with this advice without providing all the caveats. Support for 13.10 will expire **before** support for 12.04 expires in 2017.  For a non-programmer, being on an LTS release is more important than almost anything else.  We want to use the system, not reinstall the entire OS every 6 months. In theory, support for UEFI and GPT has been back-ported to 12.04.

There is an upgrade path from 12.04 to 14.04 since both are LTS releases.

**&#8203;**Maybe. The important part is what benefits original poster.

Long time support is nice to have. 
Full hardware support is need to have. 

We already have an indication that hardware support is not complete in 12.04. It's not surprising since the computer is newer than the software. 

If one is taking the chance of doing an online upgrade both releases can be upgraded to 14.04 LTS. No difference here (only that a short-step upgrade is less error prone than a long one).

---

### Post by oldfred on 2014-02-22
This can only fix minor Windows issues, as you have to have the Windows repair flash drive for Windows 8 to fix Windows issues.
But we need to see more info. That gparted is not showing anything could be many different issues.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by jamesp2 on 2014-02-22
Thanks for the help
 Ran boot repair
Gave me the URL - [http://paste.ubuntu.com/6977200/](http://paste.ubuntu.com/6977200/)

also - "No change has been performed on your computer"

NB - when the boot repair window popped up there was no option of "recommend repair" only the "create a boot info summary" option

NBB- the fact my laptop screen is completey black is very worrisome. How on earth could i fix this?

---

### Post by TheFu on 2014-02-22
That boot-info report shows that the 500G HDD doesn't have **any** partitions anymore. In short, all the data, any OS, everything that was on it is gone.

So .... looks like you have your answer about removing Win8. It is already gone.  That sucks.  It might be possible to get prior partitions back, don't touch the HDD. That is very important. [http://askubuntu.com/questions/186193/deleted-partition-recovery](http://askubuntu.com/questions/186193/deleted-partition-recovery)

---

### Post by jamesp2 on 2014-02-22
Ok.
Not planning on doing anything as i have now no idea which way to go.
Any advice on getting my laptop screen up and running would be appreciated as well.
Thanks

---

### Post by oldfred on 2014-02-22
Two other bay trail systems.
 [http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1)
      
 The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)

---

### Post by jamesp2 on 2014-02-23
So if my laptop is one of these baytrail chips I don't have much chance of getting the screen to work if i do a full install of Ubuntu and now have no windows 8.
Not sure if I have any options left.
Will contacting Toshiba be of any benefit?
How can they manufacture a machine that is so restrictive?

---

### Post by mörgæs on 2014-02-23
How does a live boot of 13.10 work? You managed to get a semi-succesful 12.04 running so there is some connection after all.

Also worth testing the development version (14.04).

Mirosoft is dictating a lot of restrictions. Getting worse for each release of Windows.

---

### Post by jamesp2 on 2014-02-23
I will try these two versions and report back.
I assume I will need the 64 bit versions of both.
Thanks

---

### Post by slooksterpsv on 2014-02-23
Always make backup discs just incase Ubuntu doesn't play nice with your hardware. Also, see if specific pieces of your hardware are supported in the Ubuntu you're installing. I know my laptop, it's about 1 1/2 months old now, doesn't like 12.04, so I'm waiting for 14.04. And you can always always always ask for help on the forums here. Hope 13.10 plays better.

---

### Post by jamesp2 on 2014-02-23
Went back to the store today an explained the catastrophe. Tech support Guy very kindly pulled the display Toshiba laptop (exact same model) off the shelf and allowed me to make a complete recovery USB off that machine (16.8gb). Ran the reinstall of that in my machine. It worked 
 thankfully.
Now have windows 8 back on the machine.
First thing I did when I got home - made a complete recovery USB from my machine. Lesson learned.
Will not be touching any more computers tonight.
Will have a play with 13.10 tomorrow and report back.
Huge relief!!!!!

---

### Post by Jhongy on 2014-03-03
Baytrail tablets with 32-bit UEFI can boot Linux now -- a few hoops to jump through but the procedure is getting easier.

Hardware support is also improving, but we still have some way to go.

I've been working on the Asus T100: [http://ubuntuforums.org/showthread.php?t=2191557](http://ubuntuforums.org/showthread.php?t=2191557)

---

### Post by monkeybrain20122 on 2014-03-03
> **TheFu said:**
> Clearly others will have a different opinion.

I disagree with this advice without providing all the caveats. Support for 13.10 will expire **before** support for 12.04 expires in 2017.  For a non-programmer, being on an LTS release is more important than almost anything else.  We want to use the system, not reinstall the entire OS every 6 months. In theory, support for UEFI and GPT has been back-ported to 12.04.

There is an upgrade path from 12.04 to 14.04 since both are LTS releases.

I wouldn't want to keep 12.04 til 2017 except for old hardware (a machine comes with Win8 is not old hardware by my book). It is already old.  Even non programers would want up to date software and drivers.
As for update path, I would rather more people go for fresh install,then there will be less threads here about issues arising from broken upgrades.

---

