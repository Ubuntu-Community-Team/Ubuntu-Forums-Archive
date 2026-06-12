---
title: "Firefox resizing is odd (and other minor annoyances)"
date: 2005-04-19
forum: General Help
---

### Post by ming0 on 2005-04-19
For some reason, when I try to resize firefox (by grabbing the tab at the lower right), it is really jerky and won't really do what I want it to (sort of jerky and seems to want to keep an aspect ratio--very unruly). Anyone else experience this?

I have some extensions:

all-in-one Gestures
tabbrowser
editcss
web developer
foxytunes
bookmark sync.

Other annoyances are definitely extension related, but I don't think the resizing deal is (but maybe someone else thinks otherwise?).

---

### Post by Vache on 2005-04-19
While I do not find it to be an annoyance, Firefox reacts in the same manner for me when I resize. I think this behavior can be changed by typing 'about:config' in the location bar, then editing ```
nglayout.initialpaint.delay
``` and ```
content.notify.interval
```

For more info regarding about:config, check out [http://www.linuxjournal.com/article/8004](http://www.linuxjournal.com/article/8004)

---

### Post by TristanMike on 2005-09-20
Well, it's been a while since any posts on this thread, so when I saw it, I yelled "yippy skippy, my problem solved" However, no good unfortunately. And the only Extension I have is the "Media Player Connectivity"

So I've done some searching on the forums and via Google, to the best of my abiltiy and I can't seem to find any thing to help me.

To elaborate the problem at hand, when I click on resize at the bottom right of the screen, and I move it, it gets all jerky. It could move ok, but it could also reverse my movement. That's to say if I moved it to make it bigger by 2", it will shrink by 2", up can become down, and then revert back, then revert again. Left and right, same thing. This all happens very quickly and very difficult to maintain a proper size of window. Maybe it doesn't respond at all.

Furthermore, this only seems to happen when I move outside of the window boarder area. This unfortuantly forces me to move extremely slow to try and resize, rediculously slow even. And that only works 90% of the time.

And if that doesn't take the icing on the cake, sometimes, I even loose the resize cursor, and I either get my arrow cursor back or nothing at all, but no! it's still continues to resize. and what's my prize. "Well TristanMike, you get the grand prize of magically closing ALL of your windows and making you start Firefox again!"

So as you can see, it is quite annoying, any help on resolving this would be warmly welcomed with open arms and a cup of tea! :)

---

### Post by SilentCacophony on 2005-09-20
Mine is a bit jerky on resizing.

I chalked it up to poor wm performance by metacity, though I'm not sure. I know it didn't do that when I had openbox installed without gnome.

---

### Post by TristanMike on 2005-09-20
[QUOTE=SilentCacophony]Mine is a bit jerky on resizing.

I chalked it up to poor wm performance by metacity, though I'm not sure. I know it didn't do that when I had openbox installed without gnome.[/QUOTE]It doesn't affect ANY of my other windows though. I'm no genius, but that begs the question why just firefox? and I'd think that since Metacity is installed by default, there would a much higher user question base then just this thread(that I could find).

---

### Post by TristanMike on 2005-09-21
Wow, did this ever fall fast.....To add a little more information to this quandery, when I resize a window in 1 direction only, the problem doesn't occur. That is to say, if I resize the window from the top, it's ok, the left *or* right alone, ok, and the bottom, same thing. The problem is only on the firefox window and only when I use the "corner resize"

can anyone please help?

---

### Post by asgard_command on 2008-01-27
I just found this thread googling for the same issue. Has this problem really not been solved yet after all this time. It's driving me mad.

---

### Post by johnthuss on 2008-03-15
There is a firefox bug filed for this.  Please go and VOTE for it to get fixed!

[https://bugzilla.mozilla.org/show_bug.cgi?id=189435](https://bugzilla.mozilla.org/show_bug.cgi?id=189435)

---

