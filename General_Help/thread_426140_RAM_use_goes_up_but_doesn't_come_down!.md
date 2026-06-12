---
title: "RAM use goes up but doesn't come down!"
date: 2007-04-28
forum: General Help
---

### Post by floke on 2007-04-28
Is this normal?
I have 1G of RAM, which top shows to be idling at around 40% or so of use (am using E17). With Firefox open it runs at around 50%. But, if I use some music players - eg Rythmbox and do some listening and ripping then the use goes up and up - even if I turn the players off - and eventually starts cutting into the swap file (2G). So why doesn't the RAM use fall back to around 50% once the other apps have been closed?

---

### Post by HunterK on 2007-04-28
Impossible! What goes up, MUST come down! :)  Sorry, treat this as a free bump.

---

### Post by floke on 2007-04-28
Well my RAM use sat at around 40-50% for most of the day until I started using Rythmbox and K3B. Is now climbing above 92% and rising....

---

### Post by tgalati4 on 2007-04-28
Normal, normal, normal.

Linux will use most of your RAM as normal memory management.  Inactive pages are kept in RAM until they are either dumped or sent to /swap.  After a few days of use, your memory will always be at ~90% in use.  Especially with KDE.  I have used Lsongs in Freespire and it does the same thing.  I think it's written in Python and it tends to stay resident in memory.  Doesn't seem to affect the rest of the machine though.  Perhaps K3B and or Rhythmbox have higher-level code that would account for the memory use?

Try logging out and logging back in and see how the memory changes.  If it goes back down, then User processes were gobbling up memory.  If it stays high, then their may in fact be a memory leak somewhere.  There are several memory profiler tools available.  Some with cool graphics.  

Let us know what you find out.

---

### Post by KrazyPenguin on 2007-04-28
My RAM right at the moment is 38% processes and 44% cache.

So that totals 82%.

For more  info on cache:  
[http://en.wikipedia.org/wiki/Cache](http://en.wikipedia.org/wiki/Cache)

The cache is the reason your memory is higher.

---

### Post by floke on 2007-04-28
My current top readings are:
Mem: 1027288k total; 951172k used; 76120k free; 50092k buffers
Swap 2168732k total; 0k used; 2168732 free; 594876k cached

(figures might not add up exactly since are changing as I type them).

Will log out and log back in and reassess....

--
Here we are. Running just Firefox and xterm. Currently using 844100k of RAM with 594008k cached
After logging out and logging back in.

I'm going to turn all my apps off and walk the dog for half an hour. Will reassess then.

---

### Post by floke on 2007-04-28
ok so no change.
Is there any way I can flush the cache other than rebooting?
Just curious now really.

---

### Post by Slim Odds on 2007-04-28
> **Steve.K said:**
> ok so no change.
Is there any way I can flush the cache other than rebooting?
Just curious now really.

Why the concern?   You **want** your RAM to be **used**.  Why not?

The memory management in linux is smart enough to use it and to make the best use of it.

So relax and let it do it's job.

This is such a common misunderstanding. I think there needs to be a bit sticky that says "linux will use your RAM, and use it wisely".

P.S. I really get a kick out of people who want "unused" memory.

---

### Post by floke on 2007-04-28
Good point :)

---

### Post by Muppeteer on 2007-04-28
I've noticed this too...Usually i'll start off with about 160 - 200MB being used. That's with just generic services enabled and Beryl & conky. Once i start up firefox and Amarok it jumps to pretty much 50%, but this is expected...

One thing i've noticed in Feisty, it doesn't seem to like Azureus. Whenever i run it, it usually takes up 70% cpu and 200MB ram sometimes. Is there a Java problem? Can't remember the name of the service but i looked it up and it was java...:confused:

---

### Post by floke on 2007-04-28
Have been looking into this and have found a useful explanation here on the Gentoo wiki

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

The short explanation is that using the command 'free -m' will give a better readout of your memory usage than top - the line -/+ buffers/cache tells you how much memory is being used with buffers and cache, and how much without. So, at the moment I am using a total of 510meg of RAM - but only 206 if you discount buffers and cache.

I can relax now :)

---

### Post by BeardlessForeigner on 2007-06-13
Using free -m reports the same thing that the Memory panel applet shows. It says how much is being used by programs, and then the cache. After having one session going for a while the memory for programs climbs, and  system monitor reports that python is using somehing like 150 - 250 mb, and nautilus like 50 mb. After restarting my session these are down to 25 and 15 mb respectively. Not really a problem in that case, just curious what is happening.

---

### Post by headcronie on 2007-06-13
Weird findings.

Of 256mb RAM on my system, after 12days non stop running, my system sits at about 40% memory used.  I've got 196mb swap used, but I also had Gimp, Frostwire, Thunderbird, Totem, Xmms, and K3b open.  Close that all down, and I'm back down to 40% again.

Then again, I'm using Xfce desktop, insted of Gnome, or KDE.

---

### Post by rscott5 on 2007-06-13
I was just curious after reading all of this so I decided to check out my RAM usage. If I open both Azureus and Firefox, my memory use jumps up about 50-75MB...but then as soon as I close them it return to the exact same number as it was at before.

I understand that that's what it should be doing but am I the only one here who has that happen? Everyone else seems to be saying that their memory use just stays the same even after closing the apps.

---

### Post by headcronie on 2007-06-13
No, my RAM drops back down to pre-use numbers after I close my applications.

---

### Post by BeardlessForeigner on 2007-06-20
The memory being used by firefox comes back if I close firefox. But the process "python" escalates in memory usage, and doesn't sound like something I should end. Right now its at 170 mb, after being logged in since yesterday and doing alot of web browsing and opening various apps. If I relogin, itll drop down to 25. I'm just a little curious about this is all.

Edit: Turns out this is actually Screenlets. When I stop screenlets the python process dies and the memory frees up.

---

