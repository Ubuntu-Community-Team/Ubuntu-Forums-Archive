---
title: "Lenovo IdeaPad 100S-11IBY Notebook Hardware Issues and how to resolve them?"
date: 2016-11-15
forum: General Help
---

### Post by zachg2 on 2016-11-15
I consider buying a Lenovo100s for some lite programming goodness 
[I]
!UPDATE #2[/I]
**Already bought It!**

I've done a title bit of research because of the unusual hardware and I found this Info:

-This particular laptop has the same chipset as Asus X205TA, Intel's Computer On A Stick (Intel Atom(TM) CPU Z3735F) e.t.c.

-This Laptop has the same issue as Asus X205TA: You need to modifly
a 32bit Ubuntu Image with Debian UEFI x86 32 bit Support (even though CPU is 64 bit)

-Sound/Wifi/Power management won't work 

So my question is: As this notebook has the same chipset as Asus
X205TA will drivers specific for these one work with this laptop or I should wait until someone creates a driver for it ? 

Has anyone successfully resolve these issues?

Some userfull threads:

<http://askubuntu.com/questions/684041/ubuntu-debian-on-a-lenovo-ideapad-100s-linux-has-issues-with-this-laptop>

<http://askubuntu.com/questions/746156/hardware-problems-running-ubuntu-on-lenovo-100s-ideapad>

Asus X205TA On Ubuntu Forums:

<https://ubuntuforums.org/showthread.php?t=2254322>

**I have clarify some info for users unfamiliar with this hardware   **

This Laptops motherboard is SOC based (System On A Chip) 
(Atom(TM) CPU Z3735F) 

So (as I saw on a teardown video) its motherboard is tiny with intergraded ram/eMMc memory 

An external wifi card may work, but is flaky; times out
UPDATE #1 

Hi again,

I've found these custom Ubuntu Builds for Bay/Cherry Trail Devices <http://linuxiumcomau.blogspot.com/>

Everything works fine except sound

Any Idea how to make this work?

---

### Post by jami128 on 2016-11-20
I also have this same exact laptop and I'm interested in hearing on how to get the sound working. The only work around I've heard is to use a USB sound card, I guess any USB sound output device would work, but this is not optimal for me as I'm looking for a system that works well without any extra devices connected.

Does anyone know if there are drivers for the Intel Bay Trail integrated sound chip found in this laptop?

Also, does anyone know what kind of patches or changes does the 4.9 Linux kernel bring for Bay Trail and Cherry Trail processor computers?

---

### Post by zachg2 on 2016-11-21
Unfortunately drivers for realtek sound card are proprietary and custom firmware is needed for the device to work. Untill Realtek release this firmware we are doomed

---

### Post by jami128 on 2016-11-21
I'm not sure if the sound card is Realtek. The wifi is from Realtek but the sound seems to be from Intel. I've also heard about people getting the sound to work with newer Linux kernels (4.5 and up) with right Alsa files and configurations.

Solus is going to release a new ISO image soon with Kernel 4.8 and support for sound for some Baytrail processors. If this processor (Z3735F) is supported by that distro then it would be great. The only thing missing would be just about everything else though, including wifi and the option to boot in 32 bit EFI.

Minix, a computer manufacturer from Hong Kong, is also developing a customized version of Ubuntu for their Cherrytrail and Baytrail systems. When and if it gets released, it would be very close to a perfectly functional Linux OS for this computer because of the very similar hardware specs. The only real difference is that their computers are not laptops so the battery indicator might not work out of the box.

Also, a Debian-based distro called SparkyLinux is able to boot in 32 bit EFI. I tried it and it booted out of the box but without wifi or sound. A new version of SparkyLinux is going to be released on 20th of December and it will have a newer kernel in it. With a newer kernel and out-of-the-box support for 32 bit EFI it would be easier to modify that distro to work well with this laptop.

I've heard of the freeze problem present in some Baytrail processors, including this one, being fixed in the 4.9 kernel. Maybe there are some other fixes for this particular Baytrail processor as well when the kernel get officially released.

Links:

[https://solus-project.com/2016/11/15/this-week-in-solus-install-39/](https://solus-project.com/2016/11/15/this-week-in-solus-install-39/)

[http://www.minixforum.com/threads/libreelec.14022/](http://www.minixforum.com/threads/libreelec.14022/)

[http://sparkylinux.org/about/](http://sparkylinux.org/about/)

[http://www.phoronix.com/scan.php?page=article&item=linux-49-features&num=1](http://www.phoronix.com/scan.php?page=article&item=linux-49-features&num=1)


By the way, feel free to post anything you find about this topic on this thread. Any comments and information from other people are also welcome.

---

### Post by zachg2 on 2016-11-21
@[**[COLOR=#000000]jami128[/COLOR]**]("https://ubuntuforums.org/member.php?u=2050696") There are two device drivers on Windows 
Also linuxium kernel works great no custom work is required for it to boot
[IMG]http://i.imgur.com/l98lSa4.jpg[/IMG]

---

### Post by jami128 on 2016-11-21
I know that the Linuxium version boots without problems. I have tried it myself and everything worked great except for the sound. I was referring to other distros because they might get the sound working before the Linuxium version gets adapted to laptops.

I've also heard that it's possible to get the sound working with the 4.9 kernel although I have no confirmation for that so it's just rumors so far. If it's true, however, we can expect a distro with working sound soon. Even with a distro with working sound some tweaking has to be done in order to get it working on this model of a laptop.

Alternatively, we can wait for Linuxium to update his version of Ubuntu to 4.9 kernel which he may or may not be interested in doing.


Edit: I tried it again today and bluetooth also didn't work with the Linuxium version.

---

### Post by zachg2 on 2016-11-24
@[**[COLOR=#000000]jami128[/COLOR]**]("https://ubuntuforums.org/member.php?u=2050696") It seems Realtek & Intel Sound Integration on Linux  is more complicated than it sounds 
[https://bugzilla.kernel.org/show_bug.cgi?id=95681](https://bugzilla.kernel.org/show_bug.cgi?id=95681)

---

### Post by jami128 on 2016-11-25
It seems that this laptop uses byt-rt5640 firmware from Intel. There are people reporting that they have got sound working by using the correct firmware that has been available for a while now. It might be that the firmware doesn't work with newer kernels though.

[https://ubuntuforums.org/showthread.php?t=2254631](https://ubuntuforums.org/showthread.php?t=2254631)

Have you tried this trick?


Edit: I also found this post about getting the sound working on newer kernel versions

[https://bugzilla.kernel.org/show_bug.cgi?id=187331](https://bugzilla.kernel.org/show_bug.cgi?id=187331)


Edit2: I also found this post on how to make the sound work on this particular laptop with 4.9 kernel

[https://bugzilla.kernel.org/show_bug.cgi?id=113181](https://bugzilla.kernel.org/show_bug.cgi?id=113181)

---

### Post by zachg2 on 2016-11-28
[**[COLOR=#000000][/COLOR]**[COLOR=#000000]@[URL="https://ubuntuforums.org/member.php?u=2050696"]**[COLOR=#000000]jami128 [/COLOR]**]("https://ubuntuforums.org/member.php?u=2050696")[/COLOR][/URL]
Thanks for the Info I didnt know this laptop uses a different sound card &there are people working on a sound driver 
Anyway ,
Is there any proper way to  install ubuntu on this laptop?
Or I Should  wait untill the new kernel is release to fix things up?

---

### Post by jami128 on 2016-11-28
The third link I posted clearly describes on how to make the sound working on this particular laptop. People have already managed to get it working so it's possible to patch your own kernel to make it work.

I'm afraid that even the new kernel won't completely fix all the problems. It will, however, get us closer to an out-of-the-box fully functional system. After the kernel gets released there will be more people trying to make Linux work on Bay Trail laptops.

My current plan is to wait until the kernel gets released and then read what other people say about the new kernel on Bay Trail devices. I have no experience whatsoever in kernel patching but if all you need is drivers to make it work then it should be easy for me to get it right.

---

### Post by zachg2 on 2016-12-08
@[**[COLOR=#000000]jami128 [/COLOR]**]("https://ubuntuforums.org/member.php?u=2050696")
Linuxium updated to support [COLOR=#1D2129][FONT=&amp]RT5640 headphone audio![/FONT][/COLOR]
**[http://linuxiumcomau.blogspot.com/2016/10/running-ubuntu-on-intel-bay-trail-and.html](http://linuxiumcomau.blogspot.com/2016/10/running-ubuntu-on-intel-bay-trail-and.html)**

---

### Post by jami128 on 2016-12-08
Yeah, I just read about it! He also provides a patched version of 4.9 kernel!

I think the best way is to install the patched 4.9 kernel first by downloading it, opening terminal in the downloads folder and typing "sudo bash ./[linuxium-install-zesty-kernel-4.9.0-8-linuxium.sh]("https://docs.google.com/open?id=0B99O3A0dDe67b1pmc3M0R0VFcmc")". After that, just reboot and then install the UMC files provided by Pierre Blossart with the instructions given by Linuxium.

I don't know if patching works on usb stick so I guess it would be better to install either the 16.04 or 16.10 Linuxium version of any of the Ubuntu flavors before starting the patching work. I'm not sure if I will try it out yet because I really need a functional laptop for now and I don't want to take any risk bricking my laptop just yet. 

If you're going to test this out any time soon be sure to tell me how it went down! Also, tell me if there was any complications regarding patching or installing of the Linuxium-patched distros.

---

### Post by jami128 on 2016-12-16
Linuxium has released a patched alpha build of Ubuntu with the audio patch applied. I tested it today and both sound (tested with PC speakers and headphones) and WiFI work out of the box. The WiFi doesn't seem to be able to connect with n-standard though so configure your router to use "automatic" or legacy standard. Also, my laptop froze when I was watching a video on YouTube but this could be because I was trying it from a live USB stick and my memory usage exceeded the 2 GB RAM this model of laptop has.

---

### Post by jesudia on 2017-02-08
i have also Lenovo ideapad 100s-11iby and i am try see youtube or videos mp4 and is not posible, wifi yes with zesty-lubuntu-desktop-alpha-2-linuxium, can you help me please, thank you.

---

### Post by zachg2 on 2017-03-09
@[[COLOR=#000000]jesudia[/COLOR]]("https://ubuntuforums.org/member.php?u=2058330")[COLOR=#000000] 
Linuxium dev has a fix if the os statters

[/COLOR]

---

### Post by jami128 on 2017-03-09
I also had this same issue but I resolved it by turning the other sound card off in the sound settings. It seems like Linuxium has kept the audio patch in his iso while the sound support for this laptop has already been included in the 4.10 kernel so that's why there's seemingly two sound card drivers in the sound settings.

---

### Post by jesudia on 2017-03-12
i have lenovo 100s 11iby and i have not sound with linuxium , can you tell me please ,help

---

### Post by zachg2 on 2017-04-30
Hi, sorry for replying that late I havent log in in ages

I didnt had this issue with linuxium ubuntu but other versions had this issue.
It seems like an audio wizard bug (ubuntu use alsa audio I think)
I'm using windows 10 because linux on this machine now seems buggy 
I would suggest waiting for 18.04 as it is said to have proper atom cpu support

---

