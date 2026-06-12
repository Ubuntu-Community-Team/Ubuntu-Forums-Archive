---
title: "Clock displaying wrong time after boot"
date: 2008-02-26
forum: General Help
---

### Post by joehte on 2008-02-26
Hi,

I have a problem that is driving me insane. Every time I reboot the machine, Ubuntu shows that time is +2 hours into the future. My localtime is +2 hours from UTC time, so it seems as if it doesn't understand my BIOS time displays my local time and not the UTC time. How can this be fixed? From the clock preferences I have disabled UTC time.

This problem started after I had obtained a larger HD and copied my Ubuntu installation from the old disk to the new disk. In the old installation the time shows right. Apparently some important setting was not copied, but I'm not expert enough in Linux / Ubuntu to know what could be wrong. I've done everything I know using the GUI and even some command-line utils, but even though I  manage to make Ubuntu understand my time after some fiddling, each time I reboot the clock shows +2 hours wrong.

What could be wrong? The BIOS time shows my localtime, but Ubuntu stubbornly shows wrong time. The timezone is correct as shown from Time & Date Settings.

---

### Post by Het Irv on 2008-02-26
Have you tried getting Ubuntu to sync time with a server.  If you don't want to do that I would suggest setting your BIOS time to UTC, since you don't spend much time there it shouldn't bother you as much.

---

### Post by joehte on 2008-02-26
Yes, synching with server is exactly like I want it to be. However I have tried with both options, out of desperation, without luck. It used to work fine with synch to server.

I wouldn't want to put the BIOS time to UTC since I do boot occasionally to Windows. It puzzles me that it used to work in my old installation. I wonder how Ubuntu determines whether the BIOS clock is in local time or UTC time and how I could change it? If I could set that, it might fix this?

---

### Post by Het Irv on 2008-02-26
I remember that I had the same problem when I dual-booted on my desktop,  I wasn't using Windows at the time, only the other people in my house.  So they had to deal with the problem because I never booted to it.  I don't know how Ubuntu reads the BIOS clock, but if you can figure it out, that would be the way to go.

---

### Post by Envirotech on 2008-02-26
I could not find the article I got it from but I did find one that had the information.

[http://www.arsgeek.com/?p=863](http://www.arsgeek.com/?p=863)

This is from that article.

    sudo cp /etc/default/rcS /etc/default/rcS.bak

    gksudo gedit /etc/default/rcS

Look for the line that says:

    UTC=yes

and change it to:

    UTC=no

Now, save the file and go to System -> Administration -> Time and Date and set your info to the correct time and date.

Lastly let’s restart the hardware clock

    sudo /etc/init.d/hwclock.sh restart

You should be at the correct time and date now.

I hope this helps :)

---

### Post by louieb on 2008-02-26
When I 1st started Dapper the clock Switching around was a annoyance this is what fixed it for me then. 

The clock switching time when alternating boots between XP and Linux is a pain. To keep Linux from using UTC Right click on the clock > Preferences > uncheck the UTC box. Or if you don't have the clock edit **/etc/default/rcS** and change the line UTC=yes to UTC=no
If you need to change the timezone this can be done by runing sudo tzselect.
[Nuts Ubuntu FAQ]("http://louboldt.com/ilinuxmisc.htm")

opps I just echoed envirotect.

---

### Post by joehte on 2008-02-29
Thanks everyone for the help!

I've tried every suggestion but the problem persists. Each time I boot into Linux it thinks time is +2 from what it really is. But maybe all the things I tried in the posts changed something, because at least now after some minutes the clock corrects itself to right time. It might have been doing that earlier too, would seem logical if this is because of the time synchronization feature.

I'm a bit lost here. Why is the clock wrong at boot time but corrects itself after a while? It's as if it thinks at first I have the hardware clock in UTC mode. Yet my /etc/default/rcS file has UTC=no

I wonder what else there could be that can cause this? The only thing different in my old and new installation, that I can think of, is that I use LVM on the new one. But that seems unlikely cause for this.

---

### Post by Het Irv on 2008-02-29
Just for the heck of it... try changing UTC to yes and see what happens.

---

### Post by joehte on 2008-02-29
> **Het Irv said:**
> Just for the heck of it... try changing UTC to yes and see what happens.

So far so good... I rebooted and the machine has been on, displaying the correct time for 30 minutes or more.

Strange thing though that it works like this. In my old installation it was just the other way around and that worked there. Well, let's see how it goes, I don't feel easy about this solution but at least it's working at the moment :).

---

### Post by Het Irv on 2008-02-29
Whatever works, If you are satisfied with the results mark the thread as solved and hand out thanks.

---

### Post by joehte on 2008-03-02
Since changing the line to UTC=yes I've had no problems for few days. Hopefully this thread helps someone with a similar admittedly weird situation :). Thanks everyone for the help!

---

