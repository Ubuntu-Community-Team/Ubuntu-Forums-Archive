---
title: "Ubuntu 14.04 Hanging on Boot after Failed Package Update"
date: 2014-05-06
forum: General Help
---

### Post by Harrison_Bolin on 2014-05-06
I am in need of help, so I did lots of research before coming here. First, my computer stats: Dell Vostro 3450, 14' screen, i5vpro Processor, and 8gig (7.7 acording to Ubuntu) of RAM. 

I have Ubuntu 14.04 installed. 

How I got my problem: I was happily skipping around Ubuntu after my second day of use, very proud of myself. I had browsers and wordprocessors, and various applications. I was all set. I then discovered that my back lit keyboard was not turning on, so I decided to look around on how to install it. It was very vague, but after a bit of searching I downloaded Synaptic from the Ubuntu software center. I then proceeded to find a package that was labeled dell-(something I cannot remember). I marked it to download. It dealt with fan operations and special key management. It had 3 items. I had Firefox, Synaptic, and I think OpenWord running, and when I started to download the packages, my computer froze. After waiting a few minutes, I shut down my computer. I then proceeded to boot, and received the splash screen, with all of the white dots filled in with orange. It then sat there, hanging.

What I have tried: I have tried adding *nomodeset* to the kernel line, and it loaded with low graphics, and produced this line:[I]* speech-dispatcher disabled; edit/etc/default/speech-dispatcher&#8211; 
[/I]
I also tried running it overnight (not a very smart idea, I know) and that did not fix it either

I also tried running the recovery mode, and did the *dpkg, fsck, network,* and* root* programs, with little to no success. Root worked as I thought it would, but I don't know what do do from there

I tried the *failsafeX* mode from recovery, which produced little results, only getting past the warning about low graphics, it did not show the mouse. 

Pressing Crtl + Alt + F1-F6   does not get a response from the splashscreen, and when replaceing the splash and other command from the kernel with "text" I got to the text login, but that froze too.

I have not tried a LiveCD, but since I do not have one, that is not an amazing solution. 

I really appreciate all the help, and hope that we can figure something out.

[Update]
No news so far, but I remember someone mentioning a Boot repair or Boot Solver program that helped sort out boot problems. I think it had to be run from a LiveCD, but I don't know if this is what I need or not. Just an idea

**[Final Update]**
Thank you everyone who helped. It eventually ended up in having to re-install, but thats fine with me. Just wanted to note that the Datastick Pro 16GB by Cention works poorly for a USB boot drive when creating it from a mac. I suggest a Sandisk for best results.

Thank you all for your help!

---

### Post by jbaerboc on 2014-05-06
One thing that might help is if you can boot in verbose mode it should show you where it is hanging exactly. My guess it what you installed broke something and so when attempting to start a service during boot it's getting stuck there. I don't remember exactly how to force boot verbose but maybe some forum searching can find that for you or someone else can post here with how to do it. If we can see what's freezing it up we can then help you fix it [hopefully].

---

### Post by jbaerboc on 2014-05-06
Saw something somewhere just now that said pressing the Esc key during boot [i would assume right at the beginning of the dots filling in] would jump it to verbose mode. If that does please let us know what you find out.

---

### Post by Harrison_Bolin on 2014-05-06
Here's some results I got from trying to get into different text modes, I don't know if any of them are verbose mode. Will try it again soon.

[ATTACH=CONFIG]252939[/ATTACH][ATTACH=CONFIG]252940[/ATTACH][ATTACH=CONFIG]252941[/ATTACH][ATTACH=CONFIG]252942[/ATTACH]

---

### Post by jbaerboc on 2014-05-06
So it looks like it stops at "Restoring Resolver State" ? Does it ever get passed that or is that where it hangs?

---

### Post by Harrison_Bolin on 2014-05-06
That is were it hangs, apparently. On that first screen type of screen, I usually get the cups error, and then the other one seems completely random. Sometimes the modem fails, or something else. But yes, that is were it hangs. Let me know if I should test it again, and how I should go about doing that,

---

### Post by Harrison_Bolin on 2014-05-07
Ok, I did the ESC thing and got near the same thing. Here is the pic:[ATTACH=CONFIG]252943[/ATTACH]

---

### Post by jbaerboc on 2014-05-07
This seems to be similar to what you're seeing. Maybe give a few of their steps a try?

[http://askubuntu.com/questions/361346/unable-to-start-after-13-04-13-10-udate](http://askubuntu.com/questions/361346/unable-to-start-after-13-04-13-10-udate)

---

### Post by oldfred on 2014-05-07
You should not need Boot-Repair as that is if you cannot get to a grub menu or start to boot. It cannot help much past that point.

You still may need to run a full fsck from your live installer. It is more complete and the one with ext4 on reboot. And having any files open or working when system crashes almost always needs a full fsck.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Are you installed in UEFI or BIOS boot mode?

Details in this apply to many Intel based systems not just M3800.
      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)

Users here have installed new kernel from ppa.
[http://ubuntuforums.org/showthread.php?t=2204287](http://ubuntuforums.org/showthread.php?t=2204287)
Also new kernel

 Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)  Dell 17R
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1300349](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1300349)

---

### Post by lennart3 on 2014-05-07
Thanks for all info.
I will read all info and act after that.
Meanwhile I found that the reason for the hang when trying Lubuntu is probably
caused by incompability with the Rage 128 Pro  Ultra GL graphics card in the Dell D530. I tried to run Lubuntu from CD again and what happens is that it can not find a proper screen setting by default, it looks like 2:5 instead
of 4:3 = most of the info is outside the visible screen area. It is impossible to read anything on screen - most info is outside viewing area. I think that the graphic card does not like that either.  BTW I remember some issues with that card as incompability with Google Earth in Windows. Not the best graphic card in the world....
I will report back ASAP.

---

### Post by lennart3 on 2014-05-07
Oh my...
Sorry for my post ...posting in the wrong thread....

---

### Post by Harrison_Bolin on 2014-05-07
Thanks so much for the help! I'll admit, I don't totally know what to do with those articles, I read through them and they were interesting and gave good tips, even though they don't apply to my specific system. Before the crash everything was working except for fingerprint reader (understandable) and the backlit keyboard (not the screen back-light). 

I believe I have it in BIOS boot mode, because it still shows the regular dell Vostro bios screen, When I press the F12 button furing startup (within first 2 seconds) I get to the Dell BIOS screen, with different settings for repai. I don't totally know a lot, coming to Ubuntu (and Linux) only three days ago. 

Once i find a flashdrive to put Ubuntu on (I'm downloading 14.04 from my Mac), how do I find the name of the partition I should replace in your suggestion with sdb1? Sorry for my cluelessness, I really appreciate the help. 

In response to lennart3: I don't think I have that particular graphics, card, but then again, I was never able to find out. Thanks for the input!

---

### Post by Harrison_Bolin on 2014-05-07
> **lennart3 said:**
> Oh my...
Sorry for my post ...posting in the wrong thread....

Thanks for telling me! Your post really confused me XD

---

### Post by oldfred on 2014-05-07
Run this and any partition with ext4 should have e2fsck run on it.

sudo parted -l

---

### Post by Harrison_Bolin on 2014-05-07
Thanks! I'll run that from the terminal from the Boot USB? 

PS: I decided to run the Dell BIOS Diagnostics, and the results are that everything is working fine from a hardware and BIOS standpoint. Don't know if this actually means anything, but I thought I would let you know.

---

### Post by Harrison_Bolin on 2014-05-07
Ok update. I got unetbootin and made a Ubuntu drive from my mac. So far, though, my computer does not recognize it as a boot drive? Is there anything I need to do, or something I'm doing wrong?

---

### Post by oldfred on 2014-05-07
Mac is different, but I would think unetbootin would work. Do not know if there are issues.

This includes persistence so you can save some data.
[h=2][/h] Fix for making bootable Ubuntu Live USB with persistence using Unetbootin on a Mac 
    [SIZE=1][FONT=arial][/FONT][/SIZE]http://ubuntuforums.org/showthread.php?t=2174630

---

### Post by Harrison_Bolin on 2014-05-08
Ok so after around 30 tries, I got it to boot with a USB stick. I know I need to do a full fsck, but how? I tried sudo e2fsck -C0 -p -f -v /dev/sdb1   but it said that it was in use. What should I do?

---

### Post by Harrison_Bolin on 2014-05-08
Finis:  It seems my problems have been resolved in the light of a glorious re-install. Thanks for the help! I'll mark this thread solved so it saves confusion

---

### Post by oldfred on 2014-05-08
Glad you managed to figure it out. I do not know much about Macs.

30 tries!! You have perseverance.

---

