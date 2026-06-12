---
title: "USB freezes when using Firefox"
date: 2007-01-18
forum: General Help
---

### Post by RobMBaker on 2007-01-18
OK, I've trawled the forums and had no joy re this topic. The problem doesn't appear to show up (that I can find) elsewhere in the forums.

A few weeks/months ago, I upgraded from Dapper to Edgy; and noticed this bug start:
Whenever I'm using Firefox (2.0); after a while, my USB mouse freezes and I have to use my touchpad (the height of tedium). Sometimes it takes a good half an hour or more, sometimes a few minutes before it freezes. I did check once or twice to see if it was just the mouse; but the whole USB goes down. The only way I can get it to work again is to reboot - restarting the USB (I did find something in the forums, but it didn't help) didn't even work.

I never had this problem with Firefox 1.5 in Dapper ... EVER ... which makes me think that Firefox is at fault (besides the fact that it only happens when I'm using FF).

My Firefox 2.0 is just as is on install, but with Adblock, DictionarySearch and I think that's it as extensions (I'm in Windows atm, to avoid the inconvenience of the usb freezing while I type this post).

Firstly, has anyone else had similar problems, or can they narrow down the problem?
Secondly, does anyone know how to fix this? Currently, I'm just browsing in short bursts (maybe 10mins at once) and hoping it doesn't freeze the USB while I'm in FF.

Thanks.

---

### Post by LexAevum on 2007-01-21
I've been having a similar problem only I havn't noticed it being connected to FF. My usb mouse will freeze (with no regular timing) after I wake up from a screen blank.
I can get mine to work again by un-plugging the mouse and plugging it back in. It only shuts down the one device though.

Oddly enough this hasn't happened since I put my mouse on an external usb hub. Though it might just be taking a break because it's only been 2 days.

---

### Post by RobMBaker on 2007-01-21
Yeah, no; this is a different issue. It crashes the whole USB - although I'm not sure if it crashes every hub every time. It certainly crashes the hub that my mouse is on.
Therefore, unplugging and re-plugging doesn't help at all.

LexAevum, I believe I found a more suitable thread for your problem; but sorry, I can't remember where it was/what it's called :(

---

### Post by johnbrown on 2007-01-22
6.10, a recent installation on my machine, is freezing during use of FireFox, and tar, and I'm too impatient to find out when else it freezes, but it has occurred at least half a dozen times since I started using it a few days ago. Was this a problem with 6.06? I'm running a gig of memory and 13gigs of swap so I don't think that is a problem. This is the absolute FIRST time Linux has ever frozen my computer. What kind of extraneous programming is going on with the Ubuntu software package to cause mouse and screen freezes? My only relief is to hit the reset button and reboot.
Any suggestions other than reverting to SuSE-10?

---

### Post by ubuntu1 on 2007-01-23
Same thing here, if I use the synaptics pad on my laptop then there is no problem. Plug in my USN mouse and freezing and juttering takes place.

---

### Post by RobMBaker on 2007-01-24
ubuntu1: does that only happen when you're using Firefox (2.0) or any time using Ubuntu?

---

### Post by ubuntu1 on 2007-01-25
It seems to be related to Firefox 2.

---

### Post by RobMBaker on 2007-01-28
Hmm ... still, no-one else (except ubuntu1) seems to have or know how to solve this one eh?

---

### Post by RobMBaker on 2007-01-28
I just thought I should add this bit of info too:

It seems that my mouse usually freezes (with the whole USB) when I'm doing something particularly intensive, like loading a video or flash object; sometimes even a pdf. I say "usually" because that's usually what kills it, after a nice long freeze-free browsing period; but sometimes it'll just die anyway, when I'm just reading a simple page, on Wikipedia say.

I thought about whether plugins or extensions are responsible; but I haven't added any since Dapper, when it all worked fine. That said, it could be the combination of any one of my plugins/extensions with the new Firefox. The only non-standard plugins I have (as in, not pre-installed) are FlashPlayer 9, Mplayer-plugin and that's it. As for extensions, I have Adblock 0.5.3.043, DictionarySearch 2.0 and UnPlug 1.5.4; altho UnPlug has been added since the trouble started, so I doubt it's the source of the problem.

---

### Post by RobMBaker on 2007-02-03
This can be quite an annoying problem ... so 'bump'

---

### Post by RobMBaker on 2007-05-02
I've found a work-around. Booting with noapic seems to solve it ... although I'm not too happy with this solution, as the problem w/ firefox is still in there, just doesn't affect me anymore.

---

### Post by RobMBaker on 2007-06-10
I've just realised that it probably isn't Firefox that's the problem - it just accentuates the problem. But using the "noapic" boot option does solve the issue.
I know this because my USB did freeze again the other day, after I had updated my kernel (I'd forgotten to add the noapic option to the auto-generation section of my menu.lst file) - then I added noapic again and it was all good!

Hope this helps anyone who had the same issue. It really annoyed me when I couldn't find an answer.

---

