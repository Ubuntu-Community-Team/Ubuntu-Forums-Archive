---
title: "A &quot;new&quot; Nvida driver -- OPEN-Source"
date: 2006-11-26
forum: General Help
---

### Post by autocrosser on 2006-11-26
OK--now that I've got your attention:D

There is a Project called "Nouveau" that is developing a open-source Nvidia driver--This is in the basic stages--2D & "some" 3D is working right now--Looks like it needs people that are willing to help test/code/debug to make it happen---

I for one would really like to rid myself of the closed driver I'm using--I play one game (UT2004);) & the Nvidia driver is the only way it plays:-?--

I think that the community has enough interest that we could get on board & give this project a boost--

In the current times of Micro$ft & other big corps trying to throttle us, ways to show that they should be more open-minded should be helped along.

Take a look at Nouveau at: [http://nouveau.freedesktop.org/wiki/FrontPage](http://nouveau.freedesktop.org/wiki/FrontPage)

To the Mods--please sticky this where it will do the most good.

Thanks!!!

Edit: rubinstein added this thread: [http://www.ubuntuforums.org/showthread.php?t=299516](http://www.ubuntuforums.org/showthread.php?t=299516)

Please take a look!!!!

---

### Post by rejser on 2006-11-26
Why would you like to get rid of nvidias closed driver? does it matter for you that it is closed, because I think it does a great work

---

### Post by autocrosser on 2006-11-26
As I stated in my first post--send a message to the big $ that they should be "more" open-source. Also, the closed driver "taints" the kernel & I for one would like my system to be more "free".

---

### Post by viciouslime on 2006-11-26
Well, good luck to them, but I can imagine this will be a very slow and painful process and what with the rate nvidia throws out new chips will they be able to keep on top of it all?

---

### Post by aysiu on 2006-11-26
[quote=Nouveau's webpage]**What is the current state of things ?**
Currently, nothing works. If you're not a developer, you're not interested in this at all.[/quote] I guess I'm not interested in this at all yet.

---

### Post by ardvark71 on 2006-11-26
> **aysiu said:**
> I guess I'm not interested in this at all yet.

I read that too. That's too bad, I'm sure a lot of people would like to help :-? 

Regards...

:KS

---

### Post by autocrosser on 2006-11-26
Hi Aysiu-- according to the people on devel-list, it is working at this time (I guess the disclaimer on the main page is a "bit" strong;))--there are install instructions for debian in a few pages---I'm game enough to see what it can do & I really think that the effort is a good one. 

For anyone that is interested--there is a VERY spirited thread about including the closed drivers in fiesty--makes some thoughtful reading--most of the devs are against it on the grounds of GPL & kernel-tainting.

---

### Post by rubinstein on 2006-11-26
And don't forget the pledge at [http://www.pledgebank.com/nouveaudriver](http://www.pledgebank.com/nouveaudriver)

See also the corresponding thread:
[http://www.ubuntuforums.org/showthread.php?t=299516](http://www.ubuntuforums.org/showthread.php?t=299516)

---

### Post by autocrosser on 2006-11-26
Thank You rubinstein!!

I went there & put my money where my mouth is:D

I think that we should support this idea in everyway we can.

---

### Post by Dubbayoo on 2006-11-26
I signed the pledge, even though I really couldn't care less. I am not a zealot about totally open kernels and what not. I use the open ATI driver now but if Nvidia continues to produce good closed drivers that's better than nothing. If they want to keep some IP to themselves I won't begrudge them for that.

---

### Post by deanlinkous on 2006-11-26
Oh I wouldn't begrudge them either, but at least give me a open driver that at least does 3D. Keep that super pixel shading texture mapping stuff closed up is fine.

---

### Post by autocrosser on 2006-11-27
This is a proposed solution from one of the developers--I suggest everyone give it a read & comment on it:

On 11/26/06, Henrik Nilsen Omma <henrik@-------.com> wrote:

I agree with Colin that we should not include non-free drivers by
default. (I am also a Canonical employee, but the opinions expressed
here are solely my own, etc. And likewise it's not my call). I've been
thinking a bit about how we might do that in an elegant way.

I suggest we are very up front about it and present it professionally to
the user. We make it a feature :) We make the 'free drivers by default'
AND the 'simple availability of desktop acceleration' major selling
points of the next release. Both to the community and to the end users.

When the user first boots the system we pop up a window with the
following message:

"Your display driver is not optimally configured to work with your
display card. Click here for more information. "

You are then given some options.
[Ignore – continue with the current setup]
[Just fix it - Install additional drivers]
[More information – See what you are missing and why]

Installing the drivers should be very easy – Obviously. We can even ship
them on the CD so there is no need for an internet connection. This is
still very different from installing them by default because it gives
the user a choice and it uses the opportunity to educate. If done
properly it will still only take 2 minutes to configure and will be
painless. It should be a much more pleasant experience than searching
the net or your CD collection for the right graphics driver for Windows.

The More info option could be accompanied by an animated gif giving a
taster of the desktop effects. It would be quite difficult to resist
clicking on it ...

Doing so would bring up a new window with an embedded video showing all
the Beryl/Compiz coolness and providing more information. It needs to be
*very* slick though. This is not just a simple feature demo it is a
marketing opportunity for desktop effects, free software principles and
Ubuntu all rolled up into one.

We should run a contest to have made the best Beryl/Compiz screen casts.
There are already a ton of these on YouTube so the expertise is clearly
out there. But we should challenge the community to make high quality
versions (which must be updated just before release to contain the
latest artwork). In addition to that there needs to be a story board
charting how to present the additional information and ensuring that it
all flows smoothly. This is no longer just about showing off desktop
coolness but also about putting across a message. The textual
information and voice-over (or music?) needs to be added professionally.
We have experience with this from the about-ubuntu video.


The points we can present to the user are quite simple and strong:

* Ubuntu is built on Free Software – Why this is good now and for the
future.
* A comparison with Vista -- MS vista also has some level of hardware
acceleration for its desktop on certain selected systems. The difference
is that selection criteria is not freedom but money: First you need to
have a powerful and secondly it only comes with the more expensive
editions of Vista. Ubuntu is free and lets you choose what software you
wish to use with it.
* It's easy to install – Just click ...

If made professionally I don't think this will irritate the users who
will soon also be faced with Widows Genuine Advantage. Even if a Windows
activation procedure is successful most users will walk away from it
with a bad taste in their mouth. MS regards them as dishonest by
default. With Ubuntu on the other hand you are given a completely free
choice of what to install and given the honest information about the
background. Users will see the difference in the approaches and will
appreciate it.


Letter campaign button

After the presentation has been made, the user should be presented with
a few additional options. Again, you can simply install the proprietary
drivers and move on, or install additional drivers with a click.
Additionally you get an option to write a letter of
complaint/encouragement to Nvidia or ATI. Clicking takes you to a
web-page where you can add your signature, send an email or download an
OpenOffice file of a pre-written letter to the relevant graphics card
maker.

It should be available in the user's native language. Just the community
effort of translating these and the subsequent work required by the
recipients to translate them back (if they do that – from experience
with Amnesty governments and companies actually do this) would create
quite a bit of buzz around the issue. What better way to measure the
number of user who are using Ubuntu and would like Nvidia/ATI to cater
better for them than in metric tons of paper!


Basically, If we go with free drivers by default though we could beat on
the big drums about it. From the community POV we will have done the
right thing and regarding the end users we can justify presenting it
up-front and centre because (a) it's a major new feature (b) their
involvement is required to activate it and (c) we are educating them.

We could even let the Live CD run with non-free drivers by default and
ask the user to confirm that choice before installing it with Ubiquity.
Letting the user run non-free drivers on the Live CD is less bad than
installing them. And even that (Live CD use) is greatly mitigated by
being up-front and educational about it IMO.

There is non-free software in the world and we have to live with that
fact. The question is not whether we put it on a server or a CD but
whether we are trying to push the world in the right direction or not.

Henrik

---

### Post by neuschnee on 2006-11-27
IMHO: I use what works good, not that which is most politically or legally appealing. Simple logic dictates that this new driver will never work as good as NVIDIA's official one -- they have paid developers who have all the (hardware) data they need on hand, whenever they need it. Besides all that, I think the NVIDIA drivers for Linux are great. They've put a nice effort into it.

---

### Post by DoctorMO on 2006-11-29
> IMHO: I use what works good, not that which is most politically or legally appealing. Simple logic dictates that this new driver will never work as good as NVIDIA's official one -- they have paid developers who have all the (hardware) data they need on hand, whenever they need it. Besides all that, I think the NVIDIA drivers for Linux are great. They've put a nice effort into it.

What works is often what was faught over before on your behalf by other people who felt that it should work within the best political and legal frameworks. pragmatism is nice but don't replace it with a rather simple trivial view point.

nVidia drivers don't work for some people because nVidia doesn't fix them and never will. nVidia drivers don't work when they have securty faults that don't get fixed. nVidia drivers don't work when the methods used are quick and dirty. we'd never know o'course but only political, ecconomic and legal presure will ensure that nVidia drivers work and continue to work in the future.

---

