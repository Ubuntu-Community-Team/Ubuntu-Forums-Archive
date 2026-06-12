---
title: "partition  sizes"
date: 2007-09-23
forum: General Help
---

### Post by markp1989 on 2007-09-23
I have an 80gb Hard drive that i would like to dedicate to ubuntu, i want a seperate home partition for when upgrading etc, what size would be suitable for the /home partition

i was thinking of having 3 partitions:

partition 1 "/"
partition 2 "/home"
partition 3 "swap"

what sizes should the listed partitions be?

i was thinking:

1gb for swap
15gb for "/"
rest for "/home"

would these sizes be suitable?


any advice i get on this subject will be highly appreciated, and i thank you all in advanced

---

### Post by alienseer23 on 2007-09-23
that should be fine

---

### Post by pluviosity on 2007-09-23
Yeah, sounds good.  My 10 gig root partition in Kubuntu is about 1/3 full; when I used Ubuntu, I used about half of it (didn't install many non-default apps though).

---

### Post by markp1989 on 2007-09-23
> **pluviosity said:**
> Yeah, sounds good.  My 10 gig root partition in Kubuntu is about 1/3 full; when I used Ubuntu, I used about half of it (didn't install many non-default apps though).

ok thankyou , il do the install in a few days, then leave my feed back here

---

### Post by markp1989 on 2007-09-24
I have decided how im going to partition it, 

5gb for windows  I need windows for my printer.
15gb for "/"
1gb for swap
remaining for "/home" so i will have about 60gb for /home

---

### Post by bigken on 2007-09-24
I would give windows 10 gig

/ 10 gig 
1 gig swap this depends on how much ram you have ie 512=1gig if you have 2 gig you dont realy need a swap partition 
the rest /home

---

### Post by meindian523 on 2007-09-24
> **markp1989 said:**
> I have decided how im going to partition it, 

5gb for windows  I need windows for my printer.
15gb for "/"
1gb for swap
remaining for "/home" so i will have about 60gb for /home
WAIT!

This is a better scheme,specially if you are using this as a home desktop....take it from me....I'm still thinking why I didn't do this specially when I see my / 61% full!

1 GB swap
10 GB /
15 GB /etc
15 GB /usr
10 GB /tmp
5 GB Windows
rest /home.....

---

### Post by az on 2007-09-24
> **meindian523 said:**
> WAIT!

This is a better scheme,specially if you are using this as a home desktop....take it from me....I'm still thinking why I didn't do this specially when I see my / 61% full!

1 GB swap
10 GB /
15 GB /etc
15 GB /usr
10 GB /tmp
5 GB Windows
rest /home.....

WTF?

Trust me, you don't want to do this.

Everything-on-one partition is what I recommend.  If you really want a separate home, go ahead, but that's just a unnecessary headache.  You certainly don't want to limit any of your filesystem to small partitions.  There is no benefit to doing this on a desktop.

---

### Post by dabl on 2007-09-24
I think I'm up to about 8 installations of *buntu in the past 12 months.  Here's what works, assuming you've got 1GB or more of RAM:

"/" = 6GB  (I've never seen more than 4.6 used, before cleanups)
"swap" = 0.5GB -- you probably won't see that used at all, unless you use a microscope
"/home" = the rest of it.

I run Win XP in a Virtual Box, and don't even do a real dual boot anymore.  But if I ever need to change the overclock on my motherboard/CPU, I'll have to find an old spare hard drive and put Win XP on it ....

:lolflag:

---

### Post by psusi on 2007-09-24
Umm, yea.. having separate /usr and /etc partitions is a pointless waste of space.  Having a /tmp partition is not only a waste of space, but will also slow your system down.  Ubuntu uses tmpfs for /tmp, which keeps the files in ram/swap.

---

### Post by rsambuca on 2007-09-24
> **meindian523 said:**
> WAIT!

This is a better scheme,specially if you are using this as a home desktop....take it from me....I'm still thinking why I didn't do this specially when I see my / 61% full!

1 GB swap
10 GB /
15 GB /etc
15 GB /usr
10 GB /tmp
5 GB Windows
rest /home.....

This partitioning scheme is far more complex than it needs to be for the average user.  I wouldn't recommend it except in vary rare circumstances.

The only thing I might recommend changing from your original plan is increasing the size of your XP partition a little bit as Windows likes to have a little breathing space to run efficiently.

---

### Post by markp1989 on 2007-09-24
> **dabl said:**
> I think I'm up to about 8 installations of *buntu in the past 12 months.  Here's what works, assuming you've got 1GB or more of RAM:

"/" = 6GB  (I've never seen more than 4.6 used, before cleanups)
"swap" = 0.5GB -- you probably won't see that used at all, unless you use a microscope
"/home" = the rest of it.

I run Win XP in a Virtual Box, and don't even do a real dual boot anymore.  But if I ever need to change the overclock on my motherboard/CPU, I'll have to find an old spare hard drive and put Win XP on it ....

:lolflag:

I need a native XP because my printer doesnt work on linux,


i have enough ram, 2gb, swap rarely gets used, but i  want to keep a swap partition just encase

---

### Post by markp1989 on 2007-09-24
> **rsambuca said:**
> This partitioning scheme is far more complex than it needs to be for the average user.  I wouldn't recommend it except in vary rare circumstances.

The only thing I might recommend changing from your original plan is increasing the size of your XP partition a little bit as Windows likes to have a little breathing space to run efficiently.

im keping xp just for printing, so all i will have installed it antivirus and open office, how big do you think i should make the win xp partition?

i know i need space for the page file, plus around 2-3 gb for windows  plus open office which is around 200-300 mb? plus abit of free space for stability/ de fragmentation

---

### Post by rsambuca on 2007-09-24
> **markp1989 said:**
> im keping xp just for printing, so all i will have installed it antivirus and open office, how big do you think i should make the win xp partition?

Sorry, I missed the part where you said it was just for printing.  If all you are going to be doing is opening OO and printing, I would think that 10GB is plenty.  What printer do you have, by the way?

---

### Post by markp1989 on 2007-09-24
> **rsambuca said:**
> Sorry, I missed the part where you said it was just for printing.  If all you are going to be doing is opening OO and printing, I would think that 10GB is plenty.  What printer do you have, by the way?


my printer is lexmark z735 all sites i have checked have said that its a paperweight and i have no money to buy a new one right now 

I have thought about what everyone has said here, and i think this sounds about right
80 gb total

0.5 gb for swap
8 gb "/" is 8gb big enough?

gives me about 70gb for /home and windows 

10 gb for windows xp
60 gb for "/home"


I wont be doing this install for about 3-5 days, i still have some data to back up, and im  waiting for a rather large download to finish

If there are any problems with the partition plan, then just explain what it is.

Ps i will be using the gparted live cd to set up the partitions

---

### Post by meindian523 on 2007-09-25
> **psusi said:**
> Umm, yea.. having separate /usr and /etc partitions is a pointless waste of space.
I beg to differ...your /etc and /usr folders are going to take up that much space anyway.......atleast wo won't have warnings about low space on / partition.....

> **psusi said:**
> Having a /tmp partition is not only a waste of space, but will also slow your system down.Ubuntu uses tmpfs for /tmp, which keeps the files in ram/swap.

Hmm,maybe,not sure about that.......

---

### Post by rsambuca on 2007-09-25
> **meindian523 said:**
> I beg to differ...your /etc and /usr folders are going to take up that much space anyway.......atleast wo won't have warnings about low space on / partition....
Sorry, but there is virtually no reason to separate your filesystem into separate partitions for a desktop environment.  There are some instances where this may be desirable for a server, though.

What often happens if you are trying to put these folders into separate partitions on the same drive is that you never know for sure how much space you need for each partition.  Then later, one folder (often /usr) gets full, but you have a lot of extra space on other partitions.  Basically, it is just very inefficient for a Desktop with one drive.

---

### Post by psusi on 2007-09-25
> **meindian523 said:**
> I beg to differ...your /etc and /usr folders are going to take up that much space anyway.......atleast wo won't have warnings about low space on / partition.....



Hmm,maybe,not sure about that.......

You don't seem to grok the conversation here... of course /etc and /usr ( well, especially /etc ) are not going to take up much space, which is exactly why it is silly to dedicate a 10 gb partition to each of them.  It wastes space because when you are only using 100 megs in /etc, you now have 9.9 gb on that partition that can not be used for files elsewhere.

---

### Post by meindian523 on 2007-09-27
> **psusi said:**
> You don't seem to grok the conversation here... of course /etc and /usr ( well, especially /etc ) are not going to take up much space, which is exactly why it is silly to dedicate a 10 gb partition to each of them.  It wastes space because when you are only using 100 megs in /etc, you now have 9.9 gb on that partition that can not be used for files elsewhere.

grok??What's that?well,i am a newbie too but the gist of my argument was that these mount points should be on different partitions......atleast these that is.....

/
/home
/usr

/usr would take up much space if you install many apps like I've done:)But these I've installed only after due care and reasoning and after weighing the pros and cons....STILL my / partition is 62% used and I guess the major part is /usr since my /home is on a separate partition.......

Please correct me if I'm wrong...I'm not looking to be troll or something,if I'm wrong,gimme a good example and I will accept it....unfortunately I can't remember where I had seen the disk usage analyzer in ubuntu.......

---

### Post by psusi on 2007-09-27
[http://en.wikipedia.org/wiki/Grok](http://en.wikipedia.org/wiki/Grok)

Any time you create separate partitions you fragment your disk into parts that can not comingle.  If your /usr fills up, you won't be able to install any more programs even though you may have plenty of space on / and /home.  If your /home fills up, you won't be able to save any more documents, even though /usr may have plenty of free space left.  Someone suggested allocating 15 GB for /etc.  I guarantee you that you will never come close to filling that up, so you then have a bunch of wasted disk space that will never be used.  

This gives a fair argument against creating a dedicated partition, so one needs a better reason FOR creating one.  For /home, there is a good reason to put it on its own partition: it makes reinstalling a bit easier since you can just reformat and reinstall to / and your /home remains untouched.  Which argument is stronger is up to you to decide.  

For /usr and /etc, there is no benefit to having their own partition, so the first argument wins and you shouldn't do it.  

As for disk utilization, conveniently enough there is a command called, of all things, du, that reports such information.  It can scan a directory and tell you how much space is used by the files and directories in it, or just report the total size of a single directory.  I know there is are gui tools that do similar things, but I can't recall their names since I never really use them.

---

### Post by meindian523 on 2007-09-28
Thanks for taking the time out to explain.In short,the only mount points which should be on their partition on a desktop system are

/
/home and
swap

correct?

---

### Post by psusi on 2007-09-28
Yes... and the /home only if you want to.

---

### Post by bigken on 2007-09-28
> **psusi said:**
> Yes... and the /home only if you want to.

I find its best for a separate home partition just incase you reinstall all your settings and data stay ie evolution settings ect

---

### Post by Niniel on 2007-09-28
So what about a separate /boot partition? Somebody mentioned that earlier. How does that work anyway?

---

### Post by bigken on 2007-09-28
you can have your boot partition on a floppy usb pen drive where ever I would imagine this would be for security reasons not to sure though

---

### Post by psusi on 2007-09-28
No reason for a typical single disk desktop install to have a separate /boot partition.  I run with one because I have a raid setup and mess around with multiple installs in different partitions and such.

---

### Post by markp1989 on 2007-09-28
i have set up my computer now , and installed using this partition scheme

part 1 :  10gb for windows xp, about 6gb used up 
part 2 :  8gb for "/" 
part 3 :  56gb for "/home"
part 4 :  0.5gb for swap


works exactly as i expected



thank you to everyone who posted on this thread, and appreciate all the help you have given me

---

### Post by Niniel on 2007-09-28
That's not 80 GB though... did your hd experience sudden shrinkage syndrome?

---

### Post by markp1989 on 2007-09-28
> **Niniel said:**
> That's not 80 GB though... did your hd experience sudden shrinkage syndrome?

80gb on the label, but i only get like 75gb of space

---

