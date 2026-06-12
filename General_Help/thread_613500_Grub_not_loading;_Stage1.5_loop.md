---
title: "Grub not loading; Stage1.5 loop"
date: 2007-11-15
forum: General Help
---

### Post by drreddog on 2007-11-15
I know there are similar threads on here, but I couldn't find anything that describes my exact problem. 

Here's the situation: I've got a dual-boot laptop with one drive, Windows and Ubuntu on separate partitions. I installed Ubuntu second and allowed GRUB to overwrite the Windows MBR (which is just fine with me, I prefer GRUB). All is fine and dandy; I am able to boot both Windows and Ubuntu several times with this arrangement. However, if I'm in Windows and then restart, the GRUB doesn't load. The screen will briefly display "Loading Stage1.5" and then the system will restart, throwing the system into a never ending loop. It does not display any error messages, it just does the loop. 

I have reinstalled GRUB several times with SGD, but the problem persists. It's getting very frustrating, especially because it locks me out of my system until I can get to my SGD cd. Any ideas what the problem could be? Thanks in advance.

---

### Post by abhinavg90 on 2008-01-19
I get the same problem
I have an AMD Athlon 64 X 2 and running 32 bit ubuntu on it - the same on I ran on my older intel dual core and I am dual booting it with Vista.
I had to ndiswrapper my wireless and had to jump through a few hoops to get the sound working on ubuntu.
But it was all working perfectly till day before.
I hadn't made any change to the system.
The night, I was working a bit on Vista. After done, I shut it down and went to sleep.
Morning I try to boot. My Toshiba logo shows, the GRUB Loading... comes and the screen goes black. Restarts and into an infinite loop like this until I press the power button. So I used ubuntu live cd and restored GRUB ( root(hd0,4) and setup(hd0) in my case ). It worked perfectly. And for the whole day. I changed b/w the OSes multiple times in the full day. No problems. At night again the last thing I did was a bit of Vista, turned off, and again in the morning the loop happened. Again I had to restore GRUB.
So this has happened 3 mornings in a row, each night, Vista being the last thing I used.
So, in other words, I have to restore GRUB every morning which is quite annoying.

Please help me fix this problem. Its hard to continue like this.

Of course the obvious thought could be that last shut down in Vista, but as I said, I switched OSes multiple times each day. And the laptop wasn't on 24 hrs a day. To think of it, I am not sure if I did a shutdown on Vista on anytime other than in the night after the last use for the day. It was normally a restart in Vista to get into Ubuntu.

Will try to see if what I am thinking is right.

But still, I hope someone has a solution for this

---

