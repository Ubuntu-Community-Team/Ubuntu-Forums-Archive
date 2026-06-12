---
title: "Unreadable burned large file DVDs"
date: 2008-06-24
forum: General Help
---

### Post by arigram on 2008-06-24
As a professional photographer, I make DVDs of photographs for my clients, where each one could well be up to half a gigabyte is size. Yet, I have tried and failed to burn them into DVDs.
Brasero and GnomeBaker just doesn't include the large files in the disk, presumably because it uses ISO and not UDF as the filesystem to be able to handle the large sizes.
K3b has an option for UDF, but it fails too. It burns the disk fine, but then its unreadable.
I've installed anything pertaining to UDF, including libraries and tools and I've tried with different brands of disks but the problem persists.
I was forced to install Windows XP in dual boot once more and do the burning there with Nero, where it worked just fine. I also have two recorders, a NEC and a LG one which work flawlessly.

Is it a known bug? I couldn't find information on it.
I seriously would appreciate any help on the matter as it affects me professionally.

---

### Post by mc4man on 2008-06-24
> Is it a known bug Bug or local issues, it's hard to tell with the linux burning apps, you could ck. the logs, might help. For a high degree of consistency and confidence in your product and compatibility with your customers playback methods I'd look elsewhere.
Two options would be to try nero4linux (21 day trial), then buy, or use Imgburn in wine.(free and better than nero) You could try it on your XP first to see how you like it ect. Read here for some install tips and link to site (guides)
[http://ubuntuforums.org/showthread.php?p=5246038#post5246038](http://ubuntuforums.org/showthread.php?p=5246038#post5246038)

What you were probably needing on these disks is for the apps to use ISO9660+UDF (1.02) extensions.

---

### Post by arigram on 2008-06-24
Thank you mc4man.

Its disappointing that I keep going back to Windows for serious work, even though I have no plans to ever return to Microsoft. Yet, it's really surprising that none of the three major OSS disk burning application can't handle something as basic as UDF. Why such support is missing is beyond me.

---

### Post by Taxman415a on 2008-06-24
Try going directly to the support sites for those applications. Or try IRC. I know each of those three burning projects have a channel on freenode and I'm sure someone in each project could either show you how to get it working or would like your help in figuring out what they need to fix.

---

### Post by arigram on 2008-06-24
Nero for Linux 3 didn't work either.
It burns the DVD and verifies it but it doesn't even show up.

This could well be a general Linux/Ubuntu problem.

---

### Post by mc4man on 2008-06-26
If you use Imgburn in wine I'll guarantee you'll never have a bad or incompatible burn.(assuming good media, burners) Drop me a line if your interested and I'll stick with it till your set. (if there are any issues setting up wine, pretty straightforward)

---

### Post by arigram on 2008-07-08
I never had any trouble with Gutsy, but so far I have been quite unsuccessful with burning DVDs in Hardy, with any application (Brasero, Nautilus, GnomeBaker, K3b, Nero).
I have to resort to dual booting in Windows XP just to burn a disc... quite pathetic...
And I am not the only one with this problem. There many reports about this on the forums.

---

