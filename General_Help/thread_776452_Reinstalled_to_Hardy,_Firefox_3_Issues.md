---
title: "Reinstalled to Hardy, Firefox 3 Issues"
date: 2008-04-30
forum: General Help
---

### Post by noremac on 2008-04-30
In the past couple days, I reinstalled Ubuntu from 7.10 to 8.04. Everything went fairly well. Outside of Firefox. Before I left 7.10, I would watch my conky and see that the Firefox 3 beta was getting up to 10-11% usage of my RAM. Rarely above that. Having a 1GB of RAM, that would mean around 100 or so MB used. 

Now that I am running it on Hardy, I am seeing right now with two tabs open and FF was just restarted, I am at 15%. Before I restarted FF it was around 20% with 5 tabs open. Thats a bit bad compared to what I was getting. The exact same usage and the Mem usage has skyrocketted. Last night, I caught it using 30%. 

Along with that, I am having issues with Flash. Just a few minutes ago, it seemed as though Flash wasn't even installed. No site using flash would work properly. I restarted Firefox and it began to perform correctly. 

What would ya'll suggest I do? Reinstall Firefox3? Or downgrade?

Thanks,
Cameron

---

### Post by Caraibes on 2008-04-30
There's one easy thing I would suggest: uninstall Adobe Flash plugin, and use SWFDEC instead (or Gnash)... It seems to help a lot for stability in FF3...

---

### Post by noremac on 2008-05-01
I have not encountered the problem since then in regards to Flash. But my RAM usage of FF3 is still rather ridiculous. 18% with 3 tabs open. Never EVER got that high.

I have not tried reinstalling FF3 yet. I should probably try that before anything else, yes?

---

### Post by vikasmk on 2008-05-01
I installed hardy yesterday, it seems faster than gutsy, but my system crashes whenever i'm using firefox. Maybe it's a bug or something..

---

### Post by noremac on 2008-05-01
I have had it freeze up a few times, go dark like they do, but comes back after a few seconds. FF2 did this as well in my previous installation.

I may end up downgrading if no one has any recommendations.

-C

---

### Post by GoranI on 2008-05-01
I also had problems with FF3 beta5. I removed it complitely and installed Firefox 2.0.0.14 which is stable version of FF and all extensions, themes working properly. i wonder why FF3b5 is included in Hardy, it is BETA version and still unsuported by community. 
I suggest you to do the same like me :)

---

### Post by warp99 on 2008-05-01
> **noremac said:**
> I have had it freeze up a few times, go dark like they do, but comes back after a few seconds. FF2 did this as well in my previous installation.

I may end up downgrading if no one has any recommendations.

-C
Reinstalling Firefox would be a waste of time since all of you settings are kept locally. Try removing you local ~/.mozilla directory so Firefox can create a new one since there may be some corruption, but first backup any bookmarks you need. You will have to reinstall any extensions and redo any custom settings that you may have.

---

### Post by Caraibes on 2008-05-01
Instead of downgrading to FF", you guys should simply remove the "flash-nonfree" plugin and install swfdec. This will create a real change. Try that !

---

### Post by noremac on 2008-05-02
> **warp99 said:**
> Reinstalling Firefox would be a waste of time since all of you settings are kept locally. Try removing you local ~/.mozilla directory so Firefox can create a new one since there may be some corruption, but first backup any bookmarks you need. You will have to reinstall any extensions and redo any custom settings that you may have.

Went ahead and gave that a shot lastnight. 4 tabs open now and were over 220mb. Still way too high. Any other recommendations?

-C

---

### Post by Caraibes on 2008-05-02
> **noremac said:**
> Any other recommendations?
Use swfdec instead of Adobe Flash !!! (read my previous posts...)

---

### Post by noremac on 2008-05-02
> **Caraibes said:**
> Use swfdec instead of Adobe Flash !!! (read my previous posts...)

Yep, I did that earlier this morning and outside of having to click "play" on every flash video before it loads, FF3 is still using just as much memory. (I havent tried messing with any settings, but I assume that I can get rid of having to click the big play logo thing before loading a youtube video)

-C

---

### Post by Kevbert on 2008-05-02
> **vikasmk said:**
> I installed hardy yesterday, it seems faster than gutsy, but my system crashes whenever i'm using firefox. Maybe it's a bug or something..

It may be this one: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996")

---

### Post by noremac on 2008-05-06
Still having these issues with Firefox. Using a lot of memory. 

Also, I use Gmail. Say I can scroll around in the inbox.. For some reason, FF is really slow to scroll through these emails or whatever. It lags behind my physical scrolling of the mouse scroller quite a bit. Seems to be the only site that does that...Any idea? I have reinstalled over and over. Deleted my ./.mozilla folder many times. Memory usage still sits at 18%, or 180MB with one site open...

-C

---

