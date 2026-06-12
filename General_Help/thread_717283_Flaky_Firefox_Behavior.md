---
title: "Flaky Firefox Behavior"
date: 2008-03-06
forum: General Help
---

### Post by cj100570 on 2008-03-06
Over the past week I've been having problems surfing the net. Pages that once loaded in 2 to 5 seconds suddenly started taking up to a minute to load if they even loaded at all. I called my ISP to see if there were any issues and even had them reset my connection. Nothing resolved the issue. On a whim I started using Opera and the sluggishness isn't apparent. I even tried opening the same page on both and it took Firefox over a minute to open a page that Opera opened in about 3 seconds. Any ideas as to what could be happening?

---

### Post by {BzF}~JOKesTER on 2008-03-06
This Worked For Me - {However I Don't Know How You Whould Have Noticed This Just Now - Maybe An Update??!!}

In The Firefox Address Bar Type:

about:config

Right - Click Anywhere In The Screen And Select "New" And Than "String"

In The "Enter Preference Name" Box Type:

network.dns.disableIPv6

Hit "Ok"

In The "String Value" Box Type

true

Hit Ok

Now Restart Your Computer.

Now Using Firefox Should Be Much Faster For You!!!

Happy Browsing!!:)

---

### Post by cj100570 on 2008-03-09
Unfortunately that didn't work. I even tried reinstalling the whole system and Firefox still loads like molasses. Out of 3 browsers on my system Firefox is the only one that has the issue. I vaguely recall seeing an update for Firefox a few days ago and I wonder if that update is at the root of my issue. I even tried an Ubuntu live cd and didn't experience the issue.

---

### Post by yaknowwat on 2008-03-09
Go through your addons and disable some of them.
Firefox support for XUL addons always tends to be its greatest advantages and greatest weakness.
 For my friend last night firefox wouldn't start because he had a bad addon or something i told him to start in safe-mode and get rid of some of his addons and he got it working normal again.

If that doesn't work then pop open Synaptic Package Manager 
search for firefox
right click and mark for reinstall.

---

### Post by cj100570 on 2008-03-10
> **yaknowwat said:**
> Go through your addons and disable some of them.
Firefox support for XUL addons always tends to be its greatest advantages and greatest weakness.
 For my friend last night firefox wouldn't start because he had a bad addon or something i told him to start in safe-mode and get rid of some of his addons and he got it working normal again.

If that doesn't work then pop open Synaptic Package Manager 
search for firefox
right click and mark for reinstall.

That didn't work either. I even reinstalled my system. It worked for a few hours and then started exhibiting the same behavior. At this point I'm left with it being due to 1 of the updates that I installed. Unfortunately I'm gonna have to give Ubuntu the boot since non of the other browsers satisfy the needs I have.

---

