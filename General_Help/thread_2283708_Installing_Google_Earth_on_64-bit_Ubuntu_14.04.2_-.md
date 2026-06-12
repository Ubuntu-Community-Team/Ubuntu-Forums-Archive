---
title: "Installing Google Earth on 64-bit Ubuntu 14.04.2 - crashes seconds after launch."
date: 2015-06-23
forum: General Help
---

### Post by Kim_Holder on 2015-06-23
This is for Google Earth, which i have been trying to reinstall because it stopped working after a day. I have a 64 bit machine and am running Ubuntu 14.04. The 64 bit version of Earth was running, but then today it crashed a few seconds after opening every time. 

I did `sudo apt-get purge google-earth-stable` to remove the package. I read there is an issue with the 64 bit version because of ia32-libs is deprecated. So i downloaded the 32 bit package and installed it with the Software Center but it wouldn't run at all. 

I removed the package again - I don't know why really, it was a stab in the dark. I deleted the installation package and downloaded it again. Now when I try to install that new package with the Software Center it says "An older version of 'google-earth-stable' is available in your normal software channels. Only install this file if you trust the origin".

What does that mean, and what should i do?

---

### Post by kostkon on 2015-06-23
Try cleaning your package cache. Close the software centre, open a terminal and do:
```
sudo apt-get clean
```
then try again. A sudo apt-get update beforehand wouldn't harm either.

---

### Post by Bucky Ball on 2015-06-24
Are you trying to install Google Earth from the Software Centre, the official repos, or are you downloading a .deb file, then using Software Centre to try and install it? Have you installed a third-party PPA from Google or anywhere else?

---

### Post by Kim_Holder on 2015-06-24
I downloaded a .deb file from Google - the Software Center doesn't have it. I have tried installing it with the SC, tried building a package for it from 2 different guides.

I did install a few PPAs yesterday, basic ones I didn't think would cause a problem and might help - like Java and Gnome3. But the problem started before that.

I'm starting a new thread because the situation has now changed and this seems to be something happening to a number of people, so I want to try to ask something they will be able to find.

---

### Post by Bucky Ball on 2015-06-24
How has it changed? If it is just a progression of this and not a new issue, please do not post a duplicate thread about the same issue. It will quite possibly be merged back with this one by myself of another staff member if this is the case. Thanks.

Why not just let us know where you are at with it now and provide a link to wherever there are these other people having the same issue.

---

### Post by Kim_Holder on 2015-06-24
I guess I didn't do a clean beforehand, I did an update. There were several attempts yesterday, I sort of need Google Earth working and I kept going when it was taking a bit for answers to come in here.

Thus I am going to start a new thread as this seems to be a known issue with no solution I can get to work :P

---

### Post by Bucky Ball on 2015-06-24
Up to you. If you think your 'new' issue is sufficiently different and not a direct result of what has been worked on here, then fire away. If it isn't, hold your fire, as one of the threads will probably be closed or they will be merged together.

Starting a new thread about the same or a similar issue will not get more support. It dilutes community support which is why we close and merge them. To give you a better chance.

Leave you to it and good luck. If you need no more help here, mark the thread as solved, please. See the second link in my signature.

---

### Post by Kim_Holder on 2015-06-24
Alright. Then I guess in a bit I should edit my first post to better reflect the issue.

I tried 3 different kinds of installs yesterday. The regular one from [Google's page]("https://www.google.com/earth/download/ge/agree.html") and using the [official guide]("https://help.ubuntu.com/community/GoogleEarth"). 

[This one]("http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html"), which seems to be the same but sets up a repository for updates through the terminal.

In the case of these two, now there is this message when I try to install the libraries they recommend:

[COLOR=#696969]The following packages have unmet dependencies:[/COLOR]
[COLOR=#696969] libcheese-gtk23 : Depends: libcogl15 (>= 1.15.8) but it is not going to be installed[/COLOR]
[COLOR=#696969] libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed[/COLOR]
[COLOR=#696969]              Depends: gstreamer1.0-clutter but it is not going to be installed[/COLOR]
[COLOR=#696969] libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed[/COLOR]
[COLOR=#696969]                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed[/COLOR]
[COLOR=#696969] libclutter-gtk-1.0-0 : Depends: libcogl15 (>= 1.15.8) but it is not going to be installed[/COLOR]
[COLOR=#696969] libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.4)[/COLOR]
[COLOR=#696969]                        Recommends: libgl1-mesa-dri:i386 (>= 7.2)[/COLOR]
[COLOR=#696969]E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

[/COLOR][COLOR=#000000]There are no held packages.

Last, I tried [this method]("http://www.gaggl.com/2014/05/install-google-earth-on-ubuntu-14-04/comment-page-1/#comment-47010"). Unlike the other two, it tries to install the 64 bit version by building a package for it. 

The guides for the 32 bit version resulted in nothing happening when I tried to open Earth. The last method returned the situation to the way it was yesterday morning - Earth opens but shuts down after 5 to 10 seconds.

The day before, Earth worked. I installed it that day, I believe the 64 bit version, and it worked without any problem.

(PS - Sorry, post #6 was an attempt to respond specifically to kostkon, and I hadn't seen your new post yet.)[/COLOR]

---

### Post by Kim_Holder on 2015-06-24
I found [this thread]("https://askubuntu.com/questions/366438/how-to-install-google-earth-64bit-in-ubuntu-13-10-ia32-libs-dependency-error"), which is for Ubuntu 13.10 but contains answers dealing with 14.04. 

First I need to completely remove the current package, then I want to try the two first answers. But that won't be until this evening so in the meantime if there are any insights it's appreciated.

---

### Post by Bucky Ball on 2015-06-24
I'd stick with number 18 and this:

> For Ubuntu 14.04.2 image 64 bit installs (when using the 14.04.2 image you get the mesa-lts-utopic stack so one package is different, ie. libgl1-mesa-glx-lts-utopic:i386

```
sudo apt-get install libc6-i386 libglib2.0-0:i386 libsm6:i386 \
libglu1-mesa:i386 libgl1-mesa-glx-lts-utopic:i386 libxext6:i386 \
libxrender1:i386 libx11-6:i386 libfontconfig1:i386 lsb-core
```

Then get the current i386 package & install it - [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

That is specifically for 14.04.2 (check that's what you're running and not .1). The first answer isn't and a bit/lot can change between releases, as can be seen by the fact that the instructions are totally different. If 18 doesn't work, see if tips from 17 can fix, which would be the instructions above the ones I've posted here.

---

### Post by Kim_Holder on 2015-06-25
I just got to this again. I followed the instructions in that 2nd answer, as you advised, Bucky Ball. I checked my version first with [COLOR=#696969]lsb_release -a[/COLOR]. It is indeed the 14.04.2 LTS.

Google Earth now opens but doesn't render correctly. The globe fills with tiny squares. I think I saw this mentioned elsewhere while i was searching for a solution before, i have to try to find that again.

[img]http://i.imgur.com/JeffKy7.png[/img]

I should maybe mention i reinstalled Ubuntu yesterday. It was maybe overkill, but i had added a few PPAs that were probably fine from a popular blog article about what to after installing Ubuntu. I am now thinking maybe that wasn't the best idea. And in a comment to inquiries about this problem on askubuntu, because there was a dependency problem i was advised to do that. Going through that taught me about backing up and restoring, so i don't really mind.

---

### Post by Bucky Ball on 2015-06-25
PPAs can cause issues so starting with a clean slate is not a bad thing. You can add them back one by one and see if one causes an issue. Remember that third-party PPAs are not supported officially by Canonical and not checked for compatibility either, so the risk is yours. The repos may contain dodgy code or the server fall over without warning at inopportune times. Always check the Software Centre for the app (the officially supported repos) before resorting to a PPA. 

You are making progress! That looks like a rendering prob. What graphics driver/card are you using? Let's see the output of this:

```
sudo lshw -C video
```

What does high def playback look like in, say, Youtube? Same?

* I did spot [this]("https://productforums.google.com/forum/#!topic/earth/__hoinbXFO4"). I don't use GEarth myself so can't play around with it at this end.

---

### Post by Kim_Holder on 2015-06-26
This is returned for video hardware:

```

 *-display               
       description: VGA compatible controller
       product: GF108 [GeForce GT 430]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:55 memory:f9000000-f9ffffff memory:e0000000-e7ffffff memory:ee000000-efffffff ioport:bf00(size=128) memory:fa000000-fa07ffff

```

A high-definition video on Vimeo played fine. I haven't had any other video issues. I'm using the proprietary Nvidia driver, version 331.113. 
GEarth has worked fine on this card, with Ubuntu Studio, which i replaced with the LTS a couple of weeks ago because it isn't very well supported and i'd messed it up, and i haven't needed GEarth until now.

---

### Post by Kim_Holder on 2015-06-26
OH - it appears to be fixed. I looked over [this pos]("http://malektips.com/google_earth_0004.html#.VY17V3UVhBd")t on Malektips. I cleared the disk cache (Tools > Options > Cache tab) and suddenly everything was fine. 

I didn't think it could possibly be that simple. Maybe an update that came in since i installed it was needed? Anyhow, i'm happy now.

---

### Post by Bucky Ball on 2015-06-26
Excellent news! Please see the second link in my thread and enjoy! ;)

PS: Ubuntu Studio is supported as Ubuntu is. Same kernel. UStudio 14.04 LTS also has long-term support.

---

### Post by monkeybrain20122 on 2015-06-26
BTW google has dropped developement for google earth since the beginning of the year and its functions are migrating to google map. Google earth pro is now free but as of Feb they didn't provide  a Linux package, the linux bin was an ordinary ge,-- now deprecated,--for Windows running in wine

---

### Post by Kim_Holder on 2015-06-26
> [COLOR=#000000]PS: Ubuntu Studio is supported as Ubuntu is.[/COLOR]

What i should have said is that the interface is different enough that when i sought help, often things were in different places and i had to search for them.

> [COLOR=#000000]BTW google has dropped developement for google earth since the beginning of the year and its functions are migrating to google map.
[/COLOR]
Hm. I hope they have planned to move their Moon interface over to Maps. I use it a lot, in fact it is why i was struggling to get it installed.

[COLOR=#000000]I changed the title of this thread, thinking it might make it easier for others to find it. 
[/COLOR]

---

### Post by BZZZzzz... on 2015-09-05
[http://www.noobslab.com/2014/03/install-google-earth-in-ubuntulinux.html](http://www.noobslab.com/2014/03/install-google-earth-in-ubuntulinux.html)

---

