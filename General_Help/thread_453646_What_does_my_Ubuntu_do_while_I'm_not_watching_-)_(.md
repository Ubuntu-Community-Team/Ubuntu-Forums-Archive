---
title: "What does my Ubuntu do while I'm not watching? :-) (or: how to make it idle...)"
date: 2007-05-24
forum: General Help
---

### Post by Finch75 on 2007-05-24
Hi everybody,

I'm currently switching from Windows XP and while I'm fighting with some of the typical problems (drivers, applications, ...), most things work quite ok and I hope I can do nice things with it that I couldn't do with Windows but always wanted to. Among others, I very much hope that it is more "predictable" than Windows is... ? :-)

Somehow, Windows always seems to keep itself busy. The processor always hovers at 1-2% (hey! That's 80 Mhz doing WHAT?) and when I'm not watching, it suddenly spins up the hard disks for some unknown reasons... The system disk never stops in the first place, of course...

ok, but we all want to talk about Ubuntu, not Windows, right? :-)
When I'm away, I would really like it to do NOTHING except for impatiently waiting for my return *bg*

I've always dreamed about the totally silent PC (I have a fanless PSU, an AMD EE-CPU with a huge Zalman cooler and "rather quiet" disks)

Can I configure Ubuntu to NOT access the hard disk for hours? How about other programs? I'd like to load a couple of CDs into memory and then have them play without hard disk activity...

How about a probably really advanced thing: Can I configure Ubuntu to load "everything that matters" into RAM after startup and run from memory? That's not *very* different from a LiveCD, but probably somewhat more complicated...

How can I find out if there was hard disk activity and who caused it?

I currently have "only" 2 GB of RAM but with the current prices, I really cannot resist the temptation ;-) Unfortunately, the 2 GB modules are *somewhat* more expensive than the 1 GB modules and I would only consider those if I could do some really cool stuff with them ;-)

Looking forward to your comments...

Finch

---

### Post by blackened on 2007-05-24
Sorry this post doesn't directly pertain to any of the questions you asked, but it fits in with your want for a silent pc. That said, have you looked into using an IDE to Compact Flash adapter to replace your magnetic media OS drive? The benefits being faster read times and entirely silent operation, though setting up your swap partition on magnetic media is a must as CF suffers from lessened lifespan issues with excessive disk writes. Was just a thought.

---

### Post by onbongos on 2007-05-24
you won't have truly switched until you stop worrying about these things and trust the os to do what's best

---

### Post by Finch75 on 2007-05-24
@blackened: Well, let's say "I'm watching the development" :-)
So far, solid state disks and the like always were either too small or too expensive. At least the ones with decent speed. Yes, an 8 GB USB stick is reasonably affordable, but just too slow. Last time I checked, SSD >= 16 GB  cost more than 500 € / 600 USD. That's a price that makes me wait a little longer ;-) Looks like quite a few product are hitting the market just recently. Definitely a development worth watching... 
Or what did you have in mind and how much would it cost?

For the swap file: I don't think I'll need one ;-) With the current RAM prices (1 GB for 30 Euro!!!), I'll just buy as much as I need. Depending on the outcome of this thread, I'll soon have at least 4, possibly 6 GB RAM! *yeah* (and yes, I'm running 64 bit Ubuntu without major problems so far and my MB supports up to 8 GB) So what data should go into the swap file? Disk cache?! *g*

> **onbongos said:**
> you won't have truly switched until you stop worrying about these things and trust the os to do what's best
I have no clue what you mean?! I won't have truly switched unless I stop worrying about what I want from my computer? That's a statement I would've expected for a switch FROM Linux TO Windows *bg* - If anything, Linux should give me more control, not less.
And no, the OS cannot make every choice for me. The "best choice" is vastly different depending on requirements and those are very different for a typical office PC, an HTPC and a developer PC (mine belongs to the last two categories although it's not a small form factor...)

---

### Post by psusi on 2007-05-24
Check out [https://wiki.ubuntu.com/IdleDisk](https://wiki.ubuntu.com/IdleDisk)

---

### Post by ios_base on 2007-05-24
> **onbongos said:**
> you won't have truly switched until you stop worrying about these things and trust the os to do what's best

WHAT?  What's that supposed to mean?

---

### Post by hartz on 2007-05-25
> **onbongos said:**
> you won't have truly switched until you stop worrying about these things and trust the os to do what's best

This reminds me of a statement by a Windows fan:
[QUOTE=WindowsFan]I like windows because it is the only viable option we have[/QUOTE]

---

### Post by ikonia on 2007-05-25
worst post on the forum I've read for ages.

Request mods delete it.

---

### Post by blackened on 2007-05-25
Well, in theory, 4 gb is plenty of room for the OS to sit on, so you would need one 4gb CF card (available for around $40 US) and one IDE to CF adapter (around $20 US).

Some info about the adapter is on Damn Small Linux's site: [http://damnsmalllinux.org/store/embedded_storage]("http://damnsmalllinux.org/store/embedded_storage")

> **onbongos said:**
> you won't have truly switched until you stop worrying about these things and trust the os to do what's best

I'm gonna hope this was sarcasm, because that's about all I can get out of it.

---

### Post by Finch75 on 2007-05-26
oh well, this is pretty much off topic, but ok, if nobody want to post on topic anyway... :-(

> **blackened said:**
> Well, in theory, 4 gb is plenty of room for the OS to sit on, so you would need one 4gb CF card (available for around $40 US) and one IDE to CF adapter (around $20 US).

Sounds interesting, BUT
- I'm not sure 4 GB is "plenty". It might be enough for the OS; but I'm not sure yet. I just installed (K)Ubuntu two weeks ago, it's far from complete and already, /usr is 3.2 GB and /var is 800 MB.
- "normal" CF-cards are far too slow (~4 MB/s??!) for "a real OS", aren't they? Can be ok for HTPC, but if I really want to use the PC for some "heavy duty" stuff, I will not be happy even with 10 MB/s
- as I see, some CF cards are supposedly fast enough, but they cost ~55 Euro (70 USD) for 4 GB or ~110 Euro (140 USD) for 8 GB.
- do normal CF cards support wear leveling? How long would a CF card survive as an OS drive?

All in all, it does sound interesting, but a little bit "too early"

> **psusi said:**
> Check out [https://wiki.ubuntu.com/IdleDisk](https://wiki.ubuntu.com/IdleDisk)

Thanks for the link. Sounds interesting. Definitely for monitoring what's going on. But "one disk write every ten minutes... does that make any sense for a desktop? Nothing wears a hard drive as much as constant start-stop cycles. For a notebook, power consumption probably is more important and the hard disk can spin up, write some data and go back to sleep every 10 minutes. I'm not sure that makes sense for a desktop, though... What I really want: When I do NOT use the computer, I want no disk activity for *hours*. I'll probably have to learn a bit more about Linux before I can take a closer look at that...

---

### Post by blackened on 2007-06-03
> **Finch75 said:**
> oh well, this is pretty much off topic, but ok, if nobody want to post on topic anyway... :-(



Sounds interesting, BUT
- I'm not sure 4 GB is "plenty". It might be enough for the OS; but I'm not sure yet. I just installed (K)Ubuntu two weeks ago, it's far from complete and already, /usr is 3.2 GB and /var is 800 MB.
- "normal" CF-cards are far too slow (~4 MB/s??!) for "a real OS", aren't they? Can be ok for HTPC, but if I really want to use the PC for some "heavy duty" stuff, I will not be happy even with 10 MB/s
- as I see, some CF cards are supposedly fast enough, but they cost ~55 Euro (70 USD) for 4 GB or ~110 Euro (140 USD) for 8 GB.
- do normal CF cards support wear leveling? How long would a CF card survive as an OS drive?

All in all, it does sound interesting, but a little bit "too early"


I had read up a bit on this days ago, but got sidetracked and forgot to post back. Please note that I'm speaking only from the standpoint of interest and curiosity, not from experience, so everything I say is up for debate and discussion.

The entirety of my root directory (/home is on a separate partition) is 2.2GB using a default install of vanilla Ubuntu (GDM, Gnome) without any other DEs. I have Beryl SVN, Amarok, Google Earth, Open Office, Java, and quite a few other large apps installed and am still not reaching the 4GB capacity of my root partition. But this could be due to the fact that I know that I'm limited on space, so I tend to be a bit miserly about things I install.

As per CF cards: you're probably right about normal CF being too slow, but if 4GB were adequate, then the faster x133 CF cards would seem quite reasonable to me pricewise. Maybe using a smaller distro like DSL would be the way to go. From what I've read, they have a version tailored to lessen disk writes for solid state media.

As per wear-leveling: The ideal would be to use a filesystem tailored to solid state media such as JFFS/JFFS2 or YAFFS. From what I've read, and I admit to having little knowledge of filesystems, these work in such a way as to negate the need for hardware wear-leveling.

---

