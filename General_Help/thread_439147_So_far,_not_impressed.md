---
title: "So far, not impressed"
date: 2007-05-10
forum: General Help
---

### Post by fairman4 on 2007-05-10
I recently downloaded and installed Wubi to see what life was like without Windows. For some time I've been wanting to get away from Windows, and maybe switch to a Mac. However, I thought with all the hype about Ubuntu, I'd give it a shot.

I had no problem with installation, which seemed to go without a hitch. I liked the fact that with Wubi you don't have to create a partition. After it finally installed, it took FOREVER for it to boot up. But, perhaps this is just a first time thing to settle in. Subsequent rebootings have definitely been shorter, but not nearly as fast as Windows XP.

The biggest problem is that is just runs sloooow. Firefox opened fairly quickly, but Open Office took at least 5 minutes to start. Compared to Windows XP, it just seems sluggish. There were also errors with the updater, which also took forever to tell me there was an error.

If I had a question it would be this: Has anyone else had a similar experience? Does Ubuntu run slower because it doesn't have its own partition and because Wubi is beta?

I have a Dell laptop with a 1.2 G processor and 320MB of memory.

---

### Post by kenflipkick on 2007-05-10
There are ways of speeding up application launch in Ubuntu elsewhere in these forums, my apps used to take a while to load until I changed some settings.

Also, the less RAM you have, the slower it takes.

---

### Post by Cresho on 2007-05-10
No problems here and my pc is ancient!

---

### Post by 65536 on 2007-05-10
Just install it the "Ubuntu way".
Nothing takes 5 mins to start.

---

### Post by ticopelp on 2007-05-10
I don't know what Wubi is, but my copy of Ubuntu does everything significantly faster than my Windows install. And my XP install is pretty fresh -- only a few months old. I'm actually kind of appalled at how long XP takes to start up and shut down now, compared to Ubuntu. 

The RAM shouldn't be too much of an isssue, as far as I know; even working my machine as hard as I can I'm hard pressed to use up 320 megs.

---

### Post by Tomosaur on 2007-05-10
It definately should NOT be anywhere near that slow. I too would recommend you ditch the Wubi method if it's causing poor performance. Linux just isn't supposed to be run like that (Wubi installs Linux to a file in your normal Windows installation). Wubi is also still beta, which mean you shouldn't expect it to be perfect just yet.

While I definately applaud the Wubi team for what they're doing, I simply wouldn't recommend it as a suitable way to get Ubuntu just yet.

I would recommend absolutely that you download the normal Ubuntu and install it properly. If you don't want to mess about with partitions etc, then I'm afraid you my be out of luck, aside from virtualisation from within Windows. For your system specs, your low performance is definately abnormal, and I would suggest that wubi is the cause.

---

### Post by ago on 2007-05-10
Wubi disk access is supposed to be slightly slower but not much slower. If it is very sluggish, most likely the reason is that we did not include the right HD/controller driver. You would start noticing that from the installer which should take way above 30 minutes. If the installation was normal (10-20min) then it's another reason. If your HD is very fragmented, it does not help...

---

### Post by JCakeC on 2007-05-10
fairman4,

Ubunto on Wubi will be slow first boot because it installs everything... then, if you have missing drivers some things will go a bit sow. But in my experience, Ubunto loads way faster than XP, and I have them loaded with at least 10 different servers (Mysql, Apache, JBox, Websphere, DB2, and a few more). so at the end, YES linux will be faster them XP. Mmmm... maybe on fresh installs Ubunto is slower.... I'll test it someday.

---

### Post by ago on 2007-05-10
> **fairman4 said:**
> After it finally installed, it took FOREVER for it to boot up. But, perhaps this is just a first time thing to settle in.

The first time you reboot Ubuntu is actually installed. So it is normal that it takes some time. Generally 10-30 minutes.

---

### Post by RTrev on 2007-05-11
> **fairman4 said:**
> I recently downloaded and installed Wubi to see what life was like without Windows. For some time I've been wanting to get away from Windows, and maybe switch to a Mac. However, I thought with all the hype about Ubuntu, I'd give it a shot.

I had no problem with installation, which seemed to go without a hitch. I liked the fact that with Wubi you don't have to create a partition. After it finally installed, it took FOREVER for it to boot up. But, perhaps this is just a first time thing to settle in. Subsequent rebootings have definitely been shorter, but not nearly as fast as Windows XP.

The biggest problem is that is just runs sloooow. Firefox opened fairly quickly, but Open Office took at least 5 minutes to start. Compared to Windows XP, it just seems sluggish. There were also errors with the updater, which also took forever to tell me there was an error.

If I had a question it would be this: Has anyone else had a similar experience? Does Ubuntu run slower because it doesn't have its own partition and because Wubi is beta?

I have a Dell laptop with a 1.2 G processor and 320MB of memory.

It may be the Wubi, whatever that is.  :)   My Feisty boots in 30 seconds, Firefox takes 1-2 seconds to open, OpenOffice takes 4 seconds, after a reboot.  If I've loaded it previously then it takes 1 second.  And that is the worst!  Most things happen before I can remove my finger from the mouse button.  I'll have to Google this "Wubi", but something is screwed up.  There's nothing that should be taking *minutes* to happen.

Bob

---

### Post by Dark Legacy on 2007-05-11
You guys are making me so damn jealous.. :frown: 

Still waiting on that RAID-0 support..

---

### Post by ago on 2007-05-11
> **Dark Legacy said:**
> You guys are making me so damn jealous.. :frown: 

Still waiting on that RAID-0 support..

Did you try Minefield 0.6? That should include it (thanks to Spegelius)  [http://ubuntuforums.org/showthread.php?t=439597](http://ubuntuforums.org/showthread.php?t=439597)

---

### Post by RTrev on 2007-05-11
> **Dark Legacy said:**
> You guys are making me so damn jealous.. :frown: 

Still waiting on that RAID-0 support..

Why jealous?  Sounds like you're having problems with a slow drive?

What kind of numbers are you seeing with a test like this:

```

bob@bob-desktop:~$ sudo hdparm -t -T /dev/sda

/dev/sda:
 Timing cached reads:   1178 MB in  2.00 seconds = 588.75 MB/sec
 Timing buffered disk reads:  254 MB in  3.02 seconds =  84.06 MB/sec
bob@bob-desktop:~$ 

```

I don't really have any sense of whether those numbers are good or bad or mediocre.  I'd be interesting in hearing what some others are seeing, if anyone feels like sharing.

Oh, this is a WD SATA Raptor 10,000 RPM.  It's only 74G (kind of an odd number) but my local data storage needs are minimal and I'm only using 9G of it.  I too would like to try RAID at some point.  I had always thought that was purely between the BIOS and the drives, and that the OS just saw a big single disk drive from its perspective.  Not so, eh?

Regards,
Bob

---

### Post by stuffradio on 2007-05-11
My Ubuntu is fairly fast on my P3 750 MHz computer :)

I know it's not the problem but 512 MB RAM is always better than 320

---

