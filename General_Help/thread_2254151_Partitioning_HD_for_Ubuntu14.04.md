---
title: "Partitioning HD for Ubuntu14.04"
date: 2014-11-25
forum: General Help
---

### Post by mountainman70 on 2014-11-25
I have a 120 GB HD that I am dual booting W7 & Ubuntu 14.04. W7 has 63.48 GiB & Ubuntu has 48.28 GiB. I have a 1GB swap file installed inside Ubuntu. Recently I had a problem & had to reinstall Ubuntu & all my files.
I would like to do a clean install & make 3 partitions in Ubuntu ( / - 1G swap - home ) so, if the need comes up again, I can just install Ubuntu without losing my files. What amount should my Mount Point / be set? 
Thanks.

---

### Post by oldfred on 2014-11-25
Only use Something Else to reinstall. You do have to backup all your data and should be doing that regularly for both Windows & Ubuntu. Hard drives do fail, users do make mistakes and things just happen.

I normally suggest 20 to 25 GB for / (root) but then expect a much larger /home. With your size it is border line on whether a separate /home is an advantage. Either way with backups of /home it really is not critical to have separate /home. I often suggest /home for newer users and for more advanced users a /mnt/data partition so just data is in the separte partition and user settings are in /home inside /. 

My / uses 11GB including about 2GB for /home. All data is in data partition. My /home is larger as it also has .wine with Picasa which is about 1.5GB of the 2GB.

---

### Post by mountainman70 on 2014-11-25
> **oldfred said:**
> Only use Something Else to reinstall. You do have to backup all your data and should be doing that regularly for both Windows & Ubuntu. Hard drives do fail, users do make mistakes and things just happen.

I normally suggest 20 to 25 GB for / (root) but then expect a much larger /home. With your size it is border line on whether a separate /home is an advantage. Either way with backups of /home it really is not critical to have separate /home. I often suggest /home for newer users and for more advanced users a /mnt/data partition so just data is in the separte partition and user settings are in /home inside /. 

My / uses 11GB including about 2GB for /home. All data is in data partition. My /home is larger as it also has .wine with Picasa which is about 1.5GB of the 2GB.

Thanks for replying oldfred. I have alway let Ubuntu install along side W7. I do clone my HD to 3 other HD's. Have had HD failure and lost everything. Learned you can never have too many backups.:) 
From the reading I have done it seems the / (root) could be from 10 to 20 GBs. I have never tried to set seperate partitions for Ubuntu. So would I be good to maybe set / to 10GB and swap to 1 GB and Home to the rest?

---

### Post by shojiimatsuro on 2014-11-25
From my expierience, you don't need an awful lot for your root partition because once you install your OS, and all your programs you use daily, the root partition doesn't really grow that much. It's the /home area that will be growing drastically with time with Documents, Music, etc. So I'd say 10G is fine for root, although a bit on the small size. To be safe, I think 15G is reasonable. That's just my opinion though. :)

---

### Post by QIII on 2014-11-25
Since installed applications go in /, 10GB may be too small for many users.  It can also become a problem when people don't clean up old kernels.  25GB is probably not unreasonable in these days of huge drive capacity.

Given your situation, however, 10GB may be appropriate.

But you will need to be careful and diligent.

---

### Post by mountainman70 on 2014-11-25
> **shojiimatsuro said:**
> From my expierience, you don't need an awful lot for your root partition because once you install your OS, and all your programs you use daily, the root partition doesn't really grow that much. It's the /home area that will be growing drastically with time with Documents, Music, etc. So I'd say 10G is fine for root, although a bit on the small size. To be safe, I think 15G is reasonable. That's just my opinion though. :)

Thanks shojiimatsuro, I was thinking about maybe going with 15GB for / and 1Gb for swap and 32.28 for Home. I will try that sometime later today.  
Thanks everyone for giving me some good advice.

---

### Post by mountainman70 on 2014-11-25
> **QIII said:**
> Since installed applications go in /, 10GB may be too small for many users.  It can also become a problem when people don't clean up old kernels.  25GB is probably not unreasonable in these days of huge drive capacity.

Given your situation, however, 10GB may be appropriate.

But you will need to be careful and diligent.

Thanks QIII, I do keep my Ubuntu drive clean by using Ubuntu Tweak. All of my HD's are 120GB. This is going on a test drive. I believe my computer will handle a 250 Gb HD. But being on a fixed income I must make do with what I have for the time being.
Again Thanks for all the information.

---

### Post by irv on 2014-11-25
I am not sure if this is a laptop or desktop. If it is a desktop I would put in another 120 gig HD. You can find them for about $25 on [Amazon.]("http://www.amazon.com/Seagate-ST3120026AS-Internal-Barracuda-Drive/dp/B0000A576B")  If it's a laptop then you would have to replace the drive and that would cost much more because you have to double the size.
Another thing to think about would be, How much do you use windows? If only once in a while for a few things then you could shrink it and use more for Ubuntu. I have windows on my laptop and only go into it a few times a year. I use Linux about 99% of the time.

---

### Post by mountainman70 on 2014-11-25
> **irv said:**
> I am not sure if this is a laptop or desktop. If it is a desktop I would put in another 120 gig HD. You can find them for about $25 on [Amazon.]("http://www.amazon.com/Seagate-ST3120026AS-Internal-Barracuda-Drive/dp/B0000A576B")  If it's a laptop then you would have to replace the drive and that would cost much more because you have to double the size.
Another thing to think about would be, How much do you use windows? If only once in a while for a few things then you could shrink it and use more for Ubuntu. I have windows on my laptop and only go into it a few times a year. I use Linux about 99% of the time.

It is a Dell Optiplex 745 Desktop and I only have room for one HD in computer. You are right about W7. Like you I keep it updated, but only use it for a couple of programs that won't work in Linux at this time. I'm not at my computer at this time, but I think I have about 17 point something GB of unused space left in W7. I could shrink W7 5GBs and add that to the Ubuntu partition. That would leave me with about 12 GB of unused space in W7 and give me 53.28 GB in Ubuntu so I could then have / at 20Gb. Does that sound like a plan?
Later I hope to upgrade to a better computer. Of course it will be someone's used.

---

### Post by irv on 2014-11-25
How about a 320 gig HD for $28. [LINK]("http://www.amazon.com/Western-Digital-Caviar-Drive-WD3200AAJS/dp/B000Q85WOK/ref=sr_1_6?ie=UTF8&qid=1416940591&sr=8-6&keywords=Desktop+hard+drive") (seeing you only have room for one drive) I myself would quit fighting the restriction and beef up the storage. Even if you get a different computer down the line who ever uses this computer will benefit by this move.  If you went this route, you could pickup an external case mount the old drive in it and use it for backups.

---

### Post by mountainman70 on 2014-11-25
> **irv said:**
> How about a 320 gig HD for $28. [LINK]("http://www.amazon.com/Western-Digital-Caviar-Drive-WD3200AAJS/dp/B000Q85WOK/ref=sr_1_6?ie=UTF8&qid=1416940591&sr=8-6&keywords=Desktop+hard+drive") (seeing you only have room for one drive) I myself would quit fighting the restriction and beef up the storage. Even if you get a different computer down the line who ever uses this computer will benefit by this move.  If you went this route, you could pickup an external case mount the old drive in it and use it for backups.

For some reason I thought that 250GB was as high as I could go in this computer.

---

### Post by mfilacchione on 2014-11-25
I agree with every one's points on here and of-course if possible another drive would greatly help.

When  manually partitioning make sure (or in my opinion) make a decent swap  partition.  When I first manually setup Ubuntu up I did not  add the swap and the OS seem to crawl.
 I currently  have my main set-up on Crucial SSD 240 gig drive.  I am running EduUbuntu  14.04.01 along side Windows 7 for those pesky games that do not run so easily under ubuntu. It works great so in the end I say it is all about what resources  you have and what your plans are for the OS... :)  games that do not want to  easily work under Ubuntu.

My current Partition goes as this 30gig  root , 80gig home, and since I have 8 gigs of ram I have given my self  14 gig swap.  In addition I have 3 1tb WD BLACK series drives where I  have added 120gigs of a temp partition.   Of course the temp is not  really needed as separate but I do this because I am trying to save the  life span of SSD since I do allot of video recording so..

But  even with out all that I set up Ubuntu 14.04.01 on a HP mini notebook  recently and only gave like 18 gigs for root 20 for home and 2 for  swap.  It works great so in the end all I cam say it is about what resources  you have and what your plans are for the OS... :) Either way it seems Ubuntu will do it's best to adapt

---

### Post by shojiimatsuro on 2014-11-25
I just wanted to mention (and perhaps help mfilacchione in the process), that swap isn't that huge of a deal depending on your hardware. Frankly, if you have 8G of RAM you wouldn't even really need a swap file at all. All swap does is act as an overflow type of system for when/if your computer ever uses up all the RAM on your computer, it will then start using swap as a virtual RAM of sorts. Typically you'd be fine with 1G of swap. The size of swap has no effect on your computer's responsiveness, unless your computer has 1G of RAM and have so many programs running at the same time that it's constantly accessing the swap partition.

---

### Post by mfilacchione on 2014-11-25
> **shojiimatsuro said:**
> I just wanted to mention (and perhaps help mfilacchione in the process), that swap isn't that huge of a deal depending on your hardware. Frankly, if you have 8G of RAM you wouldn't even really need a swap file at all. All swap does is act as an overflow type of system for when/if your computer ever uses up all the RAM on your computer, it will then start using swap as a virtual RAM of sorts. Typically you'd be fine with 1G of swap. The size of swap has no effect on your computer's responsiveness, unless your computer has 1G of RAM and have so many programs running at the same time that it's constantly accessing the swap partition.

To Added; as stated earlier I do allot of Video editing at times that simply shreds my Ram... So as started earlier depends what you are planning on doing with it ;)

Oh I forgot to add that my board limit is 8 gigs or I would get more.  It's really not the recording or anything just mostly ate up with the conversion. Other then that my photo editing eats up a lot to so I sort of look at it from a power user stand point. Power user on a budget system lol...

---

### Post by mountainman70 on 2014-11-25
Thanks everyone for all of your advice. 
Just to answer a few questions. I do not do any video editing or gaming. I might watch Netflix and Xfinity TV Shows at times. So you can see I am just a basic user. Ubuntu 14.04 has been running fine. I recently learned how to add a swap file to my OS and I could not tell any difference from before.
Since this will be on a test Dual Boot 120GB drive, I think I will go with what I posted above and see how it works.
I also will be looking into getting bigger HD's.

Thanks.

---

### Post by mfilacchione on 2014-11-25
> **mountainman70 said:**
> Thanks everyone for all of your advice. 
Just to answer a few questions. I do not do any video editing or gaming. I might watch Netflix and Xfinity TV Shows at times. So you can see I am just a basic user. Ubuntu 14.04 has been running fine. I recently learned how to add a swap file to my OS and I could not tell any difference from before.
Since this will be on a test Dual Boot 120GB drive, I think I will go with what I posted above and see how it works.
I also will be looking into getting bigger HD's.

Thanks.

Keep learning and testing that is what is all about :)... for example; I played with setting up several different directories and in different partitions that are not needed just learn and see what difference they may make for my build. Just as you said earlier keep good backups ;).   At any rate though I recommend you keep some sort of swap their, even your windows OS creates a page file system that sort of acts sort of the same as swap in Ubuntu...  I wish you the best of luck!

---

### Post by mountainman70 on 2014-11-27
> **mfilacchione said:**
> Keep learning and testing that is what is all about :)... for example; I played with setting up several different directories and in different partitions that are not needed just learn and see what difference they may make for my build. Just as you said earlier keep good backups ;).   At any rate though I recommend you keep some sort of swap their, even your windows OS creates a page file system that sort of acts sort of the same as swap in Ubuntu...  I wish you the best of luck!

I have partitioned my Ubuntu partition like I said in the previous post. I am in the process of installing Browsers and bookmarks and passwords. 
My main browser is Pale Moon with Firefox #2 and Chrome for netflix and Xfinity TV Shows. 
I have run into a problem with Chrome. Netflix and Xfinity both run fine and I can browse any web site. However when I try to add a couple of extensions, like Adblock Plus, my mouse pointer freezes when the extension page opens. I have to do Crtl-Alt-Delete and use arrow to restart.
I just tried Chromium and had the same result. Both work fine on my other HD's with Ubuntu14.04 on one partition.
Anybody else ever had this problem?

---

### Post by mfilacchione on 2014-11-27
> **mountainman70 said:**
> I have partitioned my Ubuntu partition like I said in the previous post. I am in the process of installing Browsers and bookmarks and passwords. 
My main browser is Pale Moon with Firefox #2 and Chrome for netflix and Xfinity TV Shows. 
I have run into a problem with Chrome. Netflix and Xfinity both run fine and I can browse any web site. However when I try to add a couple of extensions, like Adblock Plus, my mouse pointer freezes when the extension page opens. I have to do Crtl-Alt-Delete and use arrow to restart.
I just tried Chromium and had the same result. Both work fine on my other HD's with Ubuntu14.04 on one partition.
Anybody else ever had this problem?

Could be a possible issue with the extensions, maybe bad install of them  or ect.  I can not remember the commands off hand but google to see if  you find the commands to run chrome with out extensions enabled.  Once  their disabled I would attempt to see if the issue still occurs or if  you can go in and remove the  extensions that way. 

If none of  this helps I would suggest install an reinstall of the browser and then  reinstall the extensions.  I would also create a new thread related to  your new issue.  That way it can get the best exposure for more help.   Let me know how it all goes.

---

### Post by mountainman70 on 2014-11-28
> **mfilacchione said:**
> Could be a possible issue with the extensions, maybe bad install of them  or ect.  I can not remember the commands off hand but google to see if  you find the commands to run chrome with out extensions enabled.  Once  their disabled I would attempt to see if the issue still occurs or if  you can go in and remove the  extensions that way. 

If none of  this helps I would suggest install an reinstall of the browser and then  reinstall the extensions.  I would also create a new thread related to  your new issue.  That way it can get the best exposure for more help.   Let me know how it all goes.

Thanks mfilacchione, but this is a clean install of Ubuntu 14.04 running Unity, no bookmarks, passwords or extensions and a clean install of Chrome and Chromium without any of same. All I do is open Chrome and I can surf anywhere, but when I click on "Settings" and then click on "Extensions" and "Get more Extensions" as soon as the page opens the mouse freezes.

---

### Post by mfilacchione on 2014-11-29
> **mountainman70 said:**
> Thanks mfilacchione, but this is a clean install of Ubuntu 14.04 running Unity, no bookmarks, passwords or extensions and a clean install of Chrome and Chromium without any of same. All I do is open Chrome and I can surf anywhere, but when I click on "Settings" and then click on "Extensions" and "Get more Extensions" as soon as the page opens the mouse freezes.

OK that is a little more clear.  I just took a look at the page, I have not used extensions in chrome in a long time, I wonder if Flash or Java is needed for the page to load.  Since you said stated that it is a clean install have you ran the updater since the install? Can you verify if you have flash player installed? If not I would suggest installing  Flash and Oracle Java.  you can easily google PPA's for booth

Other than that It sill could be simply a corrupt install of the browser.  Which is still believable to me, even if you are able to view other web pages, I have seen weirder.  If all else fails un-install and reinstall the browser.

---

### Post by mountainman70 on 2014-11-29
> **mfilacchione said:**
> OK that is a little more clear.  I just took a look at the page, I have not used extensions in chrome in a long time, I wonder if Flash or Java is needed for the page to load.  Since you said stated that it is a clean install have you ran the updater since the install? Can you verify if you have flash player installed? If not I would suggest installing  Flash and Oracle Java.  you can easily google PPA's for booth

Other than that It sill could be simply a corrupt install of the browser.  Which is still believable to me, even if you are able to view other web pages, I have seen weirder.  If all else fails un-install and reinstall the browser.

I have been out of state for the last month and I only had slow Wifi where I was staying. I checked my other HD's that I thought Chromium was working correct and found that as soon as I opened extension page to DL an extension the mouse froze. I had cloned both HD's while there to keep everything up to date. I first thought that the slow Wifi was corrupting the DL's. I just got home and on my second test computer I opened Chromium, opened the extension page by clicking "Settings" and then click on "Extensions" and "Get more Extensions"and the mouse would still move. I then updated Ubuntu 14.04 and with the last extension page open I could move mouse pointer while Updater was running. I then restarted Ubuntu and when I went to "Get more Extensions and the page opened I got the error "Ah Snap". It has to be an update in Chromium and Chrome that is causing this. 
Since I only use three extensions in Chrome and Chromium and only use it to watch Netflix and Xfinity on line TV I am not going to worry about it for now. After I get caught up on everything I may start a new thread and see if anybody can help fix this problem.
Thanks for your help mfilacchione.

---

