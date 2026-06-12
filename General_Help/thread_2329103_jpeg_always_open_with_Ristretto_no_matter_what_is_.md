---
title: "jpeg always open with Ristretto no matter what is set as default program"
date: 2016-06-28
forum: General Help
---

### Post by kazakore on 2016-06-28
If I change the default program to open jpeg files from Ristretto to my prefered simple editor of Shotwell a double-click still opens them with Risteretto. Same if I try changing the default to a different program such as RawTherapee, it always opens with Risteretto.

If you right-click it shows Risteretto as being the program associated with it (Open with "Risterettor Image Viewer" being top line) but if you go into Properties you can see a different program has been selected.

Going to Settings > System > MIME Type Editor shows the default as being User Set and being my chosen program.

Changing default for every other file type I have tried has worked as expected.

Any idea what the issue may be here and how to fix it?

---

### Post by Bucky Ball on 2016-06-28
Can you right click and 'open with', choose Ristretto and tick the little box at the bottom of that window that says 'use this as default in future' and does that make any difference?

---

### Post by kazakore on 2016-06-28
> **Bucky Ball said:**
> Can you right click and 'open with', choose Ristretto and tick the little box at the bottom of that window that says 'use this as default in future' and does that make any difference?

I've done through the Preferences window in Thunar and as I said I have changed it to multiple programs in there to no avail and also checked it claims to be set as Shotwell as I want in the MIME settings but even though everything shows that it should open with Shotwell it still uses Ristretto.

But just to double-check I tested opening it via Open With and having the Set Default program checkbox set it made no difference.


EDIT: Actually it isn't only jpegs which are affected. .png files always open with Shotwell no matter what is set as the default program. I hadn't noticed this as it is my preferred program but I thought I would try changing it.

Changing audio and video media files (wav, ogg, mp3, m3u, avi, mp4 etc) has all correctly changed and opens with whichever program I set as default. I don't know why image files appear to act strange.


EDIT2: I'm guessing it's related to this issue and I'm seeing it due to the fact I could not bear to use the new Thunar with missing functionality from the old versions so I downgraded to the one from Trusty. libglib2.0-0 v2.48 so newer than the v2.41 which causes issues.
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1382977](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1382977)


Seems it affects 14.04.4 as well so they really need to backport the patch that fixed it for Utopic.
[https://lists.ubuntu.com/archives/xubuntu-users/2016-April/009233.html](https://lists.ubuntu.com/archives/xubuntu-users/2016-April/009233.html)

---

### Post by Bucky Ball on 2016-06-28
I don't use Shotwell, but ...

In the Shotwell preferences, is there an option somewhere to 'make Shotwell default ...'? Just a shot(well) in the dark, but you never know. That could be at the root of the issue. Then again, as it's fairly obvious, might be the first place you looked.

---

### Post by kazakore on 2016-06-28
> **Bucky Ball said:**
> I don't use Shotwell, but ...

In the Shotwell preferences, is there an option somewhere to 'make Shotwell default ...'? Just a shot(well) in the dark, but you never know. That could be at the root of the issue. Then again, as it's fairly obvious, might be the first place you looked.


No. I checked Risteretto for that option (which is the program I don't want to be opening them all the time) and the fact that jpeg and png both always start with a different programs point very strongly against it being something weird like that.

See the links in my last post. Pretty sure it has to be related to that bug and according to the post on the mail list it sounds like it probably affects all 14.04.4 users.

---

### Post by Bucky Ball on 2016-06-28
I'll check on my 14.04 LTS install later, but you're the first I've seen here with this issue and I don't remember having it on my three 14.04 installs previously. 

Still, that doesn't mean a lot on the bigger picture.

---

### Post by kazakore on 2016-06-28
> **Bucky Ball said:**
> I'll check on my 14.04 LTS install later, but you're the first I've seen here with this issue and I don't remember having it on my three 14.04 installs previously. 

Still, that doesn't mean a lot on the bigger picture.

Note I said 14.04.4 not just 14.04. I never had it on 14.04. Just running upgrade or even dist-upgrade doesn't always update all the libraries and core components compared to downloading the new point release (I was surprised when I found that out on either the second or third point release of 14.04) so even a fully uptodate system might still be using an old enough version of glib as they didn't risk to update it otherwise.

And just checked and it does affect more than just my image files. I have a feeling it might be allowing me to change it once from what it is set the very first time by the system but subsequent changes are being ignore but I'm not quite sure...

---

### Post by sudodus on 2016-06-28
If you have problems with ***thunar***, I suggest that you try some other file browsers, for example

***pcmanfm*** (light - I use it)
***nautilus*** (used to be the best, but changed in a way that some people don't like - I use it)
***caja*** (the MATE fork of nautilus - can be a good alternative)

I use file browsers, but most of the time I use ***terminal windows and command lines***. That way I have full control of what tool to use, for example

```
shotwell file.jpg
ristretto file.jpg
eog file.jpg
gimp file.jpg
pcmanfm file.jpg

#or to start the browser in the current directory represented by 'dot'
pcmanfm .

# alias for nautilus to keep it from grabbing the desktop
alias nautilus='nautilus --no-desktop'

```

---

### Post by kazakore on 2016-06-29
I've tried quite a few file managers in the past and Thunar was always the closest to being ideal. PCManFM I found to be second then. Maybe I should give some a try again. The bulk renaming tools are something I use in Thunar a lot, including the ability to do it from audio tags, so it would need to be able to do that to tempt me. Most likely I'll put up with the bugs I have with this version of Thunar (or see if I can patch it somehow...)

---

