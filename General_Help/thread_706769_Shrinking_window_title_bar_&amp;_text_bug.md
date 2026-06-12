---
title: "Shrinking window title bar &amp; text bug?"
date: 2008-02-24
forum: General Help
---

### Post by attercop on 2008-02-24
Using Nvidia restricted driver and 'Extra' for Visual Effects on Gutsy. Get the usual title bar changing colour bug but that's not the one that bothers me. I'm getting completely intermittent shrinking window bars and text that doesn't go away until next login. Here are a couple of screenshots.

[http://i14.photobucket.com/albums/a331/xxvm/Screenshot-1.png]("http://i14.photobucket.com/albums/a331/xxvm/Screenshot-1.png")
[http://i14.photobucket.com/albums/a331/xxvm/Screenshot.png]("http://i14.photobucket.com/albums/a331/xxvm/Screenshot.png")

As you can see. The text is tiny and unreadable, and yet the setting in System > Preferences > Appearance > Fonts > Window title font is 10 like it should be. Is there any workaround for this?

---

### Post by boombox1387 on 2008-02-24
I can confirm that I had this problem when I ran Gutsy on my family's Dell from a Live CD.  I ended up installing Gutsy on my own machine (with ATI graphics... does that matter?) and never ran into this bug.

Anyway, I was wondering if you'd tried [this thread]("http://ubuntuforums.org/showthread.php?t=599192").

I'll keep looking because I'm curious too.

---

### Post by boombox1387 on 2008-02-24
Actually, I found a very similar bug posted on Launchpad.  It looks like desktop effects occasionally do weird things with nvidia graphics.  This solution (if it actually is a solution to your problem in the first place)  involves editing your xorg.conf, so do it carefully:

[https://answers.launchpad.net/ubuntu/+question/5317]("https://answers.launchpad.net/ubuntu/+question/5317")

---

### Post by attercop on 2008-02-25
Thanks for the reply. I'm testing out the 'compiz --version' in startup items tip from the first thread. So far so good..

---

### Post by attercop on 2008-02-29
Unfortunately i have to report that it has just happened again. Possibly due to some recent updates i downloaded today? Putting compiz --version in a terminal still fixes the issue instantly. However putting that in a startup session doesn't seem to have caught it this time.

---

