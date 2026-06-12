---
title: "45 minute boot time.  Scanning Hard drives?"
date: 2007-03-09
forum: General Help
---

### Post by Johnnyb613 on 2007-03-09
Hello!

I have an interesting new problem that started when I rebooted yesterday, it now takes my system 45 minutes to boot.  It gets to the point of "starting RAID, this may take a long time!" and then sits and pounds the hard drive for 45 minutes as if it is doing some kind of scan on the raid arrays.  I have been hacking at it all day and not getting anywhere.  

Once it gets past that scan or whatever is going on, it runs fine, all my arrays look good and everything is happy.  I don't even know how to go about beginning to troubleshoot, since the system is not up enough to login to and do a TOP to see what it running.  I am booting from a non RAID disk, so I tried to disable RAID, but even though I renamed the MD directory and doing a modinfo raid1 says no such file or directory now, riad0 raid1 and md_mod still magically load.

Hmm, I guess I could unplug all my hard drives save for the boot drive and see how it boots.  Yeah, I will do that as soon as I get home and post the results.  

I am afraid I am missing something really obvious, it usually seems that if I have a problem that I can't find an answer to searching the net, it is because I am doing something so silly dumb no one else has ever done it.

I am running Edgy on an Athlon XP processor.  I'm not sure what other information to include at this point.

Thanks!!!

---

### Post by Johnnyb613 on 2007-03-09
Well, that was an interesting experiment.  I unplugged the four drives plugged into my Promise IDE controller (this is not one of the fasttracks that does the fake RAID, it is just an IDE controller) and booted up my system.  And with only on 40GB HD plugged in with no RAID partitions, the last message I see is "Begin: Starting up RAIDs. Please wait, the process may take a long time!"  and it is chugging along blinking the HD light.  I have no idea what it could be doing, you could format a 40GB drive quicker that 45 minutes.  Well, I guess I could try it with the other IDE controller totally out of the box, or see what the next message is and look at that.  

Any ideas where to go from here?

Thanks!

---

### Post by hotani on 2007-03-09
I had this problem and it turned out to be a bad drive. I went through the same process and removed drives until it booted up normally. It could be your bood disc--do you have another one you can boot from?

---

### Post by Johnnyb613 on 2007-03-09
I probably have a spare drive around here somewhere... but let me tell you what I've done since then....  I booted up into safe mode (oops, recovery mode?) and the last thing that was displayed before the "enter root password for maintenance" prompt was that it ran fsck.  (And it did end up booting a lot faster without the extra 500 GB of my RAID array hooked up).  So I did a search on the forums for fsck and found a lot of people having problems with it running every time they booted, however I didn't find anything that helped.  I *assumed* that is must be due to an update and the best thing to do would be to pull out the Ghost image of my system and re-image.  I re-imaged and after having Ghost screw with my partitions and fixing that in Grub, I booted... and fsck is running. 

So here I am with a system that was restored from a month old image, and was working great at the time image was made, but it still doesn't work.  Could be hardware, it seems like putting on a new image eliminates the software....

---

### Post by clintond on 2007-03-17
Strangely enough, this same thing occured with my system around 2-3 weeks ago. As the box is headless, i have only bothered to take a look at the possible cause today. Luckily for me though, the boot time is 5-10minutes.

The system is quite new (2mths) and only powered-up every few days so i would like to assume the issue it not hardware related - although as with your system, it too is athlon based, running 2x500gb in raid0 configuration.

As the machine is severed from the www, it is hard for me to attribute the cause to a software update and in my view occured 'randomly', i say that as i am struggling to remember what has been touched on the machine within that timeframe (though some weeks it is not switched on which makes remembering all the harder).

I will keep you updated with any findings i have, the pointer re: fsck is certainly worth investigating...

---

