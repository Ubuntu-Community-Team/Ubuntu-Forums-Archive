---
title: "software packages and grub"
date: 2008-03-03
forum: General Help
---

### Post by sfong15 on 2008-03-03
I have been with ubuntu for few months now, spend most of my time using browser and terminal.    Since I come from the Windows camp I still feel a bit lost at application packages.    I have tried half a dozen or so distro and a lot of them 'advertise/promote' themselves having bundled with thousands of packages ready to use.    My trouble is that I don't know what these are except just seeing the name or a brief description.    The info available at the package installer is very limited and I found no website yet showing various package's use and details.    In the Windows' world freeware author normally has his/her own website explaining things.

Are there any websites putting together thousands of packages for the linux world telling newbie what they are, who did it, and current development etc...?

Next is about Grub.    I like trying different distro and versions of ubuntu.   How do I do that without messing with my old XP and 7.10 partition?

Thanks in advance.

---

### Post by arimaniac on 2008-03-03
Hi there

1)
It is difficult to maintain a website will all
or even some package info...

Dont forget that there are thunders of thousands of Linux developers 
and teams out there, nobody really knows all of them...

I would recommend sticking on what you use and you will 
find out more in time... 

Check out the **Synaptic Package Manager **for more info....

2)
If you are a newbie to Linux I would recommend trying other distros
with Live CDs..

And if you want to install them to test them, 
install them on a **seperate drive** and select the
boot drive from your BIOS <---   EASY!!!.

Multiple Linux+Windows config on the same drive is tricky....
They share the same grub boot record but only one of the distros
controls the boot loader... so it gets messy...

Hope this helps...

---

### Post by Herman on 2008-03-03
I know what you mean, wouldn't it be nice if there was a magazine that tested all kinds of different open source programs and presented nice reviews about them. How to use the program and what it can do, interesting extra features and that sort of thing. 

There is a nice and very helpful video about how to add software in Ubuntu at [screencasts.ubuntu.com]("http://screencasts.ubuntu.com/") , you will find some other videos you may be interested in there too.

What I do if I have time is go through Synaptic Package Manager or Add/Remove Programs and take a look around, reading the brief descriptions and then google for more information. I especially like to find the software's home page, most have screencaps and at least a little bit of documentation, maybe FAQ, and some even have their own forums too.
If I'm in a hurry I just use the search bar in Synaptic or Add/Remove.

It doesn't do any harm to just install the software and try it out, it's free after all. :)

I have a list of links to some of the open source software home pages in my Knoppix Page, the same software is also avialable in Kubnutu and some of it in Ubuntu as well, will this help you? [      An Alphabetical Listing of *Just Some* of the Great Software]("http://users.bigpond.net.au/hermanzone/p20.html#Alphabetical_listing_of_just_some_of_the").
If I or someone else with a website  kept on going with a list of links like that it would save people a lot of googling time. It took me a long time to get as far as I did with that list. Ubuntu has around 29000 packages last time I checked, so it would be a mammoth job to find the home page of each one.
I have noticed there are links in add/remove for some, (but not all), of the software there.

Regards, Herman :)

---

### Post by Herman on 2008-03-03
> Next is about Grub. I like trying different distro and versions of ubuntu. How do I do that without messing with my old XP and 7.10 partition? Usually your new install will just install it's GRUB to MBR and add your present operating systems to its boot menu so it's no problem at all.
If you want, you can try to get your new systems to install their bootloaders to their boot sectors and configure Ubuntu's GRUB to chainload them.

Another way is to try out GAG Boot Manager. You will need each boot loader installed to its boot sector and leave GAG Boot Manager either in MBR or in a floppy disk. GAG is simple to reconfigure for people who like to install and uninstall operating systems very often, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")

Regards, Herman :)

---

### Post by sfong15 on 2008-03-03
Thanks everyone.   No wonder ubuntu is so popular it's the community that matters.

Thanks Herman about GAG I'll try that out.    arimaniac's idea of separate physical drive is what I intend to do, HDD is so affordable these days.

Herman's Knoppix page is interesting and useful (am downloading Knoppix right now, I'll try that out soon).   I guess someone with time and passion must have maintained a much larger page of info about packages free to the Linux world.   But as you have said these package authors are everywhere and once a package is done they may have moved on to something else without continuing with documentation/further development.

I guess it takes the muscle of Canonical to maintain a fair size list of most popular/useful packages.   Having a millions free packages out there without a wiki explaining doesn't really help new users at large.   May be there should be sites like [http://www.freewarehome.com/...etc](http://www.freewarehome.com/...etc)

If you use 'freeware linux' you'll get 322k results from Google while for 'freeware windows' you'll get 2.29millions.    This comparison could be very wrong.    May be there are good sites showing info I needed, I'll just have to keep looking.   BTW who can afford the time to install each and every package to find out what it does and how good it is?    Someone to start a collaborative effort?

---

### Post by Herman on 2008-03-03
:)  Maybe you would enjoy a visit to the [Community Cafe]("http://ubuntuforums.org/forumdisplay.php?f=11") area of Ubuntu Web Forums. 
Take a look around there. There are lots of interesting threads there, such as:

[Cool applications you use that others might not know of]("http://ubuntuforums.org/showthread.php?t=382137")

[Whats the coolest thing you can do in Linux you cant in windows or mac?]("http://ubuntuforums.org/showthread.php?t=399997")

			 			 			 			[Anyone ever install all the packages in the repos?]("http://ubuntuforums.org/showthread.php?t=712200")

Those a just a few. :)

Regards, Herman

---

### Post by sfong15 on 2008-03-03
Thanks Herman.

---

