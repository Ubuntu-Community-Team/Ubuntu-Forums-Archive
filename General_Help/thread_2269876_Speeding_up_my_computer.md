---
title: "Speeding up my computer"
date: 2015-03-18
forum: General Help
---

### Post by Ifaistos on 2015-03-18
Hello everyone :-)

I have an old computer intel dual core with 4 gigs of memory.
To tell you the truth I don't remember the exact specifications.

If there is a program that can identify all the components please let me know, and I will provide screenshots.

Lately I have been using a lot of programs that I need to have opened at the same time.

I use 6 desktops.
1. Thunderbird.
2. Firefox & Chrome (3-4 tabs open on each one.. sometimes more)
3. Open office with just one spreadsheet open.
4. XnView

I switch between them a lot.  I have noticed that as soon as my swap starts to get "occupied" then it's all downhill from then on.
My computer starts to stall to the point that I need to close everything and reboot in order to clear the memory and the swap and start all over again.

Can anyone suggest a solution as to what I can do to speed up my computer.. other than the obvious of upgrading or buying a new computer?

Whatever you need in terms of specs in order to give me a more detailed answer please ask and I will provide screenshots or whatever else you need.

Thank you all in advance !!

---

### Post by nerdtron on 2015-03-18
Open you normal set of programs and just run the system monitor. You can see there the list of process and their memory usage.

And 4Gb is ample enough for normal usage. But if you still want to squeeze out more RAM, you can try lighter Ubuntu alternatives like Xubuntu.

---

### Post by Ifaistos on 2015-03-18
Thank you for your answer :-)

I have done that already.  I have always the "System Load Indicator" running and checking the load.  Opening also the System Monitor to check for memory usage.  I believe that Chrome is causing "spillage" but I can't prove it.

But if I leave my computer open overnight without doing anything, next morning I see that the swap memory has been used and it is occupied even though when I left it, there was no swap memory used.

I was wondering if there was any software constantly checking that and clearing up my memory.

To give you an indication this is my memory usage as reported my by the system monitor right now.

Right now I have only 3 Chrome tabs open, but do you see how many Chrome instances are open... Isn't that weird?


[ATTACH=CONFIG]260719[/ATTACH]

---

### Post by nerdtron on 2015-03-18
I'm not using chrome (though I have chromium) and it really is weird for just a single window with only three tabs. I believe chrome have a separate process for each tab and each plugin running but I yours are too many for just a single window.

> But if I leave my computer open overnight without doing anything, next  morning I see that the swap memory has been used and it is occupied even  though when I left it, there was no swap memory used. 
That is normal behavior.

---

### Post by v3.xx on 2015-03-18
Could this tie in?

[http://ubuntuforums.org/showthread.php?t=2267828](http://ubuntuforums.org/showthread.php?t=2267828)

---

### Post by Ifaistos on 2015-03-18
How about my memory usage?  Is it normal to eat up so much memory with the amount of programs opened?

Is there any programs, software, technique that could help me?

Anyone, please?

---

### Post by nerdtron on 2015-03-18
I don't think it is a system problem, I think it's a problem of chrome.

---

### Post by mattharris4 on 2015-03-20
> **Ifaistos said:**
> How about my memory usage?  Is it normal to eat up so much memory with the amount of programs opened?

Is there any programs, software, technique that could help me?

Anyone, please?

No, this is not normal.  I run Edubuntu 14.04 on my 32 bit computer and maximum use 2.6GB of RAM with 7-8 tabs open and that is only on one site that is especially RAM-hoggy.  Most sites use 1.4-2.0GB RAM.  However, I do not use Chrome much, I prefer Firefox.  Chrome is known to be a RAM hog in and of itself but in your case it is riduculous, other than removing and reinstalling the program I am at a loss as to how to assist you.  I would install Firefox and then the Pepper Flash plug-in, both off of the Ubuntu Software Center (Pepper Flash is needed to use Flash features on web pages, the Chrome Flash plug-in only works with Chrome whereas Pepper Flash works with Firefox and Chromium).  Midori is especially light but half of the special features of web pages will not work correctly using it (Midori is intended for especially RAM constrained computers, you have plenty or RAM so that should not be an issue here) so that browser is likely not worth installing in your case.

I can attest to swap being just about useless on Ubuntu and its derivatives, I had to upgrade my RAM from 2GB to 3.5GB because once I maxed out RAM my computer slowed to a crawl.  In my experience about all swap is good for in Linux is for hibernation and to save your work once you manage to max out RAM, without a swap you would completely crash your computer attempting either one.

---

### Post by Ifaistos on 2015-03-21
Hello Matt and thank you for your answer.

I suspect that smt weird is going on but I can't figure out why.  
As you can see on my screenshot I think that Chrome is the issue.
But Chrome on the other hand is way much faster with some plugins that I use it for.
I used the same plugin with firefox, and it was not possible to work at all!!

So do you know, or anyone else for that matter, any tests that I could run, or software to install to track what is going on with my system.

It's just NOT logical that 4Gigs of Memory is not enough to run the above mentioned programs.

Thanks everyone  !  :-)

---

### Post by gordintoronto on 2015-03-21
Here is a way to see the specs for your computer. Open a terminal windows and: cd Desktop
sudo lshw -html >config.htm

This should put a file on your desktop. Double-click it, and you will see the blow-by-blow about your computer.

You might be able to solve your performance problem by adding more memory. It needs to be somewhat compatible with your existing memory.

---

### Post by oldos2er on 2015-03-22
You could run memtest overnight to see if there are any issues with your RAM. Memtest should be one of the options you see in the grub menu.

Have you tried adjusting swappiness? The default level of 60 is too high, in my opinion. See [https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by Ifaistos on 2015-03-23
Thank you for your suggestion.

I run the command, but I can't upload the file here for everyone to see.
I get the error : Invalid file when I try to upload it.

Does anyone know how I can do that?

> **oldos2er said:**
> You could run memtest overnight to see if there are any issues with your RAM. Memtest should be one of the options you see in the grub menu.

Have you tried adjusting swappiness? The default level of 60 is too high, in my opinion. See [https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

Thank you for your answer.
The problem is not the "swapiness".  It has to swap because the 4Gigs are not enough !!

What I am trying to find out is why?

Of course adding more memory would be a solution, but still 4 gigs for so little?!

It just doesn't make any sense.. !!

---

### Post by matt_symes on 2015-03-23
Hi

For an answer as to why chrome has so many open processes, you may want to take a look at this blog post from some of the developers. It's an older article but it's still relevant.

[http://blog.chromium.org/2008/09/multi-process-architecture.html](http://blog.chromium.org/2008/09/multi-process-architecture.html)

Lower the swappiness value as suggested by oldos2er. I have been setting mine to 10 for a long time. 60 is too high in my opinion also; on my machines at least. Linux will be more likely to shrink the buffers and cache than swap out pages if you do this (or at least that used to be the case. Been a while since i looked at Linux memory management).

You may also be suffering from a memory leak.

Kind regards

---

### Post by mattharris4 on 2015-03-23
> **Ifaistos said:**
> Hello Matt and thank you for your answer.

I suspect that smt weird is going on but I can't figure out why.  
As you can see on my screenshot I think that Chrome is the issue.
But Chrome on the other hand is way much faster with some plugins that I use it for.
I used the same plugin with firefox, and it was not possible to work at all!!

So do you know, or anyone else for that matter, any tests that I could run, or software to install to track what is going on with my system.

It's just NOT logical that 4Gigs of Memory is not enough to run the above mentioned programs.

Thanks everyone  !  :-)

It is definitely not logical for 4GB of RAM to not be enough for surfing the web.  If you were editing videos filmed in 4K or something I could see it but for normal usage it shows something is wrong.

I do have one question for you, though.  What plug-in are you attempting to use that will not work in Firefox?  Maybe there is a different version for that browser and that is the reason your current copy does not work in it.  Without the name of the plug-in I am at a loss as to what advice to give next.  There are those few things that only work in one browser, though.  There is one website I use that will only play videos on my computers using a supported version of Windows and then only with Internet Explorer (admittedly I haven't tried a Mac with it).  That site uses HTML5 (rather than Flash) which is a relatively new technology.  However, that isn't the case with 99.99% of websites.

I do agree that Chrome is slightly faster when it works correctly but IME it is less reliable whether you use it in Windows or Linux (or Android for that matter).  

Good luck and I hope you find a solution to the issue.

---

### Post by Ifaistos on 2015-03-27
Quick Reply before I reboot with swapiness set to 10.

I couldn't find vm.swapiness so I added it.  I hope I don't "break" smt...

My swapiness was set to 60.

Will let you know how it went..

ok Rebooted.

My swapiness is set at 10.

Hello everyone :-)

First of all I would like to thank olddos2er for the suggestion of changing my swapinness.!!
I have noticed a great improvement by setting it to 10!

I have also upgraded to 14.10 (just in case) although it is not an LTS, and it solved a couple of other issues I had.

Matt_Symes thank you for your suggestions!  
I am under the impression that I do suffer from a memory leak.

So how should I go about it?

I was thinking of updating my Chrome (if it is not updated automatically).

This is my current version : Version 41.0.2272.101 (64-bit)

Update :

I think that the problem is with Chrome.

The longer I run it, and open and close tabs, the more memory it occupies.

Just a few minutes ago, my comp was "on it's knees" with swap memory used.

I closed Chrome, waited a little and reopened it.

It opened the exact same tabs I had opened but the available memory was like a 1 Gig more !!

Isn't this a typical behavior for memory leakage?

Could someone suggest a solution, if there is one?

For the time being I will be closing - opening Chrome regularly I guess..

---

### Post by matt_symes on 2015-04-01
Hi

Tracking down a memory leak can be a real pain. There are tools that can help such as top, ps, atop, vmstat, smem and pmem.

However, if you're convinced the problem is with Chrome then the first thing i would do is leave your computer running over night but with Chrome closed and check to see if the computer still has the massive amount in the swap partition the next day.

 The next thing i would do is start chrome with a clean profile and no extensions loaded. I am currently using Firefox as my main X browser so i am not sure how to do this in Chrome but a search on the Internet suggest something like this might work and is reversible.

Ensure Chrome is closed, open a terminal and type

```
mv  ~/.config/google-chrome-old/Default{,-old}
```

Open Chrome.

It's reversible with this command

```
mv  ~/.config/google-chrome-old/Default-old  ~/.config/google-chrome-old/Default
```

If others know of a better method to create a new profile in Chrome then please post it.

Kind regards

---

### Post by Ifaistos on 2015-04-28
Update

I have upgraded to Vivid.
Along with the swapinness set to 10, the bahaviour is way much better.

However I still can't open Firefox, Chrome and Thunderbird all at the same time, without risking that my computer becomes unresponsive for long periods of time (while swaps from memory to HD and vice versa).

As far as Chrome is concerned, I can't have it closed to run tests.  It HAS to stay open at all times because it is needed for my work.

I just thought the 4 Gigs would be enough.

I am looking for an affordable laptop with 8Gigs of memory, Quad Core and 120 GB SSD.
I don't mind if it is used.

---

