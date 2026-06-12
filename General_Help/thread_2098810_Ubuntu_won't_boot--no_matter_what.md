---
title: "Ubuntu won't boot--no matter what"
date: 2012-12-27
forum: General Help
---

### Post by 32Bit on 2012-12-27
If you run into the same (or similar) problem that I did, then follow these steps. These steps worked for me:
- Open Windows or some operating system that will allow you to edit partitions.
- Delete the Linux partition and reformat it.
- Get another Linux distro (I used Linux Mint)
- Install that distribution of Linux
- (optional) If this works, then reinstall Ubuntu if you still want to use Ubuntu.



Hi. I'm new to the forum, but I have been running Ubuntu for some time now, and this is the first time I've run into a problem I wasn't able to solve. I'm on a phone, so please excuse any typos.

A bit less than a week ago, I got up one morning and turned on my two year old laptop computer, and when I tried to start Ubuntu 12.10, I got a black screen, which lasted a few hours of waiting until I force shut down the computer. After a few reboots, I managed to get to the loading screen which after a few seconds, froze, and forced me to force shut off the computer after I waited long enough to see that nothing was happening. I was able to use the "drop to root" option in the recovery mode, so that I can access the terminal. I googled the problem, but couldn't find anything that worked, so I tried to boot the computer using a USB Key that I had lying around. The same thing happened, where the booting up loading dots animation froze and the computer would not boot, even after waiting for a long time. I tried booting th computer up in failsafeX mode, and it started running fsck (filesystem check), which has been running for about 15 hours, with no sign of the computer doing anything.

I can only think of a few things that could have caused this problem:
- I installed Apache 2 and hadn't rebooted since that install. That may have caused the problem.
- I recently installed windows 7 on a dual boot, but I have performed multiple reboots since the install, and there wasn't any problems.
- I flew on an airplane right before the problem started. Not sure how this could cause a problem, but it's worth noting, I guess.

To restate what I have tried:
- Booting it up regularly many times
- LinuxLive USB key
- Booting it up in failsafeX mode

Nothing seems to work, and the problem started somewhat randomly. If anyone could help, that would be great, if you need any information about anything, just tell me what you need and I will try to get it. Thanks!

---

### Post by dabl on 2012-12-27
Given the lack of recent changes to your OS, and the sudden onset of the problem, suspicion must first fall on the hardware. A two year old laptop should not experience hardware failures, but the reality is, it sometimes happens.  You're going to have to test your hardware thoroughly before anyone is going to sink a lot of time into looking for software issues, IMO.  Off the top of my, here are some troubleshooting things to do:

- boot other Live CD/USB stick installations (there are tons of 'em).  Does video work from a Live CD/USB stick?

- from a Live CD/USB stick, run memtest overnight.  Did it run error free?

- from a Live CD/USB stick, fsck your hard drive.

- from a Live CD/USB stick, run a smartmon check of the hard drive (an error in the boot sector could cause the problem you're seeing).

One handy tool that I keep close by is a [**[color=green]parted magic live USB stick[/color]**](http://partedmagic.com/doku.php?id=downloads).

Hope this helps.

---

### Post by 32Bit on 2012-12-28
I ran memtest while I was gone. When I came back the console was spamming me with errors. This may be the problem, and if it is, is there a way to solve it without buying new RAM sticks? 

The errors appeared to start at the 128 MB location exactly, as I saw when I quickly ran it again. That is 2 to the 7th power, if that means anything. After that location, the errors just keep going. I am going to leave it on overnight to see what happens.

The one thing I'm suspicious about, is that I am able to run windows just fine. I am not able to access the Ubuntu partition in windows.

Note: When running memtest, I just selected it from the boot options in grub, instead of using it from a liveCD. If this may affect something since Linux doesn't appear to work, let me know.

---

### Post by BertN45 on 2012-12-28
The memory seems to be the problem. If you are lucky, cleaning the memory connectors and reinserting the memory card(s) will solve the problem. Your flight has been a bumpy one?

The strange thing is that windows seems to be working. But both systems will allocate physical memory in different ways, so they could end up using different parts of your RAM.

The Ubuntu partition cannot be seen by Windows, because Windows does not support the ext3/4 file system of Ubuntu. So that is normal.

---

### Post by Bucky Ball on 2012-12-28
Can't access the Ubuntu partition in Windows??? You have installed Wubi then and this is not a dual-boot?

Dual-boot = Windows and Ubuntu on separate partitions. Wubi is intended to test out Ubuntu and see if you like, not a permanent solution. If Windows is running fine and you can't run the Wubi install inside it, then it could have more to do with a dodgy Wubi install than RAM.

Not too many experts on Wubi about but someone might pop up.

---

### Post by 32Bit on 2012-12-28
> **Bucky Ball said:**
> Can't access the Ubuntu partition in Windows??? You have installed Wubi then and this is not a dual-boot?

Dual-boot = Windows and Ubuntu on separate partitions. Wubi is intended to test out Ubuntu and see if you like, not a permanent solution. If Windows is running fine and you can't run the Wubi install inside it, then it could have more to do with a dodgy Wubi install than RAM.

Not too many experts on Wubi about but someone might pop up.

I am running a dual boot, not Wubi. I have Windows and Ubuntu on separate partitions. As the post above states, Windows, apparently, doesn't support ext3 filesystems. Thanks though.

---

### Post by Primefalcon on 2012-12-28
try this and tell me if it works, when at the grub screen choose previous version of ubuntu and try booting using an older kernel.... will it boot then?

---

### Post by Elmer Fudd on 2012-12-28
Would you post your hardware specs?
Have you run any memory intensive (uses lots of) in Windows to see if it might crash then?
Tried a small footprint Linux distro from USB or CD?

---

### Post by fdrake on 2012-12-28
the kernel seems unlikely to be the problem since the live usb is not running. I'd say it is an hardware fault if it wasn't for the fact that windows is working. 

My last thought would be the Ram like some ppl have said. Check your BIOS change the RAM (deactivate or Activate multicore- or watever you can change) and boot (do not boot into windows just to make sure). See how far you can go.Either way: Shutdown again and change the BIOS settings of the RAM back, as previously, and rebbot again. Any luck then?

---

### Post by audiomick on 2012-12-28
> **32Bit said:**
> I ran memtest while I was gone. When I came back the console was spamming me with errors. ...
Note: When running memtest, I just selected it from the boot options in grub, instead of using it from a liveCD. If this may affect something since Linux doesn't appear to work, let me know.

Running memtest from there is fine.

Memtest should give you zero errors. If you are getting any at all, there is something wrong.

Do as suggested: take the RAM sticks out and plug them back in, then run memtest for a while again. 

I assume there is more than one stick of RAM in there. If you are still getting errors, try running memtest with only one RAM stick installed, and repeat this with both / all of them. You should be able to identify which one has a problem, and may well be able to run the machine without that one until you can manage to replace it.

---

### Post by Primefalcon on 2012-12-28
> **audiomick said:**
> Running memtest from there is fine.

Memtest should give you zero errors. If you are getting any at all, there is something wrong.

Do as suggested: take the RAM sticks out and plug them back in, then run memtest for a while again. 

I assume there is more than one stick of RAM in there. If you are still getting errors, try running memtest with only one RAM stick installed, and repeat this with both / all of them. You should be able to identify which one has a problem, and may well be able to run the machine without that one until you can manage to replace it.
that's very good advice

---

### Post by 32Bit on 2012-12-28
> **Elmer Fudd said:**
> Would you post your hardware specs?
Have you run any memory intensive (uses lots of) in Windows to see if it might crash then?
Tried a small footprint Linux distro from USB or CD?

My hardware specs aren't very good compared to some things out there, and I've had my computer for over two years. I can't really imagine what I could have run to crash the RAM cards.

2.27 GHz Intel i5 processor, quad core
3 GB DDR3 RAM-- one 2 GB stick, one 1 GB stick
nVidia GeForce GT 510M - 512MB dedicated RAM
Google "Vostro 3500"

---

### Post by 32Bit on 2012-12-28
> **audiomick said:**
> Running memtest from there is fine.

Memtest should give you zero errors. If you are getting any at all, there is something wrong.

Do as suggested: take the RAM sticks out and plug them back in, then run memtest for a while again. 

I assume there is more than one stick of RAM in there. If you are still getting errors, try running memtest with only one RAM stick installed, and repeat this with both / all of them. You should be able to identify which one has a problem, and may well be able to run the machine without that one until you can manage to replace it.

I plan to do this as soon as I get a chance. (Been busy lately)

---

### Post by audiomick on 2012-12-28
> **32Bit said:**
> ...I can't really imagine what I could have run to crash the RAM cards....

You don't have to have done anything. Sometimes the contacts get a bit oxidised, hence the unpluging and re-plugging to re-seat the contacts.

Apart from that, machines just break sometimes. I lost a stick of RAM a while back. No reason. It wasn't even in a laptop, so it wasn't shock, and the machine is well cooled. The RAM stick just died.

---

### Post by Primefalcon on 2012-12-28
not to mention ram can one of the touchiest things out

---

### Post by Elmer Fudd on 2012-12-28
Agreed that the 1st thing to do is to clean the contacts
Do I understand correctly that Win7 boots and runs fine?
Just for another datapoint, can you run a memtest under Win7? 

I can't remember if the Win7 install includes a native memtester so...
[http://pcsupport.about.com/od/toolsofthetrade/tp/memorytest.htm](http://pcsupport.about.com/od/toolsofthetrade/tp/memorytest.htm)

---

### Post by 32Bit on 2012-12-28
> **Elmer Fudd said:**
> Agreed that the 1st thing to do is to clean the contacts
Do I understand correctly that Win7 boots and runs fine?
Just for another datapoint, can you run a memtest under Win7? 

I can't remember if the Win7 install includes a native memtester so...
[http://pcsupport.about.com/od/toolsofthetrade/tp/memorytest.htm](http://pcsupport.about.com/od/toolsofthetrade/tp/memorytest.htm)

That is the really funny thing. I thought of this and ran it a few hours ago. It came up clean 100%.

---

### Post by 32Bit on 2012-12-29
I just tested the RAM cards, and found that both of them gave errors. I have a few suspicions, though.

- Both of the RAM cards failed at what appeared to be the exact same location: 129.0MB
- Both RAM cards shouldn't just randomly fail. At least one of them should work.
- Windows boots fine
- Windows RAM test gives no errors

---

### Post by audiomick on 2012-12-29
Hmm, very odd. 

You ran memtest from the Linux install, didn't you? Have you got a Linux CD or USB that you could run it from?

It does look like the RAM is good, so the next step is to find out what about the Linux install is causing errors. If you can run the same Linux memtest program from a different source, it might indicate that the drive has a problem.

Wait on, there was mention of problems booting from a USB earlier, weren't there? :-k

Edit: from your first post
> - I flew on an airplane right before the problem started. Not sure how this could cause a problem, but it's worth noting, I guess.

Did you have the laptop as cabin luggaged, or did it go through the baggage handling?


I think you need to have another look at getting booted into a live environment, either from a USB or a CD. Ubuntu, or anything else. Just something where you could have a look at the drive from a Linux basis.

---

### Post by dabl on 2012-12-29
> **32Bit said:**
> 
- Windows RAM test gives no errors

I have recently had the unhappy experience of seeing Windows 7 memory test find no problems, and then memtest86 found lots of problems on the same hardware.  I would trust memtest86 over the MS product.

---

### Post by BertN45 on 2012-12-29
Like I said before Linux uses the lower physical addresses for the kernel, for Windows I am not sure and I could not find it. Suppose it uses the high memory addresses for its system, then it is perfectly explainable, while one system fails and the other not. Another reason could be that Windows blacklists bad memory and Linux not. Already in the early 70-thies IBM did blacklist bad memory for the larger 360/370 systems and both companies worked together a lot in the early days of Windows NT/OS2. Still another reason could be that they run with different clock frequencies, so the error is more a memory/CPU timing issue.

I am not very convinced by the Windows memory tests, since it has three modes of operation, basic, standard and extended. I do not know, which one is used by default, surely not extended. If you press F1 you can change the mode of operation in the memory test of Windows. 

Linux has a very good memory test that will find any error also timing issues. Any good memory test program will ensure, that it can run correctly before starting the test.

All this is of course speculation. So a logical step by step approach is needed:
[LIST=1]
[*]open the box and clean the contacts
[*]Put one memory stick back and run the linux memory test preferably from an live USB stick or live CD.
[*]Swap the memory sticks and do the same.
[/LIST]
If the tests find an error you have a hardware problem. Only use the correct stick till you bought a new one.

If they did not find the error, reinserting the memory sticks probably solved the problem. You still have to try to load Ubuntu, if that works the problem is solved. If it does not work you have to re-install the system, because somehow it got corrupted, maybe because of the previous memory errors.

---

### Post by 32Bit on 2012-12-29
I solved the problem (and will be marking the thread as solved in a few minutes.) I am not quite sure what was causing the problem, possibly a corrupted partition due to something I had done (not sure what.) In windows, I formatted the Linux partition, downloaded a Linux Mint distribution and put that on a flash drive. I booted the computer up using it and reinstalled Linux, but this time not using Ubuntu. Everything seems to work fine now, I am typing this on the computer that I just fixed.

---

### Post by Bucky Ball on 2012-12-31
All good. Please mark as solved from Thread Tools to help others ... ;)

---

