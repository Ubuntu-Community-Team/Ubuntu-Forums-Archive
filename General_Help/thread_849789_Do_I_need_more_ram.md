---
title: "Do I need more ram?"
date: 2008-07-04
forum: General Help
---

### Post by f37u5g0d on 2008-07-04
Here are the specs for my computer.

3.6GHz celeron D processor
512MB 533MHz (1 stick) ram
ATI Radeon 9550 graphics (64MB ram)
40Gb IDE harddrive
I was thinking about buying another 512Mb of ram or maybe just one 1024Mb stick but I was wondering if it is really going to make a difference in my system.  What would be the most beneficial new processor, sata HDD, or more ram?  Will I see any noticeable difference with any of these options or will I need benchmark software.

Part two:  Are there any good benchmark apps for linux in the repos or otherwise?

Thanks for any and all answers!

---

### Post by Dr Small on 2008-07-04
I lived off of 512MBs for a long time and then eventually added a second stick, so now I have 1GB of RAM. It definately helps with memory hogging apps.

---

### Post by Spaceman9 on 2008-07-04
The trick to RAM is first knowing how much you really use. If you're not using graphic or video apps, if you're not working with large sound files then for most people 1GB is usually enough. Although it leaves little room to grow if you plan to keep your current hardware for 4 or more years. 

If you're doing video editing, digital graphics (animation, digital art or photo manipulation) or working with large sound files (wav, ogg, FLAC) or even midi then 2GB is better. 

Run the System Monitor and see how much ram and hard drive virtual memory your computer uses when you run different apps. Add up the total of ram an hard drive virtual memory, then round that up to thew nearest GB. So, if your total memory usage in ram and virtual is 750Mgs you'd need a total of 1GB of ram to run that in ram. 

I do digital art and often use 1GB to 1.5GB's of ram so I need to have 2GB of ram installed. I actually have only 256Mgs of ram installed. How can I do that you ask? Very, very slowly. 

Also, all the ram in the world won't make your computer run faster if you have a slow cpu or if you have a faster cpu with a slow front side bus so it takes all 3 things to make a computer really run fast. Also if you have embeded sound or video chips make sure you have plenty of memory for those too because they have no memory of their own and so they have to use the ram on your motherboard.

---

### Post by Linux&amp;Gsus on 2008-07-05
My first question would be, do you have any sorts of problems? What are they?  What are you usually doing with your computer? What programs are you using? etc.
Your system specs are above the minimum requirements. Therefore it should work. "Should" means that it really depends on your needs and habits.

E.g. I have a desktop with 1GB RAM and a 2.5GHz Celeron and a laptop with 1.5GB RAM and a 1.7GHz Pentium M (mobile processor). Both are **NO** dual core.
In short my usage profile could be described as usually having many programs running at the same time and many tabs open in Firefox. Work is usually not CPU intensive, e.g. no video, audio, graphic editing.

But no matter how many programs I have open my laptops runs better. It has a little bit more RAM but that shouldn't matter for just a couple applications right after booting. But here's the catch, the actual slower processor (as in GHz numbers) is performing better.
I believe that is because it has more Cache. The Celeron has 256KB L2 cache while the Pentium M has 2048KB (2MB) L2 cache. So, the raw numbers don't necessarily mean anything. It really depends on what you are doing.

E.g. for me a dual core would be nice but is totally not necessary for my daily work. While RAM is rather more important.
When I'll by my next computer (when ever that will be, anyways) I'm not so much concerned about the processor. For sure I don't need the latest quad core 7GHz or 8 core 3GHz or what ever will be available at this time. But the machine will have at least 2GB RAM, most likely more. Might even be a 64Bit system for the sake of having possible 4GB+ RAM. Not that I need it right now really. But it might be something for the future.

So, unless you are really doing some CPU heavy work (video, etc) I doubt that you need a new processor. Depending on what you are doing, and what your problem is, I would say if you stick in another 512MB - 1GB RAM I'm almost sure you'll be happy.
Then you'll be rockin' and rollin'... :guitar:

---

### Post by TenPlus1 on 2008-07-05
Having more ram is always a bonus, although I use 512mb on my ubuntu laptop and it can handle anything I throw it's way...

Tweaking ubuntu and disabling services/sessions you dont use will also help to save you memory and shorten boot-up time...

Lastly, going into terminal and typing:

sudo gedit /etc/sysctl.conf

..and adding this line to the very end:

vm.swappiness=10

will access virtual memory less and allow ubuntu to run from physical, which can really speed up a 512mb system...  Play with the value, it can range from 0 (all memory) to 100 (all virtual) and see what works for you...  Reboot for changed to take effect...

---

### Post by Ximal on 2008-10-20
i added it like this at the end...

#<-- put two of these and then followed next to them the command you gave us..


like this..

#linesofstuffbeforelinebelow=example
#
#vm.swappiness=10

^
the above is how i ended my " sudo gedit /etc/sysctl.conf "

did I do this right ? ... I have pastebinned below my full sysctl.conf ... 

[http://pastebin.com/m70e8bf19](http://pastebin.com/m70e8bf19)

thanks for all help given !

---

### Post by fragos on 2008-10-21
The "free" command will tell you most of what you need to know. Free will tell you if you're using swap space. Add memory until you no longer use swap space. Swap being a disk function is by nature slower than memory. I found that for my use 1GB virtually eliminated swap use. Changing swappiness to 10 is also probbaly a good idea.

---

