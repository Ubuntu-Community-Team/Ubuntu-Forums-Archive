---
title: "BitTorrent Error"
date: 2006-10-28
forum: General Help
---

### Post by Noah0504 on 2006-10-28
Under Edgy I am not able to run two instances of BitTorrent.  When I try to start another download I receive an error: "address already in use, couldn't listen"

I've never had this problem before under previous versions of Ubuntu.

---

### Post by Peter76 on 2006-10-28
Hi, this is a bug in Edgy, is reported, but not bothered to look up the number...
Anyway, to solve:

Open the gconf-editor, and go to apps->gnome-btdownload->settings.
There you'll see that the min_port and max_port have both the same value; change max_port to something higher than 6881 and it works fine again; I have mine set to 6999. Good luck

---

### Post by Noah0504 on 2006-10-28
> **Peter76 said:**
> Hi, this is a bug in Edgy, is reported, but not bothered to look up the number...
Anyway, to solve:

Open the gconf-editor, and go to apps->gnome-btdownload->settings.
There you'll see that the min_port and max_port have both the same value; change max_port to something higher than 6881 and it works fine again; I have mine set to 6999. Good luck
Thank you a million!  :-D

---

### Post by adamatari on 2006-11-18
I tried to do as you suggested but under apps->gnome-btdownload->settings the min and max port weren't even listed.  Perhaps it's because I uninstalled bittorrent but I do have BitTornado on there - in any case, am I missing something?  Is there another way to fix it?

---

### Post by CocoAUS on 2007-05-25
You removed BitTorrent?  That's the program that is used to handle torrents, whether you have a special client installed or not.  The gconf-editor method only handles Gnome apps, so it won't handle BitTornado.  I don't use BitTornado, but I imagine there is a way to open more ports in the programs settings somewhere.  You might also have to open ports on your router (port forwarding) to get it to work.  At any rate, I suggest just using the Gnome client, since it has the least overhead and is quite efficient.

---

### Post by aicrono on 2007-05-26
I'd try looking around the settings for BitTornado for the min or max, or at least something where you can set a range of ports to use for torrents. I personally like to use clients that support more than one torrent at a time with out having to open up another window. You could give Azureus or Ktorrent a go, I haven't had a problem with either of those myself.

---

