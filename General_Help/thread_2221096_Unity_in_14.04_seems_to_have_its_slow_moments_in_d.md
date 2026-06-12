---
title: "Unity in 14.04 seems to have its slow moments in dash... why?"
date: 2014-04-30
forum: General Help
---

### Post by Roasted on 2014-04-30
Hello friends. I am running several instances of Ubuntu 14.04, all fresh installs, and I'm facing the same thing on each.

Lenovo laptop, i5 Sandy Bridge processor, 2.26 GHz with 8GB DDR3 RAM, Intel integrated graphics.
Toshiba laptop, i5 Sandy Bridge processor, 1.60 GHz with 6GB DDR3 RAM, Intel integrated graphics.
ASUS laptop, i3 Ivy Bridge processor, 2.5 GHz with 4GB DDR3 RAM, Intel integrated graphics.
Custom desktop, i3 Sandy Bridge processor 2.5 GHz, 8GB DDR3 RAM, Nvidia graphics with open source driver.

There are times at random when I open the dash and using my mouse, try to click on something. The thing is, at times Unity seems to be doing a refresh of the icons listed, as if it's reordering the icons based on the last time I used that specific application. Just as I go to click, it rearranges the order, and I end up clicking on an icon I didn't intend to click.

Example:

My last used application was gedit, so gedit is the first item listed in recent items within the dash. If I then open nautilus through the Unity bar, close it, and go to dash, at times (not all the time) this is where the dash sits, and a few seconds later reorganizes the icons, thereby putting nautilus as the 1st, and gedit as the 2nd. But in that time, I already navigated my cursor to slot 1 to open gedit again, only to hit nautilus as Unity figured out at the last second that slot 1 is now reserved for nautilus since it was the most recently used.

Given the fact that my hardware is not exactly puny I'm not understanding why this is the case. All fresh installs and whatnot. I tinkered with the blur settings but that seems to have zero impact. The blur adjustments (static vs active) seems to only come into play with actually entering the dash mode. The issue I'm seeing is an occasional slowness of where Unity/dash has to figure out, oh wait, nautilus was the most recently used application so let me reorder that icon to the 1st slot.

Another work around for me personally could be to disable the recently used applications, which I can do through Unity Tweak Tool and is fine, but I still find myself wondering about this. Speaking of Unity Tweak Tool, is there a way to disable more suggestions + recent applications besides Unity Tweak Tool? Or is the tweak tool needed for that?

EDIT - It's worth noting that I have disable the online sources on all of these systems as well.

---

### Post by deadflowr on 2014-04-30
I find the online search function slows the dash.
Which is why I personally disable it.

I too, have noticed multiple refreshes of my recently used list whenever I have the online search function on.

FWIW

---

### Post by Roasted on 2014-04-30
I should have notated that first and foremost I always disable the online sources. I'll edit that above.

---

### Post by deadflowr on 2014-04-30
I open the dash and then also go to Filter Results, I set only Applications and file and folders.
Then I make sure the rest of the filters are disabled.

---

### Post by grahammechanical on 2014-04-30
The Dash is presenting the recently used applications and documents. It has to do that refresh. It does it quite fast on my machine but I do sometimes get caught out clicking an application icon only for the Dash to rearrange the order of icons just as I am clicking and I load the wrong application.

---

### Post by fkkroundabout on 2014-05-01
dash is quite intensive, looks through a very large number of files, and lately, even the internet. probably be faster with a fast HDD or just any SSD. i'm sure you could turn off how much it searches somewhere, but i don't use unity

---

### Post by Roasted on 2014-05-01
> **fkkroundabout said:**
> dash is quite intensive, looks through a very large number of files, and lately, even the internet. probably be faster with a fast HDD or just any SSD. i'm sure you could turn off how much it searches somewhere, but i don't use unity

3 of these 4 machines have SSDs.

I'm sorry, but I'm tired of making excuses for Unity. It's great in 14.04, but it has its moments where it's just not that fast. There's no excuse for this type of hardware to have its moments where it lags up. Sometimes it's as much as 4 to 5 full seconds.

So as a result, that's what has me curious if there's any additional tweaks to do. For the time being I just got into the habit of doing super A for my applications. It's not that different from my last distro, elementary OS, where you had to super + space to launch the applications menu, so whatever. At least Unity isn't trying to do its resync, which as the dash has clearly exhibited, is still quite slow at times.

Perhaps brighter days ahead with Unity 8 on the Qt build, yes? Until then I'll roll with this if nobody else has any suggestions.

Oh, speaking of which - when you use the filters, do they stick? Like if I reboot will they be held? (I'd try now but I have quite a few VMs running that I'm working on/updating...)

---

### Post by fkkroundabout on 2014-05-02
hmmmmmmmmmm definitely software side problem, then. perhaps you could try a different launcher

---

### Post by Roasted on 2014-05-02
> **fkkroundabout said:**
> hmmmmmmmmmm definitely software side problem, then. perhaps you could try a different launcher

A different launcher? Instead of using Unity? Doesn't that sound kind of like buying a brand new car just to swap out the engine just because? I mean, not to sound like a self righteous user of free software, but the car should work acceptably from the second it gets driven off the lot...

---

### Post by fkkroundabout on 2014-05-03
i am not an advocate of unity, personally, but i only discovered LXDE & numix when 14.04 was released. before that i was on cinnamon with minty, which, compared to LXDE, does feel bulky like unity too.

was also thinking today, perhaps it could be that unity is indexing files in the background, so speed would improve after an hour or three depending on quantity of files. at least, that would be the case with somewhat similar OSX

alternative: perhaps xubuntu with a launcher ? seriously i would highly recommend other desktop environments if you haven't tried already. generally most linux desktop environments copy windows or mac, with some a little in between. and one desktop environment per user tends to work better than mixing everything up too much, then things can begin to clash

---

### Post by Roasted on 2014-05-03
I've been through every desktop environment on nearly every distribution in existence. I come back to Unity and Ubuntu for a multitude of reasons. I am very happy with Unity. I just find these random hangups to be a nuisance.

Perhaps Unity 8 on the Qt build will yield a difference. Until then disabling recent applications definitely helps, but it makes the 'home' screen even more useless, since the only thing that shows then is recent files. But hey, super+a, it's acceptable. 

I have a feeling that only the anal users out there like myself really notice this. My wife has said approximately zero about it and she's quite liked Unity.

---

### Post by monkeybrain20122 on 2014-05-03
The dash is always slow the first time you use it at each session because of some updating and initiating I suppose. After the initial load it becomes fast and immediate.

---

### Post by Roasted on 2014-05-03
> **monkeybrain20122 said:**
> The dash is always slow the first time you use it at each session because of some updating and initiating I suppose. After the initial load it becomes fast and immediate.

I noticed this too, but what I'm talking about is several hours into the workday...

---

### Post by monkeybrain20122 on 2014-05-04
> **Roasted said:**
> I noticed this too, but what I'm talking about is several hours into the workday...

That I don't know. I have my laptops on for hours and hours and the dash is always fast. it is not some super computer, just a refurbished Dell Latitude 5510 (corei5 M460, 4Gs of ram), same with my old laptop (with only 3 Gs of ram) and another 4 year old hp netbook that I just set up for a friend. I disable online search on all of them

---

### Post by Roasted on 2014-05-05
Here's what I'm talking about. Take note how searching for Audacity hangs, while other searches are quicker. This Audacity-esque search happens at random with any application just at random times. It's beyond frustrating to be in the mode and bam, it happens.

It happens on literally every single computer I've tried. I'm not talking low end netbooks or 10 year old laptops. A darn i5 should be more than plenty to push Unity with ease.

[https://www.dropbox.com/s/34wlzxexthn9oid/Screencast%202014-05-05%2010%3A03%3A42.mp4](https://www.dropbox.com/s/34wlzxexthn9oid/Screencast%202014-05-05%2010%3A03%3A42.mp4)

And again, all online search is disabled on every machine...

EDIT - I think I mentioned it before, but I ended up re-enabling "recent applications" in the dash prior to today. Since I posted above I removed it again. Since then at random times I've hit the super key and quickly searched for a series of different applications. Not once has it lagged. I wonder if it has something to do with the algorithm/scanning process of recent applications that it needs to churn through enough code to make it feel sluggish during these random blips of time. At any rate, I am growing increasingly disinterested in the recent applications anyway since they continually change location, which makes me have to pause and scan each icon to find the application I want. Compare this to a series of shortcuts on say my phone or tablet where I simply click on it based on memory of location alone and NOT the icon of the app I want to launch. As a result, this functionality has me a little meh, and the increased speed I am (so far) seeing is a definite +1. We'll roll with this and see how it goes.

---

