---
title: "KDE, GNOME &amp; a little problem of mine :)"
date: 2008-03-29
forum: General Help
---

### Post by Saisin-Tae on 2008-03-29
Well, basically this is my situation:

I've installed Kubuntu Gutsy (some time ago) on my Asus F3Se laptop. I won't say everything worked fine, but somehow I've managed to get most of the things I needed working. Then, I installed gnome-desktop through command line. After some tweaking everything worked fine. Then, one day after I rebooted the system, 'cause something didn't seem right, I found myself unable to use <Super> + somethin' keyboard shortcuts, and even a problem I thought I solved some time ago: Shift + Backspace = X server restart, popped up again. I use compiz, so shortcuts making use of the <Super> key combinations are a necessity, considering how much I hate using more than two keys for shortcuts, so this really bugs me. This applies to several other things, like sound control shortcuts making use of fn + key combinations ect. The thing I wonder about the most would be, why the hell everything works fine under Gnome, but when I switch back to KDE, everything f..ks up again. Temporary solution to this might be, that when I start Movie Player (Totem) under KDE, all the things that refused to work miraculously start functioning again. Dunno what the problem might be, but considering the fact that Totem is a Gnome application, I thought that some Gnome libraries being loaded in KDE while using Totem might be the cause why it starts working all of a sudden. I know that the simplest solution to this might be switching from KDE to GNOME for good, but there are just too many things in KDE that I'm not willing to give up for GNOME. 

Well then, now to the possible causes of this mess. Several days ago, while desperately trying to fix something minor that bugged me at the time, I found some howto on the net that said that I should chmod /var/ directory to 755 (which didn't seem any different to what was set at the time) so I happily switched to su - and happily chmod-ed the whole /var/ to 755, only to find myself in the situation described above after I rebooted the system. Dunno what the cause si, but this is the only thing I remember doing that might have affected something else that network settings at the time. Anyways I've tried almost everything described in other howto-s. I tried changing the keyboard layouts, I tried changing the Xkb options for Alt and Win key, I tried changing the xorg.conf to some extent but the only thing I achieved was that the problem worsened. 

Anyways, I'm waiting for someone to come and save me (not literally of course lol :D), otherwise, I'd have to reinstall the system AGAIN which would be a lot of trouble considering all the work I've done on making it work...

---

