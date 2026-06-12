---
title: "Can I clear all in home directory cache?"
date: 2016-10-13
forum: General Help
---

### Post by xenon3 on 2016-10-13
I clear mozilla firefox cache to get rid of viruses by (kingdom is my user name by the way)

```


rm -fr /home/kingdom/.cache/mozilla/firefox/


```

Can I also clear whole home directory cache by (or does this destroy complete UBUNTU installation)?

```


rm -fr /home/kingdom/.cache/


```

Just to be certain!

It would also be nice to know though if only

 ```


/home/kingdom/.cache/mozilla/firefox/


```

directory is open on a encrypted UBUNTU installation, for spontaneously incoming traffic (I can of course by own intervention download things all over the file system)

---

### Post by jerome1232 on 2016-10-13
I wouldn't recommend deleting your cache folders unless you are having specific problems that seem to stem from it. Especially be careful throwing around that rm -rf command. It's very easy to accidentally make a typo and wipe out your entire ~/ directory by mistake, with no ability to recover outside of restoring from backup.

Those folders are where programs store files, mostly to speed things up. I know thumbnails, album art, are stored there. There is no real harm in deleting it outside of probably wiping out some preferences and causing programs to slow down as they recreate whatever it is they store in .cache. To my knowledge there are exactly zero viruses out in the wild that can run on the current linux kernel. There is no real need to wipe out your cache out of fear of viruses lurking there.

---

### Post by &amp;KyT$0P# on 2016-10-13
> **xenon3 said:**
> I clear mozilla firefox cache to get rid of viruses 

Just curious, what "viruses" do you keep getting in your Firefox cache?  How are you determining they are "viruses"?

> It would also be nice to know though if only

```


/home/kingdom/.cache/mozilla/firefox/

```
directory is open on a encrypted UBUNTU installation, for spontaneously incoming traffic (I can of course by own intervention download things all over the file system) 
Since you're not sure, it would be part of the same filesystem containing the rest of [FONT=Courier New]/home[/FONT].  You would remember if you had set up otherwise, as it's quite out-of-the-way to do so.

You could probably symlink [FONT=Courier New]/home/kingdom/.cache/mozilla/firefox[/FONT] to a directory on an unencrypted filesystem if you don't want your Firefox cache encrypted.  I haven't tried this myself, so I would suggest you completely quit Firefox, then back up your Firefox [profile]("http://kb.mozillazine.org/Profile"), **before** attempting.

---

### Post by Habitual on 2016-10-13
Don't base your decision on something like PUA results using clamtk.

---

### Post by xenon3 on 2016-10-13
> **halogen2 said:**
> 

Just curious, what "viruses" do you keep getting in your Firefox cache?  How are you determining they are "viruses"?



Strange as it may seem, it appears to me that the number of PUA viruses CLAMTK finds correlates with the increasingly slowing down of my system, just like if they, PUAs all working together, have concocted some kind of background process.

Anyways I remove viruses, clear mozilla cache, shutdown, electric current off for 60 seconds to clear all memory, startup again, computer not slow anymore, maybe for hours or days, during about a week I always suspend when I stop with computer for that day, maybe once / twice reboot the system during a week. With windows it is said that one cannot hibernate a system each day when finished longer than a couple of weeks, it got to reboot once in a while

---

### Post by &amp;KyT$0P# on 2016-10-13
> **Habitual said:**
> Don't base your decision on something like PUA results using clamtk.
Oh, this - [https://ubuntuforums.org/showthread.php?t=2332976&p=13528683&viewfull=1#post13528683](https://ubuntuforums.org/showthread.php?t=2332976&p=13528683&viewfull=1#post13528683)

> **xenon3 said:**
> Strange as it may seem, it appears to me that the number of PUA viruses CLAMTK finds correlates with the increasingly slowing down of my system, just like if they, PUAs all working together, have concocted some kind of background process.
Yep, and it appears that the increasing suicide rate correlates with the growing rabbit population, just like if they, rabbits working together, have concocted some kind of scheme to unbalance people.

Very strange, indeed.

> during about a week I always suspend when I stop with computer for that day, maybe once / twice reboot the system during a week. With windows it is said that one cannot hibernate a system each day when finished longer than a couple of weeks, it got to reboot once in a while
That isn't only a Windows thing.

---

### Post by Habitual on 2016-10-13
If it were me? I'd nuke 
 ```
.cache/mozilla/firefox/
```
in the heartbeat after closing firefox.

Take it for whatever that's worth.

---

### Post by xenon3 on 2016-10-13
> **halogen2 said:**
> 

Yep, and it appears that the increasing suicide rate correlates with the growing rabbit population, just like if they, rabbits working together, have concocted some kind of scheme to unbalance people.

Very strange, indeed.
  


Fact is that the longer, my computer is working (with intermediate suspend states) the slower he gets, until unworkable slow going to non responsive.

It also crossed my mind: PUAs are coming in all the time, moreover most people say they are harmless, so they build up all the time, does not mean a thing, correlation of number of PUAs with slowing down of system, OK correlates of course, but there is maybe no causality, maybe accidentally correlation

I have script blocker a couple of months now, only working in FireFox of course, is FireFox plug in, things are much better, no it takes much longer for the slowing down to non responsive, was 4 to 8 hours no 2 to 3 days (with intermediate suspend states) 

Why does my system still slows down, not only in browser but in desktop application too?

---

### Post by jerome1232 on 2016-10-13
Me first guess and thing I'd look for is a memory leak. Is your ram slowly filling up? Is something cosuming processor time? When a slow down begins to occur pop open a resource monitor, what is getting pegged and what is doing the pegging?

---

### Post by &amp;KyT$0P# on 2016-10-13
> **xenon3 said:**
> I have script blocker a couple of months now, only working in FireFox of course, 
Which script blocker?

> OK correlates of course, but there is maybe no causality, maybe accidentally correlation
Good, you are catching on.  Now, keeping this in mind -
> I have script blocker a couple of months now, only working in FireFox of course, is FireFox plug in, things are much better, no it takes much longer for the slowing down to non responsive, was 4 to 8 hours no 2 to 3 days (with intermediate suspend states)
Good diagnostic information, thanks.  Let's think about why exactly that occurs.

By blocking scripts, you are running less code and reducing the number of involved resources.  Which, in turn, generally means less RAM use.

When you suspend or hibernate the computer, you are essentially telling the computer you want it to just pick up exactly where it left off.  Wherever that is.
So, in order to do that, it has to (in very simple approximate terms) save the entire current state.  All of it.  Which it will then reload on resume before carrying on.

When you shutdown and reboot, you are not doing that.  In terms of RAM, you are, more or less, "resetting" the RAM to a clean state.

You see where we're going here? :)


* Posted at the same time as jerome1232 who, I should add, does see where we're going here.

---

### Post by xenon3 on 2016-10-13
> **halogen2 said:**
> 

 Which script blocker?



[https://noscript.net/](https://noscript.net/)

> **halogen2 said:**
> 

When you shutdown and reboot, you are not doing that.  In terms of RAM, you are, more or less, "resetting" the RAM to a clean state.

You see where we're going here? :)



Yes I could reboot every day, problem solved, but thats a workaround :-(

Problem could be a Pac-Man worm eating my memory ](*,)](*,)](*,)

---

### Post by xenon3 on 2016-10-16
> **halogen2 said:**
> 

Yep, and it appears that the increasing suicide rate correlates with the growing rabbit population, just like if they, rabbits working together, have concocted some kind of scheme to unbalance people.



Could be the Mexican Rabbit flu and the suicides are wrongly diagnosed :D deaths are from Rabbit Flu virus infections???

---

### Post by monkeybrain20122 on 2016-10-16
I remove the firefox cache periodically just to save space, I do that automatically with bleachbit, which also removes a lot of other junks. But you can of course do it manually.

---

### Post by xenon3 on 2016-10-19
> **monkeybrain20122 said:**
> I remove the firefox cache periodically just to save space, I do that automatically with bleachbit, which also removes a lot of other junks. But you can of course do it manually.

Briljant "BleachBit" works like a charm (bleachbit window can be grey for an hour though, for the other steps there is a progress bar, when window is grey he is most likely doing a background process pity there is no progress bar or message that he is doing something, at first I did not trust it, but than I waited longer)

BleachBit is freeware in Ubuntu Software Center by the way

---

