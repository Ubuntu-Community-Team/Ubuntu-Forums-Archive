---
title: "Generally Slow System"
date: 2013-02-05
forum: General Help
---

### Post by dcb5739 on 2013-02-05
New to Ubuntu 12.04 LTS, So far its much slower over all than Vista
Ubuntu boots much faster but slow running esp online
From all I have read it is probably a hardware or driver issue
When I check the system preferences , under driver it says UNKNOWN
screen looks sharp and clear, but playing a single video on Youtube slows the system to a crawl
Dell Inspiron 1545 Laptop
2.16 processor
4 gig Ram

I know its user error, I must have missed a detail someplace, as I have read glowing reviews for speed and reliability

Thanks
Dave

---

### Post by collisionystm on 2013-02-05
> **dcb5739 said:**
> New to Ubuntu 12.04 LTS, So far its much slower over all than Vista
Ubuntu boots much faster but slow running esp online
From all I have read it is probably a hardware or driver issue
When I check the system preferences , under driver it says UNKNOWN
screen looks sharp and clear, but playing a single video on Youtube slows the system to a crawl
Dell Inspiron 1545 Laptop
2.16 processor
4 gig Ram

I know its user error, I must have missed a detail someplace, as I have read glowing reviews for speed and reliability

Thanks
Dave


You're seeing 'UNKNOWN' because its probably just an embedded intel graphics card. I don't know why but this is generally what I see for this.
Your computer has great specs, but unfortunately in the Ubuntu world we are limited by the software that developers build. Youtube and Esp online (a game I assume?) are probably flash based. Adobe flash is horribly incompatible because adobe does not focus time into developing on linux. As linux users we are stuck with this horrible performance until either A. They properly develop flash for us or B. More things get ported to HTML5.

I think alot of people boast about the speed of ubuntu in comparison to windows because they didn't know how to take care of their windows system and speed it up. Any OS can be fast, it depends on how it gets used.

I apologize because this surely isn't the answer you were hoping for, its just kind of the reality of everything. I do computers for a living and I love ubuntu for many reasons, but it has alot of flaws that keep me from personally using it full time anymore.

With all the attention Ubuntu is getting from developers lately, I think it will only be another year or two before it becomes more up to par with Windows and the general compatibility it has.

---

### Post by dcb5739 on 2013-02-05
Thanks for the reply
It does have the intel graphics
At least now I can quit driving myself nuts hunting for the solution
Thanks
Dave

---

### Post by collisionystm on 2013-02-05
You're welcome.

You can open system monitor while your watching youtube or something and see that its firefox/adobe pinning your CPU at a high usage.

---

### Post by dcb5739 on 2013-02-05
How do I open the system monitor
Thanks
Dave

---

### Post by collisionystm on 2013-02-05
Open the Ubuntu Menu and search for **System** and it should bring back a relevant listing. When you open it, it will show CPU usage, memory usage and all the programs running.

---

### Post by dcb5739 on 2013-02-05
Just as you figured an online video took the processor close to the max
Thanks
Dave

---

### Post by collisionystm on 2013-02-05
I would give Google Chrome a shot. It has its own flash plugin built in that is maintained by google. I'd download it and give it a shot.

[www.google.com/chrome](www.google.com/chrome)

You should see some kind of performance improvement compared to firefox and the flash plugin that is in the software center.

P.S. When installing Chrome, you *might* see a warning about the package being of poor quality. You can ignore this and install anyways.

---

### Post by dcb5739 on 2013-02-05
I have Chromium installed , Is that the same as Chrome ?
Thanks
Dave

---

### Post by collisionystm on 2013-02-05
No.

Chromium is just the base that Chrome is built off of. Google Chrome has features that Google specifically adds. Flash is one of them.

---

### Post by dcb5739 on 2013-02-05
Great
 I will give it a try
Thanks
Dave

---

### Post by dcb5739 on 2013-02-05
Getting errors installing Chrome, Status bar gets to about 90% and then it says packaged failed and needs repaired. After several tries I still get the same message, rebooted and still gate the same message
Thanks
Dave

---

### Post by Autofac on 2013-02-05
I asked the same question on askubuntu and was directed to these threads:

[http://askubuntu.com/questions/2194/how-can-i-improve-overall-system-performance](http://askubuntu.com/questions/2194/how-can-i-improve-overall-system-performance)

[http://askubuntu.com/questions/95398/why-is-ubuntu-slower-than-windows-xp](http://askubuntu.com/questions/95398/why-is-ubuntu-slower-than-windows-xp)

Follow the preload thing. It is likely not the fix to your exact problem, but I did find an improvement in the problem I was having which was that everything just seemed slower from XP (indeed, it was slower). 

I am still searching for a way to speed it up drastically, application launching, among other things is still slower than XP--but it's a small price to pay for the time being.

---

### Post by collisionystm on 2013-02-06
> **dcb5739 said:**
> Getting errors installing Chrome, Status bar gets to about 90% and then it says packaged failed and needs repaired. After several tries I still get the same message, rebooted and still gate the same message
Thanks
Dave

Hmm. Not sure why its failing. Try to download the program again.



If that fails too, we might need to open up Terminal and enter these commands.

Open your Ubuntu menu, search for **TERMINAL **and open it.

Type, 

```
sudo apt-get update
```

```
sudo apt-get install -f
```
Let me know what it says.

---

### Post by dcb5739 on 2013-02-06
Tried the commands listed and started over, same errors. Heres the kicker, in windows I have the 32 bit software. i used the windows installer version to install Ubuntu. When I look at the system preferences it says I have the 64 bit Ununtu, so I tried the 64 bit chrome and it installed, So far i cannot access it from the side bar but only with the google-chrome command in terminal
Thanks
Dave

---

### Post by collisionystm on 2013-02-07
You can have a 64 bit Ubuntu and a 32 bit windows. It just means your system is 64bit compatible. They probably factory installed it with 32bit to save money on adding addition RAM.

I have had that problem with chrome no showing up in the menu after an install. A reboot fixed it.

---

### Post by dcb5739 on 2013-02-08
Chrome is working well. I have never seen the internet work so well
Thanks a lot
Dave

---

### Post by collisionystm on 2013-02-10
> **dcb5739 said:**
> Chrome is working well. I have never seen the internet work so well
Thanks a lot
Dave


Good to hear! Good luck!

---

