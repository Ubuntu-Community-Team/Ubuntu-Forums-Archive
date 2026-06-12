---
title: "Where to get advanced help?"
date: 2006-12-12
forum: General Help
---

### Post by hardyn on 2006-12-12
Where does one to go to get advanced help?  I have asked several kernel level questions in the past few weeks, and i rarely get any responses.  and i do feel i am phrasing them properly.

I seem be to be a level of linux knowledge that strattles the echelons of the ubuntu-forums help matrix; i am no longer a noobie, but not yet a power user. Just enough knowlege to be dangerous.

I am having some trouble with custom kernels (and yes, i do need to build a custom kernel, i wish i didn't but i do). cannot find solutions from google, or recieve any joy from from the forum either.

I an NOT at all flaming the ubuntu community, it has helped me countless times; but i need a place to turn to get what i want out of ubuntu install, if not here, where?

---

### Post by Topsiho on 2006-12-12
Hello Hardyn,

Seems you have reached a level which is higher than that of many in this forum, who are, I think, most of them, enthousiastic but not so advanced that they can help you out.

I suggest, only suggest, that you try to get hold of a good book on system administration, if it is administration your system(s) that bothers you.

What a good book is I am afraid I can not tell you, I am sorry :)

Good luck

Topsiho

---

### Post by hardyn on 2006-12-12
although the problems that i am having are with the new skool ubuntu kernel, with the inclusive SMP; and i have tried other distros, but ubuntu is the only one that has all my hardware working out of the box.  therefore im kinda stuck between a rock and a hard place.  and it seems if i had any other computer than a Asus notebook with Pentium M, i would not have the kernel trouble that im having.

---

### Post by koenn on 2006-12-12
There are plenty of web resources about compiling a kernel.
[http://www.google.be/search?hl=en&q=linux+kernel+compile](http://www.google.be/search?hl=en&q=linux+kernel+compile)

[http://www.freeos.com/articles/2589/](http://www.freeos.com/articles/2589/)  looks like a good intro. 

The hard part is probably that you need to know which customizations you require, and secondly, how to apply them to the kernel, either by modifying code yourself, or apply patches that others have written for situations similar to yours. 

I agree with Topsiho that this is probably too advanced for this type of forum. Also it is not really Ubuntu-specific - rather more linux kernel in general. 

I've never had or felt the need to build a kernel so I can't tell you where to look, but I think you'd be looking at linux kernel Howto's and tutorials in general, howto's on the problems you're hoping to solve with your customized kernel, possibly documentation for the ubuntu-kernels because that's what you'd start with. I suppose you'd also need a decent understanding of C and the workings of CPU's - all of which I can't help you with.

---

### Post by ciscosurfer on 2006-12-12
Maybe you've seen this thread, I don't know.  But I thought I'd throw it out here: [http://www.ubuntuforums.org/showthread.php?t=85064](http://www.ubuntuforums.org/showthread.php?t=85064)

By the way, there are many threads on the Forums that delve into kernel compilation, customization, troubleshooting, etc.  
You can find them all by using an Advanced Search: [http://ubuntuforums.org/search.php](http://ubuntuforums.org/search.php)

---

### Post by hardyn on 2006-12-12
i have no problem executing the compliation of the kernel, its why i seem to lose soooo much hardware support between an OE kernel (networking), and the ones that i build despite using ubuntu source; all i can figure is that at ubuntu HQ, there are compiling with much more in the way of source packages than is made available when you download the source.

eg... OE kernel.  out of the box with marvell lan.
my kernel, no marvell lan.  even usit their source (i might expect problems using vanilla kernel). from reading, i may be able fix my problem by downloadingthe marvel driver then recompile; at the same time this suggests that this driver does not come for the ride with the normal source.

it would be interesting to know exacty how the OE kernels are generated. as the allways seem to work better than mine.

---

