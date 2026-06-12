---
title: "I wanna use Ubuntu for my business and need solutions"
date: 2007-06-22
forum: General Help
---

### Post by thenetduck on 2007-06-22
Hi 
   I will be setting up a server running vmware to allow me to do two things. First on one side I would like to run Linux to host my websites etc. On the other virtual machine I was going to run Windows Server 2003 and use their Account software etc. I would then be able to remote login to the computer user a program called Terminal Server CAL that would let me have up to 5 users remote login to that machine at a time and use my POS software as well as my accounting software. 
   The problem is the server costs about 1600 to build (starting off small for the time being) and the software for that is 1400 for the POS, 150 for the accounting part, 800 for the Server 2003 and 500 for the Terminal Server CAL totaling $3050. Not to mention a 214.00/year that I have to pay Microsoft to maintain the accounting software. WOW twice as much for the software. Thus Ubuntu has become very interesting at the moment. 
   

  Now for the reason I posted this. First let me say I wish there was a section just for businesses to post etc but oh well. I would like to have this set up using Ubuntu Server. VMware uses both so that doesn't matter. Instead of running Microsoft Server 2003 I would like to run Ubuntu and use a POS software and accounting software that works on Linux.  I would also like to find a really really good working alternative to Terminal Server CAL. VNC really is terrible compared to it (not to bash but it is too laggy) 

  Where can I find the software to do this? I will be purchasing support from Ubuntu if I go this route as well. Also let me say that I don't care if I have to pay money for the POS, account and remote client software however I don't like the idea of paying 214/year plus spending around 3k in software. I wanna find a good solution if it be Linux or Windows but feel that the price they are charging is well just lame. Does anyone know of the best way to do this? Also if I needed to run say, Quickbooks is that possible? 

Sorry for the long post but thank you so much for the excellent support this message board provides :)

The Net Duck

---

### Post by thenetduck on 2007-06-22
I am making a list of solutions I found for anyone else that has run into this dissision.

Replaced Microsoft Terminal Server CAL  ---- NX by NoMachine

---

### Post by bbarrons on 2007-06-22
I am no expert on what you are looking for but I did do some research awhile ago to see if there were any good acct pkgs for linux. A couple of things I can tell you... if you want to use quickbooks than you need to stay with windows.... or at least a virtual windows. Have you tried virtualbox yet? I found it to be much faster than vmware and more stable. it is also a piece of cake to setup. I honestly dont remember the names of the other software out there but there was a couple that would run on linux.
 I just googled linux accounting and came up with several different pkgs.... here is a ling to one of them... [http://www.nolapro.com/linux.html?ref=2&gclid=CNz-p6jl8IwCFQTwgAodpx35CA](http://www.nolapro.com/linux.html?ref=2&gclid=CNz-p6jl8IwCFQTwgAodpx35CA)


good luck with your search.
 Bill

---

### Post by cprofitt on 2007-06-22
Are you running ESX Server or are you running Ubunu with Virtual Server?

Have you thought about buying Windows Server 2003 Small Business Edition? (still going to cost you money, but not as much as the full blown Windows Server 2003).

How many people will you have logging in to the Windows server at the same time?

When you say POS I assume you are not swearing, but are talking about a point-of-sale solution?

If you want to send me a PM with more specifics I would be happy to try to help -- I have extensive experience on the Windows side of things and am researching making a similar move to yours.

---

### Post by thenetduck on 2007-06-23
> **PrivateVoid said:**
> Are you running ESX Server or are you running Ubunu with Virtual Server?

Sorry I don't know what ESX Server but I have a server that I would set up at my hosting company (a business friend) and would get a direct connection etc. This server would do nothing host my virtual servers. I believe however I would be running Ubuntu with Virtual Server.


> 
Have you thought about buying Windows Server 2003 Small Business Edition? (still going to cost you money, but not as much as the full blown Windows Server 2003).

I just looked into that. It seems like it would be the best solution instead of the full server but the price difference is $200. If it is going to set restrictions down the road I don't wanna have to pay another licensing agreement fee. 
> 
How many people will you have logging in to the Windows server at the same time?

For now I hope that I will only get around 3 to 4 and that is if my business grows etc for the next little while. I don't expect more than that for about 8 months. 
> 
When you say POS I assume you are not swearing, but are talking about a point-of-sale solution?
Yup you got it.


I will send you a PM shortly explaining what I am doing. I found this company that might have the solution I am looking for...however I don't want the licensing fees for it's use to be in the 22,000 range like iCode so im' a little weary...


Thanks!
The Net Duck

---

### Post by cprofitt on 2007-07-03
> **thenetduck said:**
> I just looked into that. It seems like it would be the best solution instead of the full server but the price difference is $200. If it is going to set restrictions down the road I don't wanna have to pay another licensing agreement fee. 

For now I hope that I will only get around 3 to 4 and that is if my business grows etc for the next little while. I don't expect more than that for about 8 months. 


I will send you a PM shortly explaining what I am doing. I found this company that might have the solution I am looking for...however I don't want the licensing fees for it's use to be in the 22,000 range like iCode so im' a little weary...


Thanks!
The Net Duck

I have not gotten a PM for you... did you get this all sorted out?

Depending on what you are doing Small Business server should not require you to pay more... it is a rather nice solution for the small office environment.

---

### Post by thenetduck on 2007-07-04
> **PrivateVoid said:**
> I have not gotten a PM for you... did you get this all sorted out?

Depending on what you are doing Small Business server should not require you to pay more... it is a rather nice solution for the small office environment.

Oops, a lot has actually gone on. It looks like I won't even be able to use Ubuntu on the server that I have. I am going to use a hardware raid but the drivers arn't supported on Ubuntu however Suse works just nice. So This is what I will be setting up. (I really wish I could have gone with a complete linux system for my small business but it just doesn't exist :( business venture anyone?)
   I am running openSuse server 64 bit then running a vmware server on top of it (just until I can afford the 1000 version that doesn't run on an os). In my two virtual machines I am running Ubuntu for my websites (still can't beat it) and Microsoft Server 2003. I am running Microsoft's Small Business Management System with Microsoft Small Business Accounting. (Ya I know there are a lot of microsofts in that.) Over all and after hours and hours and hours and hours of searching, they really do have not only the cheapest, but best solution. I just wish it would run on Linux. For instance, I know licensing is annoying but most companies licens their software to a chipset on your computer etc, with their RMS they license it to a USB so you can move it to a different computer etc. 
   The other company I was looking at (well other two companies) were for linux but the sales man almost laughed in my face when I told him I wanted to keep it under 3k. I guess their starting package was 10k without any of the mods etc that are like 5k each. They did offer a really good service however. For around 300/month I could get the complete system that they were offering which I think is awesome, however I don't like not having complete control over my business; plus if my internet went down I would have no way of accessing my POS system, not a good situation. 
   So over all Microsoft isn't bad but I wish I could have used linux. I usually goes whats works. I would like to start an Open Source knock off (or even more innovating) of what Microsoft has. Anyway, I will most likely never have time to even try to start coding so ill leaving it to the universe. 

One more thing (if you still managed to keep reading this post) Can somone please make the hardware raid drivers for Ubuntu Server for a Tytan Tiger S3870 motherboard? openSuse has it. I posted it on launchpad.net if anyone is wants to. 

P.S. Thank you to all that have coded for Ubuntu it really does help ;) Hopfully when I have the big bucks Ill be able to pay some people to do some coding. Cheers!

The Net Duck

---

