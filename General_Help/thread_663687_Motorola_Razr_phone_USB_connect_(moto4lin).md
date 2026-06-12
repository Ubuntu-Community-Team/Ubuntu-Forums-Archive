---
title: "Motorola Razr phone USB connect (moto4lin)"
date: 2008-01-10
forum: General Help
---

### Post by atomicpc on 2008-01-10
I installed moto4lin. I changed the settings in the preferences. I have my phone plugged in and click CONNECT:

[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[info] Phone pluged as P2K
[info] Phone connected as P2K
[error] Unable to get phone model
[error] Unable to get drive name
[error] Unable to get file count
[error] Unable to get drive name

It says connected but when I go to the file manager and click update it says:

Getting file list
[info] Found drives: [ ?8J· ÁV· ]
[info] Search request: [?8J·/|*]
[debug] Unable to execute search request
[info] Search request: [ÁV· /|*]
[debug] Unable to execute search request
Complete

I'm not sure what's going on. Any help would be appreciated.

---

### Post by atomicpc on 2008-01-10
I should also note that I did this with "sudo moto4lin" and with moto4lin it pretty much says the same thing.

---

### Post by Wildboar on 2008-01-19
I'm trying to do the same thing but a quick look at the description on Moto4lin shows that it's intended for different models.  Huge differences in how they talk through the  USB.

I tried to download Floola but get.deb.org is taking their time emailing me a signup link.  I presume it's not automated and they're visiting family over the holiday so no hard feelings. 

Gammu only supports Moto through IR and that's about all I've found so far through forums.

Now that we know why it didn't work for him, is there a 9 pound head out there that knows how to download pictures, upload ringtones, sync calendar and contacts etc...  I'm not yet married to clients since I'm still working in XP and playing with Gutsy.

---

### Post by Wildboar on 2008-01-19
Bite my tongue and check out the link below.  Don't mess with the earlier posts, they don't apply to Gutsy.  
  I didn't look close enough and was putting 4902 for both for AT and P2K.  Once I figured that out I accidentally realized that shutting down the phone after reassigning it to P2K is the missing step.  I guess I'm the 9 pound head now.....  Good luck.

[http://veinhammer.wordpress.com/2006/05/18/motorola-razr-ubuntu-linux/#comment-508](http://veinhammer.wordpress.com/2006/05/18/motorola-razr-ubuntu-linux/#comment-508)

Doesn't sync and such but I figure I can live with file transfers and figure out how to edit them on the desktop.

---

