---
title: "Skype + freeze + ThinkPad T430s SSD + 12.04.1"
date: 2012-10-25
forum: General Help
---

### Post by P1C0 on 2012-10-25
Hello all!

I own a Lenovo ThinkPad T430s with an SSD drive a couple of weeks now, and I am experiencing random total freezes -with no debug info in my logs whatsoever- whenever there is some Skype activity taking place (e.g., a new message, opening the window, closing the window).

The only thing that works is to shutdown using the power button, even key combinations to bring the machine down don't work.

The interesting thing is that every single time after I reboot from such a freeze, Skype behaves as if I have installed it and used it for the first time, i.e., it asks me to agree to its terms of use, and prompts me for my username and password. Nothing else seems to behave abnormally after the reboot, all my programs and their settings are there.

I have purged Skype now and I will see if this issue occurs again. In the meantime it would be helpful if anyone has any insight on this.

:)

---

### Post by P1C0 on 2012-10-30
I purged Skype and didn't have any freeze issues for 2-3 days. Monday morning I tried to install Skype again and my laptop froze upon log-in in Skype. So, I hard rebooted, and purged Skype again. No freeze issues since then.

This time ubuntu prompted a message saying that it discovered a problem with an application. I sent all required info by pressing OK.

---

### Post by escaper on 2012-11-07
I am a T430s user for a month, and the same freeze program happened in 12.04.1, every time it happens randomly, I changed new memory module, and same problem still occurs.

I updated into 12.10, with Kernel 3.5, it behaves good nowadays.

Just for reference.

Ken

---

### Post by monnand on 2012-11-08
I am a T430s user as well.

If you bought your T430s before Sep. 7th, then there may be a hardware error on the motherboard and you have to send it back to let lenovo fix it on site. If it is the case (hardware error), then whatever kernel you use, you cannot fix this bug.

Here is the thread I started: [http://ubuntuforums.org/showthread.php?t=2065734](http://ubuntuforums.org/showthread.php?t=2065734)

another useful link: [http://help.wfu.edu/thinkpads/t430s/status](http://help.wfu.edu/thinkpads/t430s/status)

Right now, my laptop is hold by lenovo for more than two weeks and still on "part hold" status.  What's worse, their web-site always return an error with "StringIndexOutofBoundException". That means I cannot check status online and have to call them everyday, which also means I have to be put on hold on the telephone for *more than* 20 mins. In conclusion: Lenovo service sucks.

---

### Post by P1C0 on 2012-11-29
> **monnand said:**
> I am a T430s user as well.

If you bought your T430s before Sep. 7th, then there may be a hardware error on the motherboard and you have to send it back to let lenovo fix it on site. If it is the case (hardware error), then whatever kernel you use, you cannot fix this bug.

Here is the thread I started: [http://ubuntuforums.org/showthread.php?t=2065734](http://ubuntuforums.org/showthread.php?t=2065734)

another useful link: [http://help.wfu.edu/thinkpads/t430s/status](http://help.wfu.edu/thinkpads/t430s/status)

Right now, my laptop is hold by lenovo for more than two weeks and still on "part hold" status.  What's worse, their web-site always return an error with "StringIndexOutofBoundException". That means I cannot check status online and have to call them everyday, which also means I have to be put on hold on the telephone for *more than* 20 mins. In conclusion: Lenovo service sucks.
monnand, thank you very much for this info!!

I was about to post again since yesterday I got around 3-5 freezes when pushing my laptop a bit for some experiments, very annoying..

I don't remember the exact date, but I received it from my University early October.

I will contact the partner that is responsible for the orders inside the University. 

Is there an official Lenovo newsletter about this issue on the web somewhere that I could use?
Otterwise I will use the following link: [http://help.wfu.edu/thinkpads/t430s/status](http://help.wfu.edu/thinkpads/t430s/status)

Thank you so much again!

---

### Post by monnand on 2012-11-29
> **P1C0 said:**
> monnand, thank you very much for this info!!

I was about to post again since yesterday I got around 3-5 freezes when pushing my laptop a bit for some experiments, very annoying..

I don't remember the exact date, but I received it from my University early October.

I will contact the partner that is responsible for the orders inside the University. 

Is there an official Lenovo newsletter about this issue on the web somewhere that I could use?
Otterwise I will use the following link: [http://help.wfu.edu/thinkpads/t430s/status](http://help.wfu.edu/thinkpads/t430s/status)

Thank you so much again!

P1C0, I have received my laptop from Lenovo. They fixed this problem by replacing a motherboard.

I didn't find any official announcement from Lenovo. But I did found a thread from Lenovo forum and some Lenovo employees said it is the motherboard's problem: [http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/T430s-2352-Blue-Screen-and-Stop-Code-101-Issue/td-p/824467/page/4](http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/T430s-2352-Blue-Screen-and-Stop-Code-101-Issue/td-p/824467/page/4)

I think the WFU's link is concise enough to describe the problem itself.

Right now, I didn't experience any crash except one time when I was using eclipse, it crashed again. But I cannot reproduce it with eclipse or any other software. I would say it is "almost" fixed.

---

### Post by instantmove on 2013-01-08
Probably there is no need to change hardware, read [**the following thread**]("http://ubuntuforums.org/showthread.php?p=12444638#post12444638")

---

### Post by P1C0 on 2013-01-23
I believe in my case it boils down to the SSD controller.

I tried disabling the CPU power management and also fiddled with some other options in BIOS, but no good..

Hardware tests are all 'PASS' and I do not have any problems when I boot into Windows.

I suspect the SSD controller mainly because I tried to run some sqlite3 insert queries yesterday, only to bring the system to a halt! It was ridiculous, after 20-30 insert queries from a total of 200, I got disk I/O errors, all programs started to shut down, memory consumption started to reduce, I could not even run a sudo command to reboot the machine.. again disk I/O errors. In short, the laptop acted as if it was possessed. 

I tried my code in several linux machines and it worked flawlessly, it is very simple really, nothing heavy, it creates a 1mb sqlite3 database.

I think I will start tuning somehow some disk options, see if I can get it work properly, maybe define some options in fstab too, I don't know really..

---

### Post by P1C0 on 2013-01-23
Well..

[http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/T430s-Intel-SSD-520-180GB-issue/td-p/888083]("http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/T430s-Intel-SSD-520-180GB-issue/td-p/888083")

I have the same drive: INTEL SSDSC2BW180A3L

edit:// I am reffering to the user vicenzio who among other says:
> Hi all,
 
My problem seems to be fixed: a Lenovo technician came to my house and changed the motherboard.
Since then I did not experiece any problem...
 
good luck!

---

### Post by P1C0 on 2013-01-23
To add a little bit on that, that is probably also why the issue does not happen so often if I do not use Skype. Skype keeps some databases of logs, and probably commits stuff quite often.

I also shared my story in the Lenovo forums, in case it helps others to pin down the problem too.

---

