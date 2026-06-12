---
title: "RAM Usage, Beyond the 4G Wall"
date: 2008-01-25
forum: General Help
---

### Post by MicTechS on 2008-01-25
I have built up a older Supermicro P4DP6 computer and place OS Windows Xp Pro on it first...  Then I added Ubuntu 7.10 next, and then realize a dual OS system...  This is now all up and running!  My P4DP6 has two Xeon micros at 32 bits using the Intel E7500 chip that enables use on this motherboard of 64 Bit RAM interfacing along with PCI-X 64 bit cards... I have 4 2G RAM modules for a total RAM of 8Gs which Bios sees during boot ups... And yes, my Motherboard could be populated up to 16G... These two Xeon chips are not EM64T ready (early generation Xeons), but do fully support -PAE.  Microsoft has changed the first/early meaning of PAE along with placing a force limit of 4Gs... in Xp... Vista... (non 64B types...)  This is most sad... All is working nicely while I explore my dual OS setup if one limits activities to the 32 bit world... or 4Gigabytes.... Also I don't want to go the server route because I want to live in pure application mode...  I want to do very large electromagnetic simulations...

 What  I am trying to do now is break the 4G barrier.  Windows Xp Pro (non 64b or non EM64T) has a hard limit at 4Gb which is really 3.6G or so which in reality with an added .5G hit for the OS, ultimately the user ends up with about 3.1G room for applications... Xp OS ate the other .4G somewhere along the way... Ubuntu support 4G RAM on this setup ends up to about 3.6 Gbs for Linux base applications to use...  A little better...  but one still has a high end simulator future loss when getting Microsoft programs to operate within Ubuntu or Linux plate forms...  Words like Wine and Crossover then come to mind... and I expect if workable, they will eat their RAM share... to lower the expectation on Ubuntu a little...  Still Linux or Ubuntu offer the best hope...

I don't expect to do applications beyond the 4G limit ever (I would need a 64 bit true motherboard and matching software compiled for 64B!), but I like to run the upper 4Gbytes as a 64 bit RAM Drive and speed up my high end simulations that way...  I am exploring a 4G USB-2 idea concurrently, and can see some advantages in doing it this way... but I rather use my 64 bit upper RAM area on the P4DP6 motherboard...

Does anyone know of a method to do what I seek?  Break the barrier of 4G via RAM DRIVE?  This could be open source or closed source...  Is anyone working on this need now or has somebody already done this in the past?  "Point the way!!"

It seems to me that since Ubuntu is modular solution to the OS idea (Unix historical way of doing things), somewhere there must be a patch to the Ubuntu OS that will enable what I need...  Looking at many blogs I see many other trying to full-fill this need too...  

The reality here is, the PAE way is far cheaper than the full EM64T newer method available now...  When only the PAE solution was around, the RAM at that time was priced out of reach to be fully explore... RAM is  much cheaper now, then before...

Thanks

---

### Post by dcstar on 2008-01-25
> **MicTechS said:**
> 
..........
Does anyone know of a method to do what I seek?  Break the barrier of 4G via RAM DRIVE?  This could be open source or closed source...  Is anyone working on this need now or has somebody already done this in the past?  "Point the way!!"
..........

I very much doubt that the kernel developers are going to spend time on making old hardware work in this way when there is plenty of new 100% 64-bit standard hardware coming onto the market every day to keep them busy.

It would probably be far cheaper for you to purchase new hardware, or live with your non-standard hardware using a 32bit O/S.

---

### Post by MicTechS on 2008-01-27
Hi dcstar

Thank you for your input...  

There are two things of interest that can be found on the Internet that will keep me watching, for a least a little while longer...  There is a "kernel-pae" for Linux out there somewhere, and something else call "hugememory..."  I have gather up pieces of these softwares... But, I am not seeing this in the Ubuntu Internet camps!   "I like too!"   That is at least, verbally explained fully, but both of these pathway from elsewhere, both hint at a working solution that is already in existence...  Links to these have so far eluded my attempts to plug into what I've got...

This has appeared within the Internet searches where by I found Red Hat has "toy around" with this question... besides others within comments of books I have read and own...

Also within the Microsoft documents on the Internet, there are those document which speak of various third party solutions developed for OS's like Xp and other platforms... (WHAT??)  One statement by Microsoft, on this subject was a statement stating they will no longer support -PAE because,,, Microsoft felt they could not develop a -PAE solution with out running a risk of colliding with these "other third party solutions", so they passed on it... for that reason... Hum...  This is true except for their interest in server solutions... (Server 2000 & 2003 (2nd is most Active!))  I like to learn of one of these Microsoft third party solutions they hinted at.... (Where might I go?)  Plus,,, Intel still has the flag pae in their cpu list of possibilities too...  That is interesting in itself...  

So, I am looking for an existing solution, and not a new one...  "I think it is hiding!"   I am counting on my late arrival into this old question, such that, what I am trying to do, might be better describe as my further enlightenment concerning, merely how-to...  I just want to the learn how...  It has already been done, but is missing in action from where I sit....

Thanks
MicTechS

---

