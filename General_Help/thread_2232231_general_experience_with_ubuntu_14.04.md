---
title: "general experience with ubuntu 14.04"
date: 2014-06-30
forum: General Help
---

### Post by jan-bol on 2014-06-30
Hi everyone,

I'm seeking general support/experience in relation to Ubuntu 14.04. I'm experiencing so many problems that I'm not sure if Ubuntu is going to work for me.

Before I was using 10.04 and although I had to tweak a few things the system was very solid. I had occasional crashes as I remember mostly in Gimp and caused by working on large files, but all in all it was very acceptable. It was a paradise compared to my virus/disk-clean-up/system-getting-slower-and-slower windows experience

I tried to upgrade to 12.04 but got stuck mainly because of nvidia driver issues. Recently I upgraded to 14.04. I had similar issues again, but after installing the correct Nvidia driver I got it all working again, that is to say, initially.

Right now I am experiencing:
- X freezes (see my post [here]("http://ubuntuforums.org/showthread.php?t=2231397"), there I also mention my system info)
- Loss of audio
- Card reader is not working
- Blender is chocking up very quickly after start up even with the start up file.
- Gimp (2.8) crashes when I try to implement text in an image (when I try to change the font) NB: this is working fine in Gimp 2.8 on a windows box
- Error messages when printing although I can print. It is not a problem as such but I feel something is lurking here too

I am starting to wonder if I still should see Ubuntu as a mature OS. It was because of tons of frustrations about windows that I was in the beginning very happy Ubuntu user, but this is changing now. 

Unlike many of you in here I am not a system developer or something like that. I just see my self as an average user. As such I can tweak a thing or two, but to spend days googling around and trying fix after fix is not an option for me also b/c I am self-employed and can't afford spending so much time on simply getting my OS up and running.

So what would be the way to go?
1. getting another linux distro? But then which distro would work fine on my box? (and I am not in a position to try each and every single distro)
2. buying windows and swallow my windows frustrations?
3. Getting a new video card as I have the impression that nvidia and Ubuntu is not a match made in heaven. But then, what video card works well with ubuntu and other issues are likely to remain.

I would be happy if I could get Ubuntu running fine again, but my frustrations are getting to such a point that I tend towards option 2.

On the other hand, I don't want to give up on linux/ubuntu yet. Contrary to what I call the arrogant windows-approach I still very much like the Ubuntu concept. So if anyone could get me back on track again I would really appreciate it!!

---

### Post by Bucky Ball on 2014-06-30
What are the specs of your machine? Make, model, amount of RAM and CPU, please.

---

### Post by pauljwells on 2014-06-30
I never upgrade. ALWAYS do a clean install. Before you jump out of this frying pan I'd STRONGLY recommend backing up your data and doing a clean install from scratch. Make a note of your installed apps, settings etc beforehand but take the time to set everything up again. It's good to do once in a while in any case just in case you have to recover from a drive failure one day and have to do it under pressure. I've been on Ubuntu since 5.04 and I've never had an upgrade work as well as a fresh install.

---

### Post by jan-bol on 2014-06-30
Bucky,

It's a Medion MD 8822, 
CPU: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz.
RAM 3 GB
Video card: GeForce 7650 GS

I attached lshw.txt for more info. 

PaulJwelss,

I did not express myself correctly. I did do a clean install. Downloaded image (Ubuntu 14.04 LTS "Trusty Tahr" - Release i386). did a checksum check, burned to dvd and did a complete install. And yes, having learned from earlier attempts, besides backups I made notes of all the important settings and so on.

---

### Post by Bucky Ball on 2014-06-30
Perhaps you should try the 64bit version as that is a 64bit processor ...

---

### Post by jan-bol on 2014-07-01
Oops... I did not read well the instructions on the download page and misinterpreted it. Interpretting "If you have a non-64-bit processor made by AMD" as "If you don't have a 64-bit processor made by AMD..." A silly mistake.. :( 

Okay I guess I have to go through the procedure once again....

Thanks for your reply!

---

### Post by Bucky Ball on 2014-07-01
AMD64 for AMD and Intel 64bit processors. i386 same for 32bit processors. ;)

By the number of issues you have there appears to be something seriously amiss and a reinstall might be a good idea anyway. Did you check the install disk for defects before proceeding with the install or check the md5sum of the ISO?

You're better tackling the issues one by one in separate threads with descriptive thread titles if you are still getting grief after an install of the 64bit OS. The 64bit might make no difference, but perhaps worth a try. :-k

Good luck.

---

### Post by jan-bol on 2014-07-01
Thanks!!

---

### Post by Bucky Ball on 2014-07-01
BTW: Have you looked in Additional Drivers? I'm on xfce4, but Applications>Settings>Software & Updates>Additional Drivers.

Also, when you boot to the grub menu, choose the kernel you are going to use, hit 'e' to edit, find the line ending in 'quiet splash' and add 'nomodeset'. The end of the line should look like:

> quiet splash nomodeset

Instructions to save and continue are at the bottom of the screen (F10 or Control+X I think). Any luck?

---

### Post by jan-bol on 2014-07-11
hi guys

This weekend I decided it was time to perform a fresh 64 bits install. The install does not work. I get either a screen with black and white bars or a screwed up, upside down version of my normal desktop screen. 

So I started checking a few things and found out that after all i do have a 64 bits 14.04. When i run uname -a i get: 
> 
Linux Jan-Desktop 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

So, I feel a bit silly but I seem to have the right version after all. (It's some two months ago and a I fiddled around with different versions/downloads). I assume I won't get the above system info in case of 32 bits 14.04 wrongly installed on a 64 bits machine...

So the good news is I don't need to do a new install. The bad news is, my above mentioned problems are still there and aggravating (amongst others: when I export png's from Inkscape the files dont show up in nautilus)

@ Bucky Ball: I did not notice your post earlier. xfce4 is not so much a different video driver but a different distro, isn't it? That might be an option, but I would like to try to get 14.04 running before trying other distro's. The "quiet splash nomodeset" suggestion looks more like the first step to take. I'll look into that tomorrow.

---

### Post by linux_dream on 2014-07-12
I have a very similar desktop pc (Intel E6300 at 1.86 Ghz, 3 Gb of RAM. GPU: Nvidia 7300 GS). I deleted my Ubuntu 12.04 partition and did a clean and fresh install of Ubuntu 14.04 but I simply had lots of "graphical problems", posted in this forum as well as the one in French if I remember well. Nothing worked for me, it was so much trouble that I ended up choosing Lubuntu 14.04. I do not regret to have switched to Lubuntu. As you probably know, both OS are very similar and the differences lie in the desktop environement and the default programs.  So I suggest you to try Lubuntu and/or Xubuntu and/or Kubuntu with a usb flash drive. If you like one of them, why not install it instead of Ubuntu.

---

### Post by jan-bol on 2014-07-13
Yesterday I changed quiet splash to nomodeset. Today I have been working again and after some 1.5 hrs X froze again.

Here is what I did:
- Opened the kernel to edit from grub menu it showed: quiet splash $vt_handoff. Changed it into quiet splash nomodeset.
- I found out that those changes are only effective for one boot, so I changed the /etc/default/grub file.
- /etc/default/grub showed initially: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
- Changed it into GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
- Checked the kernel settings again at boot and they showed "quiet splash $vt_handoff nomodeset" (or "quiet splash nomodeset $vt_handoff"; I dont remember the order)

So this change did not solve the X freeze. Question is if the $vt_handoff should be there or not. As far as I understand it only effects the display during boot. Or is there a relation with X also after booting?

---

