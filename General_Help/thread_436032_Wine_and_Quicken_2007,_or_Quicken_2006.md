---
title: "Wine and Quicken 2007, or Quicken 2006"
date: 2007-05-07
forum: General Help
---

### Post by ronald_stall on 2007-05-07
Has anyone gotten Wine and Quicken 2007 or Quicken 2006 to work? I can get 2007 installed but cannot get it to run. Anyone who has been successful if you could please guide me in the right direction would be most appreciated!!

Thanks

---

### Post by rich.bradshaw on 2007-05-07
Not the answer to your question, but have you tried gnucash as an alternative if that is a viable choice for you?

---

### Post by ronald_stall on 2007-05-07
Yes, I've looked at Gnucash but I want to have online banking and online bill pay though my accounting program which from what I can tell Gnucash does not fullfill.

---

### Post by rich.bradshaw on 2007-05-07
Sure. Often the OSS equivalent works just as well, but evidently this isn't the case...

If you don't already know, Ubuntu is based on Debian, so any Debian tutorial will work as well - if you can find one!

Everything I have needed in Wine has just worked - I would suspect that otherwise it will not work at all.

Perhaps Quicken needs Internet Explorer to work - you could try installing that to satisfy it's possible dependancy, there is a script call ie4linux that will get it installed.

---

### Post by Das Goat on 2007-05-12
I too need Quicken to work. It is one of the few programs that I can not live with out in my Ubuntu transition.

And, no, don't even go down the Gnucash road. I tried that w/ Ubuntu 6.1. The problem is that Quicken has interdepenancies between accounts, ie. i spend $100 from checking to pay my credit card. Gnucash can import the accounts ok, but it can not handle the inter actions between accounts. so the bottom line if that once you import all of the accounts from quicken, nothing matches.

I was able to use Crossover Office and then install Quicken, and it seemed to work ok, but when I restored my data back up, then Quicken crashed and would not run. It even shrunk down to a little box that was about the size of a postage stamp and would sit there blinking at me. So even if Crossover Office and Quicken do "technically" work together, if you can't get your past data (years worth in my case) then what good is it?

It is a shame, but there are a few applications out there that we just can't live with out. Unlike games, these productivity tools are one of the true stumbling blocks preventing us from totally ditching windows.

---

### Post by dpar on 2007-05-12
This is what I found at the Wine data base.      [http://appdb.winehq.org/appview.php?iVersionId=7179](http://appdb.winehq.org/appview.php?iVersionId=7179)

---

### Post by ronald_stall on 2007-05-13
I can install Quicken 2006 with Wine but cannot get any functionality at all. It freezes. I have had to resort to running WinXP in VirtualBox which is working well so far but would really like to get away from any Windows dependency in the future.

---

### Post by Das Goat on 2007-05-17
> **ronald_stall said:**
> I can install Quicken 2006 with Wine but cannot get any functionality at all. It freezes. I have had to resort to running WinXP in VirtualBox which is working well so far but would really like to get away from any Windows dependency in the future.

please explain this "virtual box" for me. At this point I would take any leads. Getting rid for windows is my goal, but Quicken is something i can't live with out.

---

### Post by dpar on 2007-05-17
I believe he's talking about VMWare or some other type of virtual machine.

---

### Post by ronald_stall on 2007-05-18
No not VMware, Virtualbox. Go to [www.virtualbox.org]("http://www.virtualbox.org") It is free and very easy to set up. 

Follow these directions exactly!  [Howto: VirtualBox without opening the shell]("http://ubuntuforums.org/showthread.php?t=340113&highlight=VirtualBox")

I've tried VMware Server, Qemu, and KVM and Virtualbox is definately the easiest and in my opinion the fastest.

---

### Post by BlackWoxs on 2007-05-18
Have a look at [Moneydance]("http://www.moneydance.com/") - it is not free but it did allow me to leave the Quicken camp under Ubuntu. One nice feature is that, as a java app it runs on Linux, Mac OS X and MS Windows.

---

### Post by fanatik on 2007-05-18
Have a look at crossover, it is more supported than wine.

[http://www.codeweavers.com/compatibility/browse/name/?app_id=2634](http://www.codeweavers.com/compatibility/browse/name/?app_id=2634)
[http://www.codeweavers.com/compatibility/browse/name/?app_id=1393](http://www.codeweavers.com/compatibility/browse/name/?app_id=1393)

You have to pay for crossover, but its not expensive.

---

### Post by Das Goat on 2007-05-24
> **ronald_stall said:**
> No not VMware, Virtualbox. Go to [www.virtualbox.org]("http://www.virtualbox.org") It is free and very easy to set up. 

Follow these directions exactly!  [Howto: VirtualBox without opening the shell]("http://ubuntuforums.org/showthread.php?t=340113&highlight=VirtualBox")

I've tried VMware Server, Qemu, and KVM and Virtualbox is definately the easiest and in my opinion the fastest.

UHHH!!! Why is it every time I find a solution, they are only aavailable in 32-Bit?!?!? This is frustrating!

---

### Post by Das Goat on 2007-05-24
> **ronald_stall said:**
> No not VMware, Virtualbox. Go to [www.virtualbox.org]("http://www.virtualbox.org") It is free and very easy to set up. 

Follow these directions exactly!  [Howto: VirtualBox without opening the shell]("http://ubuntuforums.org/showthread.php?t=340113&highlight=VirtualBox")

I've tried VMware Server, Qemu, and KVM and Virtualbox is definately the easiest and in my opinion the fastest.

Uhh! Why is it that every solution I come across only works on 32-BIT Ubuntu?!?!? Madness I tell you!:(

---

### Post by rbmorse on 2007-05-24
Like it or not, it's still a 32-bit world.

---

### Post by Benchrest on 2007-06-19
I installed Quicken 2007 last night on Edgy with Wine. The Quicken install disk included IE 6.0 and the install of IE failed. Have not researched it yet. Quicken would not start from the desktop icon. Starting it from console I found the folder "Program Files", the space is not recognized.  I put it in quotes and received three missing modules. I have downloaded one and need to find the other two. I am not at my notes now but will list them later.Looks like a long road to get this working. I have looked at the Linux alternatives such as Gnucash and Kmymoney, even tried a few. But none have online download of credit card transactions and a few other online investment features. Quicken is sleeping with these companies and has a corner on the market. Other than Quicken I have been able to find Linux alternatives for most everything else I need.

Added: error message for missing gdiplus.dll  mfc80.dll  msvcr80.dll    After installing gdiplus.dll no longer get error message for it. Copied mfc80.dll from xp system and it still shows error. Need rename with uppercase/lowercase as appears in error message.

---

### Post by Benchrest on 2007-06-20
May need to install .NET first. But according to WINEHQ .NET will not install. This is ugly.

---

### Post by Das Goat on 2007-06-22
Virtual Box is the answer! not maybe the whole answer you wanted, but you can have a full Ubuntu system, load a virtual WinXP system, and run Quicken from there.

Check out this thread [http://ubuntuforums.org/showthread.php?p=2877149#post2877149](http://ubuntuforums.org/showthread.php?p=2877149#post2877149)

---

### Post by rhumbliner on 2008-01-26
Check out Yodlee MoneyCenter as an alternative to Quicken. It's web-based and free.

---

### Post by rhumbliner on 2008-01-26
Actually, [www.mint.com](www.mint.com) is better than Yodlee

---

### Post by mortsahl on 2008-01-26
Quicken was the only program I needed to be fully WIndows free (I've since dumped Quicken, but that's another story).  Anyway, my solution was to purchase CrossOver Office from Codeweavers.  Quicken ran perfectly.

---

### Post by krevuru on 2008-05-27
Check out
[http://ubuntuforums.org/showthread.php?p=5057577#post5057577](http://ubuntuforums.org/showthread.php?p=5057577#post5057577)

---

