---
title: "Make Ubuntu use a minimum of RAM"
date: 2013-03-25
forum: General Help
---

### Post by GameX2 on 2013-03-25
Hi,

I've done a few tests about running Adobe AfterEffects / Premiere CS6 in a Windows 7 virtual machine, in Ubuntu.  Along with 3DS Max, these are the only software I have problems with (They force me to reboot into Windows..); I've managed to make all the others Adobe products work under Wine, but these are 64-bit and perhaps too complex for Wine (For now).  Running them into a virtual machine would also use way too much memory to be usable.

But I've been wondering about this problem; I have a machine with 8GB of RAM.  Assuming I want to avoid rebooting into my real Windows 7 OS, how much can I limit the RAM of Ubuntu, so that I'll be able to allow more RAM to the Windows 7 VM ?
I'm running Ubuntu 12.04 LTS x64 with Unity (Yes, it use a lot of memory.  I want to keep it.).  I've tried stopping a few processes, and replacing for a session Compiz by Metacity with this:

```
metacity --display:=0 --replace
```
It work.  Compiz use 80MB of RAM, while Metacity, only 5MB.  By stopping a few processes, I've managed to lower the memory used by Ubuntu alone to 11% of 8GB (Well, 7,7).  Just wondering, is it safe to disable "Unity-Panel" process ?
By replacing Compiz by Metacity, I don't have the Unity dash, but I can create an empty folder of the desktop, and launch Linux applications by going to /usr/share/applications, that's ok.

I've also optimized my Windows 7 VM, and use an excellent software that I've had a great experience with, GameBooster, used to stop system process during gaming/intense activity.

How can I free more RAM in Ubuntu, so that I can allow more to Windows 7 ?  I've now allowed 4,5GB to the VM, but I was at 73% used, I could put some more.  4,5GB is very low to use AfterEffect, even at low display quality.

Would Lubuntu x64 be more efficient?  That's not a so awesome solution, because installing another OS takes up space, and I have a (small) 320GB hard drive, with already 3 OS installed (Ubuntu, Windows 7, and Windows 2000, a small partition, for testing).  How much RAM would I benefit by running Lubuntu?  Maybe running it off a ISO file (Booted from GRUB) do it?  Is it slower (Not from a USB stick.  Adding an entry to the ISO from GRUB menu) ?  Of course, I should be able to auto-install VirtualBox in the ISO file, not sure how.. :S

Any availible option?  Can I stop more processes to make Ubuntu more "transparent" ?

Thanks!

---

### Post by CatKiller on 2013-03-26
Linux will efficiently use as much RAM as you can throw at it. Empty RAM is wasted RAM. My advice would be to up the RAM available to your VM until you have enough in there to run what you need to. If that doesn't leave you enough to run the host OS, put more in. Running lighter stuff will help a little, but not that much. Randomly stopping processes is not a good plan.

---

### Post by The Cog on 2013-03-26
See the bottom of this page: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
Your free (for applications to use) memory figure is the one after the "buffers/cache:" heading.
I think you could probably give 7G to your VM.

---

### Post by tartalo on 2013-03-26
> **GameX2 said:**
> Would Lubuntu x64 be more efficient?  (...)  How much RAM would I benefit by running Lubuntu?

[http://mylinuxexplore.blogspot.com.es/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html](http://mylinuxexplore.blogspot.com.es/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html)

---

### Post by GameX2 on 2013-03-26
Thanks for all the replies!

> My advice would be to up the RAM available to your VM until you have  enough in there to run what you need to. If that doesn't leave you  enough to run the host OS, put more in. Running lighter stuff will help a  little, but not that much. Randomly stopping processes is not a good  plan.
My issue is that I can hardly use Ubuntu and Windows 7 at the same time (I do not intend to, anyways); I plan on using Adobe AfterEffects / Premiere on Windows 7, and allow the most possible memory to the VM.  AfterEffect is so much "memory-hungry" that running a usable Ubuntu at the same time (It use 20% of RAM for a normal usage) will mostly cause a crash - I've allowed 6GB to the VM.  Even 6GB of RAM is considered "low" to run AfterEffects, so I can't possibly lower it more.  I need to make Ubuntu the most freed, "blank" as possible.
By replacing Compiz with Metacity, and killing a few processes I know (Such as Zeitgeist-fts; it's useful and I keep it running normally, it's just not required to run when using only AfterEffect), I managed to allow 6GB of RAM to the VM (It's very fluid), and my RAM displayed 88% used (About 700MB used by Ubuntu).  Perhaps I could allow a bit more to the VM, so I would reach 95% (Untested, yet).

I would love to put more RAM, but unfortunately, my laptop is already pushed to the max ammount of supported RAM. :(

> See the bottom of this page: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
Your free (for applications to use) memory figure is the one after the "buffers/cache:" heading.

Thank you, I understand the idea.  So the RAM is automatically borrowed from the disk cache, if it's needed by applications, that's good.  If I understand, I do not have to try anything.

> I think you could probably give 7G to your VM.
Interesting; if Ubuntu use about 700MB of RAM with a minimum number of processes, and that 7.7GB is shown as usable (By the systeme monitor), that should be quite limit.  I was a 88% of my total RAM with a VM running using 6GB.  I guess I could allow 6,5GB just fine, I'll check about 7GB (Assuming VirtualBox allow that).  I could also try to choose the Classic GNOME Desktop (Gnome-Session-Fallback.  Not sure if that will help, but even when Unity with Metacity, barely nothing is shown on the Desktop.  A single folder, which allow me to navigate to /usr/share/applications).

I'll check the "free" command today, thanks.

> [http://mylinuxexplore.blogspot.com.e...s-kubuntu.html]("http://mylinuxexplore.blogspot.com.es/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html")
Very interesting, thanks for this comparison.  Is it slower to run a Lubuntu ISO, booted from the GRUB menu, rather than a full install?

EDIT: Done a quick test.  Using Gnome Classic save a LOT a memory, and it come with Metacity by default.  Stopping a few processes allowed me to lower the used memory to 5.5 - 6,5% by Ubuntu.  I've pushed the max, which allow give me 6,75GB of memory to Windows 7 (Still fluid).  Well, that's an exteme amount of memory used, but it's still fluid.
My whole RAM reache 97.3% (Wow), but the system is still stable (Was not expecting that.)

Look good.  I'll try AfterEffects that way! :)

EDIT: I know I want to free to much RAM, maybe, but can I prevent Gnome-Panel from restarting, when I kill the process ?

---

### Post by CatKiller on 2013-03-26
FWIW, you don't have to use only one desktop environment. When I was doing more audio work on my resource-constrained previous computer, I'd log into LXDE, but log into Gnome for everything else. There are also people that, for gaming, start an X session just for that game. It's hassle that kind of negates the advantages of using a VM in the first place, but they are options to consider if you can't get the performance you want out of that machine.

---

### Post by GameX2 on 2013-03-26
> **CatKiller said:**
> FWIW, you don't have to use only one desktop environment. When I was doing more audio work on my resource-constrained previous computer, I'd log into LXDE, but log into Gnome for everything else. There are also people that, for gaming, start an X session just for that game. It's hassle that kind of negates the advantages of using a VM in the first place, but they are options to consider if you can't get the performance you want out of that machine.

Yup, that's what I've just tried!  I've installed xfce-core and tried it (I've already tried Lubuntu before, as well as Xubuntu and Kubuntu).  I was surprised by amount of memory I was saving (it used about 500MB at the very minimum, with processes killed), but what surprised me even more was the stability.  Windows 7 was running and my RAM was at 95%.  I was surprised, because even with Windows 7 running, I was still able to use Lubuntu pretty much normally, start the file manager (I even opened Firefox.  It was sluggish, but I knew the system was not about to crash).

I've used a bit AfterEffects, it was "OK", until Windows 7 completely frozed randomly (Oddly, Windows 7 froze, and he's the one who's using all the memory.  Ubuntu with XFCE was having no fluidity problem).  Weird.
I then booted in Windows 7, and noticed AfterEffects was still much faster (Sure, nothing to be surprised about).  But well, using AfterEffects a few times with XFCE still is an option.

Oh, the only thing that I find annoying about XFCE, is that it apparently can't manage my dual-monitor well.  I have a VGA screen connected to my laptop, and when booting Ubuntu, the laptop screen turn off, as it should.  Using XFCE, I wasn't able to set the laptop display to close (And program are opening on the laptop screen, what I don't want).
I would have appreciated to push VirtualBox memory even a pinch higher, since XFCE saved a few more RAM, but apparently, VirtualBox don't want me to. :/

Thanks for the answers.  Guess that's the best ammount of performance I can get (Not *that* bad) !

EDIT: Uh, am I an idiot, or I can't find the "Marked this thread as solved" button anymore? XD It's not in the Thread Tools ?

---

### Post by CatKiller on 2013-03-27
No, that threw me too. You need to edit the first post and change the prefix.

---

### Post by The Cog on 2013-03-27
Yes, go to the **first post** in the thread, click **Edit Post**, click **Go Advanced** and change the **prefix** there. Unfortunately you lose the [ubuntu] prefix as you do it of course.

---

### Post by erind on 2013-03-27
> **GameX2 said:**
> [...]

I would love to put more RAM, but unfortunately, my laptop is already pushed to the max ammount of supported RAM. :(

[...]


Maybe a bit unrelated to your specific case - If you're referring to the max RAM size as per the laptop's *official manual*, then chances are that your laptop might actually support more RAM than what's written on the book (assuming mb has the latest BIOS). The probable reason is that the vendors make the hardware/BIOS to support the largest possible RAM capacity, but *test ( and advertise ) only the largest commercially available dimm size at that point in time*.
In my case the laptop's manual says it supports up to 4 GB of RAM, but using '*dmidecode*' command I see that it can go up to 8 GB. And my PC officially supports 4GB, but it can go up to 16 GB of RAM, ( currently being used with 6 GB with no issues, see below ). Note the bold lines in red. 

```
$ **sudo dmidecode -t memory**
# dmidecode 2.11
SMBIOS 2.2 present.

Handle 0x0007, DMI type 5, 24 bytes
Memory Controller Information
    Error Detecting Method: 64-bit ECC
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 4096 MB
    **[COLOR=#ff0000]Maximum Total Memory Size: 16384 MB[/COLOR]**
...
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    [COLOR=#ff0000]**Maximum Capacity: 16 GB**[/COLOR]
    Error Information Handle: Not Provided
    Number Of Devices: 4
...


$ **free -m**
             total       used       free     shared    buffers     cached
Mem:          [COLOR=#ff0000]**5971  **[/COLOR]     5843        128          0        210       4457
-/+ buffers/cache:       1174       4796
Swap:         4093          0       4093

```
Just my 2 cents.

---

### Post by nonedrinkwater on 2013-03-27
> **GameX2 said:**
> Hi,

I've done a few tests about running Adobe AfterEffects / Premiere CS6 in a Windows 7 virtual machine, in Ubuntu.  Along with 3DS Max, these are the only software I have problems with (They force me to reboot into Windows..); I've managed to make all the others Adobe products work under Wine, but these are 64-bit and perhaps too complex for Wine (For now).  Running them into a virtual machine would also use way too much memory to be usable.

But I've been wondering about this problem; I have a machine with 8GB of RAM.  Assuming I want to avoid rebooting into my real Windows 7 OS, how much can I limit the RAM of Ubuntu, so that I'll be able to allow more RAM to the Windows 7 VM ?
I'm running Ubuntu 12.04 LTS x64 with Unity (Yes, it use a lot of memory.  I want to keep it.).  I've tried stopping a few processes, and replacing for a session Compiz by Metacity with this:

```
metacity --display:=0 --replace
```
It work.  Compiz use 80MB of RAM, while Metacity, only 5MB.  By stopping a few processes, I've managed to lower the memory used by Ubuntu alone to 11% of 8GB (Well, 7,7).  Just wondering, is it safe to disable "Unity-Panel" process ?
By replacing Compiz by Metacity, I don't have the Unity dash, but I can create an empty folder of the desktop, and launch Linux applications by going to /usr/share/applications, that's ok.

I've also optimized my Windows 7 VM, and use an excellent software that I've had a great experience with, GameBooster, used to stop system process during gaming/intense activity.

How can I free more RAM in Ubuntu, so that I can allow more to Windows 7 ?  I've now allowed 4,5GB to the VM, but I was at 73% used, I could put some more.  4,5GB is very low to use AfterEffect, even at low display quality.

Would Lubuntu x64 be more efficient?  That's not a so awesome solution, because installing another OS takes up space, and I have a (small) 320GB hard drive, with already 3 OS installed (Ubuntu, Windows 7, and Windows 2000, a small partition, for testing).  How much RAM would I benefit by running Lubuntu?  Maybe running it off a ISO file (Booted from GRUB) do it?  Is it slower (Not from a USB stick.  Adding an entry to the ISO from GRUB menu) ?  Of course, I should be able to auto-install VirtualBox in the ISO file, not sure how.. :S

Any availible option?  Can I stop more processes to make Ubuntu more "transparent" ?

Thanks!

i installed ubuntu on a netbook because i use ubuntu on all my other machines, but ubuntu was too slow on an atom processor, after trying several other ubuntu derivations, i installed debian using the 200mb network install, and it runs really fast, i have a dual core atom with a gig of ram and it runs extremely well; im considering installing debian and removing ubuntu on all my other machines.

---

### Post by GameX2 on 2013-03-27
> **erind said:**
> Maybe a bit unrelated to your specific case - If you're referring to the max RAM size as per the laptop's *official manual*, then chances are that your laptop might actually support more RAM than what's written on the book (assuming mb has the latest BIOS). The probable reason is that the vendors make the hardware/BIOS to support the largest possible RAM capacity, but *test ( and advertise ) only the largest commercially available dimm size at that point in time*.
In my case the laptop's manual says it supports up to 4 GB of RAM, but using '*dmidecode*' command I see that it can go up to 8 GB. And my PC officially supports 4GB, but it can go up to 16 GB of RAM, ( currently being used with 6 GB with no issues, see below ). Note the bold lines in red. 

```
$ **sudo dmidecode -t memory**
# dmidecode 2.11
SMBIOS 2.2 present.

Handle 0x0007, DMI type 5, 24 bytes
Memory Controller Information
    Error Detecting Method: 64-bit ECC
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 4096 MB
    **[COLOR=#ff0000]Maximum Total Memory Size: 16384 MB[/COLOR]**
...
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    [COLOR=#ff0000]**Maximum Capacity: 16 GB**[/COLOR]
    Error Information Handle: Not Provided
    Number Of Devices: 4
...


$ **free -m**
             total       used       free     shared    buffers     cached
Mem:          [COLOR=#ff0000]**5971  **[/COLOR]     5843        128          0        210       4457
-/+ buffers/cache:       1174       4796
Swap:         4093          0       4093

```
Just my 2 cents.

That's really interesting;
I would love to try, but "dmidecode" list the max RAM as 8GB. :/ (Which is the info I found everywhere)

Is it risky to put more RAM in?  Will it simply just won't be detected, if the maximum is reached?
Thanks!

EDIT: Hey!  Check the fourth post of the Lenovo forums (My laptop is a Lenovo Thinkpad E420)! :O
[http://forums.lenovo.com/t5/ThinkPad-Edge-S-series/RAM-Upgrade-on-ThinkPad-E420-1141CTO/td-p/892413](http://forums.lenovo.com/t5/ThinkPad-Edge-S-series/RAM-Upgrade-on-ThinkPad-E420-1141CTO/td-p/892413)

COOL. :D

---

### Post by erind on 2013-03-27
> **GameX2 said:**
> That's really interesting;
I would love to try, but "dmidecode" list the max RAM as 8GB. :/ (Which is the info I found everywhere)
Hmm ... not sure what to say but it's definitely worth a try.
> 
Is it risky to put more RAM in?  Will it simply just won't be detected, if the maximum is reached?
Thanks!

Not really, the worst it could be (I think) the laptop won't boot, or BIOS won't see full 16 GB, ... but nothing serious really.
> 
EDIT: Hey!  Check the fourth post of the Lenovo forums (My laptop is a Lenovo Thinkpad E420)! :O
[http://forums.lenovo.com/t5/ThinkPad-Edge-S-series/RAM-Upgrade-on-ThinkPad-E420-1141CTO/td-p/892413](http://forums.lenovo.com/t5/ThinkPad-Edge-S-series/RAM-Upgrade-on-ThinkPad-E420-1141CTO/td-p/892413)

COOL. :D

That's really something to consider, the guy in that thread is sure that it can go up to 16 GB.
It doesn't hurt to try ... keep all the receipts, just in case :)

---

### Post by GameX2 on 2013-03-27
I want to try so bad, but it's quite expensive (for me). :S

Will a see a different in the general speed of Ubuntu (I know, 16GB is a lot) ?  Or will that be a benefit purely for video editing, virtualisation, 3D modeling and gaming (I've got only 2 games which are going to appreciate the boost much.  Harry Potter 7 Part 1 and 2.) ?

Which brand is good  (I use DDR3) ?

Thank you very much for the info ! :)

EDIT: I've read I won't get benefit from gaming by upgrading RAM - not an issue, since the only demanding games I run are the 2 last Harry Potter, and really playable, just not always 100% fluid.

I do a lot of PhotoShop, as well a video editing (Premiere/AfterEffects), and 3D modeling.  Soon, I'll start to animate 3D model, as well.  I guess that's still interesting.  But.. expensive. :(

---

### Post by erind on 2013-03-28
> **GameX2 said:**
> I want to try so bad, but it's quite expensive (for me). :S
Check the daily deals' sites, say dealnews.com ... There's always a good chance to find them on sale one day or another.
> 
Will a see a different in the general speed of Ubuntu (I know, 16GB is a lot) ?  Or will that be a benefit purely for video editing, virtualisation, 3D modeling and gaming (I've got only 2 games which are going to appreciate the boost much.  Harry Potter 7 Part 1 and 2.) ?
Yes, there'll surely be an overall improvement, however it's not only  the RAM, it's the CPU, the slower performance of the hard disk is a big  bottleneck - a SSD will definitely help a lot, but it costs though.
As  others have stated, the best performance comes from a low footprint OS  (Lubuntu or Xubuntu), an optimized VM, (use Win XP as VM if that is an  option), but still it wouldn't be the same experience as you'd get from  running the software natively by dual-booting.

> Which brand is good  (I use DDR3) ?
Any brand will do, but read the reviews first. Stay within the specs of your machine (DDR3).
> I do a lot of PhotoShop, as well a video editing  (Premiere/AfterEffects), and 3D modeling.  Soon, I'll start to animate  3D model, as well.  I guess that's still interesting.  But.. expensive. :sad:
Check those deals' sites, ... you might get lucky someday.
> Thank you very much for the info ! :)
You're welcome :)

---

### Post by jeldridge13 on 2013-03-28
Hey erind, 

  Random question, with trying the "dmidecode" command, I get this: /dev/mem: permission denied

 I am really new to this whole Ubuntu thing, however, just curious if it is possible to enable those permissions?

---

### Post by erind on 2013-03-28
Try it with **sudo**, cause it needs elevated permissions to display the results. In a terminal type:

```
sudo dmidecode -t memory

```

Or with longer output:

```

sudo dmidecode

```

PS. Files in** /dev** directory are *special device files*, and their permissions can't ( and are not supposed ) to be changed. In this case **/dev/mem** is a special file which **dmidecode** reads from.

[http://en.wikipedia.org/wiki/Device_file](http://en.wikipedia.org/wiki/Device_file)

---

