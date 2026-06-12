---
title: "[SOLVED] Slow Firefox scrolling"
date: 2008-06-11
forum: General Help
---

### Post by Shelbsterina on 2008-06-11
The past few days I've been having very slow scrolling in Firefox, and everything else, as well. In Firefox, I've disabled smooth scrolling and auto scrolling in preferences, but it didn't make any difference. I just installed Ubuntu Hardy last month from Windows XP, but not until recently has it started doing this. I think it may have something to do with either my Java plugins (The day after I installed Java 6 and the IcedTea plugin, I noticed the slow scrolling), or maybe something to do with Compiz or Emerald. I could be totally off, that's just my guess. I got rid of those Java plugins I installed, and still - nothing.
I had a theme created with Emerald I was using, but I read somewhere with someone having the same problem to try "metacity --replace". Well, this got rid of my theme and made the problem even worse than it was before. Also, now I can't get my theme to work in Emerald at all and "emerald --replace" does absolutely nothing now.
Firefox 3 beta 5 was originally installed on here when I got it, but it was far too slow, so I downgraded to Firefox 2. Opera seems to have this problem, as well.
Firefox itself isn't slowed down any, download speeds and page loading is the same as it's been. It's only the scrolling that's unbearably slow and jerky.

Any help is greatly appreciated.

---

### Post by todak on 2008-06-11
What particular websites is Firefox slow in scrolling? I tried going to  a friends myspace page and it was horrendously slow to load and it would barely scroll until the entire page loaded, flash garbage and all. :mad: If the page you are trying to view has a lot of flash content that loads with the page, then you will hardly be able to scroll, if at all, until the entire page loads. For that reason alone, I refuse to look at any pages on myspace.[-(

---

### Post by Shelbsterina on 2008-06-11
Haha, yeah, I know Myspace is a horrible place for any browser, I try to avoid things like that altogether. But this happens on any website I go on. My Hotmail, Google searches, and even here.

---

### Post by todak on 2008-06-11
Hmm...:-k  Try disabling visual effects altogether and see if that makes any improvement.

---

### Post by Shelbsterina on 2008-06-11
Disabled all visual effects, still having problems. Everything was working fine with my Emerald theme applied, but after Googling this problem, I learned that a lot of the time Compiz and/or Emerald are the culprits. But, as I said, everything worked fine for me. I'm leaning more toward Java, or some plugin associated with it being responsible. Could it have tweaked with something in the Firefox configuration, and left it there even though I uninstalled it?
But it's not just Firefox :(

---

### Post by todak on 2008-06-11
Try removing the icedtea plugin and ```
sudo apt-get install sun-java6-plugin
``` Then ```
sudo update-alternatives --config java
``` and  then choose the ```
/usr/lib/jvm/java-6-sun/jre/bin/java
``` selection. This will use Sun's Java 6 and it should help things. That is what I am using with Firefox and have no issues with scrolling. Let me know if it works! :)

---

### Post by Shelbsterina on 2008-06-11
I did what you suggested, reatarted Firefox, and the scrolling is still the same.

---

### Post by todak on 2008-06-11
:confused: I be stumped now. I do not know what else to try. Sorry any of my suggestions did not work. :(

---

### Post by Shelbsterina on 2008-06-11
It's alright, I know I'm not the only person who ahs had this problem. I'm sure I'll find a solution eventually. Thanks for your help, though! :)

---

### Post by darco on 2008-06-11
Whats your system specs? Is this a Lappy w/the Intel 945 chipset?

darco

---

### Post by Shelbsterina on 2008-06-11
Nope, not a laptop. Dell Dimension 2400. In system monitor, it tells me that my processor is: Intel Celeron CPU 2.60 GHz
Not sure if that was the info you were asking for, though.

---

### Post by the4thchild on 2008-06-11
This issue sounds similar to long lags and disk usage during scrolling I experienced with Firefox 3 beta 5 on Fedora 9.  It may have to do with an fsync problem that appears to have been fixed in Firefox 3 RC2.  Here are some of the relevant links:

[http://forums.fedoraforum.org/showthread.php?t=190855&highlight=firefox](http://forums.fedoraforum.org/showthread.php?t=190855&highlight=firefox)
[https://bugzilla.mozilla.org/show_bug.cgi?id=421482#c71](https://bugzilla.mozilla.org/show_bug.cgi?id=421482#c71)

and a workaround I haven't tried:
[http://ericbrake.ws/linux/workaround-for-heavy-cpu-load-in-firefox-beta5/](http://ericbrake.ws/linux/workaround-for-heavy-cpu-load-in-firefox-beta5/)

My workaround was simply to download the Fedora 3 RC2 binaries from the Mozilla website, which for me has fixed the scrolling lag.

---

### Post by Shelbsterina on 2008-06-16
In case anyone cares, I've found a solution and fixed this problem! (I figured it would be helpful for anyone else having a problem like this, and this thread can be labeled "solved")

In my first post, I said I tried to use "metacity --replace" as a fix for it, but it just got rid of my emerald theme and I wasn't able to get it back using "emerald --replace". I was able to get my theme back in Emerald by using the same command I needed in order for it to work correctly the first time I enabled it: "compiz --replace -c emerald &".

So, I had my theme back, but was still experiencing really slow performance in Firefox and any other applications I used. I opened System Monitor and saw that the XGL process was taking up half of my CPU. Now that I knew exactly what the problem was, I just had to find a way to fix it. I was afraid getting rid of or disabling the XGL would make me unable to use my custom Emerald theme, but I decided I didn't care and I just wanted my computer back to normal speed again. 

With Google, I found a way to easily disable XGL, without uninstalling it. All I needed to do was go to the "~/.config/xserver-xgl" directory, right click and choose "create document" and name it "disable". I restarted and everything was back to normal AND my theme stayed in tact just as I wanted it!

Firefox now works as beautifully as usual, and the rest of my applications run smoothly, as well. The XGL process taking up 50%+ CPU isn't listed in System Monitor anymore, either.

I just don't quite understand why the XGL thing is there and what it does exactly. I thought it had something to do with Compiz or Emerald and made my theme work, but everything is just fine without it. If it doesn't seem to do anything, why does it take up so much memory to run?

---

