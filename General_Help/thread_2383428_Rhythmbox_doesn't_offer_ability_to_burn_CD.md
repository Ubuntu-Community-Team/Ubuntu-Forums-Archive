---
title: "Rhythmbox doesn't offer ability to burn CD"
date: 2018-01-25
forum: General Help
---

### Post by carefulnottoolong12345 on 2018-01-25
Hi I'd like to burn a CD with Rhythmbox 3.3 on Ubuntu 16.04.

When I launch Rhythmbox and choose Tools -> Plugins, the list does not contain Audio CD Creator or anything like that. Does that ship with Rhythmbox or do I have to install it separately? The internet sure seems to imply that Rhythmbox simply always has that plugin, but I don't.

Then I go to a playlist and try to find Burn Disc in the Playlist menu, but there is nothing like that.

The internet has lots of directions (often wrong) for how to do this but none of them say anything about that plugin being missing.

---

### Post by Dennis N on 2018-01-25
There is a plugin named "rhythmbox-plugin-cdrecorder". On my Ubuntu 17.10, it's not installed by default with Rhythmbox, so perhaps your 16.04 system may not have it either. I would install that and see if that solves the problem.

---

### Post by carefulnottoolong12345 on 2018-01-29
Dennis, thank you, that did it:

sudo apt-get install [COLOR=#000000]rhythmbox-plugin-cdrecorder

After that I have Audio CD Recorder listed in my Plugins and Create Audio CD in my Playlist menu.

I sure wish the instructions for how to burn discs using Rhythmbox included this essential tidbit of information. How else am I supposed to know what package to install? Cheers, Dennia.[/COLOR]

---

