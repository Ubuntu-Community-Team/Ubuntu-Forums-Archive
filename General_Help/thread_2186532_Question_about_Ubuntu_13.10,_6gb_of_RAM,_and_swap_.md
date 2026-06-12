---
title: "Question about Ubuntu 13.10, 6gb of RAM, and swap partition use"
date: 2013-11-07
forum: General Help
---

### Post by tomdkat on 2013-11-07
A couple of weeks ago, I replaced my mom's ancient computer with a newer one which has 6gb of RAM.  Ubuntu runs well on the system but I noticed small amounts of swap space being used.  The _only_ applications she runs are:

[list]
[*]Firefox
[*]Thunderbird
[*]Banshee
[/list]

On occasion, I'll run LibreOffice Writer on the system.   At *most*, she'll have the three above listed applications running at the same time.  Now, with all three of those applications running, I've seen memory usage reach the 2gb mark, maybe even 2.5gb to be generous.  She's never used anywhere near 4gb of RAM on this system as far as I can tell.  She will have one tab open in Firefox at most and maybe 2-3 email messages open in Thunderbird at most.   So, with this "high water mark" of 2.5gb of RAM being used, as witnessed by me, I was quite surprised to discover small amounts of swap being used.  One day, 200kb of swap might be used.  A few days later, that might grow to 400kb.  As of last night, 1.1mb of swap was used.

The system will suspend after long periods of inactivity, so I wonder if the use of swap space is related to the system suspending  itself.

Any ideas on what could be causing the swap space "creep"?  When I reboot the system, the swap usage goes back to zero and stays that way until the creep happens again.

Ubuntu 13.10 64-bit is running on the system.

Thanks!

Peace...

---

### Post by fantab on 2013-11-07
You can lower the swappiness value to reduce the swap usage.

[READ HERE]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F") on how to lower swappiness.

---

### Post by hunterkasy on 2013-11-07
that is a question that I have been wondering, I have a quad with 8 gb of memory the most I have used is 2gb, I have swappiness set at 5 and I still get swap usage of around 200kb all the way up to 2mb

---

### Post by scottbomb on 2013-11-08
200k to 2mb is nothing. I'm only guessing when I say it's probably just OS operations and therefore nothing I'd be concerned about. I think that if it were actually caching memory,  you'd see a much higher utilization. This is pure speculation, but an educated guess nonetheless.

---

### Post by mastablasta on 2013-11-08
> **tomdkat said:**
>  So, with this "high water mark" of 2.5gb of RAM being used, as witnessed by me, I was quite surprised to discover small amounts of swap being used. 
It uses ram as much as it can. this is a good thing. RAM is a lot faster than HDD.

> 
One day, 200kb of swap might be used. A few days later, that might grow to 400kb. As of last night, 1.1mb of swap was used.

The system will suspend after long periods of inactivity, so I wonder if the use of swap space is related to the system suspending itself.



that is small usage probably just some temporary storage. that's less than 0,1 % of swap used. it's negligable.
yes, swap is used when system suspends itself. the state is saved to swap to get recalled when system get's back out of suspend.

also swap can be removed if there is enough ram present. only then you can't suspend i believe.

---

### Post by tomdkat on 2013-11-08
> **fantab said:**
> You can lower the swappiness value to reduce the swap usage.

[READ HERE]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F") on how to lower swappiness.
Thanks for this link!  I wasn't aware of the "swappiness" kernel parameter.  :)

Peace...

---

### Post by tomdkat on 2013-11-08
> **mastablasta said:**
> It uses ram as much as it can. this is a good thing. RAM is a lot faster than HDD.Yep, which is why I was surprised any swap was being used at all, given how much available RAM there is. :)

> that is small usage probably just some temporary storage. that's less than 0,1 % of swap used. it's negligable.
yes, swap is used when system suspends itself. the state is saved to swap to get recalled when system get's back out of suspend.
Ok, this makes sense.  The amount of swap space used was never a concern but the fact _any_ swap space was used was confusing.   So, I'll experiment with the power settings and see what impact that has, if any.

I'll also adjust the swappiness setting and see what happens.

Thanks!

Peace...

---

### Post by mcduck on 2013-11-09
Unless you are running on a laptop and wish to save some battery but allowing the hard drive to power off while idle, I wouldn't bother messsing with the swappiness value.

A bit of swap use is part of normal Linux kernel memory management, and is not the same thing as actually swapping because of running out of free RAM. The kernel uses a bit of swap to test if some old data kept in cache is still relevant or if it could be dropped, placing the data into swap for a while and dropping it completely if it isn't accessed in a certain time. This will not reduce your system's performance (actually strictly speaking swapping never does that anyway, slow system using swap is still faster than out-of-ram system which wouldn't be able to do anything at all ;))

---

