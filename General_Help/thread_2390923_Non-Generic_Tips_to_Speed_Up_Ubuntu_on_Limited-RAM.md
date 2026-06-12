---
title: "Non-Generic Tips to Speed Up Ubuntu on Limited-RAM systems"
date: 2018-05-03
forum: General Help
---

### Post by galacticstone on 2018-05-03
I currently have 4gb of RAM and plan to buy some more RAM in a few months. In the meantime, I was wondering if there is any type of bonafide "Speed Guide" to increase the apparent performance of Ubuntu? There are several blogs out there on the web with some mostly-generic advice that doesn't seem to produce much noticeable result. I installed the Gnome Flashback (Metacities) over my Unity (in 16.04 which is what I am currently running) to try and speed things up a bit, but one area where it doesn't seem to help is opening certain apps for the first time. Opening the USC for the first time generates a very long delay of upwards to 30-45 seconds. Opening Chrome sees a delay of up to 30 seconds. Subsequent opens don't have this delay because of the cache. I thought using Preload would alleviate this somewhat, but not so much, if it all (doesn't seem any faster than prior to Preload).

I also have a folder of rock and meteorite photos - maybe 5,000 of them and whenever I open it, I get a really l-o-n-g delay waiting for all of the thumbnails (for that view) or file attributes to load (for list view). I broke the big folder down into two parts, but each takes a long time to load - it didn't seem to split the total time much.

All of this behaves like inadequate RAM (or impatient user - me), so is there anything I can do (short of adding more RAM) to speed up these operations?

(Note, I tried LXDE, Xfce, MATE, vanilla Gnome, and Unity - the delays are the same/similar regardless of which desktop environment I use.)

Thanks in advance!

MikeG

---

### Post by monkeybrain20122 on 2018-05-03
I don't think it is the ram. 4 G is plenty and if you have problems even for xfce then the problems lie elsewhere. I heard snap packages take forever to start the first time (not snappy at all :)) Maybe some of the packages you installed are snaps (good chance if you install from the software center) To check which snap package is installed 
```

snap list
```

---

### Post by galacticstone on 2018-05-03
I just checked. I only have 3 snaps installed. One is VLC (which also lags a bit the first time, but is not as bad as Chrome and USC). The other is a silly keyboard sound thingy (Bucklespring) that I had forgotten about and just uninstalled. The last one is "core" - I don't recall downloading that one.

---

### Post by monkeybrain20122 on 2018-05-03
Do you have a lot of tabs open in chrome? If so try this [https://chrome.google.com/webstore/detail/lazy-tabs/aabgbgciohhaogajcnacpgilhmacdahc?hl=en](https://chrome.google.com/webstore/detail/lazy-tabs/aabgbgciohhaogajcnacpgilhmacdahc?hl=en)
You can see how many processes are running in Chrome by going to the three dot menu > more tools > task manager.
No idea about USC since I never use it may be you can try starting it in the terminal and see if there is any useful info.

---

### Post by kerry_s on 2018-05-03
you can preload chrome at startup in the startup app.
google-chrome-stable --no-startup-window

for the photos, try using a image/photo viewer instead, it'll be less overhead compared to the file manager.

i still consider 4gb plenty of ram & if your on 16.04 unity it should run just fine with 2gb(which i use in vm without issues).

try installing "beignet" from software center or command.
with intel gpu, the newer the kernel the better supported.

---

### Post by galacticstone on 2018-05-03
I rarely have more than 2 tabs open at any time, sometimes 3. But, Chrome doesn't lag during use, it's only when it's started for the first time after a reboot or shutdown. Everything runs smoothly once it's been opened and subsequent opens are much faster.

---

### Post by galacticstone on 2018-05-03
> **kerry_s said:**
> you can preload chrome at startup in the startup app.
google-chrome-stable --no-startup-window

[B]for the photos, try using a image/photo viewer instead, it'll be less overhead compared to the file manager.
[/B]
i still consider 4gb plenty of ram & if your on 16.04 unity it should run just fine with 2gb(which i use in vm without issues).

try installing "beignet" from software center or command.
with intel gpu, the newer the kernel the better supported.

This happens when I am browsing to find a file to attach to an email or when finding a file to add to an online post. I don't think I can use a photo manager in this way can i?

If I add Chrome to my startup, will this cause an increased delay during the startup (in other words, will the initial wait time for that first open be transferred to the start-up process, or will it load faster this way)?

I will look into beignet.....  :)

---

### Post by deadflowr on 2018-05-03
"core" is the main piece to actually run snaps.

All snaps require core be installed.
remove core and snaps are dead weight.

Read popey's answer (specifically the bottom part):
[https://askubuntu.com/questions/1000177/is-the-snap-core-folder-needed]("https://askubuntu.com/questions/1000177/is-the-snap-core-folder-needed")

edit: fwiw

---

### Post by kerry_s on 2018-05-03
> **galacticstone said:**
> This happens when I am browsing to find a file to attach to an email or when finding a file to add to an online post. I don't think I can use a photo manager in this way can i?

If I add Chrome to my startup, will this cause an increased delay during the startup (in other words, will the initial wait time for that first open be transferred to the start-up process, or will it load faster this way)?

I will look into beignet.....  :)

if you know the name, i think you can start typing the name to find it faster instead of scrolling for it.

no, no hit to startup, i use it all the time.

beignet, is the intel gpu driver. it'll speed up things a little where it might of lagged before.

---

### Post by HermanAB on 2018-05-04
Well, 4GB is a lot, but Gnome makes any computer slow.

---

### Post by galacticstone on 2018-05-04
I couldn't find anything named "[COLOR=#000000]beignet" in the USC....

Edit : I did find it with Synaptic, but the changelog doesn't show any updates since 2015 or 2016, so I am a little hesitant to install it. I went to the website and read the instructions, and it all sounded like Greek to me. LOL.

[/COLOR]

---

### Post by linux4me on 2018-05-04
I guess if you're waiting to upgrade the RAM, getting an SSD to replace the HDD is out of the question? That's the biggest jump in performance I've seen when it comes to boot time, opening programs, and browsing large directories.

---

### Post by Impavidus on 2018-05-04
To me, it all sounds like a slow hard drive. Loading the program itself from disk takes time, and that's what preload should avoid. But after the program has started – but maybe before it has opened a window – the program may spend some time doing things without showing anything to the user. I don't know how chrome works, but it may read all cache it has stored on disk before responding to user input. After loading the cache in ram, it appears fast. If the file manager has to show thumbnails, it has to read 5000 image files from disk. If the thumbnails are cached, that's 5000 small image files, but still. Although it may initially only load the ones currently in view. The software centre may be somewhat different, as it may be checking for updates while opening.

So replacing the HDD with an SSD may be more effective than getting more ram.

---

### Post by kerry_s on 2018-05-04
> **galacticstone said:**
> I couldn't find anything named "[COLOR=#000000]beignet" in the USC....

Edit : I did find it with Synaptic, but the changelog doesn't show any updates since 2015 or 2016, so I am a little hesitant to install it. I went to the website and read the instructions, and it all sounded like Greek to me. LOL.

[/COLOR]

my guess is because your on 16.04. here's what it looks like in my solus install.
[ATTACH=CONFIG]279572[/ATTACH][ATTACH=CONFIG]279573[/ATTACH]

---

### Post by galacticstone on 2018-05-04
> **kerry_s said:**
> my guess is because your on 16.04. here's what it looks like in my solus install.
[ATTACH=CONFIG]279572[/ATTACH][ATTACH=CONFIG]279573[/ATTACH]
There is no Beignet in the Ubuntu Software Center, but I do see an older (November 2015) version via Synaptic. Here is a screenshot of the changelog of that version.

I'm still a little green compiling stuff and figuring out dependencies and such, so I don't want to Github it yet.

---

### Post by kerry_s on 2018-05-04
in software center i usually search "intel" to find it.

try it anyways, i think the version is made to match the kernel. you are running an lts after all, your not going to get the latest, only security fixes.

---

### Post by monkeybrain20122 on 2018-05-04
You get new beignet here, but do it at your own risk,[https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa/](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa/)

Oops, sorry it is only for artful.

---

### Post by galacticstone on 2018-05-04
I will be updating to 18.04.1 when it comes out. Will I still need to download Beignet after updating, or will that newer version of Ubuntu have the updated GPU drivers?

---

### Post by kerry_s on 2018-05-04
> **galacticstone said:**
> I will be updating to 18.04.1 when it comes out. Will I still need to download Beignet after updating, or will that newer version of Ubuntu have the updated GPU drivers?

i always have to install myself in every distro. it's just basically for better performance, but your gpu will work just fine without it.

---

### Post by Autodave on 2018-05-05
Spend the money on an SSD. You don't need a big one: 30 gig would be great. Keep all your files on the older spinner drive.

---

### Post by galacticstone on 2018-05-05
AutoDave :

How fast is a micro-SD card compared to an SSD?

I already have a 32g micro-SD I could use.

Edit : (just did some Googling)

This Sandisk Ultra-Plus micro-SD has "10 to 80 MB/s" transfer speeds, depending on when the card was manufactured (according to Sandisk website). I assume this is the read speed and not the write speed.

My Western Digital HDD is a 5400rpm that averages about 86MB/s mixed i/o speed and 1.48MB/s write speed.

So I assume this means the micro-SD card would be about the same, if not a little slower, than the old fashioned spinning HDD?

I have seen those pro-grade micro-SD cards for photographers that have much higher read write speeds, but then the cost of those starts getting close to what a small SSD costs....

---

### Post by Paddy Landau on 2018-05-08
I'm with the OP here. I have 4Gb on a (relatively) old computer.

Ubuntu definitely slows things down, albeit nowhere near as slow as Windows 10 on the same machine. Apps also crashed an awful lot.

I reinstalled, but using [Lubuntu]("https://lubuntu.me") instead. It made a massive difference. Nippy again, and hardly any more crashes.

Although you can install Lubuntu over Ubuntu, when I did this, I found too many problems with clashes between the two systems. (There shouldn't be clashes at all, but "shouldn't" and "aren't" are two different things.)

---

### Post by tinylagarto on 2018-05-08
> **galacticstone said:**
> There is no Beignet in the Ubuntu Software Center...

In 18.04 the package is called beignet-opencl-icd, if you need it. I only use the command line so I do not have an idea how they call it in software centers. 

I guess in 16.04 it is called beignet, like in Debian before, in 18.04 that is now a transitional package. 

You can find out using apt in a terminal:

```
apt search beignet
```

---

### Post by galacticstone on 2018-05-16
> **Paddy Landau said:**
> I'm with the OP here. I have 4Gb on a (relatively) old computer.

Ubuntu definitely slows things down, albeit nowhere near as slow as Windows 10 on the same machine. Apps also crashed an awful lot.

I reinstalled, but using [Lubuntu]("https://lubuntu.me") instead. It made a massive difference. Nippy again, and hardly any more crashes.

Although you can install Lubuntu over Ubuntu, when I did this, I found too many problems with clashes between the two systems. (There shouldn't be clashes at all, but "shouldn't" and "aren't" are two different things.)
I noticed the same thing about conflicts. I installed Lubuntu over Ubuntu and the apps would get confused. Sometimes it would use Lubuntu's file manager (forget the name), and other times it would use Nautilus - randomly. Ditto for other default apps like the text editor, calculator, etc. I didn't help things by experimenting with different desktops in my live environment - things ended up getting corrupted and I lacked the patience or coding skills to get things running proper again...

So I nuked the whole thing. I backed up my personal files and then formatted the hard drive and did a clean install of 18.04 (straight Ubuntu). I did the minimal install to lose some of the bloat. I was expecting it to run slowly (infamous Gnome memory hunger), but it actually runs quicker than 16.04. Bluetooth appears to be better supported (my devices at least). With a good bit of fiddling and tweaking, I was able to get everything comfortably set up. It runs quite peppy on my limited system. (*fingers crossed*)   

:)

---

### Post by Paddy Landau on 2018-05-17
> **galacticstone said:**
> … I nuked the whole thing…
Thanks for that. I'm going to install Lubuntu 18.04 in a month or so. I shan't try Ubuntu until I get a better computer, because I need more than the minimal installation, but it's good to know that Ubuntu 18.04 runs well. Unity was a major RAM hog —in my tests, running Ubuntu 16.04 with the default Unity used 1Gb more than Lubuntu 16.04. That's crazy.

---

