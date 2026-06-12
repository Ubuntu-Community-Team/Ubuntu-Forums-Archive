---
title: "Best version of Ubuntu for an HP dv8130us w/ amd turion 64 mobile ml-40"
date: 2015-02-24
forum: General Help
---

### Post by wisesilver on 2015-02-24
Hello, I have an older laptop and want to find the best version of Umbuntu to install on it.  It is an HP dv8130us w/ AMD Turion 64 mobile ml-40 CPU.  Does it matter which version of Umbuntu I install?

Thank you,

Steve

---

### Post by MartyBuntu on 2015-02-24
I would go for a lighter desktop environment like XFCE or MATE...

---

### Post by mörgæs on 2015-02-24
Some of the 8130's had very little memory. If that's the case for yours I recommend a 32 bit Buntu even though you have a 64 bit processor.

Agree, a light desktop environment is necessary.

---

### Post by blue_fox on 2015-02-25
I'm using a HP dv5000 but with an** intel** core duo, 32-bit, 1.8GHz, 2GB ram and nvidia geforce go 7400 with ubuntu 14.04 and the unity desktop. Works fine, but slow if the nvidia drivers aren't used. I experimented with lubuntu and xubuntu desktops but now I prefer the simple LXDE as a second desktop for 'heavy computing'.
Best,
Arne

---

### Post by wisesilver on 2015-02-25
I reinstalled Umbuntu 14.04 last night.  The previous install worked OK but I was having problems getting my Asus N10 wireless adapter to work (and still am). And since my WiFi icon vanished, in the upper menu bar on the right, and because I thought there was a bug from a "bad" email I decided to reinstall.  Some googling suggested a "flavor" of Umbuntu for an AMD CPU.  Just incase I should install a lighter version does anyone have a link for me to download it?  At first I'm thinking I may want spend a little more time trying to 14.04 to work but plan "B" may be to move to the lighter version.

With Umbuntu 14.04 I'm experiencing the following problems.  First it just hangs when I shut down (the previous install did not do this) and second I cannot get my Asus N10 wireless USB adapter to work.  My Asus N13 works fine but not the N10.  I do not broadcast my SSID.  So I configure my wireless access with security and password.  The N13 works fine but the although the N10 recognizes the wireless access points it requires I reenter my password (which I enter correctly) and then does not connect and continues to request my password.

Thoughts/Suggestions? :)

Thank you,

Steve

---

### Post by mörgæs on 2015-02-25
There are links to Lubuntu and other distros at the top of the page.

Have you installed all updates using a wired internet connection?

And, by the way, there's no M in Ubuntu :-)

---

### Post by wisesilver on 2015-02-25
Mörgæs:

> And, by the way, there's no M in Ubuntu[INDENT]Oops - I guess you can tell I'm a noobe! :)
[/INDENT]

> Have you installed all updates using a wired internet connection?[INDENT]I do have an Ethernet cable connected to the laptop and to my home router.  I search on updates and selected the object for updates that presented itself.  I then ran the update which required a reboot.  Only the reboot did not fully shut down.  There was quite a bit of text that I did not capture so I am unable to share it.](*,)

[/INDENT]
> There are links to Lubuntu and other distros at the top of the page.[INDENT]Oh, under Ubuntu Community.:p[/INDENT]


I've noticed your links _**About problems due to upgrading **_and **_old hardware_**.  In the **_Old hardware_** link there are a number of commands that look to be a good idea.  For instance this is a 2006 computer running Windows XP 32 bit.  So I really wonder if it is a 64 bit processor.  I was thinking that AMD just happened to have 64 as part of its description.

---

### Post by mörgæs on 2015-02-25
> **wisesilver said:**
> I was thinking that AMD just happened to have 64 as part of its description.

I don't think so.
The text explains how you find out for sure if it's a 64 bit or not. 

Windows is often the last operative system to catch up with a trend. Moving to 64 bit is a good example.

---

### Post by wisesilver on 2015-02-27
Mörgæs:

I've run the following commands and here they are with the results:

> [COLOR=#ff0000]**sudo lshw -C cpu | grep -i sse2 **[/COLOR]
[sudo] password for steve-n-linda: 
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl pni lahf_lm vmmcall cpufreq


> **[COLOR=#ff0000]sudo lshw -C cpu | grep -i width [/COLOR]**
       width: 64 bits
[INDENT]Wow - I really didn't realize they made any 64 bit processors in 2006! :)[/INDENT]


> [COLOR=#ff0000]**sudo lshw -short -C memory | grep -i system **[/COLOR]
/0/c                         memory         2GiB System Memory 


> **[COLOR=#ff0000]sudo lshw -short -C memory | grep -i empty [/COLOR]**


So, I'm wondering if this provides enough information to determine if I should stick with Ubuntu 14.04 or switch to one of the lighter versions?  Since I posted last I reimaged again, last night, and ran the updater.  Then looked for drivers - I loaded a wireless driver.  The performance appears to be acceptable.  But again it won't fully shut down.  I gets further to a totally blank screen but the power does not shut off.  

So my issues/questions boil down to three items:
1) Is the version of Ubuntu appropriate for my hardware?
2) How can I get it to fully shut down?
3) Can I get the Asus N10 wireless adapter to work?


Thank you,

Steve

---

### Post by mörgæs on 2015-02-27
1) Your decision. If you are happy with the speed then everything is good.
2) Does it help pushing enter while it's hanging half shut down?
3) Only advice I can give is [this guide]("http://ubuntuforums.org/showthread.php?t=370108"). I don't have much experience here.

---

### Post by pmi2 on 2015-02-27
You can compare the performance of your CPU using published benchmarks, that would give you some idea where you stand.  

For example:

[http://www.cpubenchmark.net/cpu.php?cpu=AMD+Turion+64+Mobile+ML-40](http://www.cpubenchmark.net/cpu.php?cpu=AMD+Turion+64+Mobile+ML-40)

Most people would probably go for one of the lighter versions of whichever distro you like for this CPU.

---

### Post by mörgæs on 2015-02-27
The CPU is not always the bottleneck. Often it's the graphics processor, especially for a desktop high on eyecandy like Ubuntu and Kubuntu.

---

### Post by wisesilver on 2015-02-27
[[IMG]http://ubuntuforums.org/customavatars/avatar704369_2.gif[/IMG]											 ]("http://ubuntuforums.org/member.php?u=704369")								 [**[COLOR=#000000]MartyBuntu[/COLOR]**]("http://ubuntuforums.org/member.php?u=704369"):

I see a link for Xubuntu (and Lubuntu) but not Mate above.  Can you recommend a safe site to download Mate?  If I cannot solve my shutdown problem I may try one of these three choices.  Probably 32 bit as recommended above even though I have a 64 bit laptop.

Thank you,

Steve

---

### Post by pmi2 on 2015-02-27
> **wisesilver said:**
> [[IMG]http://ubuntuforums.org/customavatars/avatar704369_2.gif[/IMG]                                             ]("http://ubuntuforums.org/member.php?u=704369")                                 [**[COLOR=#000000]MartyBuntu[/COLOR]**]("http://ubuntuforums.org/member.php?u=704369"):

...If I cannot solve my shutdown problem I may try one of these three choices. ...

[http://linuxmint.com/](http://linuxmint.com/)

Mate is part of another branch of the Linux family, Linux Mint, so that is why there is no link on this page.  The download link can be found on the Linux Mint home page.  There is a lot of good basic information on the various families of Linux, and different distributions of the OS on Wikipedia.  Not very technical, but a good place to do some quick reading.

Frankly, it does not seem that your shutdown problem is related to which  Linux you choose to run, so it would be a shame to avoid one or the  other for that reason.

Most of the major distributions of Linux have excellent  graphical user interfaces now, but the graphics and processor  requirements for good operation do set them apart.  The "minimum"  requirements are just a guide, so typically yoou need more than that for  good operation, and laptops are harder to upgrade than the typical  desktop.  Try a couple, they can coexist on one hard disk just fine with  a dual boot.

---

### Post by mörgæs on 2015-02-28
> **wisesilver said:**
> Probably 32 bit as recommended above even though I have a 64 bit laptop.


I mentioned 32 bit as a safe approach for the case that you were low on memory. With 2 GB a 64 bit ISO will do fine.

---

### Post by wisesilver on 2015-02-28
Thank you all for assisting me in my start in the Ubuntu world! :p I created 32 and 64 bit install disks from ISOs for Xubuntu and Lubuntu so I would have them all ready for experimenting.  I installed 64 bit Xubuntu.  It shuts down completely and quickely! \\:D/:biggrin: I will file the Linux Mint link and CPU benchmark links away for future reference.:cool:  My N10 wireless adapter recognizes all the SSIDs in its local but, I cannot connect to mine even with a correct password. :!::evil: I think I will review the link Mörgæs provided for attempting to resolve the wireless issue with the N10 adapter (there is also the original wireless adapter that came with the laptop which doesn't work).  The N13 adapter works fine so I'm not out of luck, I just want the cuter smaller N10 adapter to work.:lolflag:

Thank you! :D

---

### Post by mörgæs on 2015-02-28
You're welcome. Please mark the thread 'solved'

---

