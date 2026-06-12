---
title: "Firefox 30 cpu 300% on vimeo"
date: 2014-06-17
forum: General Help
---

### Post by monkeybrain20122 on 2014-06-17
Hi,

I am just wondering if anyone can reproduce this. In Firefox 30 go to [https://vimeo.com](https://vimeo.com), then go to staff picks, browse a few videos, then pick one, and switch to the video's own page by clicking the tag on the left upper corner of the video's box, do this back and forth a few times with a few videos and check the cpu usage for Firefox. In my case it goes up to 300% after a few trials like that and it stays that way for a long time even when the tab is closed.

I tested with a fresh profile and it is the same. 

However, this doesn't happen if I download Firefox from Mozilla and use the same profile (tested on both Firefox 30 and 31rc) So I think this may be a Ubuntu bug.

My system is Ubuntu 14.04 64 bit, intel core i5, gpu is ironlake mobile.

---

### Post by claracc on 2014-06-18
HP compaq 6720s laptop, 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c), ubuntu 12.04 fully updated and firefox 30.0

Firefox with 3 tabs opened, 2 in vimeo staff picks, playing frankie video arrives to 100 % CPU, trying to play tsume video arrives to 160 % and then freezes, trying to play other videos as magpie doesn't reach 100% CPU. I think problem is that certain videos in this site are very much CPU consuming, apart my graphics card is not very good. Also, I can see a lot of firefox processes in htop.

Please, see attached image.

---

### Post by monkeybrain20122 on 2014-06-18
> **claracc said:**
>  I think problem is that certain videos in this site are very much CPU consuming.

They do consume a bit more cpu, but not that much. I didn't experience it in F29, and as I said it doesn't happen with FF30 and FF31-beta downloaded from Mozilla.

---

### Post by monkeybrain20122 on 2014-06-21
In Firefox 31-beta it is about 80% when video is playing and as soon as video stops playing it drops back to < 10% as oppose to 300% even when video is not playing. So there is definitely something wrong with Firefox 30. I used the same profile for the tests.

---

### Post by Frogs Hair on 2014-06-21
I show from 27 to 30 % with single tab.

---

### Post by monkeybrain20122 on 2014-06-21
> **Frogs Hair said:**
> I show from 27 to 30 % with single tab.

Did you switch a few videos, browse a bit and so on (see my first post). It usually doesn't happen immediately. I have also tested with a fresh profile (no addons, only one tab) Same thing.

---

### Post by sammiev on 2014-06-21
> **Frogs Hair said:**
> I show from 27 to 30 % with single tab.

I start at 80% for 30 seconds or less and drop down to below 50% quickly. Even after using it and switching from one to another.

---

### Post by monkeybrain20122 on 2014-06-21
> **sammiev said:**
> I start at 80% for 30 seconds or less and drop down to below 50% quickly. Even after using it and switching from one to another.

I found that as long as I browse and watch on the page "Staff Picks" it is ok. But if I switch to the video's own page then cpu shoots up without even playing the video. See the screenshots. The first one = OK, second = high cpu.

I check this on Fedora 20 with gnome shell and the result is the same, so it has nothing to do with Ubuntu's packaging or Unity. Again it happens only on FF30, FF31 beta and FF32 nighty doesn't have this issue.

---

### Post by monkeybrain20122 on 2014-07-23
Upgraded to FF 31 and it works normally again. :)

---

