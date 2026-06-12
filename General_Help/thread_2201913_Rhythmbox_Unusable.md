---
title: "Rhythmbox Unusable"
date: 2014-01-26
forum: General Help
---

### Post by jamesisin on 2014-01-26
I mostly use Clementine but I want to be able to support Rhythmbox since it's still the default player in Ubuntu.

With a large collection of (86K of) FLAC files located on a network drive (via SMB), Rb is unable to do any meaningful work.  It opens but shifts between being grayed out and not and runs one CPU core at 100% as long as it is open.  I believe it is communicating across the network during this period as I see about a 7Mb pulse in the System Monitor about every second or two.  I can leave it in this state indefinitely.

By comparison Clementine uses one or two per cent of one core *while playing*.

Any suggestions?

(This is on a 13.10 machine.)

---

### Post by jamesisin on 2014-02-09
Anybody have any insight or troubleshooting suggestions?

---

### Post by tgalati4 on 2014-02-10
How did you create your music library?  If it is simply a uPnP music share, then rhythmbox will read and populate the music share on the fly.  That requires reading every track and getting the ID3 info.  How large is your music collection in gigabytes?  If you have 10k mp3's with a similar network share, the performance is OK.  

Rhythmbox works best if the music and the database is created locally on a fast disk drive.  If you want a music server, then set up mpd or some other network music server.

---

### Post by jamesisin on 2014-03-29
The library is created automatically by Rhythmbox because I create a shortcut to the share (located at /media/share) in the Music folder where Rb expects music to be located.

The share is using the SMB protocol currently (probably a slightly older version since it's Ubu 10.04) though I am looking into creating an NFS share as well.

The size of the collection (as mentioned above) is substantial.  Rb does eventually complete its initial scan of the collection.  Subsequent scans (verifications of known file paths) take longer than expected (longer than Rb on a 10.04 machine).

Using MPD or other streaming service is a poor option, and this *was* working using Rb.  At this point I suspect the problem is partially with versions of SMB (because of activity I see when using Clementine or VLC or...) between 10.04 and 13.10, but at least most of the problem is clearly Rb.

And since Rb (on 12.04 +) is totally unusable it would be nice sort out why.

---

