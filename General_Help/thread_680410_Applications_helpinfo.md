---
title: "Applications help/info"
date: 2008-01-27
forum: General Help
---

### Post by Wan_Lin on 2008-01-27
Hi, I'm really starting to get into Ubuntu, and am gonna try using it more and more and eventually (hopefully) run it exclusively. Hence, I'm looking to get into some applications so I can just do normal computer stuff. I have some questions!

Email Client:
I've configured Evolution, and it's working great with my gmail and school email, but my one problem with it is that it doesn't go to the system tray when I click close or minimize. Is there a way to do this? I don't really like seeing the window open on the taskbar. Also, I am assuming that Evolution is a GNOME application (I can't really tell the difference between GNOME and KDE in applications), is Thunderbird GNOME, and can Thunderbird shrink into the system tray? I kinda wanna stick with GNOME stuff.

Music Player:
I have downloaded Banshee, and it's pretty cool. I got that since it is GNOME (again, I assume) and can also sync with an iPod. Is this true?

Video:
I'm using VLC, I don't really have any questions with that.

VOIP:
I used Skype once when I used Windows XP, and it was cool because I could call land-lines in the US for free without creating an account. Is there a good GNOME voip application that can call land lines for free without an account? If an account is needed, is there at least a free account? (I have a cell phone, I don't really NEED voip, just would like to use it, but not unless it's free)

Instant Messaging:
Is there a free IM client that has video chat capabilities for Ubuntu? Again, preferably GNOME. I am using pidgin now but it has no video support.

Any advice would be greatly appreciated! Thanks!

---

### Post by accatagon on 2008-01-28
VOIP: You can technically use Skype with ubuntu, they have a skype .debi package on their website, but it is not free software and not in the repositories. As far as I know, there is no VOIP software through Linux that offers calls to the US and canada(landlines) for free. Ekiga softphone is good if you want to use SIP, which is an open standard and thus supported by multiple packages (SIP is used by Vonage and a lot of businesses), unlike Skype. Another option is Wengophone, which is supported by some company in France, and also uses SIP. If you want to call people in the US and Canada, it was around 2.4 cents a minute with Wengophone last time I checked. It costs money for them to connect to regular telephone lines, and as far as I know, none of the providers that use open protocols have the extra money to throw into providing calls for free. You need an account to do any calling with any VoIP service, but the account is free on ekiga and wengophone at least, unless you want to call landlines.

IM: Use Pidgin. It supports MSN, yahoo, IRC, XMPP (googletalk), MySpace IM, AIM, and several protocols you've never heard of. It doesn't support the latest and greatest features of MSN. . . yet, but it works for basic messages.
EDIT: *cough* didn't see the "video chat". Unfortunately, the protocols are closed, so there is really no easy way to support video chat through one of the aforementioned reverse-engineered protocols.  If you can convince your friends to use an open protocol like SIP through ekiga or wengophone&#65288;wengophone supports most types of IM as well), you can do video chat, but otherwise it would take excessively large amounts of effort to reverse-engineer the video and voice-chat of established IM protocols.

---

### Post by bodhi.zazen on 2008-01-28
See if this link helps : [http://linuxappfinder.com/windows](http://linuxappfinder.com/windows)

---

