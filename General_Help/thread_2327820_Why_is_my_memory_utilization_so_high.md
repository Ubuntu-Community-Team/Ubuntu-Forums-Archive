---
title: "Why is my memory utilization so high?"
date: 2016-06-14
forum: General Help
---

### Post by xeddog on 2016-06-14
I WAS running Ubuntu 15.10 on an older machine that has an Intel I7-920 processor and 8GB ram.   It sorta worked but SOMEthing was always crashing and it was something different almost every time.  I found the SMART data for my disk and saw a buttload of read errors to I replaced the disk and did a clean install.  That didn't help at all.  Then I found I had some mismatched DIMMS.  I got that straightened out, but that left me with only 6GB RAM.  

That may only be relevant because when the machine had 8GB RAM, even though something or other kept happening, memory utilization was always low.  According to the system monitor, memory use was always down to around 25% or less and swap was always zero and that is while running all of my applications.  Since reducing to 6GB ram, memory utilization is at 50% immediately after the boot is completed and before any applications or anything else have been launched.  Sometimes there will even be small amount of swap allocated.  Now when I have my applications launched, memory shows 75-80% utilized and swap is up to about 30% or more of it's maximum.

According to the screenshot, three of the four processes using the most memory are indicator-something-service.  Those 4 by themselves are using almost 2GB RAM, so there goes more than 33% of my memory right there.  Why are those processes using so much memory?

Thanks,

Wayne

---

### Post by mastablasta on 2016-06-15
what are you using to measure ram usage? "top" command or "htop" maybe?

usage should not be so Hugh. on boot it should be between 400 and 500 MB i believe.

what is the GPU chip? is the chip using the system ram or is it a separate graphics card with it's own ram?

---

### Post by Bucky Ball on 2016-06-15
> **xeddog said:**
> According to the screenshot, three of the four processes using the most memory are indicator-something-service.

Help us help you by being specific and providing the exact services in question. We can't do much with 'indicator-something-service'. Thanks. ;)

---

### Post by xeddog on 2016-06-15
Well [expletive deleted]!  I guess it might help if I actually included the screenshot.

Also, there is a nVidia GeForce GT220 graphics card installed.

---

### Post by Bucky Ball on 2016-06-15
Are you using those indicators you have highlighted in the screenshot on your panel? If no, disable in 'Session and Startup'. I have none of them installed, although I'm using xfce4 as a desktop environment. Looking at what they do, unless you're using them intentionally, you could probably even uninstall them, but unsure of the impact of that on Unity, if any. 

As for the Unity entry, not using Unity or Ubuntu so not sure whether that needs to be enabled, but looking in Synaptic at what it does I'd say yes, leave it until a wiser head says otherwise, as disabled may cause chaos. :| ;)

---

### Post by xeddog on 2016-06-15
The only indicator app in the start-up is indicator-application-service.  I think all of these indicator-* applications are part of unity and can't be disabled.  Once, I tried using the system monitor to kill them one at a time.  I saw a drop in memory usage in system monitor, but they would immediately start back up and memory usage with it.  I also have my primary computer running Ubuntu 15.10 as well.  The system monitor shows those four applications using 26.4MB IN TOTAL, and it has 6 applications running at the time.  I also have a third old machine running Ubuntu 16.04, and immediately after boot the four applications are using about 21MB total.


Wayne

---

### Post by Bucky Ball on 2016-06-16
You're on 15.10 still and you have just installed 15.10 on this machine and that's what we're working on? I'd install 16.04 LTS and see how you go. 15.10 has about a month of support left, at which time you'll need to upgrade to 16.04 anyway and all this fixage will be for nought.

Not a fix for this problem in this install directly, but will probably save you some time in the long run.

---

### Post by mastablasta on 2016-06-16
you can also try switching to another destkop or osme fallback mode and see if that helps. it could be a bug. those services shouldn't ieat ram unless there is a memory leak.

---

### Post by Bucky Ball on 2016-06-16
> **mastablasta said:**
> ... it could be a bug. those services shouldn't ieat ram unless there is a memory leak.

+1. Something is amiss.

---

### Post by xeddog on 2016-06-16
Thanks for the replies.

For the time being I'd rather not upgrade to 16.04 because 16.04 installs PHP7 and the applications I am using require PHP5 for now.  They do offer a solution that involves adding a PPA for the php5 stuff, but I am hoping that they will come up to php7 level sooner rather than later.  I'd just rather not fart around with PPAs because sooner or later they get abandoned.  It may come to that, but for now . . .

Now I hadn't thought about a different desktop.  That is a definite maybe.  :-)  xfce4 is light and clean and would probably do just fine for this machine.  Actually, practically anything would do besides Unity.

Wayne

---

### Post by xeddog on 2016-06-16
OK, I put up xfce4 and according to system monitor, the memory utilization is much lower, but still looks a little wonky.  With my applications running, memory utilization shows a little less than 40%, but swap is already up to over 5%.  Back when the machine had 8GB ram, the memory utilization rarely ever got to 40%, but the swap was ALWAYS 0.  Even though I am down to only 6GB ram, at 40% memory utilization I think the swap should still be zero.

I think I'm just going to have to bite the bullet and re-install again.

Oh, even though I still think there is something amiss, the system is MUCH more responsive with Xfce4.  It looks like the overall cpu utilization is more levelled out and lower too.

Wayne

Man!  Getting used to the launcher at the bottom of the screen is tough.  :biggrin:  Now that I think about it, so is having the close button on the right of the menu instead of the left.  Sheez.  Never satisfied.

---

### Post by Bucky Ball on 2016-06-17
How many RAM sticks do you have in there? Have you done a RAM check? Are you sure they are all matched and all fully functional?

You could test them one by one. Take them all out, put them in slot one, one by one. All good, test slot two, slot three, slot four ONLY, with one stick in one slot ONLY, no sticks in the others. All slots and sticks good?

(Off-topic: Move the panel at the bottom to the top or get rid of it. I only ever use one panel across the top. ;) xfce4 is extremely flexible. You can also right click icons on the panel, 'move' and move them to where you want. So if you don't like the buttons on the right, move them.)

---

### Post by xeddog on 2016-06-17
The ram I have in the machine now is a matched set of 3 Patriot 2GB DIMMs for 6GB total.  The were purchased as a matched set, and they do indeed all have the same part numbers, etc.  They are installed in the slots as shown in the motherboard manual, slots 1, 2, and 4.  I did run the memtest on the 6GB before using the machine, but I only let it complete a single pass.  Since correcting the mismatched DIMMs I had before, nothing has crashed or otherwise become dis-functional or suspect, so I didn't think it was necessary for additional memtests.  It's just the  high memory usage, and that has dropped A LOT by switching to xcfe4 desktop.  The machines performance has also increased significantly with xfce4(make that SIGNIFICANTLY), so that tells me that there is something knackered in Unity.

One more thing, I don't know if this is fact or not, but it seems like the memory utilization increases every time I boot the machine with Unity.  Like some memory from the previous boot is cached and never gets freed.    I might look into this further.

(off topic - moving or removing the bottom launcher won't help because the Unity launcher is along the left edge of the screen.  Having the launcher(or panel if you prefer) anywhere else now is just hard to get used to.  The maximize/minimize/close buttons on the windows are on the top right with xfce (and every other desktop I know of in the civilized world including Windows), but for some reason the Unity folks decided they would be better on the top left corner.  And for all the ranting and raving about how customizable linux is, this is one that is NOT customizable.  :-({|= )


Thanks,

Wayne

---

### Post by Bucky Ball on 2016-06-18
> **xeddog said:**
> (off topic - moving or removing the bottom launcher won't help because the Unity launcher is along the left edge of the screen.

Sorry, thought you were talking about xfce4. Ignore. I know nothing about Unity. Don't like it. :| ;)

---

