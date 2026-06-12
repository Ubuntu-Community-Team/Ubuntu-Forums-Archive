---
title: "Browser Hijacking"
date: 2006-11-20
forum: General Help
---

### Post by meenfreem on 2006-11-20
Repost from the server&security section... sorry

Somewhere along the way my colleague probably picked up an adware (or virus I suppose), and now googlelink.com (actually cnomy) keeps on overriding our webbrowser (lastest firefox) when we try to accesss our homepage. And I can't seem to find anything about this...

Just tried opening the site in Epiphany and the same thing.

Any ideas?

edit: Seems that windows users have had a similar problem a little while ago with a "cnomy browser hack" which overrides certain root domains in all browsers used on a system.

---

### Post by yopnono on 2006-11-20
How did it get in to the machine? Was it install as root, user?
Have you tried to create a new profile for FX.

Open you home folder and CTRL+H to show hidden files/folders. Then rename the .mozilla folder, and make sure the FX is closed before doing this.

Then start FX and see if it's fixed. Also check processes ps -A in terminal to see if you have any (no good stuff) running

---

### Post by john_spiral on 2006-11-20
What version of firefox is this? I thought firefox on Linux was just about immune to hijacking.

johne

---

### Post by meenfreem on 2006-11-20
> **yopnono said:**
> How did it get in to the machine? Was it install as root, user?
Have you tried to create a new profile for FX.

Open you home folder and CTRL+H to show hidden files/folders. Then rename the .mozilla folder, and make sure the FX is closed before doing this.

Then start FX and see if it's fixed. Also check processes ps -A in terminal to see if you have any (no good stuff) running

I got it through the network I think. it's really weird, my computer was fine one moment, the next I had it...

Fixed... for now. After ending a process called at-spi-registyd or something like it, all the computers on the network work again :S Very very odd

---

### Post by john_spiral on 2006-11-20
It's always good practice to do a md5sum on any code you download.

---

### Post by Gaweph on 2006-11-20
how would you go about doing the md5sum? and what would it show anyways?

---

### Post by john_spiral on 2006-11-20
open up a terminal and type:

[COLOR="Indigo"][FONT="Microsoft Sans Serif"]md5sum filename[/FONT][/COLOR]

Replace [COLOR="Indigo"][FONT="Microsoft Sans Serif"]filename[/FONT][/COLOR] with the name of the program you downloaded

It will output a long string of characters. Make sure the outputted string matches the md5sum from the website that hosts the program you downloaded.

If they don't have a md5sum ask them to publish one. 

All software downloaded from a good source like sourceforge.net has available md5sums.

A md5sum is just about a 100% way of checking the authenticity of a program.

johne

---

### Post by meenfreem on 2006-11-21
Right, we're back to square one.

As far as we know, we have not downloaded or installed anything over the past few days. So we doubt it's that.

After coming in to work this morning, the system seemed fine... till my colleague turned on his computer again, so it's most likely his comp where the problem originates from. 

The whole issue gets stranger though... the pages we couldn't access yesterday, are accessable again, but other url's get hijacked! And new ones get added sometimes?! Even with his computer off now, the problem remains. We're now turning off comps to check whether we can locate the problem computer.

At first it was only the ubuntu boxes that we're affected (two desktops, one wireless laptop), and now it's also managed to spread to the windows machine!

We've gone around the router and the problem remained (plugged one comp directly into the internet connection instead of through the router (wireless LinkSys WRT54G)) so we don't think its that.

After doing on of them chkroot-something (forgot the name of it :D) it did show up a port sniffer, but since the comps were fine in the morning I'm not convinced that that is the real underlying problem. It could be ofcourse, and it should definately be removed somehow. Could it be that this port sniffer is redirecting traffic from our IP's? 

Any help is appreciated!

---

### Post by yopnono on 2006-11-21
This just don't make sense. Sorry to say but...

How on earth can you have your linux based machine infected by a win virus, and the also infect other machines?? windows and linux based.

Or have I misunderstood it.

---

### Post by yopnono on 2006-11-21
Try to use a different DNS server. Or connect the machine to an other ISP network.

---

### Post by meenfreem on 2006-11-21
yopnono, I think you understand it okay... it's mind baffling! As far as I know, and from the people I've spoken to (on freenode irc)... this is impossible! But yet, we still have it :S

My colleagues laptop had no issues at home, so another ISP surely works. We're about to contact our ISP here to check whether they know something we don't.

---

