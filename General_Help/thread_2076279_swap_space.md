---
title: "swap space"
date: 2012-10-25
forum: General Help
---

### Post by Twilk73 on 2012-10-25
Ok so my laptop has 12 gigs of ram and after go through the basic setup I noticed that the system allocated 12 gigs of swap space.  Should I remove this or just let it be. I have plenty of free space to just let it be but at the same time I dont ever see me using more then my 12 gigs of ram.

---

### Post by ajgreeny on 2012-10-25
If you want to suspend the machine or more importantly, hibernate, you need as much swap as you have ram, that's why the installer gave you the full 12GB.

If you don't ever want or need to do that, you can probably reduce swap to around 4GB, but if you have plenty of disk space why not just leave things as they are?

---

### Post by jerrrys on 2012-10-25
Hibernation (suspend-to-disk) The  hibernation feature (suspend-to-disk) writes out the contents of RAM to  the swap partition before turning off the machine. Therefore, your swap  partition should be at least as big as your RAM size. The hibernation  implementation currently used in Ubuntu, swsusp, needs a swap or suspend  partition. It cannot use a swap file on an active file system.

Other than that, I vote no swap.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=do+i+need+swap&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=do+i+need+swap&as_qdr=all&sa=Google+Search&lang=en)

Or if you decide to keep swap; set swappiness to zero.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=swappiness&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=swappiness&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Twilk73 on 2012-10-25
Thanks both of you. For now I will just keep the swap even though I never hibernate. 

At the moment I am to new to linux to start tweaking however I do plan to get to that level at some point. Its just at this point I still have a lot of basics to learn. When I was finally fed up with windows I was pretty damn good at tweaking pretty much every aspect of it. Not a pro but by no means an avg user. Id like to get to that level with linux but I am not willing to go full throttle yet. Last time I tried linux i scared myself away for a few months trying to set everthing up perfectly.

I have 4 basic problems to solve right now then from that point ill just be enjoying linux and learning as I go till I feel comfortable enough to dig in.

- fix brightness adjuster
- fix nvidia card not being detected
- (solved)ask about 12gb of swap 
- fix java in web browser
- (solved mostly) find out what recomended programs/toolz to install to make system function/work better

I bet my current problems are simple for most of you but being new these are all major tasks lol. I need to learn how to install filles that are not in the ubuntu software center. I know thats pretty damn basic but I am getting there tonight.

---

### Post by vandorjw on 2012-10-26
MYTH:
> 
your swap partition should be at least as big as your RAM size

uswsusp can compress the hibernate image about 50%, often more...
TuxOnIce can compress even higher, and does it faster


> 
I need to learn how to install filles that are not in the ubuntu software center.


why?
> 
fix nvidia card not being detected

What card do you have?
open a terminal.

```

lspci | grep VGA

```

---

### Post by Twilk73 on 2012-10-26
tom@Nanashi:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1213 (rev a1)

Results 
lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1213 (rev a1)


The graphics are for sure fixed but it still isnt recognizing the card.

---

### Post by koby90 on 2012-10-26
Its a great informative thread thanks everyone for this information and I am very glad to be part of this community.

---

### Post by Twilk73 on 2012-10-26
> **koby90 said:**
> Its a great informative thread thanks everyone for this information and I am very glad to be part of this community.

Yes thanks again guys. I know I am asking a lot of questions that are probably dumb to most of you but I am new. I have done search's prior to asking my questions however most the information is either dated or in a language that I dont yet understand considering linux is a different beast from windows. 

With that said I have found this forum to be very helpful and inviting thus far. Thanks!

---

