---
title: "Can't load X.. I screwed up my xorg.conf file"
date: 2007-07-07
forum: General Help
---

### Post by Kevix on 2007-07-07
Hi all. I've installed feisty on a dual boot with XP. I've d/l the nvidia driver and enabled it so I could change my resolution to 1152x864, which I use on XP. After doing this, the display is not aligned right. It's not filling the screen of my 19" CRT Samsung monitor. The left side is aligned fine, but the right side display ends about 1 3/4" from the edge, giving me a big black space on the right. The top and bottoms are also coming up about 3/4" too short. I ran xvidtune and while it seemed to be exactly what I was looking for, when I make adjustments and hit test or apply I get an error saying I requested a mode-line that is not possible or not supported by my hardware config. Again, the display is perfect on XP at the exact same resolution. My monitor doesn't have an autofill/autocenter option. I could use the front buttons of the monitor to adjust it, but then I'd have to do it every time I switch OS, and there is no happy medium b/c the difference between the two is just too great. Thanks in advance.

---

### Post by letkemanp on 2007-07-08
This is a very common problem with NVIDIA drivers. Many people have this problem. I suggest you take a look at [http://www.nvnews.net/vbulletin/](http://www.nvnews.net/vbulletin/) and search for Linux and black bar. 

If you are still able to boot into WinXP I suggest you download Phoenix EDID Designer 1.3 from [http://www.tucows.com/preview/329441](http://www.tucows.com/preview/329441), extract the EDIDs (there may be more than one). Once you have the EDID files you can use tell xserver to use that EDID by modifying the xorg.conf file.  This is how I fix my resolution after a lot of trail and error.

You can find out more about Extended display identification data (EDID) here [http://en.wikipedia.org/wiki/EDID](http://en.wikipedia.org/wiki/EDID). 

Generally speaking EDID files are less 1 KB

---

### Post by Kevix on 2007-07-08
Thanks. I'll check it out and report back if I get it right.

---

### Post by HermanAB on 2007-07-08
Yup, it helps if your LCD display has an 'Auto Configure' button.  I just press that: Click, bzzzrrrttt, done.  

Since I discovered the auto feature I always insist on it when I buy a LCD panel.

---

### Post by Uncle Spellbinder on 2007-07-15
I started a thread regarding [**1440x900 resolution**](http://ubuntuforums.org/showthread.php?t=497613). Finally got an option for that. But now I have the 'black bar/display not aligned" problem.

I have an intel embedded card and I get a large black bar on the *left* of the monitor screen. With 1440x900 at 60 Hz, I get the black bar on the left.  Switching to 75 Hz and back to 60 Hz, the bar is gone and the screen displays 1440x900 just fine. I have to do this each time I boot Feisty.  Annoying as heck. My monitor's Auto Adjust feature does not help with this issue. Any ideas?

---

### Post by Uncle Spellbinder on 2007-07-15
Anyone?

---

### Post by dagnabit dang doohickey on 2007-07-15
There's some info on this page that might be helpful: [How to adjust position of your screen]("http://doc.gwos.org/index.php/ChangeResolution#How_to_adjust_position_of_your_screen.3F")

---

### Post by Uncle Spellbinder on 2007-07-15
> **dagnabit dang doohickey said:**
> There's some info on this page that might be helpful: [How to adjust position of your screen]("http://doc.gwos.org/index.php/ChangeResolution#How_to_adjust_position_of_your_screen.3F")

Quite a bit of info there.  Links to other info that might be helpful as well.  Thanks.

---

### Post by nwadams on 2007-07-15
don't most monitors have a manual screen position changer...maybe just the old crt ones like i have...stupid old technology

---

### Post by Auax on 2007-07-16
What happened here?!! This thread has my thread's title but it's someone else's post!

---

### Post by bodhi.zazen on 2007-07-16
> **Auax said:**
> What happened here?!! This thread has my thread's title but it's someone else's post!

You started multiple threads and I tried to merge them. Sorry if I made a mistake.

---

