---
title: "Guest mode doesnt load properly"
date: 2018-09-05
forum: General Help
---

### Post by webmiester on 2018-09-05
Hi everyone,

I setup a guest mode and it works quite well except for a few quirks:
I set it up so that it will replicate a special user account.  So I used the 
"sudo ln -s /home/guest-prefs /etc/guest-session/skel" command.

I placed a bash script which the startup application will load it says:

#! /bin/bash
sleep 40
xmodmap -e "clear Control"
chromium

Now in the special user account, this works to remove Control key, and it works everytime.  In the guest mode the clear Control command rarely works, and most of the time it doesnt

Could this be a bug in xmodmap?

I tried putting another bash script in the startup, this time with a longer sleep time then clear control, but it still inconsistent.
Why is this?

Im using 16.04 Mate by the way

Thanks

---

