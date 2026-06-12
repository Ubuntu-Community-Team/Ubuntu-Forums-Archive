---
title: "Can anyone decipher a bootchart?"
date: 2006-11-23
forum: General Help
---

### Post by voodoonirvana on 2006-11-23
I have been trying to speed up my boot time because it normally takes anywhere from 5 to 10 minutes just to boot. I tweaked a few things and cut it down maybe a minute or two but nothing significant. Somebody suggested installing Bootchart to see what was making it take so long. I took a screenshot of the part that looks inmporant so someone here could help me decipher it. Cause it's way over my head.
[http://i57.photobucket.com/albums/g238/voodoonirvana/Screenshot-3.png](http://i57.photobucket.com/albums/g238/voodoonirvana/Screenshot-3.png)

---

### Post by voodoonirvana on 2006-11-23
bump

---

### Post by taurus on 2006-11-23
Maybe you should look for your answer here...

[http://www.bootchart.org/](http://www.bootchart.org/)

---

### Post by voodoonirvana on 2006-11-23
> **taurus said:**
> Maybe you should look for your answer here...

[http://www.bootchart.org/](http://www.bootchart.org/)

Believe me, I looked all over that site. About half of it was jibber jabber to me and it gives no way to show you how the chart works or anything like that.

---

### Post by taurus on 2006-11-23
Then I guess you just have to wait for somebody who uses it and knows how to interpret it.

---

### Post by voodoonirvana on 2006-11-23
bump

---

### Post by glotz on 2006-11-23
I wondered about this too. It's pretty queer that there's no advice on this subject on the homepage! Makes the utility kinda useless.

---

### Post by RAOF on 2006-11-23
As far as I'm aware, the top two charts are CPU usage and I/O usage over time, but that's pretty obvious.

The bars beneath are what processes are running at any given time, with the dotted lines denoting "what spawned what".

So that's **not** actually the interesting part of the boot chart.  Everything there either needs to be running the whole time, or starts up, does it's thing, and shuts down pretty quickly.

Five to ten minutes sounds outrageously long, so there'll almost certainly be something in the bootchart that obviously takes a very long time to do it's thing.  Also, what sort of system specs is this running on?

---

### Post by voodoonirvana on 2006-11-23
> **RAOF said:**
> As far as I'm aware, the top two charts are CPU usage and I/O usage over time, but that's pretty obvious.

The bars beneath are what processes are running at any given time, with the dotted lines denoting "what spawned what".

So that's **not** actually the interesting part of the boot chart.  Everything there either needs to be running the whole time, or starts up, does it's thing, and shuts down pretty quickly.

Five to ten minutes sounds outrageously long, so there'll almost certainly be something in the bootchart that obviously takes a very long time to do it's thing.  Also, what sort of system specs is this running on?

I'm running dapper on a Gateway SOLO 5350 laptop, 20 GB HD, 256 MB of RAM, 1.6 megahertz processor.

---

### Post by RAOF on 2006-11-23
Well, that's pretty low-end.  Still, 5-10 minutes is much longer than I'd expect.  Why don't you just post the whole bootchart .png somewhere, and we can look at it?

---

### Post by Peepsalot on 2006-11-23
It would help if you posted the entire file.  From your screenshot you can't see the whole timeline, and can't see the programs on the lower portion.  The file is a png, so you should be able to upload it to the forums.

One thing you can do is look for points where neither the CPU or the disk is being utlilized vary much or at all, and try to find out why.  This means your cimputer is sitting inactive for some reason, which should be remedied.

What are your hardware specs like, and what is your OS filesystem.  I have noticed that users with ReiserFS tend to have very long boot times.

---

### Post by glotz on 2006-11-23
I used to boot Dapper on a Pentium 3 450@527MHz with whopping 192 megs of ram and an ancient harddisk in just over 1 minute...

---

### Post by voodoonirvana on 2006-11-23
> **RAOF said:**
> Well, that's pretty low-end.  Still, 5-10 minutes is much longer than I'd expect.  Why don't you just post the whole bootchart .png somewhere, and we can look at it?

[http://i57.photobucket.com/albums/g238/voodoonirvana/dapper-20061123-1.png](http://i57.photobucket.com/albums/g238/voodoonirvana/dapper-20061123-1.png)


That might be too small, I could find another image host if needed.

---

### Post by RAOF on 2006-11-23
Yup, too small! :)

---

### Post by Peepsalot on 2006-11-23
> **voodoonirvana said:**
> [http://i57.photobucket.com/albums/g238/voodoonirvana/dapper-20061123-1.png](http://i57.photobucket.com/albums/g238/voodoonirvana/dapper-20061123-1.png)


That might be too small, I could find another image host if needed.

The forums accept PNGs up to 976.6 KB, just click "Manage Attachments" to upload a file.

Also, I recommend [http://imageshack.us](http://imageshack.us) for a nice image hosting site alternative to photobucket.

---

### Post by voodoonirvana on 2006-11-23
Did it work?

---

### Post by RAOF on 2006-11-24
That worked, but it looks like your boot is finished in under 60 seconds :).  Maybe I can't read bootcharts that well :).

---

### Post by Peepsalot on 2006-11-24
Hmm, look like boothcart cuts off at 60seconds, that's unfortunate.  I wonder if there is some setting to allow it to save more.  I think bootchart stores as an svg also.  Do you see that file, and can you try posting that also.  Maybe that one won't be cut off.

A couple things:
Looks like you are running clam antivirus.  Personally I think it's simply unnecessary on a Liinux box.  This would save you some time to not load this if you are comfortable with that.   Another tweak is that the default /etc/network/interfaces file has settings for network devices that do not exist or are not being used.  Removing the unused devices from this file saves a little time in your network setup boot time.

---

### Post by Peepsalot on 2006-11-24
Oh, I guess maybe your boot time really is 60 seconds.  You know, every 30 boot cycles an ext filesystem will do a thorough sytem check during bootup.  This can easily take 5-10 minutes, so maybe you experienced this one time?

There are a few tips I learned in this thread: [http://www.ubuntuforums.org/showthread.php?t=274742](http://www.ubuntuforums.org/showthread.php?t=274742)
Like this:
> Specifically, at the grub loading menu, hit esc to bring up the list of bootable kernels, and select the one that you normally boot. Then hit e, select the kernel boot options line (usually line 2), hit e again, and go to the end of the line and type "profile". Then hit enter to save, and b to boot. This will profile your boot process so that the physical location of the boot files on the hard disk are optimized. This will take some time...that's normal. Once this is done you'll get to your login prompt, and you can then reboot normally. You should notice a significant increase in boot speed for this reboot, and all others following it. You should repeat the profile process following any reboot that is caused by a dist-upgrade, but in all other instances you can leave it alone.

---

### Post by voodoonirvana on 2006-11-24
No, my boot time is definitely not 60 seconds. The chart just cuts off there I guess. I don't see any other files in the bootchart folder.:-k 
I just removed clam antivirus.

And how would I go about doing that tweak you mentioned for the /etc/network/interfaces?

---

