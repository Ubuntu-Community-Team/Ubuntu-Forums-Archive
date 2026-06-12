---
title: "Help with building a pure (ubuntu)linux mythtv box ."
date: 2007-03-29
forum: General Help
---

### Post by kilgor3 on 2007-03-29
What can I say?  I'm a bit of a mommas boy.  To show my appreciation for my mother, this coming mothers day I would like to give her a personal video recorder.  I was thinking about getting her a TiVO, or something like that, but I figure if I actually build the thing, it would mean so much more.  I've been around linux for close to 3 years now and I think if the process isn't TOO difficult, I'd like to make a MythTV box.  With that said I have a  bunch of questions.  Perhaps this community can guide me in the right direction.

My budget is around 500$(though I would like to spend less), I have lots of spare parts lying around.  Like ram, power supplies, old (noisey)motherboards and hardrives.  The main purchases I think will be a large hard drive, a TV tuner, infrared remote (or possibly wireless keboard and mouse for web browsing from the couch) and a sleek case.  I always have a problem with hardware and linux.  It seems, with my luck, I always get hardware that is not linux friendly.  For this box I'd like all parts to be as linux friendly as possible.  So what CPU, MOBO, DVD-rom, TVtuner, Graphics Card Wireless network card, et cetera would you guys recommend?  Im looking to run ubuntu.

If anyone has done this before, I'd like as much feedback as possible.  What type of specs would you recommend?  Is this process very hard?  Will i have to compile alot of things from source or is the process streamlined?

Is it possible to make MythTV or any other recording software as user friendly as possible?  My mother isnt very tech savvy.  She understands the concept of remotes and is a master of playing online card games lol.  I can work out the bugs if they arise, but what worries me is the interface.  I need it to be streamlined for a newb.  Can I boot straight to the mythTV program? 

Thank you for your time,

-Kilgore

---

### Post by kilgor3 on 2007-03-29
I just realized this post belongs in the multimedia section.  Could someone move it for me or should I cross post?

---

### Post by majoridiot on 2007-03-30
for a dedicated mythbox, i suggest installing the backend/frontend setup for feisty when it is
released.  installation ease is improved and it also has autologon scripts to keep the frontend
logged in and active from boot up- which would be a boon for a non-tech-savvy user.

from a tuner standpoint, you can find a list here: [https://help.ubuntu.com/community/MythTV_Feisty_hardware_list](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list)  
for regular SD tuning, i recommend the hauppauge PVR series.  firewire tuning is also a possibility 
if you have a compatible cable box.

i wouldn't recommend trying to get a mythtv setup streaming over wireless- it can be done, but
only if it is the only network traffic over wireless and you have a rock-solid, strong strong signal.
i definitely recommend a hard line if you intend to stream over the network.

---

### Post by kilgor3 on 2007-03-30
Thanks for your response.  I've noticed through my research that alot of people use dual tv tuners.  Why is that?  Is it so you can watch TV and record a different channel at the same time?  also when playing back, do i need to have a sound output?

When does this backend/frontend system come out?

thank you again for your help,
Kilgor3

---

### Post by majoridiot on 2007-03-31
> **kilgor3 said:**
> Is it so you can watch TV and record a different channel at the same time? 

yes... or record two different channels at the same time.

> **kilgor3 said:**
> also when playing back, do i need to have a sound output? 

only if you want to hear it. ;)

you will need to route the sound out from the computer to speakers of some type... this can be out to 
an existing media amplifier, to a stand-alone speaker setup or routed to the television.  working in 
your budget range, i suggest getting a motherboard with built-in sound- just make sure that it is 
compatible.  i've always been very satisfied with nvidia's chipsets... and you can find on-board sound
anywhere from two to 6 channels at reasonable prices many times.

> **kilgor3 said:**
> When does this backend/frontend system come out? 

the new feisty mythtv packages will be "officially" available in a couple of weeks.  mythtv packages
are currently available for both dapper and edgy.

---

### Post by Maestro23 on 2007-03-31
Go to the following link and search "mythtv".  Will bring up the community docs.

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

Good luck on your project.

---

### Post by majoridiot on 2007-03-31
sorry... thought i had posted that.  [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

