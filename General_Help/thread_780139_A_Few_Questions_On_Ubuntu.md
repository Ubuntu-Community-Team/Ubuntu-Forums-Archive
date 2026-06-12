---
title: "A Few Questions On Ubuntu"
date: 2008-05-03
forum: General Help
---

### Post by Crazysah on 2008-05-03
First of all I have a Dell XPS 420 fitted with Windows Vista Ultimate.

Today... I decided to put Ubuntu 8.04 LTS on it...
So I installed Ubuntu and everything went fine...

Then when I restart and select Ubuntu... it won't start... It says some stuff and then shuts down... Why is that?

It will only start if you select Ubuntu go into the setup and then select one of the three... Which one?

Also... my sound just won't work in Ubuntu... Why?

I have a few questions;

1. Why won't Ubuntu start straight away?
2. What is the difference between the 3 options?
3. Why won't my sound work in Ubuntu?
4. What do I need to get Ubuntu setup?
5. Is there a way to dual boot Windows Vista Ultimate and Ubuntu 8.04
6. When I am using Ubuntu and I click restart... it restarts and goes to Windows... how do I change this?
7. I have 3GB of RAM and I have a Q6600 in my computer. What version of Ubuntu shall I be using?
8. Is there any software or any plugins I should install after installing Ubuntu?
9. Anything else I should know about Ubuntu?

Thanks
Crazysah

---

### Post by Zorael on 2008-05-03
> **Crazysah said:**
> First of all I have a Dell XPS 420 fitted with Windows Vista Ultimate.

Today... I decided to put Ubuntu 8.04 LTS on it...
So I installed Ubuntu and everything went fine...

Then when I restart and select Ubuntu... it won't start... It says some stuff and then shuts down... Why is that?

It will only start if you select Ubuntu go into the setup and then select one of the three... Which one?

Also... my sound just won't work in Ubuntu... Why?

I have a few questions;

1. Why won't Ubuntu start straight away?
2. What is the difference between the 3 options?
3. Why won't my sound work in Ubuntu?
4. What do I need to get Ubuntu setup?
5. Is there a way to dual boot Windows Vista Ultimate and Ubuntu 8.04
6. When I am using Ubuntu and I click restart... it restarts and goes to Windows... how do I change this?
7. I have 3GB of RAM and I have a Q6600 in my computer. What version of Ubuntu shall I be using?
8. Is there any software or any plugins I should install after installing Ubuntu?
9. Anything else I should know about Ubuntu?

Thanks
Crazysah
[list=1][*]It's hard to say without knowing *what* it says. :>
[*]If the three options you mention are something like 'boot normally', root shell' and 'fix X', that means that the graphical environment failed to load, likely because of videocard settings. Fix X should hopefully make it start, though you'll only have basic graphics. Then you can troubleshoot.
[*]Some cards take a bit of tinkering to work, such as Intel HDA cards. Supplying the terminal output of the following command would make it easier to help.
```
$ lshw -C multimedia
```
[*]You just need a live CD; pop it in, choose to try Ubuntu, see if you like it, then hit the Install icon on the desktop. While you seem to have already installed it, I suggest you try the other flavors of *ubuntu as well, before deciding. Kubuntu rocks, see.
[*]Short answer: yes. After having installed, you should have a boot manager pop up when you start your computer, where you'll be offered a choice of which OS to start; Ubuntu or Vista.
[*]This can be either because of the mentioned boot loader not loading (happens if Vista is installed after Ubuntu, or if you've somehow had Vista try to restore its boot process), or if Vista is set to be the default OS in that loader. Both can be dealt with.
[*]You only need to worry about the 64-bit version if you have more than 4gb ram. That said, if your processor supports it, you're free to pick that flavor anyway. While not all applications are available as 64-bit packages, 99.8% of them can still be run due to 32-bit compatibility. You'd also avoid the 2038 problem: [http://en.wikipedia.org/wiki/Year_2038_problem](http://en.wikipedia.org/wiki/Year_2038_problem).
[*]You likely want to grab the Restricted Extras, unless you put great weight on not having non-free software installed. This should get you Flash support, etc. Google 'ubuntu dvd support' to get some information on how to enable DVD playback. Also, read the wikipedia entry on 'Medibuntu'.
[*]Basically; linux is not windows. Please read this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

If you approach it as an alternative operating system, you'll likely live happily ever after. If you approach it as a cheap copy of Windows, you'll inevitably be frustrated by how things "just aren't the same". Linux suffers from lack of corporate support, so most drivers are **made by linux developers** rather than by the manufacturers. As such, there are devices that plain don't work, much like there are applications that plain don't exist for linux platforms (iTunes, for instance). This is not linux's fault.

I like the comparison between a toy car and a lego set mentioned in that link. With the toy car, you have a toy car. With a lego set, you can build a toy car with instructions, but you could also build so much more. If the instructions are unclear or don't exactly reflect your system, you will have some issues, but the large majority of which are solvable.[/list]

---

### Post by Crazysah on 2008-05-03
Thanks for your replies...

So I have a Dell XPS 420...

1. Now how do I get my sound to work in Ubuntu? (I still can't get it to work)
2. How do I dual boot Windows Vista Ultimate and Ubuntu? (How???)
3. When I am using Ubuntu and I click restart... it restarts and goes to Windows... how do I change this? (I still don't know how to do this...)

---

### Post by Crazysah on 2008-05-04
Anyone???

---

### Post by ghost_ryder35 on 2008-05-04
> **Crazysah said:**
> Thanks for your replies...
 
So I have a Dell XPS 420...
 
1. Now how do I get my sound to work in Ubuntu? (I still can't get it to work)
2. How do I dual boot Windows Vista Ultimate and Ubuntu? (How???)
3. When I am using Ubuntu and I click restart... it restarts and goes to Windows... how do I change this? (I still don't know how to do this...)
2. install grub
3. install grub and edit menu.lst

---

### Post by ugm6hr on 2008-05-04
@crazysah:

There are plenty of guides available on how to "dual-boot".

The OS you are dual-booting with is largely irrelevant (except with regard to creating space on the HD).

You state you installed Ubuntu already - how did you do that?

The other questions will be answered more easily once you tell us how you have installed.

As for sound - supply the information asked for by zorael - you will not have much luck getting help unless you read and respond to requests for more information.

---

### Post by ghost_ryder35 on 2008-05-04
is this your computer [http://review.zdnet.com/desktops/dell-xps-420/4507-3118_16-32716531.html?tag=ut](http://review.zdnet.com/desktops/dell-xps-420/4507-3118_16-32716531.html?tag=ut) ?  if so looks like you probally either have a sigmatel or realtek audio card...
you can try 
```

sudo apt-get install linux-backports-modules-generic

```

---

### Post by the8thstar on 2008-05-04
Looks like we are at it again **Ghost_Ryder35**! The weekend rescue team is back! :)

---

### Post by ghost_ryder35 on 2008-05-04
> **the8thstar said:**
> Looks like we are at it again **Ghost_Ryder35**! The weekend rescue team is back! :)
:guitar:

---

### Post by Crazysah on 2008-05-06
> **ghost_ryder35 said:**
> 2. install grub
3. install grub and edit menu.lst

How do I install Grub and then what do I edit the menu.lst too?

> **ugm6hr said:**
> @crazysah:

There are plenty of guides available on how to "dual-boot".

The OS you are dual-booting with is largely irrelevant (except with regard to creating space on the HD).

You state you installed Ubuntu already - how did you do that?

The other questions will be answered more easily once you tell us how you have installed.

As for sound - supply the information asked for by zorael - you will not have much luck getting help unless you read and respond to requests for more information.

Can you point me to a guide on dual-booting?

I downloaded Ubuntu 32-bit 8.04 LTS and then burned it to a CD. Then I inserted the CD and chose the drive and clicked install...

I have to go into Ubuntu and tyoe what zorael said into the terminal right?

I have a Creative SB X-Fi... so...

> **ghost_ryder35 said:**
> is this your computer [http://review.zdnet.com/desktops/dell-xps-420/4507-3118_16-32716531.html?tag=ut](http://review.zdnet.com/desktops/dell-xps-420/4507-3118_16-32716531.html?tag=ut) ?  if so looks like you probally either have a sigmatel or realtek audio card...
you can try 
```

sudo apt-get install linux-backports-modules-generic

```

Yes that is my computer but I customized it a little differently. I have a Creative SB X-Fi... so maybe I have a Creative card in there? How do I check what card I have?

> **the8thstar said:**
> Looks like we are at it again **Ghost_Ryder35**! The weekend rescue team is back! :)

Thanks guys for all the hard work!

Crazysah

---

### Post by ugm6hr on 2008-05-06
> **Crazysah said:**
> Can you point me to a guide on dual-booting?

I downloaded Ubuntu 32-bit 8.04 LTS and then burned it to a CD. Then I inserted the CD and chose the drive and clicked install...

Sounds like you used the LiveCD, so you haven't installed at all.

Try this for a good walk-through on dual-booting: [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

---

### Post by Crazysah on 2008-05-07
Yes. I inserted the CD and clicked install. Now I don't have to use the CD to boot... that means I must have installed it?

Unless you are talking about something else?

---

### Post by ugm6hr on 2008-05-07
> **Crazysah said:**
> Yes. I inserted the CD and clicked install. Now I don't have to use the CD to boot... that means I must have installed it?

Unless you are talking about something else?

OK. Misunderstood.

You clearly have installed.

I'm confused as to what you are asking now.  Do you have Windows as well, or not?

You were looking for advice how to dual-boot, but I am unsure whether you already have a dual-boot.

---

