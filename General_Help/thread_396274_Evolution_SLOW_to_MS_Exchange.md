---
title: "Evolution SLOW to MS Exchange"
date: 2007-03-29
forum: General Help
---

### Post by sanicki on 2007-03-29
Trying to roll out Ubuntu desktops at work. Right now using OWA, want to use Evolution. However it takes upwards of 5 minutes to launch against some of my users' mailboxes.

I've tried downloading certain folders for offline use, as well as downloading none. I'll admit some of my users have ungodly large boxes (and use it against advice as a filing system with sub-sub-sub folders). Sometimes they'll be connecting on broadband, other times using wireless aircards (if that's even going to be possible with Evolution's speed. May have to keep OWA as webmail for those circumstances.)

Can anyone recommend steps for optimizing Evolution for Exchange. I don't need to outperform OWA, just match it at least. I've searched but cannot find anything besides the basic configuration.

Thanks in advance.

---

### Post by dcstar on 2007-03-29
> **sanicki said:**
> 
.........
Can anyone recommend steps for optimizing Evolution for Exchange. I don't need to outperform OWA, just match it at least. I've searched but cannot find anything besides the basic configuration.

Thanks in advance.

If Ubuntu also seems slow just on normal network access, do a forum search for "disable ipv6" and try those solutions - it may help with this.

---

### Post by rundgren on 2007-04-02
I think the root problem is that it's currently impossible for evolution (or any other non-MS client) to talk MAPI, the native Exchange protocol.
Actually, evolution-exchange plugin is communicationg over WebDAV which is the OWA protocol...
This guy at [www.omesc.com](www.omesc.com) (also on this forum, search for "Brutus" which is the project name) tries to solve this by making a translator between MAPI and a plugin for Evolution. It's in beta, and I've been trying to make it work with no success.. But you might have better luck, of course.

I'm in sort of the same situation: I work at a 60/40 windows/linux shop and we have Exchange for our mailserver (why? nobody knows...). So a lot of us are eager to find a better and faster way to read our mail - so far Brutus is the only promising project I've found..

Actually I'm quite surprised by the lack of attention to this serious hurdle in the way of widespread Linux-use on the corporate desktop. It's currently impossible to use the by far most common mailserver with linux if you have any more than the most basic needs.

PS: the IPv6 thing helps somewhat on network speeds, but I've found I earned the most in perceived internet-speed by tuning Firefox (Swiftfox) (or you could just use Opera :-)

---

### Post by jzimmerman on 2007-04-29
I have got the same problem with Evolution being unbearably slow.

Entourage, which also connects through WebDAV has no problem though.  The problem is on Evolution's end.  

There is a bug filed in Launchpad.

---

### Post by Sir Rodness on 2008-07-19
I've been having this same problem as well (in Hardy Heron 8.04) when using ms exchange in evolution so I decided to mess around a bit. Does anyone know what the **"Exchange Operations**" plugin does? I have no idea but I figure by the name it was related to how exchange works so I figure what's the worst that could happen if I turned it off since evolution's exchange slow start up and sync already had me annoyed. 
...I turned it off
...restarted evolution 
...and there an immediate and **drastic** increase in startup and sync speed for me. Not sure if anyone else will see these kind of improvements, but I have to ask...**What exactly does that plugin do anyway**?

---

