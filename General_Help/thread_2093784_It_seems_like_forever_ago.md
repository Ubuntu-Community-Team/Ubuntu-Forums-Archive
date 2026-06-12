---
title: "It seems like forever ago"
date: 2012-12-11
forum: General Help
---

### Post by Sylynce on 2012-12-11
Well Im new to Ubuntu.  I used Red Hat for a short while eons ago, but have been using windows for the most part.  I finally decided that I need to learn Linux and Unix so I did a clean install of Ubuntu on my laptop (HP Pavilion dv6 w/AMD A6 cpu).  Just installed today and it seems to be taxing my system heavily.  Im assuming that I just need to hunt for the proper drivers.  I know there is a ton of Linux stuff out there, but what is the best place to start?  Thank you for your input, even the "smart" comments that usually follow lol.

---

### Post by tgalati4 on 2012-12-11
How much RAM do you have?  If less than 1 GB then your machine will be thrashing.  2 GB is better.  Do you have a swap partition?

Open a terminal:
```
free
```

---

### Post by Sylynce on 2012-12-12
8GB of RAM, so thats not an issue. Hardware wise I should be more than ok. 1.6 GHz quad core AMD CPU, 750GB HDD, ATI radeon dual graphics GPU's etc...  When I start the system, it gets to the Ubuntu purpleish screen, the Ubuntu chime plays but the screen stays dark approximatly 4 ut of 5 times I start the system.  Im currently trying to find a video driver as I think that may be a big part of the issue there.  No swap partition I dont think.  I did not select the LVM mode when installing, perhaps I should re-install and select that?

---

### Post by orb9220 on 2012-12-12
> ATI radeon dual graphics GPU's 

Specific card? card model will determine how succesful it is covered in linux.
So list the specific of video card model will help.

---

### Post by Sylynce on 2012-12-12
Radeon HD 6520G and HD 6400.  I just went through the additional drivers and installed the catalyst driver update for linux from AMD's site.

---

### Post by Sylynce on 2012-12-12
Well it appears that part of the problem is that I was given a 32bit copy of 12.10 and I run a 64bit system.  So no that I downloaded and installed the 64bit 12.10 I need I need to find 64 bit catalyst drivers.  I downloaded catalyst 12.9 from AMD but that pooched my graphics and I had to start up in command line and r do a driver roll back.  I was still getting errors after I succesfully logged into the GUI.  Im currently re-installing 12.1 x64  Am I just going to have to live with the fglrx that is embeded in 12.1?

---

### Post by Bashing-om on 2012-12-12
Sylynce; Hi !

Try this. Boot up ubuntu to the desk top (12.04 version: launcher on left side of the screen choose System settings -> Additional drivers; and install the recommended driver from this utility.

[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by Sylynce on 2012-12-13
Yeah, ive got 12.10...  Im downloading a copy of 12.04 now, seems like maybe its a little more stable for my system.

---

### Post by mastablasta on 2012-12-13
the 12.10 has additional drivers untility in software sources (not sure why they moved it there hidden from the users view....)
 
the 32bit version will also run just fine on such a maschine.

---

### Post by 3rdalbum on 2012-12-13
Use the driver in Additional Drivers (12.04) or in Software Sources (12.10)  rather than downloading it directly from AMD.

It's the same driver, but a more reliable installation method.

---

### Post by Sylynce on 2012-12-13
Thank you for all the advice thus far. After spending a few hours last night trying different thingsm ive found that 32 bit 12.04 lts seems the most stable so far.  it auto updates the fglrx driver and seems to be doing great.  System fan isnt working overtime to keep the GPU cool, so thats a good sign.  I decided to get into Ubuntu to expand my OS knowledge base, as well as to start learning Unix.  I have an older tower server that was given to me and Im going to run BSD on it and try to make it a dedicated SWTOR server, or Ill just say screw it and turn it into a Minecraft server lol.

---

