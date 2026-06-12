---
title: "Gaim not showing all buddy icons"
date: 2007-04-17
forum: General Help
---

### Post by mohshami on 2007-04-17
Hi guys,

Recently I started noticing some of my contacts don't have any buddy icons/display pictures. I thought they just stopped using them till I logged in to a client's PC and saw he had a display picture set but it didn't show up on my side.

I'm using gaim2 beta 6, from the debuntu repository.

Thanks

---

### Post by Brucevdk on 2007-04-17
Are we talking about the contact list here or the individual windows? 

It's not disabled in the preferences is it? Tools -> Preferences -> Conversations -> Show buddy icons.

---

### Post by mohshami on 2007-04-17
> **Brucevdk said:**
> Are we talking about the contact list here or the individual windows? 

It's not disabled in the preferences is it? Tools -> Preferences -> Conversations -> Show buddy icons.

Thanks for your prompt response :) 

Both contact list and individual windows. They are not disabled, just checked. I have the icons for some of my contacts, bot not all of them.

Sorry that I forgot to mention that was on msn only.

---

### Post by Brucevdk on 2007-04-17
Sorry for my previous response, I installed beta 6 from the debuntu repository and verified this problem. However, if I recall correctly the problem was also present in previous versions.

I can verify that this is a bug, see [[Gaim-bugs] [ gaim-Bugs-1675659 ] Gaim buddy icons problem msn]("http://66.102.9.104/search?q=cache:acz76T-FIUwJ:www.mail-archive.com/gaim-bugs%40lists.sourceforge.net/msg01067.html+1675659+gaim&hl=en&client=firefox-a&strip=1") (Google cache). It seems a patch has been submitted, see [http://developer.pidgin.im/ticket/113]("http://developer.pidgin.im/ticket/113"). If it's accepted, It'll most likely be integrated into the next release.

Quoting from the ticket:
> 
Newer Live Messenger -versions doesn't always send SHA1C-field in msnobj's and so Pidgin discards them. This new version of patch uses sha1c as icon checksum if it exists, otherwise it falls back to using sha1d, as datallah suggested. Are they unique enough then to be mixed like this?


---

### Post by mohshami on 2007-04-18
Thanks a million, I downloaded the latest snapshot of pidgin, patched, complied, and now everything is working properly.

Thanks again :)

---

