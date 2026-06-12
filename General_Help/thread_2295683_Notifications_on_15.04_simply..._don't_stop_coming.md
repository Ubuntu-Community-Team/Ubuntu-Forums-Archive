---
title: "Notifications on 15.04 simply... don't stop coming."
date: 2015-09-20
forum: General Help
---

### Post by Roasted on 2015-09-20
About 4 hours ago my laptop was on, but the screen was blank due to my power settings. I moved the cursor and saw an IRC notification a friend sent me. 

It came up a few times while I was using the laptop, thought that was interesting, but went on with my home renovation while the laptop played music.

Here we are 4 hours later, and despite me giving IRC attention, closing Quassel and re-opening Quassel, the notifications simply keep coming up. The same message - one after another after another.

Anybody else seeing this? I know I can kill notify-osd, but uh... I shouldn't have to. ;)

Thoughts?

---

### Post by Roasted on 2015-09-21
I'm on my 15.04 desktop, totally different system than what I posted about originally (laptop), and I'm still getting weird notification behavior. Someone in IRC (using the Quassel IRC client) highlighted me despite the fact I was in the channel talking. It's been a half hour and their notification is literally staying put on my screen no matter how many times I click on the IRC window to dismiss it.

Is anybody else having weirdness with notifications on 15.04? This is getting a little frustrating...

EDIT - I just had it happen again. Something dawned on me, though. I only recall these notifications only hanging around when using Quassel. I wonder if it's something specific to Quassel...

---

### Post by Portaro on 2015-09-21
You can search in your quassel the area to the notifications options and clear it, if the program dont have this option you can edit this manually on the work path of program, but you need to search on the documentation of the program to see what is the file that do this operation.

---

### Post by Roasted on 2015-09-21
Thanks for your response. :) I hate to clear the actual notification preferences, though. I do see the option to do so within Quassel. I rely on the notifications and in an effort to find a fix I'd rather keep them around. Notify-osd is hardly that customizable, but I keep suspecting there might be something I can do, somewhere, to get them to play nice. As I said I'm only seeing them with Quassel (so far), but I'm not 100% convinced it's a Quassel specific issue -- more like 98% sure. :P

More than anything I'm just curious if any other users are running into this. Anybody out there running 15.04 with Unity and Quassel Client?

EDIT - Well look what I found. :(

[https://bugs.launchpad.net/ubuntu/+source/quassel/+bug/1442005](https://bugs.launchpad.net/ubuntu/+source/quassel/+bug/1442005)

---

### Post by Roasted on 2015-09-30
Looks like it's not just Quassel. On a totally different freshly installed 15.04 box my kdenlive notification comes up, but then it never disappears until I close down kdenlive. Awesome.

I distinctly remember there being a debate about notifications, that they should have an X to click-and-cancel them. Really wishing I had some notifications I could, you know, close. :(

---

### Post by Roasted on 2015-10-18
Anybody else seeing this? I'm seeing it constantly with kdenlive. Very easy to replicate there just by rendering a video to instigate the notification. Still seeing the same thing on quassel, but quassel, at times, admittedly works fine. I've duplicated this on multiple systems. Surely I can't be the only one?

---

