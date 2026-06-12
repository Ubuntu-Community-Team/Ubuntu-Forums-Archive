---
title: "[SOLVED] FTP/samba for sharing/serving music to Vista Media Centre?"
date: 2008-01-15
forum: General Help
---

### Post by njparton on 2008-01-15
Well, I've been doing some research this morning into how to improve how my ubuntu based NAS device shares my 20GB mp3 music library with Vista Media Centre which runs the HTPC in my living room (via a gigabit LAN).

I store my music in an iTunes library on the NAS which is current shared with samba. I've mapped this as a drive in Vista and added it to the media centre watch list.

This works fine for a week or so, after which things go awry and I start getting duplicate or missing songs.  I then need to go into Windows Media Player and manually delete and re-add the library. Really annoying.

I started my research this morning looking for a music server I could run in ubnutu to serve my music files to Vista Media Centre.  However, whilst there are lots of media servers out there, none would allow me to browse and select songs in VMC it would seem (?).  This appears to be the stumbling block for a media server(the need to select and browse songs via a browser)?

The samba options are giving me problems so I was thinking of trying ftp instead, but that's still just a file sharing method.

I manage my music library via iTunes installed on a third (Vista) PC so my HTPC only needs read-only access.

Any ideas for the approach I should take?

---

### Post by jd65pl on 2008-01-15
I don't know if windows MCE supports daap, if it does you could use firefly, see [this]("http://jamiedumbill.com/index.php?page=28") on how to do it.

---

### Post by njparton on 2008-01-15
Great thanks, I'll give that a whirl tonight and post back.

I came across so many posts on the web this morning but I don't think I came across this one.

The ability to browse and select via Vista Media Centre is the crux of my problem.  As far as I understand it it's just Windows Media Player with a fancy front end.

---

### Post by njparton on 2008-01-16
mt-daap is a nightmare.  I can't get the version in the repos or the latest build to work... :(

---

### Post by njparton on 2008-01-16
Got it working but had to use webmin to configure iptables...

---

### Post by jd65pl on 2008-01-17
Glad you got it working!

---

### Post by njparton on 2008-01-17
Unfortunately it's all for nothing as for serving to Windows Media Player the correct protocol appears to be upnp not daap...  I don't know why I didn't pick up on that earlier.

Nevermind, there are plenty of upnp based servers in the repos ](*,)

---

