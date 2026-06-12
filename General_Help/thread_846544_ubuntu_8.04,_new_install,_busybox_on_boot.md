---
title: "ubuntu 8.04, new install, busybox on boot"
date: 2008-07-01
forum: General Help
---

### Post by DJYoshaBYD on 2008-07-01
ok.. I have had ubuntu 8.04 lts on my pc since the first day.. it installed just fine, and has been running fine.. I recently downloaded Mythbuntu, burned the iso, and tried to install it on the same computer, but with a different hard drive.. the install went fine, then I rebooted, and it takes forever to get past the ubuntu logo, then it goes to a command prompt for busybox (whatever that is), from which there is no escape.. 

then I tried my ubuntu 8.04 lts version (the same one that used for the same computer), and it did the same thing.. so I tried a new HD, did the same thing.. 

My pc hardware has all been replaced, except for the motherboard and CPU.. those are fine, because Im not having any other issues..

why would it boot straight into busybox, when it worked fine before?

---

### Post by DJYoshaBYD on 2008-07-01
I just did some searching, and everyone is saying to change the drive type from IDE to raid.. but the thing is, Im not using a sata hard drive, and I wasnt when I first installed using the same CD.. it worked on the same computer, and now I cannot get past this.. could it be some sort of hardware issue? Im assuming it would be in the bios, but what else should I check?

---

### Post by avtolle on 2008-07-01
Take a look at this [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) and see if there's anything there which will help you.

---

### Post by DJYoshaBYD on 2008-07-01
it was the same machine, and I didnt have to do that before.. its the same disk, and I have tried it on 2 different hard drives... that is what is so odd... what am I looking for on here?

again.. all the solutions have said to check the bios to make sure its set to raid.. would this work for an IDE drive as well? like I said, its just so odd that the same CD that I used doesnt work now... I did reset my BIOS recently, but I have never really messed with it...

---

### Post by avtolle on 2008-07-01
Have you updated your 8.04 installation by downloading the updates? If so, there could be an issue with the newer kernel, for example.

You are looking for, in the link, a series of things to try from the boot line. Try them one at a time, then in combination, to see if you can get booted. Again, this is just a thought; and may not help. BTW, try as a boot option all_generic_ide and see if that gives you any joy.

---

### Post by DJYoshaBYD on 2008-07-01
like I said, I didnt have to do it before.. its a clean install, formatted HD.. I tried it on 2 separate drives.. there is no kernal except for the one on the CD that gets installed, and that worked just fine before.. I have the ubuntu 8.04 lts cd, and it worked when I got a week or more ago, now it doesnt.. mythbuntu does the same thing..

it is impossible, if I am formatting the drive, for it to be anything software related... its the same disk I have been using, now it wont work...

what should I look for in the bios settings?

---

### Post by Famicommander on 2008-07-01
Adding the option all_generic_ide solved this problem for me when I had it.

---

### Post by DJYoshaBYD on 2008-07-01
do I just do that at the beginning when I am getting ready to install it?

What could have changed on my system to cause that?

---

### Post by DJYoshaBYD on 2008-07-01
just to be clear, it boots fine to the livecd, and installs perfect.. its just on restart it does this.. do i still put that boot option at the beginning before install?

and, again, what could I have changed in my bios that would stop this install from booting, then I plug in my other HD (thats already functioning fine) and its kosher?

are the boot options specifically for the install, or just for the time that the computer is running after selecting that?

---

### Post by avtolle on 2008-07-01
OK, if it installs fine, then it is on the restart. The link speaks to this as well. Need some clarification, however; does it boot with the other HD plugged in? This suggests to me there may be a problem with grub, or in your fstab file, rather than the need for a boot parameter.

---

### Post by Spaceman9 on 2008-07-01
I had this Busy Box problem with Linux Mint 5 when I installed it on my second drive. Installing it by it's self on my boot drive solved the problem.

I had the same problem with Ubuntu 8.04 installing it to my second drive. Never had the problem with Ubuntu 8.04 on my boot drive though. Now I just have Ubuntu 8.04 on my boot drive.

---

### Post by DJYoshaBYD on 2008-07-01
it does it on a new install, with any HD I try.. installs fine, then boots to busybox.. 

like I have said.. I used this SAME cd on my main hd before and it worked fine.. same computer.. as a matter of fact, I tested this CD out on the same test drives before I committed to it.. it was flawless..

the only thing that would be different would be me resetting the BIOS.. but I just cannot imagine anything..

WAIT!! When I tried it out, it was dual booted.. would that make a difference? ANY time I have tried it and had it work before, it was dual booted.. 

Now I just want it installed by itself...

so yeah... what can I do to make it go away.. lol.. like I said, no sata.. just IDE.. all system hardware is good.. it has to be the way I am installing it, but I have been installing linux distros almost every day for people, and this is the first issue I had..

so, yeah.. how do I make it go past that damn busybox? haha

The main goal for this machine right now is to get mythbuntu 8.04 on there.. so it will be the only OS on the system... it just wont pass busybox:(

---

### Post by DJYoshaBYD on 2008-07-01
again.. I have stated that its the only drive in the system.. 1 IDE drive.. and I have tried a few... its not the HD or where the HD is.. its the IDE Master, and the only device on that bus..

it has to be the way im installing it.. but I just followed all the same exact steps I did when I first installed it.. now it does this.. any other suggestions for killing this busybox thing?

---

### Post by DJYoshaBYD on 2008-07-02
HAHA!!! I figured this one out

really odd, and I have never had this happen with an OS..

single drive on IDE ribbon should be set at cable select and at the end of the ribbon..

I have never had this happen before.. odd.. but yeah.. that fixed it right up.. and Mythbuntu 8.04 is the shi+.. get it..

---

### Post by danwood76 on 2008-07-02
To be honest its better to choose the drives master and slave manually.

What was happening when it dropped to the busybox shell is that it couldnt find the kernel to load and only the initramfs loaded.

This is probably due to a bad line in your menu.lst as the drive order may get messed around by your second HD.
It could also be caused by an incorrect initramfs which could have been solved by updating it.

---

### Post by DJYoshaBYD on 2008-07-02
ummm.. yeah.. like I said before.. it was one drive, set for master, on the IDE.. no second drive.. it was a new install with the same CD that I had used before and it was fine.. you gotta read the whole thread before posting.. rule of thumb in any forum[-X..

And I know how to install drives.. set as master, it wouldnt pick up the drive.. then I set it to cable select and it was fine..

---

### Post by franklinbeezy on 2008-09-28
> **famicommander said:**
> adding the option all_generic_ide solved this problem for me when i had it.
perfect!!!

---

