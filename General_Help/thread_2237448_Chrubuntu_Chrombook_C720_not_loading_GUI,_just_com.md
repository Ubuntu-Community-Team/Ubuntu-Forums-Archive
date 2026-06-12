---
title: "Chrubuntu Chrombook C720 not loading GUI, just command prompt."
date: 2014-08-01
forum: General Help
---

### Post by brant4 on 2014-08-01
Hello everyone! Really excited to start my Ubuntu journey but I ran into a problem almost immediately.

When I type in the username 'user' and password (which doesn't actually type anything) 'user' I'm just given a command prompt user@chrubuntu:'$

I've spent about an hour googling and scouring random threads looking for an answer, but so far I have nothing.

Using Ubuntu 14.04.1 LTS chrubuntu tty1

I'm under the impression that I should now be logging into a GUI, not a continuation of the command prompt. Any ideas?

Thanks!

So I tried [COLOR=#666666][FONT=Tahoma]sudo apt-get install ubuntu-desktop[/FONT][/COLOR] which gave me:

E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Actually that error was from apt-get update.

install ubuntu-desktop gave me:
E: failed to fetch (website) Could not resolve 'archive.ubuntu.com'

---

### Post by TheFu on 2014-08-02
I suspect you are in developer mode under ChromeOS still.
[http://jeanlouisnguyen.blogspot.com/2014/01/guide-how-to-install-elementary-os-on.html](http://jeanlouisnguyen.blogspot.com/2014/01/guide-how-to-install-elementary-os-on.html) is how I got Ubuntu (not crubuntu) installed on my C720.  Also, I've wiped ChromeOS - only booted into it once - long enough to get into legacy BIOS mode.

---

